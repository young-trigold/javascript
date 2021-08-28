**目录：**
- [15. DOM扩展](#15-dom扩展)
  - [15.1. Slector API](#151-slector-api)
    - [15.1.1. querySelector()](#1511-queryselector)
    - [15.1.2. querySelectorAll()](#1512-queryselectorall)
    - [15.1.3. matches()](#1513-matches)
  - [15.2. 元素遍历](#152-元素遍历)
  - [15.3. HTML 5](#153-html-5)
    - [15.3.1. CSS 类扩展](#1531-css-类扩展)
    - [15.3.2. 焦点管理](#1532-焦点管理)
    - [15.3.3. HTMLDocument扩展](#1533-htmldocument扩展)
    - [15.3.4. 字符集属性](#1534-字符集属性)
    - [15.3.5. 自定义数据属性](#1535-自定义数据属性)
    - [15.3.6. 插入标记](#1536-插入标记)

# 15. DOM扩展

本章内容
- 理解Selectors API
- 使用HTML5 DOM 扩展

尽管DOM API 已经相当不错，但仍然不断有标准或专有的扩展出现，以支持更多功能。2008 年以前，大部分浏览器对DOM的扩展是专有的。此后，W3C 开始着手将这些已成为事实标准的专有扩展编制成正式规范。

基于以上背景，诞生了描述DOM扩展的两个标准：Selectors API 与HTML5。这两个标准体现了社区需求和标准化某些手段及API 的愿景。另外还有较小的Element Traversal 规范，增加了一些DOM属性。专有扩展虽然还有，但这两个规范（特别是HTML5）已经涵盖其中大部分。本章也会讨论专有扩展。

本章所有内容已经得到市场占有率名列前茅的所有主流浏览器支持，除非特别说明。

## 15.1. Slector API

JavaScript 库中最流行的一种能力就是根据CSS 选择符的模式匹配DOM 元素。比如，jQuery 就完全以CSS 选择符查询DOM获取元素引用，而不是使用getElementById()和getElementsByTagName()。

Selectors API（参见W3C 网站上的Selectors API Level 1）是W3C 推荐标准，规定了浏览器原生支持的CSS 查询API。支持这一特性的所有JavaScript 库都会实现一个基本的CSS 解析器，然后使用已有的DOM 方法搜索文档并匹配目标节点。虽然库开发者在不断改进其性能，但JavaScript 代码能做到的毕竟有限。通过浏览器原生支持这个API，解析和遍历DOM 树可以通过底层编译语言实现，性能也有了数量级的提升。

Selectors API Level 1 的核心是两个方法：querySelector()和querySelectorAll()。在兼容浏览器中，Document 类型和Element 类型的实例上都会暴露这两个方法。

Selectors API Level 2 规范在Element 类型上新增了更多方法，比如matches()、find()和findAll()。不过，目前还没有浏览器实现或宣称实现find()和findAll()。

### 15.1.1. querySelector()

querySelector()方法接收CSS 选择符参数，返回匹配该模式的第一个后代元素，如果没有匹配项则返回null。下面是一些例子：

```js
// 取得<body>元素
let body = document.querySelector("body");
// 取得ID 为"myDiv"的元素
let myDiv = document.querySelector("#myDiv");
// 取得类名为"selected"的第一个元素
let selected = document.querySelector(".selected");
// 取得类名为"button"的图片
let img = document.body.querySelector("img.button");
```

在Document 上使用querySelector()方法时，会从文档元素开始搜索；在Element 上使用querySelector()方法时，则只会从当前元素的后代中查询。

用于查询模式的CSS 选择符可繁可简，依需求而定。如果选择符有语法错误或碰到不支持的选择符，则querySelector()方法会抛出错误。

### 15.1.2. querySelectorAll()

querySelectorAll()方法跟querySelector()一样，也接收一个用于查询的参数，但它会返回所有匹配的节点，而不止一个。这个方法返回的是一个NodeList 的静态实例。

再强调一次，querySelectorAll()返回的NodeList 实例一个属性和方法都不缺，但它是一个静态的“快照”，而非“实时”的查询。这样的底层实现避免了使用NodeList 对象可能造成的性能问题。

以有效CSS 选择符调用querySelectorAll()都会返回NodeList，无论匹配多少个元素都可以。如果没有匹配项，则返回空的NodeList 实例。

与querySelector()一样，querySelectorAll()也可以在Document、DocumentFragment 和Element 类型上使用。下面是几个例子：

```js
// 取得ID 为"myDiv"的<div>元素中的所有<em>元素
let ems = document.getElementById("myDiv").querySelectorAll("em");
// 取得所有类名中包含"selected"的元素
let selecteds = document.querySelectorAll(".selected");
// 取得所有是<p>元素子元素的<strong>元素
let strongs = document.querySelectorAll("p strong");
```

返回的NodeList 对象可以通过for-of 循环、item()方法或中括号语法取得个别元素。比如：

```js
let strongElements = document.querySelectorAll("p strong");
// 以下3 个循环的效果一样
for (let strong of strongElements) {
strong.className = "important";
}
for (let i = 0; i < strongElements.length; ++i) {
strongElements.item(i).className = "important";
}
for (let i = 0; i < strongElements.length; ++i) {
strongElements[i].className = "important";
}
```

与querySelector()方法一样，如果选择符有语法错误或碰到不支持的选择符，则querySelectorAll()方法会抛出错误。

### 15.1.3. matches()

matches()方法（在规范草案中称为matchesSelector()）接收一个CSS 选择符参数，如果元素匹配则该选择符返回true，否则返回false。例如：

```js
if (document.body.matches("body.page1")){
// true
}
```

使用这个方法可以方便地检测某个元素会不会被querySelector()或querySelectorAll()方法返回。

所有主流浏览器都支持matches()。Edge、Chrome、Firefox、Safari 和Opera 完全支持，IE9~11及一些移动浏览器支持带前缀的方法。

## 15.2. 元素遍历

IE9 之前的版本不会把元素间的空格当成空白节点，而其他浏览器则会。这样就导致了childNodes和firstChild 等属性上的差异。为了弥补这个差异，同时不影响DOM规范，W3C 通过新的ElementTraversal 规范定义了一组新属性。

Element Traversal API 为DOM元素添加了5 个属性：

- childElementCount，返回子元素数量（不包含文本节点和注释）；
- firstElementChild，指向第一个Element 类型的子元素（Element 版firstChild）；
- lastElementChild，指向最后一个Element 类型的子元素（Element 版lastChild）；
- previousElementSibling ， 指向前一个Element 类型的同胞元素（ Element 版previousSibling）；
- nextElementSibling，指向后一个Element 类型的同胞元素（Element 版nextSibling）。

在支持的浏览器中，所有DOM 元素都会有这些属性，为遍历DOM 元素提供便利。这样开发者就不用担心空白文本节点的问题了。

举个例子，过去要以跨浏览器方式遍历特定元素的所有子元素，代码大致是这样写的：

```js
let parentElement = document.getElementById('parent');
let currentChildNode = parentElement.firstChild;
// 没有子元素，firstChild 返回null，跳过循环
while (currentChildNode) {
if (currentChildNode.nodeType === 1) {
// 如果有元素节点，则做相应处理
processChild(currentChildNode);
}
if (currentChildNode === parentElement.lastChild) {
break;
}
currentChildNode = currentChildNode.nextSibling;
}
```

使用Element Traversal 属性之后，以上代码可以简化如下：

```js
let parentElement = document.getElementById('parent');
let currentChildElement = parentElement.firstElementChild;
// 没有子元素，firstElementChild 返回null，跳过循环
while (currentChildElement) {
// 这就是元素节点，做相应处理
processChild(currentChildElement);
if (currentChildElement === parentElement.lastElementChild) {
break;
}
currentChildElement = currentChildElement.nextElementSibling;
}
```

IE9 及以上版本，以及所有现代浏览器都支持Element Traversal 属性。

## 15.3. HTML 5

HTML5 代表着与以前的HTML 截然不同的方向。在所有以前的HTML 规范中，从未出现过描述JavaScript 接口的情形，HTML 就是一个纯标记语言。JavaScript 绑定的事，一概交给DOM 规范去定义。

然而，HTML5 规范却包含了与标记相关的大量JavaScript API 定义。其中有的API 与DOM 重合，定义了浏览器应该提供的DOM扩展。

注意 因为HTML5 覆盖的范围极其广泛，所以本节主要讨论其影响所有DOM 节点的部分。HTML5 的其他部分将在本书后面的相关章节中再讨论。

### 15.3.1. CSS 类扩展

自HTML4 被广泛采用以来，Web 开发中一个主要的变化是class 属性用得越来越多，其用处是为元素添加样式以及语义信息。自然地，JavaScript 与CSS 类的交互就增多了，包括动态修改类名，以及根据给定的一个或一组类名查询元素，等等。为了适应开发者和他们对class 属性的认可，HTML5 增加了一些特性以方便使用CSS 类。

1. **getElementsByClassName()**

getElementsByClassName()是HTML5 新增的最受欢迎的一个方法，暴露在document 对象和所有HTML 元素上。 这个方法脱胎于基于原有DOM 特性实现该功能的JavaScript 库，提供了性能高好的原生实现。

getElementsByClassName()方法接收一个参数，即包含一个或多个类名的字符串，返回类名中包含相应类的元素的NodeList。如果提供了多个类名，则顺序无关紧要。下面是几个示例：

```js
// 取得所有类名中包含"username"和"current"元素
// 这两个类名的顺序无关紧要
let allCurrentUsernames = document.getElementsByClassName("username current");
// 取得ID 为"myDiv"的元素子树中所有包含"selected"类的元素
let selected = document.getElementById("myDiv").getElementsByClassName("selected");
```

这个方法只会返回以调用它的对象为根元素的子树中所有匹配的元素。在document 上调用getElementsByClassName()返回文档中所有匹配的元素，而在特定元素上调用getElementsByClassName()则返回该元素后代中匹配的元素。

如果要给包含特定类（而不是特定ID 或标签）的元素添加事件处理程序，使用这个方法会很方便。不过要记住，因为返回值是NodeList，所以使用这个方法会遇到跟使用getElementsByTagName()和其他返回NodeList 对象的DOM 方法同样的问题。

IE9 及以上版本，以及所有现代浏览器都支持getElementsByClassName()方法。

2. **classList 属性**

要操作类名，可以通过className 属性实现添加、删除和替换。但className 是一个字符串，所以每次操作之后都需要重新设置这个值才能生效，即使只改动了部分字符串也一样。以下面的HTML代码为例：

```html
<div class="bd user disabled">...</div>
```

这个`<div>`元素有3 个类名。要想删除其中一个，就得先把className 拆开，删除不想要的那个，再把包含剩余类的字符串设置回去。比如：

```js
// 要删除"user"类
let targetClass = "user";
// 把类名拆成数组
let classNames = div.className.split(/\s+/);
// 找到要删除类名的索引
let idx = classNames.indexOf(targetClass);
// 如果有则删除
if (idx > -1) {
classNames.splice(i,1);
}
// 重新设置类名
div.className = classNames.join(" ");
```

这就是从`<div>`元素的类名中删除"user"类要写的代码。替换类名和检测类名也要涉及同样的算法。添加类名只涉及字符串拼接，但必须先检查一下以确保不会重复添加相同的类名。很多JavaScript库为这些操作实现了便利方法。

HTML5 通过给所有元素增加classList 属性为这些操作提供了更简单也更安全的实现方式。classList 是一个新的集合类型DOMTokenList 的实例。与其他DOM集合类型一样，DOMTokenList也有length 属性表示自己包含多少项，也可以通过item()或中括号取得个别的元素。此外，
DOMTokenList 还增加了以下方法。

- add(value)，向类名列表中添加指定的字符串值value。如果这个值已经存在，则什么也不做。
- contains(value)，返回布尔值，表示给定的value 是否存在。
- remove(value)，从类名列表中删除指定的字符串值value。
- toggle(value)，如果类名列表中已经存在指定的value，则删除；如果不存在，则添加。

这样以来，前面的例子中那么多行代码就可以简化成下面的一行：

```js
div.classList.remove("user");
```

这行代码可以在不影响其他类名的情况下完成删除。其他方法同样极大地简化了操作类名的复杂性，如下面的例子所示：

```js
// 删除"disabled"类
div.classList.remove("disabled");
// 添加"current"类
div.classList.add("current");
// 切换"user"类
div.classList.toggle("user");
// 检测类名
if (div.classList.contains("bd") && !div.classList.contains("disabled")){
// 执行操作
)
// 迭代类名
for (let class of div.classList){
doStuff(class);
}
```

添加了classList 属性之后，除非是完全删除或完全重写元素的class 属性，否则className属性就用不到了。IE10 及以上版本（部分）和其他主流浏览器（完全）实现了classList 属性。

### 15.3.2. 焦点管理

HTML5 增加了辅助DOM焦点管理的功能。首先是document.activeElement，始终包含当前拥有焦点的DOM 元素。页面加载时，可以通过用户输入（按Tab 键或代码中使用focus()方法）让某个元素自动获得焦点。例如：

```js
let button = document.getElementById("myButton");
button.focus();
console.log(document.activeElement === button); // true
```

默认情况下，document.activeElement 在页面刚加载完之后会设置为document.body。而在页面完全加载之前，document.activeElement 的值为null。

其次是document.hasFocus()方法，该方法返回布尔值，表示文档是否拥有焦点：

```js
let button = document.getElementById("myButton");
button.focus();
console.log(document.hasFocus()); // true
```

确定文档是否获得了焦点，就可以帮助确定用户是否在操作页面。

第一个方法可以用来查询文档，确定哪个元素拥有焦点，第二个方法可以查询文档是否获得了焦点，而这对于保证Web 应用程序的无障碍使用是非常重要的。无障碍Web 应用程序的一个重要方面就是焦点管理，而能够确定哪个元素当前拥有焦点（相比于之前的猜测）是一个很大的进步。

### 15.3.3. HTMLDocument扩展

HTML5 扩展了HTMLDocument 类型，增加了更多功能。与其他HTML5 定义的DOM扩展一样，这些变化同样基于所有浏览器事实上都已经支持的专有扩展。为此，即使这些扩展的标准化相对较晚，很多浏览器也早就实现了相应的功能。

1. **readyState 属性**

readyState 是IE4 最早添加到document 对象上的属性，后来其他浏览器也都依葫芦画瓢地支持这个属性。最终，HTML5 将这个属性写进了标准。document.readyState 属性有两个可能的值：

- loading，表示文档正在加载；
- complete，表示文档加载完成。

实际开发中，最好是把document.readState 当成一个指示器，以判断文档是否加载完毕。在这个属性得到广泛支持以前，通常要依赖onload 事件处理程序设置一个标记，表示文档加载完了。这个属性的基本用法如下：

```js
if (document.readyState == "complete"){
// 执行操作
}
```

2. **compatMode 属性**

自从IE6 提供了以标准或混杂模式渲染页面的能力之后，检测页面渲染模式成为一个必要的需求。IE 为document 添加了compatMode 属性，这个属性唯一的任务是指示浏览器当前处于什么渲染模式。如下面的例子所示，标准模式下document.compatMode 的值是"CSS1Compat"，而在混杂模式下，document.compatMode 的值是"BackCompat"：

```js
if (document.compatMode == "CSS1Compat"){
console.log("Standards mode");
} else {
console.log("Quirks mode");
}
```

HTML5 最终也把compatMode 属性的实现标准化了。

3. **head 属性**

作为对document.body（指向文档的`<body>`元素）的补充，HTML5 增加了document.head 属性，指向文档的`<head>`元素。可以像下面这样直接取得`<head>`元素：

```js
let head = document.head;
```

### 15.3.4. 字符集属性

HTML5 增加了几个与文档字符集有关的新属性。其中，characterSet 属性表示文档实际使用的字符集，也可以用来指定新字符集。这个属性的默认值是"UTF-16"，但可以通过`<meta>`元素或响应头，以及新增的characterSeet 属性来修改。下面是一个例子：

```js
console.log(document.characterSet); // "UTF-16"
document.characterSet = "UTF-8";
```

### 15.3.5. 自定义数据属性

HTML5 允许给元素指定非标准的属性，但要使用前缀data-以便告诉浏览器，这些属性既不包含与渲染有关的信息，也不包含元素的语义信息。除了前缀，自定义属性对命名是没有限制的，data-后面跟什么都可以。下面是一个例子：

```html
<div id="myDiv" data-appId="12345" data-myname="Nicholas"></div>
```

定义了自定义数据属性后，可以通过元素的dataset 属性来访问。dataset 属性是一个DOMStringMap 的实例，包含一组键/值对映射。元素的每个data-name 属性在dataset 中都可以通过data-后面的字符串作为键来访问（例如，属性data-myname、data-myName 可以通过myname 访
问，但要注意data-my-name、data-My-Name 要通过myName 来访问）。下面是一个使用自定义数据属性的例子：

```js
// 本例中使用的方法仅用于示范
let div = document.getElementById("myDiv");
// 取得自定义数据属性的值
let appId = div.dataset.appId;
let myName = div.dataset.myname;
// 设置自定义数据属性的值
div.dataset.appId = 23456;
div.dataset.myname = "Michael";
// 有"myname"吗？
if (div.dataset.myname){
console.log(`Hello, ${div.dataset.myname}`);
}
```

自定义数据属性非常适合需要给元素附加某些数据的场景，比如链接追踪和在聚合应用程序中标识页面的不同部分。另外，单页应用程序框架也非常多地使用了自定义数据属性。

### 15.3.6. 插入标记

DOM 虽然已经为操纵节点提供了很多API，但向文档中一次性插入大量HTML 时还是比较麻烦。相比先创建一堆节点，再把它们以正确的顺序连接起来，直接插入一个HTML 字符串要简单（快速）得多。HTML5 已经通过以下DOM 扩展将这种能力标准化了。

1. **innerHTML 属性**

在读取innerHTML 属性时，会返回元素所有后代的HTML 字符串，包括元素、注释和文本节点。而在写入innerHTML 时，则会根据提供的字符串值以新的DOM 子树替代元素中原来包含的所有节点。比如下面的HTML 代码：

```html
<div id="content">
<p>This is a <strong>paragraph</strong> with a list following it.</p>
<ul>
<li>Item 1</li>
<li>Item 2</li>
<li>Item 3</li>
</ul>
</div>
```

对于这里的`<div>`元素而言，其innerHTML 属性会返回以下字符串：

```js
<p>This is a <strong>paragraph</strong> with a list following it.</p>
<ul>
<li>Item 1</li>
<li>Item 2</li>
<li>Item 3</li>
</ul>
```

实际返回的文本内容会因浏览器而不同。IE 和Opera 会把所有元素标签转换为大写，而Safari、Chrome 和Firefox 则会按照文档源代码的格式返回，包含空格和缩进。因此不要指望不同浏览器的innerHTML 会返回完全一样的值。

在写入模式下，赋给innerHTML 属性的值会被解析为DOM 子树，并替代元素之前的所有节点。因为所赋的值默认为HTML，所以其中的所有标签都会以浏览器处理HTML 的方式转换为元素（同样，转换结果也会因浏览器不同而不同）。如果赋值中不包含任何HTML 标签，则直接生成一个文本节点，
如下所示：

```js
div.innerHTML = "Hello world!";
```

因为浏览器会解析设置的值，所以给innerHTML 设置包含HTML 的字符串时，结果会大不一样。来看下面的例子：

```js
div.innerHTML = "Hello & welcome, <b>\"reader\"!</b>";
```

这个操作的结果相当于：

```html
<div id="content">Hello &amp; welcome, <b>&quot;reader&quot;!</b></div>
```

设置完innerHTML，马上就可以像访问其他节点一样访问这些新节点。

注意 设置innerHTML 会导致浏览器将HTML 字符串解析为相应的DOM 树。这意味着设置innerHTML 属性后马上再读出来会得到不同的字符串。这是因为返回的字符串是将原始字符串对应的DOM 子树序列化之后的结果。

2. **旧IE 中的innerHTML**

在所有现代浏览器中，通过innerHTML 插入的`<script>`标签是不会执行的。而在IE8 及之前的版本中，只要这样插入的`<script>`元素指定了defer 属性，且`<script>`之前是“受控元素”（scoped element），那就是可以执行的。`<script>`元素与`<style>`或注释一样，都是“非受控元素”（NoScope element），也就是在页面上看不到它们。IE 会把innerHTML 中从非受控元素开始的内容都删掉，也就是说下面的例子是行不通的：

```js
// 行不通
div.innerHTML = "<script defer>console.log('hi');<\/script>";
```

在这个例子中，innerHTML 字符串以一个非受控元素开始，因此整个字符串都会被清空。为了达到目的，必须在`<script>`前面加上一个受控元素，例如文本节点或没有结束标签的元素（如`<input>`）。因此，下面的代码就是可行的：

```js
// 以下都可行
div.innerHTML = "_<script defer>console.log('hi');<\/script>";
div.innerHTML = "<div>&nbsp;</div><script defer>console.log('hi');<\/script>";
div.innerHTML = "<input type=\"hidden\"><script defer>console.
log('hi');<\/script>";
```

第一行会在`<script>`元素前面插入一个文本节点。为了不影响页面排版，可能稍后需要删掉这个文本节点。第二行与之类似，使用了包含空格的`<div>`元素。空`<div>`是不行的，必须包含一点内容，以强制创建一个文本节点。同样，这个`<div>`元素可能也需要事后删除，以免影响页面外观。第三行使用了一个隐藏的`<input>`字段来达成同样的目的。因为这个字段不影响页面布局，所以应该是最理想的方案。

在IE 中，通过innerHTML 插入`<style>`也会有类似的问题。多数浏览器支持使用innerHTML 插入`<style>`元素：

```js
div.innerHTML = "<style type=\"text/css\">body {background-color: red; }</style>";
```

但在IE8 及之前的版本中，`<style>`也被认为是非受控元素，所以必须前置一个受控元素：

```js
div.innerHTML = "_<style type=\"text/css\">body {background-color: red; }</style>";
div.removeChild(div.firstChild);
```

注意 Firefox 在内容类型为application/xhtml+xml 的XHTML 文档中对innerHTML更加严格。在XHTML 文档中使用innerHTML，必须使用格式良好的XHTML 代码。否则，在Firefox 中会静默失败。

3. **outerHTML 属性**

读取outerHTML 属性时，会返回调用它的元素（及所有后代元素）的HTML 字符串。在写入outerHTML 属性时，调用它的元素会被传入的HTML 字符串经解释之后生成的DOM 子树取代。比如下面的HTML 代码：

```html
<div id="content">
<p>This is a <strong>paragraph</strong> with a list following it.</p>
<ul>
<li>Item 1</li>
<li>Item 2</li>
<li>Item 3</li>
</ul>
</div>
```

在这个`<div>`元素上调用outerHTML 会返回相同的字符串，包括`<div>`本身。注意，浏览器因解析和解释HTML 代码的机制不同，返回的字符串也可能不同。（跟innerHTML 的情况是一样的。）

如果使用outerHTML 设置HTML，比如：

```js
div.outerHTML = "<p>This is a paragraph.</p>";
```

则会得到与执行以下脚本相同的结果：`

```js
let p = document.createElement("p");
p.appendChild(document.createTextNode("This is a paragraph."));
div.parentNode.replaceChild(p, div);
```

新的`<p>`元素会取代DOM树中原来的`<div>`元素。

4. **insertAdjacentHTML()与insertAdjacentText()**

关于插入标签的最后两个新增方法是insertAdjacentHTML()和insertAdjacentText()。这两个方法最早源自IE，它们都接收两个参数：要插入标记的位置和要插入的HTML 或文本。第一个参数必须是下列值中的一个：

