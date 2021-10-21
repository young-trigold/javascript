**目录：**

- [18. BOM](#18-bom)
  - [18.1. window](#181-window)
    - [18.1.1. window 与 Gobal](#1811-window-与-gobal)
    - [18.1.2. 窗口关系](#1812-窗口关系)
    - [18.1.3. 导航与打开新窗口](#1813-导航与打开新窗口)
    - [18.1.4. 窗口位置和像素比](#1814-窗口位置和像素比)
    - [18.1.5. 窗口大小](#1815-窗口大小)
    - [18.1.6. 视口位置](#1816-视口位置)
    - [18.1.7. 定时器](#1817-定时器)
    - [18.1.8. 系统对话框](#1818-系统对话框)
  - [18.2. location](#182-location)
    - [18.2.1. 查询字符串](#1821-查询字符串)
    - [18.2.2. 操作地址](#1822-操作地址)
  - [18.3. navigator](#183-navigator)
    - [18.3.1. 检测插件](#1831-检测插件)
    - [18.3.2. 注册处理程序](#1832-注册处理程序)
  - [18.4. screen](#184-screen)
  - [18.5. history](#185-history)
    - [18.5.1. 导航](#1851-导航)
    - [18.5.2. 历史状态管理](#1852-历史状态管理)

# 18. BOM

本章内容

- 理解和使用 window 对象操纵窗口
- 使用 navigator 对象了解浏览器
- 通过 history 对象操作浏览器历史

虽然 ECMAScript 把浏览器对象模型（BOM，Browser Object Model）描述为 JavaScript 的核心，但实际上 BOM 是使用 JavaScript 开发 Web 应用程序的核心。BOM 提供了与网页无关的浏览器功能对象。多年来，BOM 是在缺乏规范的背景下发展起来的，因此既充满乐趣又问题多多。毕竟，浏览器开发商都按照自己的意愿来为它添砖加瓦。最终，浏览器实现之间共通的部分成为了事实标准，为 Web 开发提供了浏览器间互操作的基础。HTML5 规范中有一部分涵盖了 BOM 的主要内容，因为 W3C 希望将 JavaScript 在浏览器中最基础的部分标准化。

## 18.1. window

BOM 的核心是 window 对象，表示浏览器的实例。window 对象在浏览器中有两重身份，一个是 ECMAScript 中的 Global 对象，另一个就是浏览器窗口的 JavaScript 接口。这意味着网页中定义的所有对象、变量和函数都以 window 作为其 Global 对象，都可以访问其上定义的 parseInt()等全局方法。

注意 因为 window 对象的属性在全局作用域中有效，所以很多浏览器 API 及相关构造函数都以 window 对象属性的形式暴露出来。这些 API 将在全书各章中介绍，特别是第 20 章。另外，由于实现不同，某些 window 对象的属性在不同浏览器间可能差异很大。本章不会介绍已经废弃的、非标准化或特定于浏览器的 window 属性。

### 18.1.1. window 与 Gobal

因为 window 对象被复用为 ECMAScript 的 Global 对象，所以通过 var 声明的所有全局变量和函数都会变成 window 对象的属性和方法。比如：

```javascript
var age = 29;
var sayAge = () => alert(this.age);
alert(window.age); // 29
sayAge(); // 29
window.sayAge(); // 29
```

这里，变量 age 和函数 sayAge()被定义在全局作用域中，它们自动成为了 window 对象的成员。因此，变量 age 可以通过 window.age 来访问，而函数 sayAge()也可以通过 window.sayAge()来访问。因为 sayAge()存在于全局作用域，this.age 映射到 window.age，所以就可以显示正确的结果了。

如果在这里使用 let 或 const 替代 var，则不会把变量添加给全局对象：

```javascript
let age = 29;
const sayAge = () => alert(this.age);
alert(window.age); // undefined
sayAge(); // undefined
window.sayAge(); // TypeError: window.sayAge is not a function
```

另外，访问未声明的变量会抛出错误，但是可以在 window 对象上查询是否存在可能未声明的变量。比如：

```javascript
// 这会导致抛出错误，因为oldValue 没有声明
var newValue = oldValue;
// 这不会抛出错误，因为这里是属性查询
// newValue 会被设置为undefined
var newValue = window.oldValue;
```

记住，JavaScript 中有很多对象都暴露在全局作用域中，比如 location 和 navigator（本章后面都会讨论），因而它们也是 window 对象的属性。

### 18.1.2. 窗口关系

top 对象始终指向最上层（最外层）窗口，即浏览器窗口本身。而 parent 对象则始终指向当前窗口的父窗口。如果当前窗口是最上层窗口，则 parent 等于 top（都等于 window）。最上层的 window 如果不是通过 window.open()打开的，那么其 name 属性就不会包含值，本章后面会讨论。

还有一个 self 对象，它是终极 window 属性，始终会指向 window。实际上，self 和 window 就是同一个对象。之所以还要暴露 self，就是为了和 top、parent 保持一致。

这些属性都是 window 对象的属性，因此访问 window.parent、window.top 和 window.self 都可以。这意味着可以把访问多个窗口的 window 对象串联起来，比如 window.parent.parent。

### 18.1.3. 导航与打开新窗口

window.open()方法可以用于导航到指定 URL，也可以用于打开新浏览器窗口。这个方法接收 4 个参数：要加载的 URL、目标窗口、特性字符串和表示新窗口在浏览器历史记录中是否替代当前加载页面的布尔值。通常，调用这个方法时只传前 3 个参数，最后一个参数只有在不打开新窗口时才会使用。

如果 window.open()的第二个参数是一个已经存在的窗口或窗格（frame）的名字，则会在对应的窗口或窗格中打开 URL。下面是一个例子：

```javascript
// 与<a href='http://www.google.com' target='topFrame'/>相同
window.open('http://www.google.com/', 'topFrame');
```

执行这行代码的结果就如同用户点击了一个 href 属性为'http://www.google.com'，target 属性为'topFrame'的链接。如果有一个窗口名叫'topFrame'，则这个窗口就会打开这个 URL；否则就会打开一个新窗口并将其命名为'topFrame'。第二个参数也可以是一个特殊的窗口名，比如\_self、\_parent、\_top 或\_blank。

1. **弹出窗口**

如果 window.open()的第二个参数不是已有窗口，则会打开一个新窗口或标签页。第三个参数，即特性字符串，用于指定新窗口的配置。如果没有传第三个参数，则新窗口（或标签页）会带有所有默认的浏览器特性（工具栏、地址栏、状态栏等都是默认配置）。如果打开的不是新窗口，则忽略第三个参数。

特性字符串是一个逗号分隔的设置字符串，用于指定新窗口包含的特性。下表列出了一些选项。

| 设 置      | 值          | 说 明                                                                                                |
| ---------- | ----------- | ---------------------------------------------------------------------------------------------------- |
| fullscreen | 'yes'或'no' | 表示新窗口是否最大化。仅限 IE 支持                                                                   |
| height     | 数值        | 新窗口高度。这个值不能小于 100                                                                       |
| left       | 数值        | 新窗口的 x 轴坐标。这个值不能是负值                                                                  |
| location   | 'yes'或'no' | 表示是否显示地址栏。不同浏览器的默认值也不一样。在设置为'no'时，地址栏可能隐藏或禁用（取决于浏览器） |
| Menubar    | 'yes'或'no' | 表示是否显示菜单栏。默认为'no'                                                                       |
| resizable  | 'yes'或'no' | 表示是否可以拖动改变新窗口大小。默认为'no'                                                           |
| scrollbars | 'yes'或'no' | 表示是否可以在内容过长时滚动。默认为'no'                                                             |
| status     | 'yes'或'no' | 表示是否显示状态栏。不同浏览器的默认值也不一样                                                       |
| toolbar    | 'yes'或'no' | 表示是否显示工具栏。默认为'no'                                                                       |
| top        | 数值        | 新窗口的 y 轴坐标。这个值不能是负值                                                                  |
| width      | 数值        | 新窗口的宽度。这个值不能小于 100                                                                     |

这些设置需要以逗号分隔的名值对形式出现，其中名值对以等号连接。（特性字符串中不能包含空格。）来看下面的例子：

```javascript
window.open(
  'http://www.google.com/',
  'googleWindow',
  'height=400,width=400,top=10,left=10,resizable=yes',
);
```

这行代码会打开一个可缩放的新窗口，大小为 400 像素 ×400 像素，位于离屏幕左边及顶边各 10 像素的位置。

window.open()方法返回一个对新建窗口的引用。这个对象与普通 window 对象没有区别，只是为控制新窗口提供了方便。例如，某些浏览器默认不允许缩放或移动主窗口，但可能允许缩放或移动通过 window.open()创建的窗口。跟使用任何 window 对象一样，可以使用这个对象操纵新打开的窗口。

```javascript
let googleWin = window.open(
  'http://www.google.com/',
  'googleWindow',
  'height=400,width=400,top=10,left=10,resizable=yes',
);
// 缩放
googleWin.resizeTo(500, 500);
// 移动
googleWin.moveTo(100, 100);
```

还可以使用 close()方法像这样关闭新打开的窗口：

```javascript
googleWin.close();
```

这个方法只能用于 window.open()创建的弹出窗口。虽然不可能不经用户确认就关闭主窗口，但弹出窗口可以调用 top.close()来关闭自己。关闭窗口以后，窗口的引用虽然还在，但只能用于检查其 closed 属性了：

```javascript
googleWin.close();
alert(googleWin.closed); // true
```

新创建窗口的 window 对象有一个属性 opener，指向打开它的窗口。这个属性只在弹出窗口的最上层 window 对象（top）有定义，是指向调用 window.open()打开它的窗口或窗格的指针。例如：

```javascript
let googleWin = window.open(
  'http://www.google.com/',
  'googleWindow',
  'height=400,width=400,top=10,left=10,resizable=yes',
);
alert(googleWin.opener === window); // true
```

虽然新建窗口中有指向打开它的窗口的指针，但反之则不然。窗口不会跟踪记录自己打开的新窗口，因此开发者需要自己记录。

在某些浏览器中，每个标签页会运行在独立的进程中。如果一个标签页打开了另一个，而 window 对象需要跟另一个标签页通信，那么标签便不能运行在独立的进程中。在这些浏览器中，可以将新打开的标签页的 opener 属性设置为 null，表示新打开的标签页可以运行在独立的进程中。比如：

```javascript
let googleWin = window.open(
  'http://www.google.com/',
  'googleWindow',
  'height=400,width=400,top=10,left=10,resizable=yes',
);
googleWin.opener = null;
```

把 opener 设置为 null 表示新打开的标签页不需要与打开它的标签页通信，因此可以在独立进程中运行。这个连接一旦切断，就无法恢复了。

2. **安全限制**

弹出窗口有段时间被在线广告用滥了。很多在线广告会把弹出窗口伪装成系统对话框，诱导用户点击。因为长得像系统对话框，所以用户很难分清这些弹窗的来源。为了让用户能够区分清楚，浏览器开始对弹窗施加限制。

IE 的早期版本实现针对弹窗的多重安全限制，包括不允许创建弹窗或把弹窗移出屏幕之外，以及不允许隐藏状态栏等。从 IE7 开始，地址栏也不能隐藏了，而且弹窗默认是不能移动或缩放的。Firefox 1 禁用了隐藏状态栏的功能，因此无论 window.open()的特性字符串是什么，都不会隐藏弹窗的状态栏。Firefox 3 强制弹窗始终显示地址栏。Opera 只会在主窗口中打开新窗口，但不允许它们出现在系统对话框的位置。

此外，浏览器会在用户操作下才允许创建弹窗。在网页加载过程中调用 window.open()没有效果，而且还可能导致向用户显示错误。弹窗通常可能在鼠标点击或按下键盘中某个键的情况下才能打开。

3. **弹窗屏蔽程序**

所有现代浏览器都内置了屏蔽弹窗的程序，因此大多数意料之外的弹窗都会被屏蔽。在浏览器屏蔽弹窗时，可能会发生一些事。如果浏览器内置的弹窗屏蔽程序阻止了弹窗，那么 window.open()很可能会返回 null。此时，只要检查这个方法的返回值就可以知道弹窗是否被屏蔽了，比如：

```javascript
let googleWin = window.open('http://www.google.com/', '_blank');
if (googleWin == null) {
  alert('The popup was blocked!');
}
```

在浏览器扩展或其他程序屏蔽弹窗时，window.open()通常会抛出错误。因此要准确检测弹窗是否被屏蔽，除了检测 window.open()的返回值，还要把它用 try/catch 包装起来，像这样：

```javascript
let blocked = false;
try {
  let googleWin = window.open('http://www.google.com/', '_blank');
  if (googleWin == null) {
    blocked = true;
  }
} catch (ex) {
  blocked = true;
}
if (blocked) {
  alert('The popup was blocked!');
}
```

无论弹窗是用什么方法屏蔽的，以上代码都可以准确判断调用 window.open()的弹窗是否被屏蔽了。

### 18.1.4. 窗口位置和像素比

window 对象的位置可以通过不同的属性和方法来确定。现代浏览器提供了 screenLeft 和 screenTop 属性，用于表示窗口相对于屏幕左侧和顶部的位置 ，返回值的单位是 CSS 像素。

可以使用 moveTo()和 moveBy()方法移动窗口。这两个方法都接收两个参数，其中 moveTo()接收要移动到的新位置的绝对坐标 x 和 y；而 moveBy()则接收相对当前位置在两个方向上移动的像素数。比如：

```javascript
// 把窗口移动到左上角
window.moveTo(0, 0);
// 把窗口向下移动100 像素
window.moveBy(0, 100);
// 把窗口移动到坐标位置(200, 300)
window.moveTo(200, 300);
// 把窗口向左移动50 像素
window.moveBy(-50, 0);
```

这些方法只对使用 window.open() (见 12.1.6 节) 打开的窗口有效。

**像素比**

CSS 像素是 Web 开发中使用的统一像素单位。这个单位的背后其实是一个角度：0.0213°。如果屏幕距离人眼是一臂长，则以这个角度计算的 CSS 像素大小约为 1/96 英寸。这样定义像素大小是为了在不同设备上统一标准。比如，低分辨率平板设备上 12 像素（CSS 像素）的文字应该与高清 4K 屏幕下 12 像素（CSS 像素）的文字具有相同大小。这就带来了一个问题，不同像素密度的屏幕下就会有不同的缩放系数，以便把物理像素（屏幕实际的分辨率）转换为 CSS 像素（浏览器报告的虚拟分辨率）。

举个例子，手机屏幕的物理分辨率可能是 1920×1080，但因为其像素可能非常小，所以浏览器就需要将其分辨率降为较低的逻辑分辨率，比如 640×320。这个物理像素与 CSS 像素之间的转换比率由 window.devicePixelRatio 属性提供。对于分辨率从 1920×1080 转换为 640×320 的设备，window.devicePixelRatio 的值就是 3。这样一来，12 像素（CSS 像素）的文字实际上就会用 36 像素的物理像素来显示。

window.devicePixelRatio 实际上与每英寸像素数（DPI，dots per inch）是对应的。DPI 表示单位像素密度，而 window.devicePixelRatio 表示物理像素与逻辑像素之间的缩放系数。

### 18.1.5. 窗口大小

在不同浏览器中确定浏览器窗口大小没有想象中那么容易。所有现代浏览器都支持 4 个属性：innerWidth、innerHeight、outerWidth 和 outerHeight。outerWidth 和 outerHeight 返回浏览器窗口自身的大小（不管是在最外层 window 上使用，还是在窗格`<frame>`中使用）。innerWidth 和 innerHeight 返回浏览器窗口中页面视口的大小（不包含浏览器边框和工具栏）。

document.documentElement.clientWidth 和 document.documentElement.clientHeight 返回页面视口的宽度和高度。

浏览器窗口自身的精确尺寸不好确定，但可以确定页面视口的大小，如下所示：

```javascript
let pageWidth = window.innerWidth,
  pageHeight = window.innerHeight;
if (typeof pageWidth != 'number') {
  if (document.compatMode == 'CSS1Compat') {
    pageWidth = document.documentElement.clientWidth;
    pageHeight = document.documentElement.clientHeight;
  } else {
    pageWidth = document.body.clientWidth;
    pageHeight = document.body.clientHeight;
  }
}
```

这里，先将 pageWidth 和 pageHeight 的值分别设置为 window.innerWidth 和 window.innerHeight。然后，检查 pageWidth 是不是一个数值，如果不是则通过 document.compatMode 来检查页面是否处于标准模式。如果是，则使用 document.documentElement.clientWidth 和 document.documentElement.clientHeight；否则，就使用 document.body.clientWidth 和 document.body.clientHeight。

在移动设备上，window.innerWidth 和 window.innerHeight 返回视口的大小，也就是屏幕上页面可视区域的大小。Mobile Internet Explorer 支持这些属性，但在 document.documentElement.clientWidth 和 document.documentElement.clientHeight 中提供了相同的信息。在放大或缩小页面时，这些值也会相应变化。

在其他移动浏览器中，document.documentElement.clientWidth 和 document.documentElement.clientHeight 返回的布局视口的大小，即渲染页面的实际大小。布局视口是相对于可见视口的概念，可见视口只能显示整个页面的一小部分。Mobile Internet Explorer 把布局视口的信息保存在 document.body.clientWidth 和 document.body.clientHeight 中。在放大或缩小页面时，这些值也会相应变化。

因为桌面浏览器的差异，所以需要先确定用户是不是在使用移动设备，然后再决定使用哪个属性。

注意 手机视口的概念比较复杂，有各种各样的问题。如果读者在做移动开发，推荐阅读 Peter-Paul Koch 发表在 QuirksMode 网站上的文章“A Tale of Two Viewports— Part Two”。

可以使用 resizeTo()和 resizeBy()方法调整窗口大小。这两个方法都接收两个参数，resizeTo()接收新的宽度和高度值，而 resizeBy()接收宽度和高度各要缩放多少。下面看个例子：

```javascript
// 缩放到100×100
window.resizeTo(100, 100);
// 缩放到200×150
window.resizeBy(100, 50);
// 缩放到300×300
window.resizeTo(300, 300);
```

与移动窗口的方法一样，缩放窗口的方法可能会被浏览器禁用，而且在某些浏览器中默认是禁用的。同样，缩放窗口的方法只能应用到最上层的 window 对象。

### 18.1.6. 视口位置

浏览器窗口尺寸通常无法满足完整显示整个页面，为此用户可以通过滚动在有限的视口中查看文档。度量文档相对于视口滚动距离的属性有两对，返回相等的值：window.pageXoffset/window.scrollX 和 window.pageYoffset/window.scrollY。

可以使用 scroll()、scrollTo()和 scrollBy()方法滚动页面。这 3 个方法都接收表示相对视口距离的 x 和 y 坐标，这两个参数在前两个方法中表示要滚动到的坐标，在最后一个方法中表示滚动的距离。

```javascript
// 相对于当前视口向下滚动100 像素
window.scrollBy(0, 100);
// 相对于当前视口向右滚动40 像素
window.scrollBy(40, 0);
// 滚动到页面左上角
window.scrollTo(0, 0);
// 滚动到距离屏幕左边及顶边各100 像素的位置
window.scrollTo(100, 100);
```

这几个方法也都接收一个 ScrollToOptions 字典，除了提供偏移值，还可以通过 behavior 属性告诉浏览器是否平滑滚动。

```javascript
// 正常滚动
window.scrollTo({
  left: 100,
  top: 100,
  behavior: 'auto',
});
// 平滑滚动
window.scrollTo({
  left: 100,
  top: 100,
  behavior: 'smooth',
});
```

### 18.1.7. 定时器

JavaScript 在浏览器中是单线程执行的，但允许使用定时器指定在某个时间之后或每隔一段时间就执行相应的代码。setTimeout()用于指定在一定时间后执行某些代码，而 setInterval()用于指定每隔一段时间执行某些代码。

setTimeout()方法通常接收两个参数：要执行的代码和在执行回调函数前等待的时间（毫秒）。第一个参数可以是包含 JavaScript 代码的字符串（类似于传给 eval()的字符串）或者一个函数，比如：

```javascript
// 在1 秒后显示警告框
setTimeout(() => alert('Hello world!'), 1000);
```

第二个参数是要等待的毫秒数，而不是要执行代码的确切时间。JavaScript 是单线程的，所以每次只能执行一段代码。为了调度不同代码的执行，JavaScript 维护了一个任务队列。其中的任务会按照添加到队列的先后顺序执行。setTimeout()的第二个参数只是告诉 JavaScript 引擎在指定的毫秒数过后把任务添加到这个队列。如果队列是空的，则会立即执行该代码。如果队列不是空的，则代码必须等待前面的任务执行完才能执行。

调用 setTimeout()时，会返回一个表示该超时排期的数值 ID。这个超时 ID 是被排期执行代码的唯一标识符，可用于取消该任务。要取消等待中的排期任务，可以调用 clearTimeout()方法并传入超时 ID，如下面的例子所示：

```javascript
// 设置超时任务
let timeoutId = setTimeout(() => alert('Hello world!'), 1000);
// 取消超时任务
clearTimeout(timeoutId);
```

只要是在指定时间到达之前调用 clearTimeout()，就可以取消超时任务。在任务执行后再调用 clearTimeout()没有效果。

注意 所有超时执行的代码（函数）都会在全局作用域中的一个匿名函数中运行，因此函数中的 this 值在非严格模式下始终指向 window，而在严格模式下是 undefined。如果给 setTimeout()提供了一个箭头函数，那么 this 会保留为定义它时所在的词法作用域。

setInterval()与 setTimeout()的使用方法类似，只不过指定的任务会每隔指定时间就执行一次，直到取消循环定时或者页面卸载。setInterval()同样可以接收两个参数：要执行的代码（字符串或函数），以及把下一次执行定时代码的任务添加到队列要等待的时间（毫秒）。下面是一个例子：

```javascript
setInterval(() => alert('Hello world!'), 10000);
```

注意 这里的关键点是，第二个参数，也就是间隔时间，指的是向队列添加新任务之前等待的时间。比如，调用 setInterval()的时间为 01:00:00，间隔时间为 3000 毫秒。这意味着 01:00:03 时，浏览器会把任务添加到执行队列。浏览器不关心这个任务什么时候执行或者执行要花多长时间。因此，到了 01:00:06，它会再向队列中添加一个任务。由此可看出，执行时间短、非阻塞的回调函数比较适合 setInterval()。

setInterval()方法也会返回一个循环定时 ID，可以用于在未来某个时间点上取消循环定时。要取消循环定时，可以调用 clearInterval()并传入定时 ID。相对于 setTimeout()而言，取消定时的能力对 setInterval()更加重要。毕竟，如果一直不管它，那么定时任务会一直执行到页面卸载。下
面是一个常见的例子：

```javascript
let num = 0,
  intervalId = null;
let max = 10;
let incrementNumber = function () {
  num++;
  // 如果达到最大值，则取消所有未执行的任务
  if (num == max) {
    clearInterval(intervalId);
    alert('Done');
  }
};
intervalId = setInterval(incrementNumber, 500);
```

在这个例子中，变量 num 会每半秒递增一次，直至达到最大限制值。此时循环定时会被取消。这个模式也可以使用 setTimeout()来实现，比如：

```javascript
let num = 0;
let max = 10;
let incrementNumber = function () {
  num++;
  // 如果还没有达到最大值，再设置一个超时任务
  if (num < max) {
    setTimeout(incrementNumber, 500);
  } else {
    alert('Done');
  }
};
setTimeout(incrementNumber, 500);
```

注意在使用 setTimeout()时，不一定要记录超时 ID，因为它会在条件满足时自动停止，否则会自动设置另一个超时任务。这个模式是设置循环任务的推荐做法。setIntervale()在实践中很少会在生产环境下使用，因为一个任务结束和下一个任务开始之间的时间间隔是无法保证的，有些循环定时任务可能会因此而被跳过。而像前面这个例子中一样使用 setTimeout()则能确保不会出现这种情况。一般来说，最好不要使用 setInterval()。

### 18.1.8. 系统对话框

使用 alert()、confirm()和 prompt()方法，可以让浏览器调用系统对话框向用户显示消息。这些对话框与浏览器中显示的网页无关，而且也不包含 HTML。它们的外观由操作系统或者浏览器决定，无法使用 CSS 设置。此外，这些对话框都是同步的模态对话框，即在它们显示的时候，代码会停止执行，在它们消失以后，代码才会恢复执行。

alert()方法在本书示例中经常用到。它接收一个要显示给用户的字符串。与 console.log 可以接收任意数量的参数且能一次性打印这些参数不同，alert()只接收一个参数。调用 alert()时，传入的字符串会显示在一个系统对话框中。对话框只有一个“OK”（确定）按钮。如果传给 alert()的参数
不是一个原始字符串，则会调用这个值的 toString()方法将其转换为字符串。

警告框（alert）通常用于向用户显示一些他们无法控制的消息，比如报错。用户唯一的选择就是在看到警告框之后把它关闭。

第二种对话框叫确认框，通过调用 confirm()来显示。确认框跟警告框类似，都会向用户显示消息。但不同之处在于，确认框有两个按钮：“Cancel”（取消）和“OK”（确定）。用户通过单击不同的按钮表明希望接下来执行什么操作。

要知道用户单击了 OK 按钮还是 Cancel 按钮，可以判断 confirm()方法的返回值：true 表示单击了 OK 按钮，false 表示单击了 Cancel 按钮或者通过单击某一角上的 X 图标关闭了确认框。确认框的典型用法如下所示：

```javascript
if (confirm('Are you sure?')) {
  alert('I'm so glad you're sure!');
} else {
  alert('I'm sorry to hear you're not sure.');
}
```

在这个例子中，第一行代码向用户显示了确认框，也就是 if 语句的条件。如果用户单击了 OK 按钮，则会弹出警告框显示'I'm so glad you're sure!'。如果单击了 Cancel，则会显示'I'm sorry tohear you're not sure.'。确认框通常用于让用户确认执行某个操作，比如删除邮件等。因为这种对话框会完全打断正在浏览网页的用户，所以应该在必要时再使用。

最后一种对话框是提示框，通过调用 prompt()方法来显示。提示框的用途是提示用户输入消息。除了 OK 和 Cancel 按钮，提示框还会显示一个文本框，让用户输入内容。prompt()方法接收两个参数：要显示给用户的文本，以及文本框的默认值（可以是空字符串）。

如果用户单击了 OK 按钮，则 prompt()会返回文本框中的值。如果用户单击了 Cancel 按钮，或者对话框被关闭，则 prompt()会返回 null。下面是一个例子：

```javascript
let result = prompt('What is your name? ', '');
if (result !== null) {
  alert('Welcome, ' + result);
}
```

这些系统对话框可以向用户显示消息、确认操作和获取输入。由于不需要 HTML 和 CSS，所以系统对话框是 Web 应用程序最简单快捷的沟通手段。

很多浏览器针对这些系统对话框添加了特殊功能。如果网页中的脚本生成了两个或更多系统对话框，则除第一个之外所有后续的对话框上都会显示一个复选框，如果用户选中则会禁用后续的弹框，直到页面刷新。

如果用户选中了复选框并关闭了对话框，在页面刷新之前，所有系统对话框（警告框、确认框、提示框）都会被屏蔽。开发者无法获悉这些对话框是否显示了。对话框计数器会在浏览器空闲时重置，因此如果两次独立的用户操作分别产生了两个警告框，则两个警告框上都不会显示屏蔽复选框。如果一次独立的用户操作连续产生了两个警告框，则第二个警告框会显示复选框。

JavaScript 还可以显示另外两种对话框：find()和 print()。这两种对话框都是异步显示的，即控制权会立即返回给脚本。用户在浏览器菜单上选择“查找”（find）和“打印”（print）时显示的就是这两种对话框。通过在 window 对象上调用 find()和 print()可以显示它们，比如：

```javascript
// 显示打印对话框
window.print();
// 显示查找对话框
window.find();
```

这两个方法不会返回任何有关用户在对话框中执行了什么操作的信息，因此很难加以利用。此外，因为这两种对话框是异步的，所以浏览器的对话框计数器不会涉及它们，而且用户选择禁用对话框对它们也没有影响。

## 18.2. location

location 是最有用的 BOM 对象之一，提供了当前窗口中加载文档的信息，以及通常的导航功能。这个对象独特的地方在于， 它既是 window 的属性， 也是 document 的属性。也就是说，window.location 和 document.location 指向同一个对象。location 对象不仅保存着当前加载文档的信息，也保存着把 URL 解析为离散片段后能够通过属性访问的信息。这些解析后的属性在下表中有详细说明（location 前缀是必需的）。

假设浏览器当前加载的 URL 是 http://foouser:barpassword@www.wrox.com:80/WileyCDA/?q=javascript#contents，location 对象的内容如下表所示。

| 属 性             | 值                                                         | 说 明                                                        |
| ----------------- | ---------------------------------------------------------- | ------------------------------------------------------------ |
| location.hash     | '#contents'                                                | URL 散列值（井号后跟零或多个字符），如果没有则为空字符串     |
| location.host     | 'www.wrox.com:80'                                          | 服务器名及端口号                                             |
| location.hostname | 'www.wrox.com'                                             | 服务器名                                                     |
| location.href     | 'http://www.google.com:80/WileyCDA/?q=javascript#contents' | 当前加载页面的完整 URL。location 的 toString()方法返回这个值 |
| location.pathname | '/WileyCDA/'                                               | URL 中的路径和（或）文件名                                   |
| location.port     | '80'                                                       | 请求的端口。如果 URL 中没有端口，则返回空字符串              |
| location.protocol | 'http:'                                                    | 页面使用的协议。通常是'http:'或'https:'                      |
| location.search   | '?q=javascript'                                            | URL 的查询字符串。这个字符串以问号开头                       |
| location.username | 'foouser'                                                  | 域名前指定的用户名                                           |
| location.password | 'barpassword'                                              | 域名前指定的密码                                             |
| location.origin   | 'http://www.google.com'                                    | URL 的源地址。只读                                           |

### 18.2.1. 查询字符串

location 的多数信息都可以通过上面的属性获取。但是 URL 中的查询字符串并不容易使用。虽然 location.search 返回了从问号开始直到 URL 末尾的所有内容，但没有办法逐个访问每个查询参数。下面的函数解析了查询字符串，并返回一个以每个查询参数为属性的对象：

```javascript
const getQueryArgs = function () {
  // 取得没有开头问号的查询字符串
  const querys = location.search.length > 0 ? location.search.slice(1) : '';

  // 保存结果
  let args = {};

  // 把每个参数添加到 args 对象
  for (const pair of querys.split('&')) {
    const key = decodeURIComponent(pair.split('=')[0]);
    const value = decodeURIComponent(pair.split('=')[1]);

    if (key.length) {
      args[key] = value;
    }
  }

  return args;
};
```

这个函数首先删除了查询字符串开头的问号，当然前提是 location.search 必须有内容。解析后的参数将被保存到 args 对象，这个对象以字面量形式创建。接着，先把查询字符串按照&分割成数组，每个元素的形式为 name=value。for 循环迭代这个数组，将每一个元素按照=分割成数组，这个数组第一项是参数名，第二项是参数值。参数名和参数值在使用 decodeURIComponent()解码后（这是因为查询字符串通常是被编码后的格式）分别保存在 key 和 value 变量中。最后，key 作为属性而 value 作为该属性的值被添加到 args 对象。

不过，如果键名有重复，这种方法并不适用，例如，查询字符串为 `'?key=1&key=2&value=3'`。所以，我们此时用数组来存储。

```javascript
const getQueryMap = function () {
  // '?key=1&key=2&value=3'
  const queryStr = location.search.length > 0 ? location.search.slice(1) : '';
  const pairStrs = queryStr.split('&');

  const queryMap = pairStrs.reduce((map, pairStr) => {
    const key = decodeURIComponent(pairStr.split('=')[0]);
    const value = decodeURIComponent(pairStr.split('=')[1]);

    if (map.has(key)) {
      map.set(key, Array.from(map.get(key)).concat(value));
    } else {
      map.set(key, value);
    }

    return map;
  }, new Map());

  return queryMap;
};

console.log(getQueryMap());
// Map(2) { 'key' => [ '1', '2' ], 'value' => '3' }
```

现在，查询字符串中的每个参数都是一个键，这样使用起来就方便了：

```javascript
const queryMap = getQueryMap();
console.log(queryMap['key']); // ['1', '2']
console.log(queryMap['value']); // '3'
```

**URLSearchParams**

URLSearchParams 提供了一组标准 API 方法，通过它们可以检查和修改查询字符串。给 URLSearchParams 构造函数传入一个查询字符串，就可以创建一个实例。这个实例上暴露了 get()、set()和 delete()等方法，可以对查询字符串执行相应操作。下面来看一个例子：

```javascript
let qs = '?q=javascript&num=10';
let searchParams = new URLSearchParams(qs);
alert(searchParams.toString()); // ' q=javascript&num=10'
searchParams.has('num'); // true
searchParams.get('num'); // 10
searchParams.set('page', '3');
alert(searchParams.toString()); // ' q=javascript&num=10&page=3'
searchParams.delete('q');
alert(searchParams.toString()); // ' num=10&page=3'
```

大多数支持 URLSearchParams 的浏览器也支持将 URLSearchParams 的实例用作可迭代对象：

```javascript
let qs = '?q=javascript&num=10';
let searchParams = new URLSearchParams(qs);
for (let param of searchParams) {
  console.log(param);
}
// ['q', 'javascript']
// ['num', '10']
```

### 18.2.2. 操作地址

可以通过修改 location 对象修改浏览器的地址。首先，最常见的是使用 assign()方法并传入一个 URL，如下所示：

```javascript
location.assign('http://www.google.com/');
```

这行代码会立即启动导航到新 URL 的操作，同时在浏览器历史记录中增加一条记录。如果给 location.href 或 window.location 设置一个 URL，也会以同一个 URL 值调用 assign()方法。比如，下面两行代码都会执行与显式调用 assign()一样的操作：

```javascript
window.location = 'http://www.google.com/';
location.href = 'http://www.google.com/';
```

在这 3 种修改浏览器地址的方法中，设置 location.href 是最常见的。

修改 location 对象的属性也会修改当前加载的页面。其中，hash、search、hostname、pathname 和 port 属性被设置为新值之后都会修改当前 URL，如下面的例子所示：

```javascript
// 假设当前URL 为http://www.google.com/WileyCDA/
// 把URL 修改为http://www.google.com/WileyCDA/#section1
location.hash = '#section1';
// 把URL 修改为http://www.google.com/WileyCDA/?q=javascript
location.search = '?q=javascript';
// 把URL 修改为http://www.somewhere.com/WileyCDA/
location.hostname = 'www.somewhere.com';
// 把URL 修改为http://www.somewhere.com/mydir/
location.pathname = 'mydir';
// 把URL 修改为http://www.somewhere.com:8080/WileyCDA/
location.port = 8080;
```

除了 hash 之外，只要修改 location 的一个属性，就会导致页面重新加载新 URL。

注意 修改 hash 的值会在浏览器历史中增加一条新记录。在早期的 IE 中，点击“后退”和“前进”按钮不会更新 hash 属性，只有点击包含散列的 URL 才会更新 hash 的值。

在以前面提到的方式修改 URL 之后，浏览器历史记录中就会增加相应的记录。当用户单击“后退”按钮时，就会导航到前一个页面。如果不希望增加历史记录，可以使用 replace()方法。这个方法接收一个 URL 参数，但重新加载后不会增加历史记录。调用 replace()之后，用户不能回到前一页。比
如下面的例子：

```html
<!DOCTYPE html>
<html>
  <head>
    <title>You won't be able to get back here</title>
  </head>
  <body>
    <p>Enjoy this page for a second, because you won't be coming back here.</p>
    <script>
      setTimeout(() => location.replace('http://www.google.com/'), 1000);
    </script>
  </body>
</html>
```

浏览器加载这个页面 1 秒之后会重定向到www.wrox.com。此时，“后退”按钮是禁用状态，即不能返回这个示例页面，除非手动输入完整的URL。

最后一个修改地址的方法是 reload()，它能重新加载当前显示的页面。调用 reload()而不传参数，页面会以最有效的方式重新加载。也就是说，如果页面自上次请求以来没有修改过，浏览器可能会从缓存中加载页面。如果想强制从服务器重新加载，可以像下面这样给 reload()传个 true：

```javascript
location.reload(); // 重新加载，可能是从缓存加载
location.reload(true); // 重新加载，从服务器加载
```

脚本中位于 reload()调用之后的代码可能执行也可能不执行，这取决于网络延迟和系统资源等因素。为此，最好把 reload()作为最后一行代码。

## 18.3. navigator

navigator 是由 Netscape Navigator 2 最早引入浏览器的，现在已经成为客户端标识浏览器的标准。只要浏览器启用 JavaScript，navigator 对象就一定存在。但是与其他 BOM 对象一样，每个浏览器都支持自己的属性。

注意 navigator 对象中关于系统能力的属性将在第 13 章详细介绍。

navigator 对象实现了 NavigatorID 、NavigatorLanguage 、NavigatorOnLine 、NavigatorContentUtils 、NavigatorStorage 、NavigatorStorageUtils 、NavigatorConcurrentHardware、NavigatorPlugins 和 NavigatorUserMedia 接口定义的属性和方法。

下表列出了这些接口定义的属性和方法：

| 属性/方法                     | 说 明                                                                   |
| ----------------------------- | ----------------------------------------------------------------------- |
| activeVrDisplays              | 返回数组，包含 ispresenting 属性为 true 的 VRDisplay 实例               |
| appCodeName                   | 即使在非 Mozilla 浏览器中也会返回'Mozilla'                              |
| appName                       | 浏览器全名                                                              |
| appVersion                    | 浏览器版本。通常与实际的浏览器版本不一致                                |
| battery                       | 返回暴露 Battery Status API 的 BatteryManager 对象                      |
| buildId                       | 浏览器的构建编号                                                        |
| connection                    | 返回暴露 Network Information API 的 NetworkInformation 对象             |
| cookieEnabled                 | 返回布尔值，表示是否启用了 cookie                                       |
| credentials                   | 返回暴露 Credentials Management API 的 CredentialsContainer 对象        |
| deviceMemory                  | 返回单位为 GB 的设备内存容量                                            |
| doNotTrack                    | 返回用户的“不跟踪”（do-not-track）设置                                  |
| geolocation                   | 返回暴露 Geolocation API 的 Geolocation 对象                            |
| getVRDisplays()               | 返回数组，包含可用的每个 VRDisplay 实例                                 |
| getUserMedia()                | 返回与可用媒体设备硬件关联的流                                          |
| hardwareConcurrency           | 返回设备的处理器核心数量                                                |
| javaEnabled                   | 返回布尔值，表示浏览器是否启用了 Java                                   |
| language                      | 返回浏览器的主语言                                                      |
| languages                     | 返回浏览器偏好的语言数组                                                |
| locks                         | 返回暴露 Web Locks API 的 LockManager 对象                              |
| mediaCapabilities             | 返回暴露 Media Capabilities API 的 MediaCapabilities 对象               |
| mediaDevices                  | 返回可用的媒体设备                                                      |
| maxTouchPoints                | 返回设备触摸屏支持的最大触点数                                          |
| mimeTypes                     | 返回浏览器中注册的 MIME 类型数组                                        |
| onLine                        | 返回布尔值，表示浏览器是否联网                                          |
| oscpu                         | 返回浏览器运行设备的操作系统和（或）CPU                                 |
| permissions                   | 返回暴露 Permissions API 的 Permissions 对象                            |
| platform                      | 返回浏览器运行的系统平台                                                |
| plugins                       | 返回浏览器安装的插件数组。在 IE 中，这个数组包含页面中所有`<embed>`元素 |
| product                       | 返回产品名称（通常是'Gecko'）                                           |
| productSub                    | 返回产品的额外信息（通常是 Gecko 的版本）                               |
| registerProtocolHandler()     | 将一个网站注册为特定协议的处理程序                                      |
| requestMediaKeySystemAccess() | 返回一个期约，解决为 MediaKeySystemAccess 对象                          |
| sendBeacon()                  | 异步传输一些小数据                                                      |
| serviceWorker                 | 返回用来与 ServiceWorker 实例交互的 ServiceWorkerContainer              |
| share()                       | 返回当前平台的原生共享机制                                              |
| storage                       | 返回暴露 Storage API 的 StorageManager 对象                             |
| userAgent                     | 返回浏览器的用户代理字符串                                              |
| vendor                        | 返回浏览器的厂商名称                                                    |
| vendorSub                     | 返回浏览器厂商的更多信息                                                |
| vibrate()                     | 触发设备振动                                                            |
| webdriver                     | 返回浏览器当前是否被自动化程序控制                                      |

navigator 对象的属性通常用于确定浏览器的类型。

### 18.3.1. 检测插件

检测浏览器是否安装了某个插件是开发中常见的需求。除 IE10 及更低版本外的浏览器，都可以通过 plugins 类数组对象来确定。这个对象中的每一项都包含如下属性。

- name：插件名称。
- description：插件介绍。
- filename：插件的文件名。
- length：由当前插件处理的 MIME 类型数量。

通常，name 属性包含识别插件所需的必要信息，尽管不是特别准确。检测插件就是遍历浏览器中可用的插件，并逐个比较插件的名称，如下所示：

```javascript
// 插件检测，IE10 及更低版本无效
let hasPlugin = function (name) {
  name = name.toLowerCase();
  for (let plugin of window.navigator.plugins) {
    if (plugin.name.toLowerCase().indexOf(name) > -1) {
      return true;
    }
  }
  return false;
};
// 检测Flash
alert(hasPlugin('Flash'));
// 检测QuickTime
alert(hasPlugin('QuickTime'));
```

这个 hasPlugin()方法接收一个参数，即待检测插件的名称。第一步是把插件名称转换为小写形式，以便于比较。然后，遍历 plugins 数组，通过 indexOf()方法检测每个 name 属性，看传入的名称是不是存在于某个数组中。比较的字符串全部小写，可以避免大小写问题。传入的参数应该尽可能独一无二，以避免混淆。像'Flash'、'QuickTime'这样的字符串就可以避免混淆。这个方法可以在 Firefox、Safari、Opera 和 Chrome 中检测插件。

注意 plugins 数组中的每个插件对象还有一个 MimeType 对象，可以通过中括号访问。每个 MimeType 对象有 4 个属性：description 描述 MIME 类型，enabledPlugin 是指向插件对象的指针，suffixes 是该 MIME 类型对应扩展名的逗号分隔的字符串，type 是完整的 MIME 类型字符串。

IE11 的 window.navigator 对象开始支持 plugins 和 mimeTypes 属性。这意味着前面定义的函数可以适用于所有较新版本的浏览器。而且，IE11 中的 ActiveXObject 也从 DOM 中隐身了，意味着不能再用它来作为检测特性的手段。

**旧版本 IE 中的插件检测**

IE10 及更低版本中检测插件的问题比较多，因为这些浏览器不支持 Netscape 式的插件。在这些 IE 中检测插件要使用专有的 ActiveXObject，并尝试实例化特定的插件。IE 中的插件是实现为 COM 对象的，由唯一的字符串标识。因此，要检测某个插件就必须知道其 COM 标识符。例如，Flash 的标识符是'ShockwaveFlash.ShockwaveFlash'。知道了这个信息后，就可以像这样检测 IE 中是否安装了 Flash：

```javascript
// 在旧版本IE 中检测插件
function hasIEPlugin(name) {
  try {
    new ActiveXObject(name);
    return true;
  } catch (ex) {
    return false;
  }
}
// 检测Flash
alert(hasIEPlugin('ShockwaveFlash.ShockwaveFlash'));
// 检测QuickTime
alert(hasIEPlugin('QuickTime.QuickTime'));
```

在这个例子中，hasIEPlugin()函数接收一个 DOM 标识符参数。为检测插件，这个函数会使用传入的标识符创建一个新 ActiveXObject 实例。相应代码封装在一个 try/catch 语句中，因此如果创建的插件不存在则会抛出错误。如果创建成功则返回 true，如果失败则在 catch 块中返回 false。上
面的例子还演示了如何检测 Flash 和 QuickTime 插件。

因为检测插件涉及两种方式，所以一般要针对特定插件写一个函数，而不是使用通常的检测函数。比如下面的例子：

```javascript
// 在所有浏览器中检测Flash
function hasFlash() {
  var result = hasPlugin('Flash');
  if (!result) {
    result = hasIEPlugin('ShockwaveFlash.ShockwaveFlash');
  }
  return result;
}
// 在所有浏览器中检测QuickTime
function hasQuickTime() {
  var result = hasPlugin('QuickTime');
  if (!result) {
    result = hasIEPlugin('QuickTime.QuickTime');
  }
  return result;
}
// 检测Flash
alert(hasFlash());
// 检测QuickTime
alert(hasQuickTime());
```

以上代码定义了两个函数 hasFlash()和 hasQuickTime()。每个函数都先尝试使用非 IE 插件检测方式，如果返回 false（对 IE 可能会），则再使用 IE 插件检测方式。如果 IE 插件检测方式再返回 false，整个检测方法也返回 false。只要有一种方式返回 true，检测方法就会返回 true。

注意 plugins 有一个 refresh()方法，用于刷新 plugins 属性以反映新安装的插件。这个方法接收一个布尔值参数，表示刷新时是否重新加载页面。如果传入 true，则所有包含插件的页面都会重新加载。否则，只有 plugins 会更新，但页面不会重新加载。

### 18.3.2. 注册处理程序

现代浏览器支持 navigator 上的（在 HTML5 中定义的）registerProtocolHandler()方法。这个方法可以把一个网站注册为处理某种特定类型信息应用程序。随着在线 RSS 阅读器和电子邮件客户端的流行，可以借助这个方法将 Web 应用程序注册为像桌面软件一样的默认应用程序。

要使用 registerProtocolHandler()方法，必须传入 3 个参数：要处理的协议（如'mailto'或'ftp'）、处理该协议的 URL，以及应用名称。比如，要把一个 Web 应用程序注册为默认邮件客户端，可以这样做：

```javascript
navigator.registerProtocolHandler(
  'mailto',
  'http://www.somemailclient.com?cmd=%s',
  'Some Mail Client',
);
```

这个例子为'mailto'协议注册了一个处理程序，这样邮件地址就可以通过指定的 Web 应用程序打开。注意，第二个参数是负责处理请求的 URL，%s 表示原始的请求。

## 18.4. screen

window 的另一个属性 screen 对象，是为数不多的几个在编程中很少用的 JavaScript 对象。这个对象中保存的纯粹是客户端能力信息，也就是浏览器窗口外面的客户端显示器的信息，比如像素宽度和像素高度。每个浏览器都会在 screen 对象上暴露不同的属性。下表总结了这些属性。

| 属 性       | 说 明                                        |
| ----------- | -------------------------------------------- |
| availHeight | 屏幕像素高度减去系统组件高度（只读）         |
| availLeft   | 没有被系统组件占用的屏幕的最左侧像素（只读） |
| availTop    | 没有被系统组件占用的屏幕的最顶端像素（只读） |
| availWidth  | 屏幕像素宽度减去系统组件宽度（只读）         |
| colorDepth  | 表示屏幕颜色的位数；多数系统是 32（只读）    |
| height      | 屏幕像素高度                                 |
| left        | 当前屏幕左边的像素距离                       |
| pixelDepth  | 屏幕的位深（只读）                           |
| top         | 当前屏幕顶端的像素距离                       |
| width       | 屏幕像素宽度                                 |
| orientation | 返回 Screen Orientation API 中屏幕的朝向     |

## 18.5. history

history 对象表示当前窗口首次使用以来用户的导航历史记录。因为 history 是 window 的属性，所以每个 window 都有自己的 history 对象。出于安全考虑，这个对象不会暴露用户访问过的 URL，但可以通过它在不知道实际 URL 的情况下前进和后退。

### 18.5.1. 导航

go()方法可以在用户历史记录中沿任何方向导航，可以前进也可以后退。这个方法只接收一个参数，这个参数可以是一个整数，表示前进或后退多少步。负值表示在历史记录中后退（类似点击浏览器的“后退”按钮），而正值表示在历史记录中前进（类似点击浏览器的“前进”按钮）。下面来看几个例子：

```javascript
// 后退一页
history.go(-1);
// 前进一页
history.go(1);
// 前进两页
history.go(2);
```

在旧版本的一些浏览器中，go()方法的参数也可以是一个字符串，这种情况下浏览器会导航到历史中包含该字符串的第一个位置。最接近的位置可能涉及后退，也可能涉及前进。如果历史记录中没有匹配的项，则这个方法什么也不做，如下所示：

```javascript
// 导航到最近的wrox.com 页面
history.go('google.com');
// 导航到最近的nczonline.net 页面
history.go('nczonline.net');
```

go()有两个简写方法：back()和 forward()。顾名思义，这两个方法模拟了浏览器的后退按钮和前进按钮：

```javascript
// 后退一页
history.back();
// 前进一页
history.forward();
```

history 对象还有一个 length 属性，表示历史记录中有多个条目。这个属性反映了历史记录的数量，包括可以前进和后退的页面。对于窗口或标签页中加载的第一个页面，history.length 等于 1。通过以下方法测试这个值，可以确定用户浏览器的起点是不是你的页面：

```javascript
if (history.length == 1) {
  // 这是用户窗口中的第一个页面
}
```

history 对象通常被用于创建“后退”和“前进”按钮，以及确定页面是不是用户历史记录中的第一条记录。

注意 如果页面 URL 发生变化，则会在历史记录中生成一个新条目。对于 2009 年以来发布的主流浏览器，这包括改变 URL 的散列值（因此，把 location.hash 设置为一个新值会在这些浏览器的历史记录中增加一条记录）。这个行为常被单页应用程序框架用来模拟前进和后退，这样做是为了不会因导航而触发页面刷新。

### 18.5.2. 历史状态管理

现代 Web 应用程序开发中最难的环节之一就是历史记录管理。用户每次点击都会触发页面刷新的时代早已过去，“后退”和“前进”按钮对用户来说就代表“帮我切换一个状态”的历史也就随之结束了。为解决这个问题，首先出现的是 hashchange 事件（第 17 章介绍事件时会讨论）。HTML5 也为 history 对象增加了方便的状态管理特性。

hashchange 会在页面 URL 的散列变化时被触发，开发者可以在此时执行某些操作。而状态管理 API 则可以让开发者改变浏览器 URL 而不会加载新页面。为此，可以使用 history.pushState()方法。这个方法接收 3 个参数：一个 state 对象、一个新状态的标题和一个（可选的）相对 URL。例如：

```javascript
const stateObject = {foo: 'bar'};
history.pushState(stateObject, 'My title', 'baz.html');
```

pushState()方法执行后，状态信息就会被推到历史记录中，浏览器地址栏也会改变以反映新的相对 URL。除了这些变化之外，即使 location.href 返回的是地址栏中的内容，浏览器页不会向服务器发送请求。第二个参数并未被当前实现所使用，因此既可以传一个空字符串也可以传一个短标题。第一个参数应该包含正确初始化页面状态所必需的信息。为防止滥用，这个状态的对象大小是有限制的，通常在 500KB ～ 1MB 以内。

因为 pushState()会创建新的历史记录，所以也会相应地启用“后退”按钮。此时单击“后退”按钮，就会触发 window 对象上的 popstate 事件。popstate 事件的事件对象有一个 state 属性，其中包含通过 pushState()第一个参数传入的 state 对象：

```javascript
window.addEventListener('popstate', (event) => {
  let state = event.state;
  if (state) {
    // 第一个页面加载时状态是null
    processState(state);
  }
});
```

基于这个状态，应该把页面重置为状态对象所表示的状态（因为浏览器不会自动为你做这些）。记住，页面初次加载时没有状态。因此点击“后退”按钮直到返回最初页面时，event.state 会为 null。

可以通过 history.state 获取当前的状态对象，也可以使用 replaceState()并传入与 pushState()同样的前两个参数来更新状态。更新状态不会创建新历史记录，只会覆盖当前状态：

```javascript
history.replaceState({newFoo: 'newBar'}, 'New title');
```

传给 pushState()和 replaceState()的 state 对象应该只包含可以被序列化的信息。因此，DOM 元素之类并不适合放到状态对象里保存。

注意 使用 HTML5 状态管理时，要确保通过 pushState()创建的每个“假”URL 背后都对应着服务器上一个真实的物理 URL。否则，单击“刷新”按钮会导致 404 错误。所有单页应用程序（SPA，Single Page Application）框架都必须通过服务器或客户端的某些配置解决这个问题。
