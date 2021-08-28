**目录：**
- [14. DOM](#14-dom)
  - [14.1. 节点层次](#141-节点层次)
    - [14.1.1. Node 类型](#1411-node-类型)
    - [14.1.2. Document 类型](#1412-document-类型)
    - [14.1.3. Element 类型](#1413-element-类型)
    - [14.1.4. Text 类型](#1414-text-类型)
    - [14.1.5. Comment 类型](#1415-comment-类型)
    - [14.1.6. CDATASection 类型](#1416-cdatasection-类型)
    - [14.1.7. DocumentType 类型](#1417-documenttype-类型)
    - [14.1.8. DocumentFragment 类型](#1418-documentfragment-类型)
    - [14.1.9. Attr 类型](#1419-attr-类型)
  - [14.2. DOM 编程](#142-dom-编程)
    - [14.2.1. 动态脚本](#1421-动态脚本)
    - [14.2.2. 动态样式](#1422-动态样式)
    - [14.2.3. 操作表格](#1423-操作表格)
    - [14.2.4. 使用 NodeList](#1424-使用-nodelist)
  - [14.3. MutationObserver 接口](#143-mutationobserver-接口)
    - [14.3.1. 基本用法](#1431-基本用法)
    - [14.3.2. MutationObserverInit 与观察范围](#1432-mutationobserverinit-与观察范围)
    - [14.3.3. 异步回调与记录队列](#1433-异步回调与记录队列)
    - [14.3.4. 性能，内存与垃圾回收](#1434-性能内存与垃圾回收)

# 14. DOM

本章内容

- 理解文档对象模型（DOM）的构成
- 节点类型
- 浏览器兼容性
- MutationObserver 接口

**文档对象模型（DOM，Document Object Model）** 是 HTML 和 XML 文档的编程接口。DOM 表示由多层节点构成的文档，通过它开发者可以添加、删除和修改页面的各个部分。脱胎于网景和微软早期的动态 HTML（DHTML，Dynamic HTML），DOM 现在是真正跨平台、语言无关的表示和操作网页的方式。

DOM Level 1 在 1998 年成为 W3C 推荐标准，提供了基本文档结构和查询的接口。本章之所以介绍 DOM，主要因为它与浏览器中的 HTML 网页相关，并且在 JavaScript 中提供了 DOM API。

注意 IE8 及更低版本中的 DOM 是通过 COM 对象实现的。这意味着这些版本的 IE 中，DOM 对象跟原生 JavaScript 对象具有不同的行为和功能。

## 14.1. 节点层次

任何 HTML 或 XML 文档都可以用 DOM 表示为一个由节点构成的层级结构。节点分很多类型，每种类型对应着文档中不同的信息和（或）标记，也都有自己不同的特性、数据和方法，而且与其他类型有某种关系。这些关系构成了层级，让标记可以表示为一个以特定节点为根的树形结构。以下面的 HTML 为例：

```html
<html>
  <head>
    <title>Sample Page</title>
  </head>
  <body>
    <p>Hello World!</p>
  </body>
</html>
```

如果表示为层级结构，则如下图所示。

![14-1-DOM层次](illustrations/14-1-DOM层次.png)

其中，document 节点表示每个文档的根节点。在这里，根节点的唯一子节点是`<html>`元素，我们称之为 **文档元素（documentElement）**。文档元素是文档最外层的元素，所有其他元素都存在于这个元素之内。每个文档只能有一个文档元素。在 HTML 页面中，文档元素始终是`<html>`元素。在 XML 文档中，则没有这样预定义的元素，任何元素都可能成为文档元素。

HTML 中的每段标记都可以表示为这个树形结构中的一个节点。元素节点表示 HTML 元素，属性节点表示属性，文档类型节点表示文档类型，注释节点表示注释。DOM 中总共有 12 种节点类型，这些类型都继承一种基本类型。

### 14.1.1. Node 类型

DOM Level 1 描述了名为 Node 的接口，这个接口是所有 DOM 节点类型都必须实现的。Node 接口在 JavaScript 中被实现为 Node 类型，在除 IE 之外的所有浏览器中都可以直接访问这个类型。在 JavaScript 中，所有节点类型都继承 Node 类型，因此所有类型都共享相同的基本属性和方法。

每个节点都有 nodeType 属性，表示该节点的类型。节点类型由定义在 Node 类型上的 12 个数值常量表示：

- Node.ELEMENT_NODE（1）
- Node.ATTRIBUTE_NODE（2）
- Node.TEXT_NODE（3）
- Node.CDATA_SECTION_NODE（4）
- Node.ENTITY_REFERENCE_NODE（5）
- Node.ENTITY_NODE（6）
- Node.PROCESSING_INSTRUCTION_NODE（7）
- Node.COMMENT_NODE（8）
- Node.DOCUMENT_NODE（9）
- Node.DOCUMENT_TYPE_NODE（10）
- Node.DOCUMENT_FRAGMENT_NODE（11）
- Node.NOTATION_NODE（12）

节点类型可通过与这些常量比较来确定，比如：

```js
if (someNode.nodeType == Node.ELEMENT_NODE) {
  alert("Node is an element.");
}
```

这个例子比较了 someNode.nodeType 与 Node.ELEMENT_NODE 常量。如果两者相等，则意味着 someNode 是一个元素节点。

浏览器并不支持所有节点类型。开发者最常用到的是元素节点和文本节点。本章后面会讨论每种节点受支持的程度及其用法。

1. **nodeName 与 nodeValue**

nodeName 与 nodeValue 保存着有关节点的信息。这两个属性的值完全取决于节点类型。在使用这两个属性前，最好先检测节点类型，如下所示：

```js
if (someNode.nodeType == 1) {
  value = someNode.nodeName; // 会显示元素的标签名
}
```

在这个例子中，先检查了节点是不是元素。如果是，则将其 nodeName 的值赋给一个变量。对元素而言，nodeName 始终等于元素的标签名，而 nodeValue 则始终为 null。

2. **节点关系**

文档中的所有节点都与其他节点有关系。这些关系可以形容为家族关系，相当于把文档树比作家谱。在 HTML 中，`<body>`元素是`<html>`元素的子元素，而`<html>`元素则是`<body>`元素的父元素。`<head>`元素是`<body>`元素的同胞元素，因为它们有共同的父元素`<html>`。

每个节点都有一个 childNodes 属性，其中包含一个 NodeList 的实例。NodeList 是一个类数组对象，用于存储可以按位置存取的有序节点。注意，NodeList 并不是 Array 的实例，但可以使用中括号访问它的值，而且它也有 length 属性。NodeList 对象独特的地方在于，它其实是一个对 DOM 结构的查询，因此 DOM 结构的变化会自动地在 NodeList 中反映出来。我们通常说 NodeList 是实时的活动对象，而不是第一次访问时所获得内容的快照。

下面的例子展示了如何使用中括号或使用 item()方法访问 NodeList 中的元素：

```js
let firstChild = someNode.childNodes[0];
let secondChild = someNode.childNodes.item(1);
let count = someNode.childNodes.length;
```

无论是使用中括号还是 item()方法都是可以的，但多数开发者倾向于使用中括号，因为它是一个类数组对象。注意，length 属性表示那一时刻 NodeList 中节点的数量。使用...可以像前面介绍 arguments 时一样把 NodeList 对象转换为数组。比如：

```js
let arrayOfNodes = [...someNode.childNodes];
```

每个节点都有一个 parentNode 属性，指向其 DOM 树中的父元素。childNodes 中的所有节点都有同一个父元素，因此它们的 parentNode 属性都指向同一个节点。此外，childNodes 列表中的每个节点都是同一列表中其他节点的同胞节点。而使用 previousSibling 和 nextSibling 可以在这个列表的节点间导航。这个列表中第一个节点的 previousSibling 属性是 null，最后一个节点的 nextSibling 属性也是 null，如下所示：

```js
if (someNode.nextSibling === null) {
  alert("Last node in the parent's childNodes list.");
} else if (someNode.previousSibling === null) {
  alert("First node in the parent's childNodes list.");
}
```

注意，如果 childNodes 中只有一个节点，则它的 previousSibling 和 nextSibling 属性都是 null。

父节点和它的第一个及最后一个子节点也有专门属性：firstChild 和 lastChild 分别指向 childNodes 中的第一个和最后一个子节点。someNode.firstChild 的值始终等于 someNode.childNodes[0]，而 someNode.lastChild 的值始终等于 someNode.childNodes[someNode.childNodes.length-1]。如果只有一个子节点，则 firstChild 和 lastChild 指向同一个节点。如果没有子节点，则 firstChild 和 lastChild 都是 null。上述这些节点之间的关系为在文档树的节点之间导航提供了方便。下图形象地展示了这些关系。

![14-2-节点关系](illustrations/14-2-节点关系.png)

有了这些关系，childNodes 属性的作用远远不止是必备属性那么简单了。这是因为利用这些关系指针，几乎可以访问到文档树中的任何节点，而这种便利性是 childNodes 的最大亮点。还有一个便利的方法是 hasChildNodes()，这个方法如果返回 true 则说明节点有一个或多个子节点。相比查询 childNodes 的 length 属性，这个方法无疑更方便。

最后还有一个所有节点都共享的关系。ownerDocument 属性是一个指向代表整个文档的文档节点的指针。所有节点都被创建它们（或自己所在）的文档所拥有，因为一个节点不可能同时存在于两个或者多个文档中。这个属性为迅速访问文档节点提供了便利，因为无需在文档结构中逐层上溯了。

注意 虽然所有节点类型都继承了 Node，但并非所有节点都有子节点。本章后面会讨论不同节点类型的差异。

3. **操纵节点**

因为所有关系指针都是只读的，所以 DOM 又提供了一些操纵节点的方法。最常用的方法是 appendChild()，用于在 childNodes 列表末尾添加节点。添加新节点会更新相关的关系指针，包括父节点和之前的最后一个子节点。appendChild()方法返回新添加的节点，如下所示：

```js
let returnedNode = someNode.appendChild(newNode);
alert(returnedNode == newNode); // true
alert(someNode.lastChild == newNode); // true
```

如果把文档中已经存在的节点传给 appendChild()，则这个节点会从之前的位置被转移到新位置。即使 DOM 树通过各种关系指针维系，一个节点也不会在文档中同时出现在两个或更多个地方。因此，如果调用 appendChild()传入父元素的第一个子节点，则这个节点会成为父元素的最后一个子节点，如下所示：

```js
// 假设someNode 有多个子节点
let returnedNode = someNode.appendChild(someNode.firstChild);
alert(returnedNode == someNode.firstChild); // false
alert(returnedNode == someNode.lastChild); // true
```

如果想把节点放到 childNodes 中的特定位置而不是末尾，则可以使用 insertBefore()方法。这个方法接收两个参数：要插入的节点和参照节点。调用这个方法后，要插入的节点会变成参照节点的前一个同胞节点，并被返回。如果参照节点是 null，则 insertBefore()与 appendChild()效果相
同，如下面的例子所示：

```js
// 作为最后一个子节点插入
returnedNode = someNode.insertBefore(newNode, null);
alert(newNode == someNode.lastChild); // true
// 作为新的第一个子节点插入
returnedNode = someNode.insertBefore(newNode, someNode.firstChild);
alert(returnedNode == newNode); // true
alert(newNode == someNode.firstChild); // true
// 插入最后一个子节点前面
returnedNode = someNode.insertBefore(newNode, someNode.lastChild);
alert(newNode == someNode.childNodes[someNode.childNodes.length - 2]); // true
```

appendChild() 和 insertBefore() 在插入节点时不会删除任何已有节点。相对地，replaceChild()方法接收两个参数：要插入的节点和要替换的节点。要替换的节点会被返回并从文档树中完全移除，要插入的节点会取而代之。下面看一个例子：

```js
// 替换第一个子节点
let returnedNode = someNode.replaceChild(newNode, someNode.firstChild);
// 替换最后一个子节点
returnedNode = someNode.replaceChild(newNode, someNode.lastChild);
```

使用 replaceChild()插入一个节点后，所有关系指针都会从被替换的节点复制过来。虽然被替换的节点从技术上说仍然被同一个文档所拥有，但文档中已经没有它的位置。

要移除节点而不是替换节点，可以使用 removeChild()方法。这个方法接收一个参数，即要移除的节点。被移除的节点会被返回，如下面的例子所示：

```js
// 删除第一个子节点
let formerFirstChild = someNode.removeChild(someNode.firstChild);
// 删除最后一个子节点
let formerLastChild = someNode.removeChild(someNode.lastChild);
```

与 replaceChild()方法一样，通过 removeChild()被移除的节点从技术上说仍然被同一个文档所拥有，但文档中已经没有它的位置。

上面介绍的 4 个方法都用于操纵某个节点的子元素，也就是说使用它们之前必须先取得父节点（使用前面介绍的 parentNode 属性）。并非所有节点类型都有子节点，如果在不支持子节点的节点上调用这些方法，则会导致抛出错误。

4. **其他方法**

所有节点类型还共享了两个方法。第一个是 cloneNode()，会返回与调用它的节点一模一样的节点。cloneNode()方法接收一个布尔值参数，表示是否深复制。在传入 true 参数时，会进行深复制，即复制节点及其整个子 DOM 树。如果传入 false，则只会复制调用该方法的节点。复制返回的节点属
于文档所有，但尚未指定父节点，所以可称为孤儿节点（orphan）。可以通过 appendChild()、insertBefore()或 replaceChild()方法把孤儿节点添加到文档中。以下面的 HTML 片段为例：

```html
<ul>
  <li>item 1</li>
  <li>item 2</li>
  <li>item 3</li>
</ul>
```

如果 myList 保存着对这个`<ul>`元素的引用，则下列代码展示了使用 cloneNode()方法的两种方式：

```js
let deepList = myList.cloneNode(true);
alert(deepList.childNodes.length); // 3（IE9 之前的版本）或7（其他浏览器）
let shallowList = myList.cloneNode(false);
alert(shallowList.childNodes.length); // 0
```

在这个例子中，deepList 保存着 myList 的副本。这意味着 deepList 有 3 个列表项，每个列表项又各自包含文本。变量 shallowList 则保存着 myList 的浅副本， 因此没有子节点。deepList.childNodes.length 的值会因 IE8 及更低版本和其他浏览器对空格的处理方式而不同。IE9
之前的版本不会为空格创建节点。

注意 cloneNode()方法不会复制添加到 DOM 节点的 JavaScript 属性，比如事件处理程序。这个方法只复制 HTML 属性，以及可选地复制子节点。除此之外则一概不会复制。IE 在很长时间内会复制事件处理程序，这是一个 bug，所以推荐在复制前先删除事件处理程序。

本节要介绍的最后一个方法是 normalize()。这个方法唯一的任务就是处理文档子树中的文本节点。由于解析器实现的差异或 DOM 操作等原因，可能会出现并不包含文本的文本节点，或者文本节点之间互为同胞关系。在节点上调用 normalize()方法会检测这个节点的所有后代，从中搜索上述两种
情形。如果发现空文本节点，则将其删除；如果两个同胞节点是相邻的，则将其合并为一个文本节点。这个方法将在本章后面进一步讨论。

### 14.1.2. Document 类型

Document 类型是 JavaScript 中表示文档节点的类型。在浏览器中，文档对象 document 是 HTMLDocument 的实例（HTMLDocument 继承 Document），表示整个 HTML 页面。document 是 window 对象的属性，因此是一个全局对象。Document 类型的节点有以下特征：

- nodeType 等于 9；
- nodeName 值为"#document"；
- nodeValue 值为 null；
- parentNode 值为 null；
- ownerDocument 值为 null；
- 子节点可以是 DocumentType（最多一个）、Element（最多一个）、ProcessingInstruction 或 Comment 类型。

Document 类型可以表示 HTML 页面或其他 XML 文档，但最常用的还是通过 HTMLDocument 的实例取得 document 对象。document 对象可用于获取关于页面的信息以及操纵其外观和底层结构。

1. **文档子节点**

虽然 DOM 规范规定 Document 节点的子节点可以是 DocumentType、Element、ProcessingInstruction 或 Comment，但也提供了两个访问子节点的快捷方式。第一个是 documentElement 属性，始终指向 HTML 页面中的`<html>`元素。虽然 document.childNodes 中始终有`<html>`元素，但使用 documentElement 属性可以更快更直接地访问该元素。假如有以下简单的页面：

```html
<html>
  <body></body>
</html>
```

浏览器解析完这个页面之后，文档只有一个子节点，即`<html>`元素。这个元素既可以通过 documentElement 属性获取，也可以通过 childNodes 列表访问，如下所示：

```js
let html = document.documentElement; // 取得对<html>的引用
alert(html === document.childNodes[0]); // true
alert(html === document.firstChild); // true
```

作为 HTMLDocument 的实例，document 对象还有一个 body 属性，直接指向`<body>`元素。因为这个元素是开发者使用最多的元素，所以 JavaScript 代码中经常可以看到 document.body，比如：

```js
let body = document.body; // 取得对<body>的引用
```

所有主流浏览器都支持 document.documentElement 和 document.body。

Document 类型另一种可能的子节点是 DocumentType。<!doctype>标签是文档中独立的部分，其信息可以通过 doctype 属性（在浏览器中是 document.doctype）来访问，比如：

```js
let doctype = document.doctype; // 取得对<!doctype>的引用
```

另外，严格来讲出现在`<html>`元素外面的注释也是文档的子节点，它们的类型是 Comment。不过，由于浏览器实现不同，这些注释不一定能被识别，或者表现可能不一致。比如以下 HTML 页面：

```html
<!-- 第一条注释 -->
<html>
  <body></body>
</html>
<!-- 第二条注释 -->
```

这个页面看起来有 3 个子节点：注释、`<html>`元素、注释。逻辑上讲，document.childNodes 应该包含 3 项，对应代码中的每个节点。但实际上，浏览器有可能以不同方式对待`<html>`元素外部的注释，比如忽略一个或两个注释。

一般来说，appendChild()、removeChild()和 replaceChild()方法不会用在 document 对象上。这是因为文档类型（如果存在）是只读的，而且只能有一个 Element 类型的子节点（即`<html>`，已经存在了）。

2. **文档信息**

document 作为 HTMLDocument 的实例，还有一些标准 Document 对象上所没有的属性。这些属性提供浏览器所加载网页的信息。其中第一个属性是 title，包含`<title>`元素中的文本，通常显示在浏览器窗口或标签页的标题栏。通过这个属性可以读写页面的标题，修改后的标题也会反映在浏览器标题栏上。不过，修改 title 属性并不会改变`<title>`元素。下面是一个例子：

```js
// 读取文档标题
let originalTitle = document.title;
// 修改文档标题
document.title = "New page title";
```

接下来要介绍的 3 个属性是 URL、domain 和 referrer。其中，URL 包含当前页面的完整 URL（地址栏中的 URL），domain 包含页面的域名，而 referrer 包含链接到当前页面的那个页面的 URL。如果当前页面没有来源，则 referrer 属性包含空字符串。所有这些信息都可以在请求的 HTTP 头部信息中获取，只是在 JavaScript 中通过这几个属性暴露出来而已，如下面的例子所示：

```js
// 取得完整的URL
let url = document.URL;
// 取得域名
let domain = document.domain;
// 取得来源
let referrer = document.referrer;
```

URL 跟域名是相关的。比如，如果 document.URL 是http://www.google.com/something，则document.domain 就是www.google.com。

在这些属性中，只有 domain 属性是可以设置的。出于安全考虑，给 domain 属性设置的值是有限制的。如果 URL 包含子域名如 topics.google.com，则可以将 domain 设置为"google.com"（URL 包含“www”时也一样，比如www.google.com）。不能给这个属性设置URL 中不包含的值，比如：

```js
// 页面来自topics.google.com
document.domain = "google.com"; // 成功
document.domain = "baidu.com"; // 出错！
```

当页面中包含来自某个不同子域的窗格（`<frame>`）或内嵌窗格（`<iframe>`）时，设置 document.domain 是有用的。因为跨源通信存在安全隐患，所以不同子域的页面间无法通过 JavaScript 通信。此时，在每个页面上把 document.domain 设置为相同的值，这些页面就可以访问对方的 JavaScript 对象了。比如，一个加载自www.google.com 的页面中包含一个内嵌窗格，其中的页面加载自 topics.google.com。这两个页面的 document.domain 包含不同的字符串，内部和外部页面相互之间不能访问对方的 JavaScript 对象。如果每个页面都把 document.domain 设置为 google.com，那这两个页面之间就可以通信了。

浏览器对 domain 属性还有一个限制， 即这个属性一旦放松就不能再收紧。比如， 把 document.domain 设置为"google.com"之后，就不能再将其设置回"topics.google.com"，后者会导致错误，比如：

```js
// 页面来自topics.google.com
document.domain = "google.com"; // 放松，成功
document.domain = "topics.google.com"; // 收紧，错误！
```

3. **定位元素**

使用 DOM 最常见的情形可能就是获取某个或某组元素的引用，然后对它们执行某些操作。document 对象上暴露了一些方法，可以实现这些操作。getElementById()和 getElementsByTagName()就是 Document 类型提供的两个方法。

getElementById()方法接收一个参数，即要获取元素的 ID，如果找到了则返回这个元素，如果没找到则返回 null。参数 ID 必须跟元素在页面中的 id 属性值完全匹配，包括大小写。比如页面中有以下元素：

```html
<div id="myDiv">Some text</div>
```

可以使用如下代码取得这个元素：

```js
let div = document.getElementById("myDiv"); // 取得对这个<div>元素的引用
```

但参数大小写不匹配会返回 null：

```js
let div = document.getElementById("mydiv"); // null
```

如果页面中存在多个具有相同 ID 的元素，则 getElementById()返回在文档中出现的第一个元素。

getElementsByTagName()是另一个常用来获取元素引用的方法。这个方法接收一个参数，即要获取元素的标签名，返回包含零个或多个元素的 NodeList。在 HTML 文档中，这个方法返回一个 HTMLCollection 对象。考虑到二者都是“实时”列表，HTMLCollection 与 NodeList 是很相似的。
例如，下面的代码会取得页面中所有的`<img>`元素并返回包含它们的 HTMLCollection：

```js
let images = document.getElementsByTagName("img");
```

这里把返回的 HTMLCollection 对象保存在了变量 images 中。与 NodeList 对象一样，也可以使用中括号或 item()方法从 HTMLCollection 取得特定的元素。而取得元素的数量同样可以通过 length 属性得知，如下所示：

```js
alert(images.length); // 图片数量
alert(images[0].src); // 第一张图片的src 属性
alert(images.item(0).src); // 同上
```

HTMLCollection 对象还有一个额外的方法 namedItem()，可通过标签的 name 属性取得某一项的引用。例如，假设页面中包含如下的`<img>`元素：

```html
<img src="myimage.gif" name="myImage" />
```

那么也可以像这样从 images 中取得对这个`<img>`元素的引用：

```js
let myImage = images.namedItem("myImage");
```

这样，HTMLCollection 就提供了除索引之外的另一种获取列表项的方式，从而为取得元素提供了便利。对于 name 属性的元素，还可以直接使用中括号来获取，如下面的例子所示：

```js
let myImage = images["myImage"];
```

对 HTMLCollection 对象而言，中括号既可以接收数值索引，也可以接收字符串索引。而在后台，数值索引会调用 item()，字符串索引会调用 namedItem()。

要取得文档中的所有元素，可以给 getElementsByTagName()传入*。在 JavaScript 和 CSS 中，*一般被认为是匹配一切的字符。来看下面的例子：

```
let allElements = document.getElementsByTagName("*");
```

这行代码可以返回包含页面中所有元素的 HTMLCollection 对象，顺序就是它们在页面中出现的顺序。因此第一项是`<html>`元素，第二项是`<head>`元素，以此类推。

注意 对于 document.getElementsByTagName()方法，虽然规范要求区分标签的大小写，但为了最大限度兼容原有 HTML 页面，实际上是不区分大小写的。如果是在 XML 页面（如 XHTML）中使用，那么 document.getElementsByTagName()就是区分大小写的。

HTMLDocument 类型上定义的获取元素的第三个方法是 getElementsByName()。顾名思义，这个方法会返回具有给定 name 属性的所有元素。getElementsByName()方法最常用于单选按钮，因为同一字段的单选按钮必须具有相同的 name 属性才能确保把正确的值发送给服务器，比如下面的例子：

```html
<fieldset>
  <legend>Which color do you prefer?</legend>
  <ul>
    <li>
      <input type="radio" value="red" name="color" id="colorRed" />
      <label for="colorRed">Red</label>
    </li>
    <li>
      <input type="radio" value="green" name="color" id="colorGreen" />
      <label for="colorGreen">Green</label>
    </li>
    <li>
      <input type="radio" value="blue" name="color" id="colorBlue" />
      <label for="colorBlue">Blue</label>
    </li>
  </ul>
</fieldset>
```

这里所有的单选按钮都有名为"color"的 name 属性，但它们的 ID 都不一样。这是因为 ID 是为了匹配对应的`<label>`元素，而 name 相同是为了保证只将三个中的一个值发送给服务器。然后就可以像下面这样取得所有单选按钮：

```js
let radios = document.getElementsByName("color");
```

与 getElementsByTagName()一样，getElementsByName()方法也返回 HTMLCollection。不过在这种情况下，namedItem()方法只会取得第一项（因为所有项的 name 属性都一样）。

4. **特殊集合**

document 对象上还暴露了几个特殊集合，这些集合也都是 HTMLCollection 的实例。这些集合是访问文档中公共部分的快捷方式，列举如下。

- document.anchors 包含文档中所有带 name 属性的`<a>`元素。
- document.forms 包含文档中所有`<form>`元素（与 document.getElementsByTagName("form")返回的结果相同）。
- document.images 包含文档中所有`<img>`元素（与 document.getElementsByTagName("img")返回的结果相同）。
- document.links 包含文档中所有带 href 属性的`<a>`元素。

这些特殊集合始终存在于 HTMLDocument 对象上，而且与所有 HTMLCollection 对象一样，其内容也会实时更新以符合当前文档的内容。

5. **DOM 兼容性检测**

由于 DOM 有多个 Level 和多个部分，因此确定浏览器实现了 DOM 的哪些部分是很必要的。document.implementation 属性是一个对象，其中提供了与浏览器 DOM 实现相关的信息和能力。DOM Level 1 在 document.implementation 上只定义了一个方法，即 hasFeature()。这个方法接
收两个参数：特性名称和 DOM 版本。如果浏览器支持指定的特性和版本，则 hasFeature()方法返回 true，如下面的例子所示：

```js
let hasXmlDom = document.implementation.hasFeature("XML", "1.0");
```

可以使用 hasFeature()方法测试的特性及版本如下表所列。

| 特 性              | 支持的版本    | 说 明                                                       |
| ------------------ | ------------- | ----------------------------------------------------------- |
| Core               | 1.0、2.0、3.0 | 定义树形文档结构的基本 DOM                                  |
| XML                | 1.0、2.0、3.0 | Core 的 XML 扩展，增加了对 CDATA 区块、处理指令和实体的支持 |
| HTML               | 1.0、2.0      | XML 的 HTML 扩展，增加了 HTML 特定的元素和实体              |
| Views              | 2.0           | 文档基于某些样式的实现格式                                  |
| StyleSheets        | 2.0           | 文档的相关样式表                                            |
| CSS                | 2.0           | Cascading Style Sheets Level 1                              |
| CSS2               | 2.0           | Cascading Style Sheets Level 2                              |
| Events             | 2.0、3.0      | 通用 DOM 事件                                               |
| UIEvents           | 2.0、3.0      | 用户界面事件                                                |
| TextEvents         | 3.0           | 文本输入设备触发的事件                                      |
| MouseEvents        | 2.0、3.0      | 鼠标导致的事件（单击、悬停等）                              |
| MutationEvents     | 2.0、3.0      | DOM 树变化时触发的事件                                      |
| MutationNameEvents | 3.0           | DOM 元素或元素属性被重命名时触发的事件                      |
| HTMLEvents         | 2.0           | HTML 4.01 事件                                              |
| Range              | 2.0           | 在 DOM 树中操作一定范围的对象和方法                         |
| Traversal          | 2.0           | 遍历 DOM 树的方法                                           |
| LS                 | 3.0           | 文件与 DOM 树之间的同步加载与保存                           |
| LS-Async           | 3.0           | 文件与 DOM 树之间的异步加载与保存                           |
| Validation         | 3.0           | 修改 DOM 树并保证其继续有效的方法                           |
| XPath              | 3.0           | 访问 XML 文档不同部分的语言                                 |

由于实现不一致，因此 hasFeature()的返回值并不可靠。目前这个方法已经被废弃，不再建议使用。为了向后兼容，目前主流浏览器仍然支持这个方法，但无论检测什么都一律返回 true。

6. **文档写入**

document 对象有一个古老的能力，即向网页输出流中写入内容。这个能力对应 4 个方法：write()、writeln()、open()和 close()。其中，write()和 writeln()方法都接收一个字符串参数，可以将这个字符串写入网页中。write()简单地写入文本，而 writeln()还会在字符串末尾追加一个换行符（\n）。这两个方法可以用来在页面加载期间向页面中动态添加内容，如下所示：

```html
<html>
  <head>
    <title>document.write() Example</title>
  </head>
  <body>
    <p>
      The current date and time is:
      <script type="text/javascript">
        document.write("<strong>" + new Date().toString() + "</strong>");
      </script>
    </p>
  </body>
</html>
```

这个例子会在页面加载过程中输出当前日期和时间。日期放在了`<strong>`元素中，如同它们之前就包含在 HTML 页面中一样。这意味着会创建一个 DOM 元素，以后也可以访问。通过 write()和 writeln()输出的任何 HTML 都会以这种方式来处理。

write()和 writeln()方法经常用于动态包含外部资源，如 JavaScript 文件。在包含 JavaScript 文件时，记住不能像下面的例子中这样直接包含字符串"`</script>`"，因为这个字符串会被解释为脚本块的结尾，导致后面的代码不能执行：

```html
<html>
<head>
  <title>document.write() Example</title>
</head>
<body>
<script type="text/javascript">
document.write("<script type=\"text/javascript\" src=\"file.js\">" +
"</script>");
</script>
</body>
</html>
```

虽然这样写看起来没错，但输出之后的"`</script>`"会匹配最外层的`<script>`标签，导致页面中显示出");。为避免出现这个问题，需要对前面的例子稍加修改：

```html
<html>
  <head>
    <title>document.write() Example</title>
  </head>
  <body>
    <script type="text/javascript">
      document.write(
        '<script type="text/javascript" src="file.js">' + "<\/script>"
      );
    </script>
  </body>
</html>
```

这里的字符串"<\/script>"不会再匹配最外层的`<script>`标签，因此不会在页面中输出额外内容。

前面的例子展示了在页面渲染期间通过 document.write()向文档中输出内容。如果是在页面加载完之后再调用 document.write()，则输出的内容会重写整个页面，如下面的例子所示：

```html
<html>
  <head>
    <title>document.write() Example</title>
  </head>
  <body>
    <p>
      This is some content that you won't get to see because it will be
      overwritten.
    </p>
    <script type="text/javascript">
      window.onload = function () {
        document.write("Hello world!");
      };
    </script>
  </body>
</html>
```

这个例子使用了 window.onload 事件处理程序，将调用 document.write()的函数推迟到页面加载完毕后执行。执行之后，字符串"Hello world!"会重写整个页面内容。

open()和 close()方法分别用于打开和关闭网页输出流。在调用 write()和 writeln()时，这两个方法都不是必需的。

注意 严格的 XHTML 文档不支持文档写入。对于内容类型为 application/xml+xhtml 的页面，这些方法不起作用。

### 14.1.3. Element 类型

除了 Document 类型，Element 类型就是 Web 开发中最常用的类型了。Element 表示 XML 或 HTML 元素，对外暴露出访问元素标签名、子节点和属性的能力。Element 类型的节点具有以下特征：

- nodeType 等于 1；
- nodeName 值为元素的标签名；
- nodeValue 值为 null；
- parentNode 值为 Document 或 Element 对象；
- 子节点可以是 Element、Text、Comment、ProcessingInstruction、CDATASection、EntityReference 类型。

可以通过 nodeName 或 tagName 属性来获取元素的标签名。这两个属性返回同样的值（添加后一个属性明显是为了不让人误会）。比如有下面的元素：

```html
<div id="myDiv"></div>
```

可以像这样取得这个元素的标签名：

```js
const myDiv = document.getElementById("myDiv");
console.log(myDiv.nodeName); // DIV
console.log(myDIv.tagName); // DIV
```

例子中的元素标签名为 div，ID 为"myDiv"。注意，div.tagName 实际上返回的是"DIV"而不是"div"。在 HTML 中，元素标签名始终以全大写表示；在 XML（包括 XHTML）中，标签名始终与源代码中的大小写一致。如果不确定脚本是在 HTML 文档还是 XML 文档中运行，最好将标签名转换为小写形式，以便于比较：

```js
if (element.tagName === "div") {
  // 不要这样做，可能出错！
  // do something here
}
if (element.tagName.toLowerCase() === "div") {
  // 推荐，适用于所有文档
  // 做点什么
}
```

这个例子演示了比较 tagName 属性的情形。第一个是容易出错的写法，因为 HTML 文档中 tagName 返回大写形式的标签名。第二个先把标签名转换为全部小写后再比较，这是推荐的做法，因为这对 HTML 和 XML 都适用。

1. **HTML 元素**

所有 HTML 元素都通过 HTMLElement 类型表示，包括其直接实例和间接实例。另外，HTMLElement 直接继承 Element 并增加了一些属性。每个属性都对应下列属性之一，它们是所有 HTML 元素上都有的标准属性：

- id，元素在文档中的唯一标识符；
- title，包含元素的额外信息，通常以提示条形式展示；
- lang，元素内容的语言代码（很少用）；
- dir，语言的书写方向（"ltr"表示从左到右，"rtl"表示从右到左，同样很少用）；
- className，相当于 class 属性，用于指定元素的 CSS 类（因为 class 是 ECMAScript 关键字，所以不能直接用这个名字）。

所有这些都可以用来获取对应的属性值，也可以用来修改相应的值。比如有下面的 HTML 元素：

```html
<div id="myDiv" class="bd" title="Body text" lang="en" dir="ltr"></div>
```

这个元素中的所有属性都可以使用下列 JavaScript 代码读取：

```js
let div = document.getElementById("myDiv");
console.log(div.id); // "myDiv"
console.log(div.className); // "bd"
console.log(div.title); // "Body text"
console.log(div.lang); // "en"
console.log(div.dir); // "ltr"
```

而且，可以使用下列代码修改元素的属性：

```js
div.id = "someOtherId";
div.className = "ft";
div.title = "Some other text";
div.lang = "fr";
div.dir = "rtl";
```

并非所有这些属性的修改都会对页面产生影响。比如，把 id 或 lang 改成其他值对用户是不可见的（假设没有基于这两个属性应用 CSS 样式），而修改 title 属性则只会在鼠标移到这个元素上时才会反映出来。修改 dir 会导致页面文本立即向左或向右对齐。修改 className 会立即反映应用到新类名的 CSS 样式（如果定义了不同的样式）。

如前所述，所有 HTML 元素都是 HTMLElement 或其子类型的实例。下表列出了所有 HTML 元素及其对应的类型（斜体表示已经废弃的元素）。

| 元 素      | 类 型                   | 元 素    | 类 型                   |
| ---------- | ----------------------- | -------- | ----------------------- |
| A          | HTMLAnchorElement       | COL      | HTMLTableColElement     |
| ABBR       | HTMLElement             | COLGROUP | HTMLTableColElement     |
| ACRONYM    | HTMLElement             | DD       | HTMLElement             |
| ADDRESS    | HTMLElement             | DEL      | HTMLModElement          |
| _APPLET_   | HTMLAppletElement       | DFN      | HTMLElement             |
| AREA       | HTMLAreaElement         | _DIR_    | HTMLDirectoryElement    |
| B          | HTMLElement             | DIV      | HTMLDivElement          |
| BASE       | HTMLBaseElement         | DL       | HTMLDListElement        |
| _BASEFONT_ | HTMLBaseFontElement     | DT       | HTMLElement             |
| BDO        | HTMLElement             | EM       | HTMLElement             |
| BIG        | HTMLElement             | FIELDSET | HTMLFieldSetElement     |
| BLOCKQUOTE | HTMLQuoteElement        | _FONT_   | HTMLFontElement         |
| BODY       | HTMLBodyElement         | FORM     | HTMLFormElement         |
| BR         | HTMLBRElement           | FRAME    | HTMLFrameElement        |
| BUTTON     | HTMLButtonElement       | FRAMESET | HTMLFrameSetElement     |
| CAPTION    | HTMLTableCaptionElement | H1       | HTMLHeadingElement      |
| _CENTER_   | HTMLElement             | H2       | HTMLHeadingElement      |
| CITE       | HTMLElement             | H3       | HTMLHeadingElement      |
| CODE       | HTMLElement             | H4       | HTMLHeadingElement      |
| H5         | HTMLHeadingElement      | PRE      | HTMLPreElement          |
| H6         | HTMLHeadingElement      | Q        | HTMLQuoteElement        |
| HEAD       | HTMLHeadElement         | _S_      | HTMLElement             |
| HR         | HTMLHRElement           | SAMP     | HTMLElement             |
| HTML       | HTMLHtmlElement         | SCRIPT   | HTMLScriptElement       |
| I          | HTMLElement             | SELECT   | HTMLSelectElement       |
| IFRAME     | HTMLIFrameElement       | SMALL    | HTMLElement             |
| IMG        | HTMLImageElement        | SPAN     | HTMLElement             |
| INPUT      | HTMLInputElement        | _STRIKE_ | HTMLElement             |
| INS        | HTMLModElement          | STRONG   | HTMLElement             |
| _ISINDEX_  | HTMLIsIndexElement      | STYLE    | HTMLStyleElement        |
| KBD        | HTMLElement             | SUB      | HTMLElement             |
| LABEL      | HTMLLabelElement        | SUP      | HTMLElement             |
| LEGEND     | HTMLLegendElement       | TABLE    | HTMLTableElement        |
| LI         | HTMLLIElement           | TBODY    | HTMLTableSectionElement |
| LINK       | HTMLLinkElement         | TD       | HTMLTableCellElement    |
| MAP        | HTMLMapElement          | TEXTAREA | HTMLTextAreaElement     |
| _MENU_     | HTMLMenuElement         | TFOOT    | HTMLTableSectionElement |
| META       | HTMLMetaElement         | TH       | HTMLTableCellElement    |
| NOFRAMES   | HTMLElement             | THEAD    | HTMLTableSectionElement |
| NOSCRIPT   | HTMLElement             | TITLE    | HTMLTitleElement        |
| OBJECT     | HTMLObjectElement       | TR       | HTMLTableRowElement     |
| OL         | HTMLOListElement        | TT       | HTMLElement             |
| OPTGROUP   | HTMLOptGroupElement     | _U_      | HTMLElement             |
| OPTION     | HTMLOptionElement       | UL       | HTMLUListElement        |
| P          | HTMLParagraphElement    | VAR      | HTMLElement             |
| PARAM      | HTMLParamElement        |          |                         |

这里列出的每种类型都有关联的属性和方法。本书会涉及其中的很多类型。

2. **取得属性**

每个元素都有零个或多个属性，通常用于为元素或其内容附加更多信息。与属性相关的 DOM 方法主要有 3 个：getAttribute()、setAttribute()和 removeAttribute()。这些方法主要用于操纵属性，包括在 HTMLElement 类型上定义的属性。下面看一个例子：

```js
let div = document.getElementById("myDiv");
console.log(div.getAttribute("id")); // "myDiv"
console.log(div.getAttribute("class")); // "bd"
console.log(div.getAttribute("title")); // "Body text"
console.log(div.getAttribute("lang")); // "en"
console.log(div.getAttribute("dir")); // "ltr"
```

注意传给 getAttribute()的属性名与它们实际的属性名是一样的，因此这里要传"class"而非"className"（className 是作为对象属性时才那么拼写的）。如果给定的属性不存在，则 getAttribute()返回 null。

getAttribute()方法也能取得不是 HTML 语言正式属性的自定义属性的值。比如下面的元素：

```html
<div id="myDiv" my_special_attribute="hello!"></div>
```

这个元素有一个自定义属性 my_special_attribute，值为"hello!"。可以像其他属性一样使用 getAttribute()取得这个属性的值：

```js
let value = div.getAttribute("my_special_attribute");
```

注意，属性名不区分大小写，因此"ID"和"id"被认为是同一个属性。另外，根据 HTML5 规范的要求，自定义属性名应该前缀 data-以方便验证。

元素的所有属性也可以通过相应 DOM 元素对象的属性来取得。当然，这包括 HTMLElement 上定义的直接映射对应属性的 5 个属性，还有所有公认（非自定义）的属性也会被添加为 DOM 对象的属性。比如下面的例子：

```html
<div id="myDiv" align="left" my_special_attribute="hello"></div>
```

因为 id 和 align 在 HTML 中是`<div>`元素公认的属性，所以 DOM 对象上也会有这两个属性。但 my_special_attribute 是自定义属性，因此不会成为 DOM 对象的属性。

通过 DOM 对象访问的属性中有两个返回的值跟使用 getAttribute()取得的值不一样。首先是 style 属性，这个属性用于为元素设定 CSS 样式。在使用 getAttribute()访问 style 属性时，返回的是 CSS 字符串。而在通过 DOM 对象的属性访问时，style 属性返回的是一个（CSSStyleDeclaration）对象。DOM 对象的 style 属性用于以编程方式读写元素样式，因此不会直接映射为元素中 style 属性的字符串值。

第二个属性其实是一类，即事件处理程序（或者事件属性），比如 onclick。在元素上使用事件属性时（比如 onclick），属性的值是一段 JavaScript 代码。如果使用 getAttribute()访问事件属性，则返回的是字符串形式的源代码。而通过 DOM 对象的属性访问事件属性时返回的则是一个 JavaScript 函数（未指定该属性则返回 null）。这是因为 onclick 及其他事件属性是可以接受函数作为值的。

考虑到以上差异，开发者在进行 DOM 编程时通常会放弃使用 getAttribute()而只使用对象属性。getAttribute()主要用于取得自定义属性的值。

3. **设置属性**

与 getAttribute()配套的方法是 setAttribute()，这个方法接收两个参数：要设置的属性名和属性的值。如果属性已经存在，则 setAttribute()会以指定的值替换原来的值；如果属性不存在，则 setAttribute()会以指定的值创建该属性。下面看一个例子：

```js
div.setAttribute("id", "someOtherId");
div.setAttribute("class", "ft");
div.setAttribute("title", "Some other text");
div.setAttribute("lang", "fr");
div.setAttribute("dir", "rtl");
```

setAttribute()适用于 HTML 属性，也适用于自定义属性。另外，使用 setAttribute()方法设置的属性名会规范为小写形式，因此"ID"会变成"id"。

因为元素属性也是 DOM 对象属性，所以直接给 DOM 对象的属性赋值也可以设置元素属性的值，如下所示：

```js
div.id = "someOtherId";
div.align = "left";
```

注意，在 DOM 对象上添加自定义属性，如下面的例子所示，不会自动让它变成元素的属性：

```js
div.mycolor = "red";
console.log(div.getAttribute("mycolor")); // null（IE 除外）
```

这个例子添加了一个自定义属性 mycolor 并将其值设置为"red"。在多数浏览器中，这个属性不会自动变成元素属性。因此调用 getAttribute()取得 mycolor 的值会返回 null。

最后一个方法 removeAttribute()用于从元素中删除属性。这样不单单是清除属性的值，而是会把整个属性完全从元素中去掉，如下所示：

```js
div.removeAttribute("class");
```

这个方法用得并不多，但在序列化 DOM 元素时可以通过它控制要包含的属性。

4. **attributes 属性**

Element 类型是唯一使用 attributes 属性的 DOM 节点类型。attributes 属性包含一个 NamedNodeMap 实例，是一个类似 NodeList 的“实时”集合。元素的每个属性都表示为一个 Attr 节点，并保存在这个 NamedNodeMap 对象中。NamedNodeMap 对象包含下列方法：

- getNamedItem(name)，返回 nodeName 属性等于 name 的节点；
- removeNamedItem(name)，删除 nodeName 属性等于 name 的节点；
- setNamedItem(node)，向列表中添加 node 节点，以其 nodeName 为索引；
- item(pos)，返回索引位置 pos 处的节点。

attributes 属性中的每个节点的 nodeName 是对应属性的名字，nodeValue 是属性的值。比如，要取得元素 id 属性的值，可以使用以下代码：

```js
let id = element.attributes.getNamedItem("id").nodeValue;
```

下面是使用中括号访问属性的简写形式：

```js
let id = element.attributes["id"].nodeValue;
```

同样，也可以用这种语法设置属性的值，即先取得属性节点，再将其 nodeValue 设置为新值，如下所示：

```js
element.attributes["id"].nodeValue = "someOtherId";
```

removeNamedItem()方法与元素上的 removeAttribute()方法类似，也是删除指定名字的属性。下面的例子展示了这两个方法唯一的不同之处，就是 removeNamedItem()返回表示被删除属性的 Attr 节点：

```js
let oldAttr = element.attributes.removeNamedItem("id");
```

setNamedItem()方法很少使用，它接收一个属性节点，然后给元素添加一个新属性，如下所示：

```js
element.attributes.setNamedItem(newAttr);
```

一般来说，因为使用起来更简便，通常开发者更喜欢使用 getAttribute()、removeAttribute()和 setAttribute()方法，而不是刚刚介绍的 NamedNodeMap 对象的方法。

attributes 属性最有用的场景是需要迭代元素上所有属性的时候。这时候往往是要把 DOM 结构序列化为 XML 或 HTML 字符串。比如，以下代码能够迭代一个元素上的所有属性并以 attribute1="value1" attribute2="value2"的形式生成格式化字符串：

```js
function outputAttributes(element) {
  let pairs = [];
  for (let i = 0, len = element.attributes.length; i < len; ++i) {
    const attribute = element.attributes[i];
    pairs.push(`${attribute.nodeName}="${attribute.nodeValue}"`);
  }
  return pairs.join(" ");
}
```

这个函数使用数组存储每个名/值对，迭代完所有属性后，再将这些名/值对用空格拼接在一起。（这个技术常用于序列化为长字符串。）这个函数中的 for 循环使用 attributes.length 属性迭代每个属性，将每个属性的名字和值输出为字符串。不同浏览器返回的 attributes 中的属性顺序也可能不一样。HTML 或 XML 代码中属性出现的顺序不一定与 attributes 中的顺序一致。

5. **创建元素**

可以使用 document.createElement()方法创建新元素。这个方法接收一个参数，即要创建元素的标签名。在 HTML 文档中，标签名是不区分大小写的，而 XML 文档（包括 XHTML）是区分大小写的。要创建`<div>`元素，可以使用下面的代码：

```js
let div = document.createElement("div");
```

使用 createElement()方法创建新元素的同时也会将其 ownerDocument 属性设置为 document。此时，可以再为其添加属性、添加更多子元素。比如：

```js
div.id = "myNewDiv";
div.className = "box";
```

在新元素上设置这些属性只会附加信息。因为这个元素还没有添加到文档树，所以不会影响浏览器显示。要把元素添加到文档树，可以使用 appendChild()、insertBefore()或 replaceChild()。比如，以下代码会把刚才创建的元素添加到文档的`<body>`元素中：

```js
document.body.appendChild(div);
```

元素被添加到文档树之后，浏览器会立即将其渲染出来。之后再对这个元素所做的任何修改，都会立即在浏览器中反映出来。

6. **元素后代**

元素可以拥有任意多个子元素和后代元素，因为元素本身也可以是其他元素的子元素。childNodes 属性包含元素所有的子节点，这些子节点可能是其他元素、文本节点、注释或处理指令。不同浏览器在识别这些节点时的表现有明显不同。比如下面的代码：

```html
<ul id="myList">
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
</ul>
```

在解析以上代码时，`<ul>`元素会包含 7 个子元素，其中 3 个是`<li>`元素，还有 4 个 Text 节点（表示`<li>`元素周围的空格）。如果把元素之间的空格删掉，变成下面这样，则所有浏览器都会返回同样数量的子节点：

```html
<ul id="myList">
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
</ul>
```

所有浏览器解析上面的代码后，`<ul>`元素都会包含 3 个子节点。考虑到这种情况，通常在执行某个操作之后需要先检测一下节点的 nodeType，如下所示：

```js
for (let i = 0, len = element.childNodes.length; i < len; ++i) {
  if (element.childNodes[i].nodeType == 1) {
    // 执行某个操作
  }
}
```

以上代码会遍历某个元素的子节点，并且只在 nodeType 等于 1（即 Element 节点）时执行某个操作。

要取得某个元素的子节点和其他后代节点，可以使用元素的 getElementsByTagName()方法。在元素上调用这个方法与在文档上调用是一样的，只不过搜索范围限制在当前元素之内，即只会返回当前元素的后代。对于本节前面`<ul>`的例子，可以像下面这样取得其所有的`<li>`元素：

```js
let ul = document.getElementById("myList");
let items = ul.getElementsByTagName("li");
```

这里例子中的`<ul>`元素只有一级子节点，如果它包含更多层级，则所有层级中的`<li>`元素都会返回。

### 14.1.4. Text 类型

Text 节点由 Text 类型表示，包含按字面解释的纯文本，也可能包含转义后的 HTML 字符，但不含 HTML 代码。Text 类型的节点具有以下特征：

- nodeType 等于 3；
- nodeName 值为"#text"；
- nodeValue 值为节点中包含的文本；
- parentNode 值为 Element 对象；
- 不支持子节点。

Text 节点中包含的文本可以通过 nodeValue 属性访问，也可以通过 data 属性访问，这两个属性包含相同的值。修改 nodeValue 或 data 的值，也会在另一个属性反映出来。文本节点暴露了以下操作文本的方法：

- appendData(text)，向节点末尾添加文本 text；
- deleteData(offset, count)，从位置 offset 开始删除 count 个字符；
- insertData(offset, text)，在位置 offset 插入 text；
- replaceData(offset, count, text)，用 text 替换从位置 offset 到 offset + count 的文本；
- splitText(offset)，在位置 offset 将当前文本节点拆分为两个文本节点；
- substringData(offset, count)，提取从位置 offset 到 offset + count 的文本。

除了这些方法，还可以通过 length 属性获取文本节点中包含的字符数量。这个值等于 nodeValue.length 和 data.length。

默认情况下，包含文本内容的每个元素最多只能有一个文本节点。例如：

```html
<!-- 没有内容，因此没有文本节点 -->
<div></div>
```

<!-- 有空格，因此有一个文本节点 -->
<div> </div>

<!-- 有内容，因此有一个文本节点 -->
<div>Hello World!</div>
```

示例中的第一个`<div>`元素中不包含内容，因此不会产生文本节点。只要开始标签和结束标签之间有内容，就会创建一个文本节点，因此第二个`<div>`元素会有一个文本节点的子节点，虽然它只包含空格。这个文本节点的 nodeValue 就是一个空格。第三个`<div>`元素也有一个文本节点的子节点，其 nodeValue 的值为"Hello World!"。下列代码可以用来访问这个文本节点：

```js
let textNode = div.firstChild; // 或div.childNodes[0]
```

取得文本节点的引用后，可以像这样来修改它：

```js
div.firstChild.nodeValue = "Some other message";
```

只要节点在当前的文档树中，这样的修改就会马上反映出来。修改文本节点还有一点要注意，就是 HTML 或 XML 代码（取决于文档类型）会被转换成实体编码，即小于号、大于号或引号会被转义，如下所示：

```js
// 输出为"Some &lt;strong&gt;other&lt;/strong&gt; message"
div.firstChild.nodeValue = "Some <strong>other</strong> message";
```

这实际上是在将 HTML 字符串插入 DOM 文档前进行编码的有效方式。

1. **创建文本节点**

document.createTextNode()可以用来创建新文本节点，它接收一个参数，即要插入节点的文本。跟设置已有文本节点的值一样，这些要插入的文本也会应用 HTML 或 XML 编码，如下面的例子所示：

```js
let textNode = document.createTextNode("<strong>Hello</strong> world!");
```

创建新文本节点后，其 ownerDocument 属性会被设置为 document。但在把这个节点添加到文档树之前，我们不会在浏览器中看到它。以下代码创建了一个`<div>`元素并给它添加了一段文本消息：

```js
let element = document.createElement("div");
element.className = "message";
let textNode = document.createTextNode("Hello world!");
element.appendChild(textNode);
document.body.appendChild(element);
```

这个例子首先创建了一个`<div>`元素并给它添加了值为"message"的 class 属性，然后又创建了一个文本节点并添加到该元素。最后一步是把这个元素添加到文档的主体上，这样元素及其包含的文本会出现在浏览器中。

一般来说一个元素只包含一个文本子节点。不过，也可以让元素包含多个文本子节点，如下面的例子所示：

```js
let element = document.createElement("div");
element.className = "message";
let textNode = document.createTextNode("Hello world!");
element.appendChild(textNode);
let anotherTextNode = document.createTextNode("Yippee!");
element.appendChild(anotherTextNode);
document.body.appendChild(element);
```

在将一个文本节点作为另一个文本节点的同胞插入后，两个文本节点的文本之间不会包含空格。

2. **规范化文本节点**

DOM 文档中的同胞文本节点可能导致困惑，因为一个文本节点足以表示一个文本字符串。同样，DOM 文档中也经常会出现两个相邻文本节点。为此，有一个方法可以合并相邻的文本节点。这个方法叫 normalize()，是在 Node 类型中定义的（因此所有类型的节点上都有这个方法）。在包含两个或多
个相邻文本节点的父节点上调用 normalize()时，所有同胞文本节点会被合并为一个文本节点，这个文本节点的 nodeValue 就等于之前所有同胞节点 nodeValue 拼接在一起得到的字符串。来看下面的例子：

```js
let element = document.createElement("div");
element.className = "message";
let textNode = document.createTextNode("Hello world!");
element.appendChild(textNode);
let anotherTextNode = document.createTextNode("Yippee!");
element.appendChild(anotherTextNode);
document.body.appendChild(element);
console.log(element.childNodes.length); // 2
element.normalize();
console.log(element.childNodes.length); // 1
console.log(element.firstChild.nodeValue); // "Hello world!Yippee!"
```

浏览器在解析文档时，永远不会创建同胞文本节点。同胞文本节点只会出现在 DOM 脚本生成的文档树中。

3. **拆分文本节点**

Text 类型定义了一个与 normalize()相反的方法——splitText()。这个方法可以在指定的偏移位置拆分 nodeValue，将一个文本节点拆分成两个文本节点。拆分之后，原来的文本节点包含开头到偏移位置前的文本，新文本节点包含剩下的文本。这个方法返回新的文本节点，具有与原来的文本节点
相同的 parentNode。来看下面的例子：

```js
let element = document.createElement("div");
element.className = "message";
let textNode = document.createTextNode("Hello world!");
element.appendChild(textNode);
document.body.appendChild(element);
let newNode = element.firstChild.splitText(5);
console.log(element.firstChild.nodeValue); // "Hello"
console.log(newNode.nodeValue); // " world!"
console.log(element.childNodes.length); // 2
```

在这个例子中，包含"Hello world!"的文本节点被从位置 5 拆分成两个文本节点。位置 5 对应"Hello"和"world!"之间的空格，因此原始文本节点包含字符串"Hello"，而新文本节点包含文本"world!"（包含空格）。

拆分文本节点最常用于从文本节点中提取数据的 DOM 解析技术。

### 14.1.5. Comment 类型

DOM 中的注释通过 Comment 类型表示。Comment 类型的节点具有以下特征：

- nodeType 等于 8；
- nodeName 值为"#comment"；
- nodeValue 值为注释的内容；
- parentNode 值为 Document 或 Element 对象；
- 不支持子节点。

Comment 类型与 Text 类型继承同一个基类（CharacterData），因此拥有除 splitText()之外 Text 节点所有的字符串操作方法。与 Text 类型相似，注释的实际内容可以通过 nodeValue 或 data 属性获得。

注释节点可以作为父节点的子节点来访问。比如下面的 HTML 代码：

```html
<div id="myDiv"><!-- A comment --></div>
```

这里的注释是`<div>`元素的子节点，这意味着可以像下面这样访问它：

```js
let div = document.getElementById("myDiv");
let comment = div.firstChild;
console.log(comment.data); // "A comment"
```

可以使用 document.createComment()方法创建注释节点，参数为注释文本，如下所示：

```js
let comment = document.createComment("A comment");
```

显然，注释节点很少通过 JavaScrpit 创建和访问，因为注释几乎不涉及算法逻辑。此外，浏览器不承认结束的`</html>`标签之后的注释。如果要访问注释节点，则必须确定它们是`<html>`元素的后代。

### 14.1.6. CDATASection 类型

CDATASection 类型表示 XML 中特有的 CDATA 区块。CDATASection 类型继承 Text 类型，因此拥有包括 splitText()在内的所有字符串操作方法。CDATASection 类型的节点具有以下特征：

- nodeType 等于 4；
- nodeName 值为"#cdata-section"；
- nodeValue 值为 CDATA 区块的内容；
- parentNode 值为 Document 或 Element 对象；
- 不支持子节点。

CDATA 区块只在 XML 文档中有效，因此某些浏览器比较陈旧的版本会错误地将 CDATA 区块解析为 Comment 或 Element。比如下面这行代码：

```html
<div id="myDiv"><![CDATA[This is some content.]]></div>
```

这里`<div>`的第一个子节点应该是 CDATASection 节点。但主流的四大浏览器没有一个将其识别为 CDATASection。即使在有效的 XHTML 文档中，这些浏览器也不能恰当地支持嵌入的 CDATA 区块。

在真正的 XML 文档中，可以使用 document.createCDataSection()并传入节点内容来创建 CDATA 区块。

### 14.1.7. DocumentType 类型

DocumentType 类型的节点包含文档的文档类型（doctype）信息，具有以下特征：

- nodeType 等于 10；
- nodeName 值为文档类型的名称；
- nodeValue 值为 null；
- parentNode 值为 Document 对象；
- 不支持子节点。

DocumentType 对象在 DOM Level 1 中不支持动态创建，只能在解析文档代码时创建。对于支持这个类型的浏览器，DocumentType 对象保存在 document.doctype 属性中。DOM Level 1 规定了 DocumentType 对象的 3 个属性：name、entities 和 notations。其中，name 是文档类型的名称，entities 是这个文档类型描述的实体的 NamedNodeMap，而 notations 是这个文档类型描述的表示法的 NamedNodeMap。因为浏览器中的文档通常是 HTML 或 XHTML 文档类型，所以 entities 和 notations 列表为空。（这个对象只包含行内声明的文档类型。）无论如何，只有 name 属性是有用的。这个属性包含文档类型的名称，即紧跟在`<!DOCTYPE` 后面的那串文本。比如下面的 HTML 4.01 严格文档类型：

```html
<!DOCTYPE html PUBLIC "-// W3C// DTD HTML 4.01// EN" "http:// www.w3.org/TR/html4/strict.dtd">
```

对于这个文档类型，name 属性的值是"html"：

```js
console.log(document.doctype.name); // "html"
```

### 14.1.8. DocumentFragment 类型

在所有节点类型中，DocumentFragment 类型是唯一一个在标记中没有对应表示的类型。DOM 将文档片段定义为“轻量级”文档，能够包含和操作节点，却没有完整文档那样额外的消耗。DocumentFragment 节点具有以下特征：

- nodeType 等于 11；
- nodeName 值为"#document-fragment"；
- nodeValue 值为 null；
- parentNode 值为 null；
- 子节点可以是 Element、ProcessingInstruction、Comment、Text、CDATASection 或 EntityReference。

不能直接把文档片段添加到文档。相反，文档片段的作用是充当其他要被添加到文档的节点的仓库。可以使用 document.createDocumentFragment()方法像下面这样创建文档片段：

```js
let fragment = document.createDocumentFragment();
```

文档片段从 Node 类型继承了所有文档类型具备的可以执行 DOM 操作的方法。如果文档中的一个节点被添加到一个文档片段，则该节点会从文档树中移除，不会再被浏览器渲染。添加到文档片段的新节点同样不属于文档树，不会被浏览器渲染。可以通过 appendChild()或 insertBefore()方法将文
档片段的内容添加到文档。在把文档片段作为参数传给这些方法时，这个文档片段的所有子节点会被添加到文档中相应的位置。文档片段本身永远不会被添加到文档树。以下面的 HTML 为例：

```html
<ul id="myList"></ul>
```

假设想给这个`<ul>`元素添加 3 个列表项。如果分 3 次给这个元素添加列表项，浏览器就要重新渲染 3 次页面，以反映新添加的内容。为避免多次渲染，下面的代码示例使用文档片段创建了所有列表项，然后一次性将它们添加到了`<ul>`元素：

```js
let fragment = document.createDocumentFragment();
let ul = document.getElementById("myList");
for (let i = 0; i < 3; ++i) {
  let li = document.createElement("li");
  li.appendChild(document.createTextNode(`Item ${i + 1}`));
  fragment.appendChild(li);
}
ul.appendChild(fragment);
```

这个例子先创建了一个文档片段，然后取得了`<ul>`元素的引用。接着通过 for 循环创建了 3 个列表项，每一项都包含表明自己身份的文本。为此先创建`<li>`元素，再创建文本节点并添加到该元素。然后通过 appendChild()把`<li>`元素添加到文档片段。循环结束后，通过把文档片段传给 appendChild()将所有列表项添加到了`<ul>`元素。此时，文档片段的子节点全部被转移到了`<ul>`元素。

### 14.1.9. Attr 类型

元素数据在 DOM 中通过 Attr 类型表示。Attr 类型构造函数和原型在所有浏览器中都可以直接访问。技术上讲，属性是存在于元素 attributes 属性中的节点。Attr 节点具有以下特征：

- nodeType 等于 2；
- nodeName 值为属性名；
- nodeValue 值为属性值；
- parentNode 值为 null；
- 在 HTML 中不支持子节点；
- 在 XML 中子节点可以是 Text 或 EntityReference。

属性节点尽管是节点，却不被认为是 DOM 文档树的一部分。Attr 节点很少直接被引用，通常开发者更喜欢使用 getAttribute()、removeAttribute()和 setAttribute()方法操作属性。

Attr 对象上有 3 个属性：name、value 和 specified。其中，name 包含属性名（与 nodeName 一样），value 包含属性值（与 nodeValue 一样），而 specified 是一个布尔值，表示属性使用的是默认值还是被指定的值。

可以使用 document.createAttribute()方法创建新的 Attr 节点，参数为属性名。比如，要给元素添加 align 属性，可以使用下列代码：

```js
let attr = document.createAttribute("align");
attr.value = "left";
element.setAttributeNode(attr);
console.log(element.attributes["align"].value); // "left"
console.log(element.getAttributeNode("align").value); // "left"
console.log(element.getAttribute("align")); // "left"
```

在这个例子中，首先创建了一个新属性。调用 createAttribute()并传入"align"为新属性设置了 name 属性，因此就不用再设置了。随后，value 属性被赋值为"left"。为把这个新属性添加到元素上，可以使用元素的 setAttributeNode()方法。添加这个属性后，可以通过不同方式访问它，包
括 attributes 属性、getAttributeNode()和 getAttribute()方法。其中，attributes 属性和 getAttributeNode()方法都返回属性对应的 Attr 节点，而 getAttribute()方法只返回属性的值。

注意 将属性作为节点来访问多数情况下并无必要。推荐使用 getAttribute()、removeAttribute()和 setAttribute()方法操作属性，而不是直接操作属性节点。

## 14.2. DOM 编程

很多时候，操作 DOM 是很直观的。通过 HTML 代码能实现的，也一样能通过 JavaScript 实现。但有时候，DOM 也没有看起来那么简单。浏览器能力的参差不齐和各种问题，也会导致 DOM 的某些方面会复杂一些。

### 14.2.1. 动态脚本

`<script>`元素用于向网页中插入 JavaScript 代码，可以是 src 属性包含的外部文件，也可以是作为该元素内容的源代码。动态脚本就是在页面初始加载时不存在，之后又通过 DOM 包含的脚本。与对应的 HTML 元素一样，有两种方式通过`<script>`动态为网页添加脚本：引入外部文件和直接插入源代码。

动态加载外部文件很容易实现，比如下面的`<script>`元素：

```html
<script src="foo.js"></script>
```

可以像这样通过 DOM 编程创建这个节点：

```js
let script = document.createElement("script");
script.src = "foo.js";
document.body.appendChild(script);
```

这里的 DOM 代码实际上完全照搬了它要表示的 HTML 代码。注意，在上面最后一行把`<script>`元素添加到页面之前，是不会开始下载外部文件的。当然也可以把它添加到`<head>`元素，同样可以实现动态脚本加载。这个过程可以抽象为一个函数，比如：

```js
function loadScript(url) {
  let script = document.createElement("script");
  script.src = url;
  document.body.appendChild(script);
}
```

然后，就可以像下面这样加载外部 JavaScript 文件了：

```js
loadScript("client.js");
```

加载之后，这个脚本就可以对页面执行操作了。这里有个问题：怎么能知道脚本什么时候加载完？这个问题并没有标准答案。第 17 章会讨论一些与加载相关的事件，具体情况取决于使用的浏览器。

另一个动态插入 JavaScript 的方式是嵌入源代码，如下面的例子所示：

```html
<script>
  function sayHi() {
    console.log("hi");
  }
</script>
```

使用 DOM，可以实现以下逻辑：

```js
let script = document.createElement("script");
script.appendChild(document.createTextNode("function sayHi(){alert('hi');}"));
document.body.appendChild(script);
```

以上代码可以在 Firefox、Safari、Chrome 和 Opera 中运行。不过在旧版本的 IE 中可能会导致问题。这是因为 IE 对`<script>`元素做了特殊处理，不允许常规 DOM 访问其子节点。但`<script>`元素上有一个 text 属性，可以用来添加 JavaScript 代码，如下所示：

```js
var script = document.createElement("script");
script.text = "function sayHi(){alert('hi');}";
document.body.appendChild(script);
```

这样修改后，上面的代码可以在 IE、Firefox、Opera 和 Safari 3 及更高版本中运行。Safari 3 之前的版本不能正确支持这个 text 属性，但这些版本却支持文本节点赋值。对于早期的 Safari 版本，需要使用以下代码：

```js
var script = document.createElement("script");
var code = "function sayHi(){alert('hi');}";
try {
  script.appendChild(document.createTextNode("code"));
} catch (ex) {
  script.text = "code";
}
document.body.appendChild(script);
```

这里先尝试使用标准的 DOM 文本节点插入方式，因为除 IE 之外的浏览器都支持这种方式。IE 此时会抛出错误，那么可以在捕获错误之后再使用 text 属性来插入 JavaScript 代码。于是，我们就可以抽象出一个跨浏览器的函数：

```js
function loadScriptString(code) {
  var script = document.createElement("script");
  script.type = "text/javascript";
  try {
    script.appendChild(document.createTextNode(code));
  } catch (ex) {
    script.text = code;
  }
  document.body.appendChild(script);
}
```

这个函数可以这样调用：

```js
loadScriptString("function sayHi(){alert('hi');}");
```

以这种方式加载的代码会在全局作用域中执行，并在调用返回后立即生效。基本上，这就相当于在全局作用域中把源代码传给 eval()方法。

注意，通过 innerHTML 属性创建的`<script>`元素永远不会执行。浏览器会尽责地创建`<script>`元素，以及其中的脚本文本，但解析器会给这个`<script>`元素打上永不执行的标签。只要是使用 innerHTML 创建的`<script>`元素，以后也没有办法强制其执行。

### 14.2.2. 动态样式

CSS 样式在 HTML 页面中可以通过两个元素加载。`<link>`元素用于包含 CSS 外部文件，而`<style>`元素用于添加嵌入样式。与动态脚本类似，动态样式也是页面初始加载时并不存在，而是在之后才添加到页面中的。

来看下面这个典型的`<link>`元素：

```html
<link rel="stylesheet" type="text/css" href="styles.css" />
```

这个元素很容易使用 DOM 编程创建出来：

```js
let link = document.createElement("link");
link.rel = "stylesheet";
link.type = "text/css";
link.href = "styles.css";
let head = document.getElementsByTagName("head")[0];
head.appendChild(link);
```

以上代码在所有主流浏览器中都能正常运行。注意应该把`<link>`元素添加到`<head>`元素而不是`<body>`元素，这样才能保证所有浏览器都能正常运行。这个过程可以抽象为以下通用函数：

```js
function loadStyles(url) {
  let link = document.createElement("link");
  link.rel = "stylesheet";
  link.type = "text/css";
  link.href = url;
  let head = document.getElementsByTagName("head")[0];
  head.appendChild(link);
}
```

然后就可以这样调用这个 loadStyles()函数了：

```js
loadStyles("styles.css");
```

通过外部文件加载样式是一个异步过程。因此，样式的加载和正执行的 JavaScript 代码并没有先后顺序。一般来说，也没有必要知道样式什么时候加载完成。

另一种定义样式的方式是使用`<script>`元素包含嵌入的 CSS 规则，例如：

```html
<style type="text/css">
  body {
    background-color: red;
  }
</style>
```

逻辑上，下列 DOM 代码会有同样的效果：

```js
let style = document.createElement("style");
style.type = "text/css";
style.appendChild(document.createTextNode("body{background-color:red}"));
let head = document.getElementsByTagName("head")[0];
head.appendChild(style);
```

以上代码在 Firefox、Safari、Chrome 和 Opera 中都可以运行，但 IE 除外。IE 对`<style>`节点会施加限制，不允许访问其子节点，这一点与它对`<script>`元素施加的限制一样。事实上，IE 在执行到给`<style>`添加子节点的代码时，会抛出与给`<script>`添加子节点时同样的错误。对于 IE，解决方案是访问元素的 styleSheet 属性，这个属性又有一个 cssText 属性，然后给这个属性添加 CSS 代码：

```js
let style = document.createElement("style");
style.type = "text/css";
try {
  style.appendChild(document.createTextNode("body{background-color:red}"));
} catch (ex) {
  style.styleSheet.cssText = "body{background-color:red}";
}
let head = document.getElementsByTagName("head")[0];
head.appendChild(style);
```

与动态添加脚本源代码类似，这里也使用了 try...catch 语句捕获 IE 抛出的错误，然后再以 IE 特有的方式来设置样式。这是最终的通用函数：

```js
function loadStyleString(css) {
  let style = document.createElement("style");
  style.type = "text/css";
  try {
    style.appendChild(document.createTextNode(css));
  } catch (ex) {
    style.styleSheet.cssText = css;
  }
  let head = document.getElementsByTagName("head")[0];
  head.appendChild(style);
}
```

可以这样调用这个函数：

```js
loadStyleString("body{background-color:red}");
```

这样添加的样式会立即生效，因此所有变化会立即反映出来。

注意 对于 IE，要小心使用 styleSheet.cssText。如果重用同一个`<style>`元素并设置该属性超过一次，则可能导致浏览器崩溃。同样，将 cssText 设置为空字符串也可能导致浏览器崩溃。

### 14.2.3. 操作表格

表格是 HTML 中最复杂的结构之一。通过 DOM 编程创建`<table>`元素，通常要涉及大量标签，包括表行、表元、表题，等等。因此，通过 DOM 编程创建和修改表格时可能要写很多代码。假设要通过 DOM 来创建以下 HTML 表格：

```html
<table border="1" width="100%">
  <tbody>
    <tr>
      <td>Cell 1,1</td>
      <td>Cell 2,1</td>
    </tr>
    <tr>
      <td>Cell 1,2</td>
      <td>Cell 2,2</td>
    </tr>
  </tbody>
</table>
```

下面就是以 DOM 编程方式重建这个表格的代码：

```js
// 创建表格
let table = document.createElement("table");
table.border = 1;
table.width = "100%";
// 创建表体
let tbody = document.createElement("tbody");
table.appendChild(tbody);
// 创建第一行
let row1 = document.createElement("tr");
tbody.appendChild(row1);
let cell1_1 = document.createElement("td");
cell1_1.appendChild(document.createTextNode("Cell 1,1"));
row1.appendChild(cell1_1);
let cell2_1 = document.createElement("td");
cell2_1.appendChild(document.createTextNode("Cell 2,1"));
row1.appendChild(cell2_1);
// 创建第二行
let row2 = document.createElement("tr");
tbody.appendChild(row2);
let cell1_2 = document.createElement("td");
cell1_2.appendChild(document.createTextNode("Cell 1,2"));
row2.appendChild(cell1_2);
let cell2_2 = document.createElement("td");
cell2_2.appendChild(document.createTextNode("Cell 2,2"));
row2.appendChild(cell2_2);
// 把表格添加到文档主体
document.body.appendChild(table);
```

以上代码相当烦琐，也不好理解。为了方便创建表格，HTML DOM 给`<table>`、`<tbody>`和`<tr>`元素添加了一些属性和方法。

`<table>`元素添加了以下属性和方法：

- caption，指向`<caption>`元素的指针（如果存在）；
- tBodies，包含`<tbody>`元素的 HTMLCollection；
- tFoot，指向`<tfoot>`元素（如果存在）；
- tHead，指向`<thead>`元素（如果存在）；
- rows，包含表示所有行的 HTMLCollection；
- createTHead()，创建`<thead>`元素，放到表格中，返回引用；
- createTFoot()，创建`<tfoot>`元素，放到表格中，返回引用；
- createCaption()，创建`<caption>`元素，放到表格中，返回引用；
- deleteTHead()，删除`<thead>`元素；
- deleteTFoot()，删除`<tfoot>`元素；
- deleteCaption()，删除`<caption>`元素；
- deleteRow(pos)，删除给定位置的行；
- insertRow(pos)，在行集合中给定位置插入一行。`<tbody>`元素添加了以下属性和方法：
- rows，包含`<tbody>`元素中所有行的 HTMLCollection；
- deleteRow(pos)，删除给定位置的行；
- insertRow(pos)，在行集合中给定位置插入一行，返回该行的引用。`<tr>`元素添加了以下属性和方法：
- cells，包含`<tr>`元素所有表元的 HTMLCollection；
- deleteCell(pos)，删除给定位置的表元；
- insertCell(pos)，在表元集合给定位置插入一个表元，返回该表元的引用。

这些属性和方法极大地减少了创建表格所需的代码量。例如，使用这些方法重写前面的代码之后是这样的（加粗代码表示更新的部分）：

```js
// 创建表格
let table = document.createElement("table");
table.border = 1;
table.width = "100%";
// 创建表体
let tbody = document.createElement("tbody");
table.appendChild(tbody);
// 创建第一行
tbody.insertRow(0);
tbody.rows[0].insertCell(0);
tbody.rows[0].cells[0].appendChild(document.createTextNode("Cell 1,1"));
tbody.rows[0].insertCell(1);
tbody.rows[0].cells[1].appendChild(document.createTextNode("Cell 2,1"));
// 创建第二行
tbody.insertRow(1);
tbody.rows[1].insertCell(0);
tbody.rows[1].cells[0].appendChild(document.createTextNode("Cell 1,2"));
tbody.rows[1].insertCell(1);
tbody.rows[1].cells[1].appendChild(document.createTextNode("Cell 2,2"));
// 把表格添加到文档主体
document.body.appendChild(table);
```

这里创建`<table>`和`<tbody>`元素的代码没有变。变化的是创建两行的部分，这次使用了 HTML DOM 表格的属性和方法。创建第一行时，在`<tbody>` 元素上调用了 insertRow()方法。传入参数 0，表示把这一行放在什么位置。然后，使用 tbody.rows[0]来引用这一行，因为这一行刚刚创建并被添加到了`<tbody>`的位置 0。

创建表元的方式也与之类似。在`<tr>`元素上调用 insertCell()方法，传入参数 0，表示把这个表元放在什么位置上。然后，使用 tbody.rows[0].cells[0]来引用这个表元，因为这个表元刚刚创建并被添加到了`<tr>`的位置 0。

虽然以上两种代码在技术上都是正确的，但使用这些属性和方法创建表格让代码变得更有逻辑性，也更容易理解。

### 14.2.4. 使用 NodeList

理解 NodeList 对象和相关的 NamedNodeMap、HTMLCollection，是理解 DOM 编程的关键。这 3 个集合类型都是“实时的”，意味着文档结构的变化会实时地在它们身上反映出来，因此它们的值始终代表最新的状态。实际上，NodeList 就是基于 DOM 文档的实时查询。例如，下面的代码会导致无穷
循环：

```js
let divs = document.getElementsByTagName("div");
for (let i = 0; i < divs.length; ++i) {
  let div = document.createElement("div");
  document.body.appendChild(div);
}
```

第一行取得了包含文档中所有`<div>`元素的 HTMLCollection。因为这个集合是“实时的”，所以任何时候只要向页面中添加一个新`<div>`元素，再查询这个集合就会多一项。因为浏览器不希望保存每次创建的集合，所以就会在每次访问时更新集合。这样就会出现前面使用循环的例子中所演示的问题。每次循环开始，都会求值 i < divs.length。这意味着要执行获取所有`<div>`元素的查询。因为循环体中会创建并向文档添加一个新`<div>`元素，所以每次循环 divs.length 的值也会递增。因为两个值都会递增，所以 i 将永远不会等于 divs.length。

使用 ES6 迭代器并不会解决这个问题，因为迭代的是一个永远增长的实时集合。以下代码仍然会导致无穷循环：

```js
for (let div of document.getElementsByTagName("div")) {
  let newDiv = document.createElement("div");
  document.body.appendChild(newDiv);
}
```

任何时候要迭代 NodeList，最好再初始化一个变量保存当时查询时的长度，然后用循环变量与这个变量进行比较，如下所示：

```js
let divs = document.getElementsByTagName("div");
for (let i = 0, len = divs.length; i < len; ++i) {
  let div = document.createElement("div");
  document.body.appendChild(div);
}
```

在这个例子中，又初始化了一个保存集合长度的变量 len。因为 len 保存着循环开始时集合的长度，而这个值不会随集合增大动态增长，所以就可以避免前面例子中出现的无穷循环。本章还会使用这种技术来演示迭代 NodeList 对象的首选方式。

另外，如果不想再初始化一个变量，也可以像下面这样反向迭代集合：

```js
let divs = document.getElementsByTagName("div");
for (let i = divs.length - 1; i >= 0; --i) {
  let div = document.createElement("div");
  document.body.appendChild(div);
}
```

一般来说，最好限制操作 NodeList 的次数。因为每次查询都会搜索整个文档，所以最好把查询到的 NodeList 缓存起来。

## 14.3. MutationObserver 接口

不久前添加到 DOM 规范中的 MutationObserver 接口，可以在 DOM 被修改时异步执行回调。使用 MutationObserver 可以观察整个文档、DOM 树的一部分，或某个元素。此外还可以观察元素属性、子节点、文本，或者前三者任意组合的变化。

注意 新引进 MutationObserver 接口是为了取代废弃的 MutationEvent。

### 14.3.1. 基本用法

MutationObserver 的实例要通过调用 MutationObserver 构造函数并传入一个回调函数来创建：

```js
let observer = new MutationObserver(() => console.log("DOM 改动了！"));
```

1. **observe()** 方法

新创建的 MutationObserver 实例不会关联 DOM 的任何部分。要把这个 observer 与 DOM 关联起来，需要使用 observe()方法。这个方法接收两个必需的参数：要观察其变化的 DOM 节点，以及一个 MutationObserverInit 对象。

MutationObserverInit 对象用于控制观察哪些方面的变化，是一个键/值对形式配置选项的字典。例如，下面的代码会创建一个观察者（observer）并配置它观察`<body>`元素上的属性变化：

```js
let observer = new MutationObserver(() => console.log("<body> 属性改变了"));
observer.observe(document.body, { attributes: true });
```

执行以上代码后，`<body>`元素上任何属性发生变化都会被这个 MutationObserver 实例发现，然后就会异步执行注册的回调函数。`<body>`元素后代的修改或其他非属性修改都不会触发回调进入任务队列。可以通过以下代码来验证：

```js
let observer = new MutationObserver(() =>
  console.log("<body> attributes changed")
);
observer.observe(document.body, { attributes: true });
setTimeout(() => (document.body.className = "foo"), 2000);
console.log("Changed body class");
// Changed body class
// 2秒后
// <body> attributes changed
```

2. **回调与 MutationRecord**

每个回调都会收到一个 MutationRecord 实例的数组。MutationRecord 实例包含的信息包括发生了什么变化，以及 DOM 的哪一部分受到了影响。因为回调执行之前可能同时发生多个满足观察条件的事件，所以每次执行回调都会传入一个包含按顺序入队的 MutationRecord 实例的数组。

下面展示了反映一个属性变化的 MutationRecord 实例的数组：

```js
let observer = new MutationObserver((mutationRecords) =>
  console.log(mutationRecords)
);
observer.observe(document.body, { attributes: true });
document.body.setAttribute("foo", "bar");
// [
//  {
// addedNodes: NodeList [],
// attributeName: "foo",
// attributeNamespace: null,
// nextSibling: null,
// oldValue: null,
// previousSibling: null
// removedNodes: NodeList [],
// target: body
// type: "attributes"
//  }
// ]
```

下面是一次涉及命名空间的类似变化：

```js
let observer = new MutationObserver((mutationRecords) =>
  console.log(mutationRecords)
);
observer.observe(document.body, { attributes: true });
document.body.setAttributeNS("baz", "foo", "bar");
// [
// {
// addedNodes: NodeList [],
// attributeName: "foo",
// attributeNamespace: "baz",
// nextSibling: null,
// oldValue: null,
// previousSibling: null
// removedNodes: NodeList [],
// target: body
// type: "attributes"
// }
// ]
```

连续修改会生成多个 MutationRecord 实例，下次回调执行时就会收到包含所有这些实例的数组，顺序为变化事件发生的顺序：

```js
let observer = new MutationObserver((mutationRecords) =>
  console.log(mutationRecords)
);
observer.observe(document.body, { attributes: true });
document.body.className = "foo";
document.body.className = "bar";
document.body.className = "baz";
// [MutationRecord, MutationRecord, MutationRecord]
```

下表列出了 MutationRecord 实例的属性。

| 属 性              | 说 明                                                                                                                                                                        |
| ------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------- |
| target             | 被修改影响的目标节点                                                                                                                                                         |
| type               | 字符串，表示变化的类型："attributes"、"characterData"或"childList"                                                                                                           |
| oldValue           | 如果在 MutationObserverInit 对象中启用（attributeOldValue 或 characterData OldValue 为 true），"attributes"或"characterData"的变化事件会设置这个属性为被替代的值 "childList" | 类型的变化始终将这个属性设置为 null |
| attributeName      | 对于"attributes"类型的变化，这里保存被修改属性的名字其他变化事件会将这个属性设置为 null                                                                                      |
| attributeNamespace | 对于使用了命名空间的"attributes"类型的变化，这里保存被修改属性的名字 其他变化事件会将这个属性设置为 null                                                                     |
| addedNodes         | 对于"childList"类型的变化，返回包含变化中添加节点的 NodeList 默认为空 NodeList                                                                                               |
| removedNodes       | 对于"childList"类型的变化，返回包含变化中删除节点的 NodeList 默认为空 NodeList                                                                                               |
| previousSibling    | 对于"childList"类型的变化，返回变化节点的前一个同胞 Node 默认为 null                                                                                                         |
| nextSibling        | 对于"childList"类型的变化，返回变化节点的后一个同胞 Node 默认为 null                                                                                                         |

传给回调函数的第二个参数是观察变化的 MutationObserver 的实例，演示如下：

```js
let observer = new MutationObserver((mutationRecords, mutationObserver) =>
  console.log(mutationRecords, mutationObserver)
);
observer.observe(document.body, { attributes: true });
document.body.className = "foo";
// [MutationRecord], MutationObserver
```

3. **disconnect()方法**

默认情况下，只要被观察的元素不被垃圾回收，MutationObserver 的回调就会响应 DOM 变化事件，从而被执行。要提前终止执行回调，可以调用 disconnect()方法。下面的例子演示了同步调用 disconnect()之后，不仅会停止此后变化事件的回调，也会抛弃已经加入任务队列要异步执行的回调：

```js
let observer = new MutationObserver(() =>
  console.log("<body> attributes changed")
);
observer.observe(document.body, { attributes: true });
document.body.className = "foo";
observer.disconnect();
document.body.className = "bar";
//（没有日志输出）
```

要想让已经加入任务队列的回调执行，可以使用 setTimeout()让已经入列的回调执行完毕再调用 disconnect()：

```js
let observer = new MutationObserver(() =>
  console.log("<body> attributes changed")
);
observer.observe(document.body, { attributes: true });
document.body.className = "foo";
setTimeout(() => {
  observer.disconnect();
  document.body.className = "bar";
}, 0);
// <body> attributes changed
```

4. **复用 MutationObserver**

多次调用 observe()方法，可以复用一个 MutationObserver 对象观察多个不同的目标节点。此时，MutationRecord 的 target 属性可以标识发生变化事件的目标节点。下面的示例演示了这个过程：

```js
let observer = new MutationObserver((mutationRecords) =>
  console.log(mutationRecords.map((x) => x.target))
);
// 向页面主体添加两个子节点
let childA = document.createElement("div"),
  childB = document.createElement("span");
document.body.appendChild(childA);
document.body.appendChild(childB);
// 观察两个子节点
observer.observe(childA, { attributes: true });
observer.observe(childB, { attributes: true });
// 修改两个子节点的属性
childA.setAttribute("foo", "bar");
childB.setAttribute("foo", "bar");
// [<div>, <span>]
```

disconnect()方法是一个“一刀切”的方案，调用它会停止观察所有目标：

```js
let observer = new MutationObserver((mutationRecords) =>
  console.log(mutationRecords.map((x) => x.target))
);
// 向页面主体添加两个子节点
let childA = document.createElement("div"),
  childB = document.createElement("span");
document.body.appendChild(childA);
document.body.appendChild(childB);
// 观察两个子节点
observer.observe(childA, { attributes: true });
observer.observe(childB, { attributes: true });
observer.disconnect();
// 修改两个子节点的属性
childA.setAttribute("foo", "bar");
childB.setAttribute("foo", "bar");
// （没有日志输出）
```

5. **重用 MutationObserver**

调用 disconnect()并不会结束 MutationObserver 的生命。还可以重新使用这个观察者，再将它关联到新的目标节点。下面的示例在两个连续的异步块中先断开然后又恢复了观察者与`<body>`元素的关联：

```js
let observer = new MutationObserver(() => console.log('<body> attributes
changed'));
observer.observe(document.body, { attributes: true });
// 这行代码会触发变化事件
document.body.setAttribute('foo', 'bar');
setTimeout(() => {
observer.disconnect();
// 这行代码不会触发变化事件
document.body.setAttribute('bar', 'baz');
}, 0);
setTimeout(() => {
// Reattach
observer.observe(document.body, { attributes: true });
// 这行代码会触发变化事件
document.body.setAttribute('baz', 'qux');
}, 0);
// <body> attributes changed
// <body> attributes changed
```

### 14.3.2. MutationObserverInit 与观察范围

MutationObserverInit 对象用于控制对目标节点的观察范围。粗略地讲，观察者可以观察的事件包括属性变化、文本变化和子节点变化。

下表列出了 MutationObserverInit 对象的属性。

| 属 性                                                                   | 说 明                                                                                                                                              |
| ----------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| subtree                                                                 | 布尔值，表示除了目标节点，是否观察目标节点的子树（后代）如果是 false，则只观察目标节点的变化；如果是 true，则观察目标节点及其整个子树 默认为 false |
| attributes                                                              | 布尔值，表示是否观察目标节点的属性变化 默认为 false                                                                                                |
| attributeFilter                                                         | 字符串数组，表示要观察哪些属性的变化 把这个值设置为 true 也会将 attributes 的值转换为 true 默认为观察所有属性                                      |
| attributeOldValue                                                       | 布尔值，表示 MutationRecord 是否记录变化之前的属性值 把这个值设置为 true 也会将 attributes 的值转换为 true                                         |
| 默认为 false                                                            |
| characterData                                                           | 布尔值，表示修改字符数据是否触发变化事件 默认为 false                                                                                              |
| characterDataOldValue                                                   | 布尔值，表示 MutationRecord 是否记录变化之前的字符数据 把这个值设置为 true 也会将 characterData 的值转换为 true 默认为 false                       |
| childList 布尔值，表示修改目标节点的子节点是否触发变化事件 默认为 false |

注意 在调用 observe()时，MutationObserverInit 对象中的 attribute、characterData 和 childList 属性必须至少有一项为 true（无论是直接设置这几个属性，还是通过设置 attributeOldValue 等属性间接导致它们的值转换为 true）。否则会抛出错误，因为没有任何变化事件可能触发回调。

1. **观察属性**

MutationObserver 可以观察节点属性的添加、移除和修改。要为属性变化注册回调，需要在 MutationObserverInit 对象中将 attributes 属性设置为 true，如下所示：

```js
let observer = new MutationObserver((mutationRecords) =>
  console.log(mutationRecords)
);
observer.observe(document.body, { attributes: true });
// 添加属性
document.body.setAttribute("foo", "bar");
// 修改属性
document.body.setAttribute("foo", "baz");
// 移除属性
document.body.removeAttribute("foo");
// 以上变化都被记录下来了
// [MutationRecord, MutationRecord, MutationRecord]
```

把 attributes 设置为 true 的默认行为是观察所有属性，但不会在 MutationRecord 对象中记录原来的属性值。如果想观察某个或某几个属性，可以使用 attributeFilter 属性来设置白名单，即一个属性名字符串数组：

```js
let observer = new MutationObserver((mutationRecords) =>
  console.log(mutationRecords)
);
observer.observe(document.body, { attributeFilter: ["foo"] });
// 添加白名单属性
document.body.setAttribute("foo", "bar");
// 添加被排除的属性
document.body.setAttribute("baz", "qux");
// 只有foo 属性的变化被记录了
// [MutationRecord]
```

如果想在变化记录中保存属性原来的值，可以将 attributeOldValue 属性设置为 true：

```js
let observer = new MutationObserver((mutationRecords) =>
  console.log(mutationRecords.map((x) => x.oldValue))
);
observer.observe(document.body, { attributeOldValue: true });
document.body.setAttribute("foo", "bar");
document.body.setAttribute("foo", "baz");
document.body.setAttribute("foo", "qux");
// 每次变化都保留了上一次的值
// [null, 'bar', 'baz']
```

2. **观察字符数据**

MutationObserver 可以观察文本节点（如 Text、Comment 或 ProcessingInstruction 节点）中字符的添加、删除和修改。要为字符数据注册回调，需要在 MutationObserverInit 对象中将 characterData 属性设置为 true，如下所示：

```js
let observer = new MutationObserver((mutationRecords) =>
  console.log(mutationRecords)
);
// 创建要观察的文本节点
document.body.firstChild.textContent = "foo";
observer.observe(document.body.firstChild, { characterData: true });
// 赋值为相同的字符串
document.body.firstChild.textContent = "foo";
// 赋值为新字符串
document.body.firstChild.textContent = "bar";
// 通过节点设置函数赋值
document.body.firstChild.textContent = "baz";
// 以上变化都被记录下来了
// [MutationRecord, MutationRecord, MutationRecord]
```

将 characterData 属性设置为 true 的默认行为不会在 MutationRecord 对象中记录原来的字符数据。如果想在变化记录中保存原来的字符数据，可以将 characterDataOldValue 属性设置为 true：

```js
let observer = new MutationObserver((mutationRecords) =>
  console.log(mutationRecords.map((x) => x.oldValue))
);
document.body.innerText = "foo";
observer.observe(document.body.firstChild, { characterDataOldValue: true });
document.body.innerText = "foo";
document.body.innerText = "bar";
document.body.firstChild.textContent = "baz";
// 每次变化都保留了上一次的值
// ["foo", "foo", "bar"]
```

3. **观察子节点**

MutationObserver 可以观察目标节点子节点的添加和移除。要观察子节点，需要在 MutationObserverInit 对象中将 childList 属性设置为 true。下面的例子演示了添加子节点：

```js
let observer = new MutationObserver((mutationRecords) =>
  console.log(mutationRecords)
);
observer.observe(document.body, { childList: true });
document.body.appendChild(document.createElement("div"));
// [
// {
// addedNodes: NodeList [div]
// attributeName: null
// attributeNamespace: null
// nextSibling: null
// oldValue: null
// previousSibling: script
// removedNodes: NodeList []
// target: body
// type: "childList"
// },
// {
// addedNodes: NodeList [text]
// attributeName: null
// attributeNamespace: null
// nextSibling: null
// oldValue: null
// previousSibling: div
// removedNodes: NodeList []
// target: body
// type: "childList"
// }
// ]
```

下面的例子演示了移除子节点：

```js
const div = document.createElement("div");
document.body.qppendChild(div);
let observer = new MutationObserver((mutationRecords) =>
  console.log(mutationRecords)
);
observer.observe(document.body, { childList: true });
document.body.removeChild(document.body.firstChild);
// [
// {
// addedNodes: NodeList []
// attributeName: null
// attributeNamespace: null
// nextSibling: null
// oldValue: null
// previousSibling: null
// removedNodes: NodeList [div]
// target: body
// type: "childList"
// },
// {
// addedNodes: NodeList [text]
// attributeName: null
// attributeNamespace: null
// nextSibling: null
// oldValue: null
// previousSibling: div
// removedNodes: NodeList []
// target: body
// type: "childList"
// }
// ]
```

对子节点 **重新排序**（尽管调用一个方法即可实现）会报告两次变化事件，因为从技术上会涉及先移除和再添加：

```js
// 清空主体
document.body.innerHTML = "";
let observer = new MutationObserver((mutationRecords) =>
  console.log(mutationRecords)
);
// 创建两个初始子节点
document.body.appendChild(document.createElement("div"));
document.body.appendChild(document.createElement("span"));
observer.observe(document.body, { childList: true });
// 交换子节点顺序
document.body.insertBefore(document.body.lastChild, document.body.firstChild);
// 发生了两次变化：第一次是节点被移除，第二次是节点被添加
// [
// {
// addedNodes: NodeList[],
// attributeName: null,
// attributeNamespace: null,
// oldValue: null,
// nextSibling: null,
// previousSibling: div,
// removedNodes: NodeList[span],
// target: body,
// type: childList,
// },
// {
// addedNodes: NodeList[span],
// attributeName: null,
// attributeNamespace: null,
// oldValue: null,
// nextSibling: div,
// previousSibling: null,
// removedNodes: NodeList[],
// target: body,
// type: "childList",
// }
// ]
```

4. **观察子树**

默认情况下，MutationObserver 将观察的范围限定为一个元素及其子节点的变化。可以把观察的范围扩展到这个元素的子树（所有后代节点），这需要在 MutationObserverInit 对象中将 subtree 属性设置为 true。

下面的代码展示了观察元素及其后代节点属性的变化：

```js
// 清空主体
document.body.innerHTML = "";
let observer = new MutationObserver((mutationRecords) =>
  console.log(mutationRecords)
);
// 创建一个后代
document.body.appendChild(document.createElement("div"));
// 观察<body>元素及其子树
observer.observe(document.body, { attributes: true, subtree: true });
// 修改<body>元素的子树
document.body.firstChild.setAttribute("foo", "bar");
// 记录了子树变化的事件
// [
// {
// addedNodes: NodeList[],
// attributeName: "foo",
// attributeNamespace: null,
// oldValue: null,
// nextSibling: null,
// previousSibling: null,
// removedNodes: NodeList[],
// target: div,
// type: "attributes",
// }
// ]
```

有意思的是，被观察子树中的节点被移出子树之后仍然能够触发变化事件。这意味着在子树中的节点离开该子树后，即使严格来讲该节点已经脱离了原来的子树，但它仍然会触发变化事件。

下面的代码演示了这种情况：

```js
// 清空主体
document.body.innerHTML = "";
let observer = new MutationObserver((mutationRecords) =>
  console.log(mutationRecords)
);
let subtreeRoot = document.createElement("div"),
  subtreeLeaf = document.createElement("span");
// 创建包含两层的子树
document.body.appendChild(subtreeRoot);
subtreeRoot.appendChild(subtreeLeaf);
// 观察子树
observer.observe(subtreeRoot, { attributes: true, subtree: true });
// 把节点转移到其他子树
document.body.insertBefore(subtreeLeaf, subtreeRoot);
subtreeLeaf.setAttribute("foo", "bar");
// 移出的节点仍然触发变化事件
// [MutationRecord]
```

### 14.3.3. 异步回调与记录队列

MutationObserver 接口是出于性能考虑而设计的，其核心是异步回调与记录队列模型。为了在大量变化事件发生时不影响性能，每次变化的信息（由观察者实例决定）会保存在 MutationRecord 实例中，然后添加到 **记录队列**。这个队列对每个 MutationObserver 实例都是唯一的，是所有 DOM 变化事件的有序列表。

1. **记录队列**

每次 MutationRecord 被添加到 MutationObserver 的记录队列时，仅当之前没有已排期的微任务回调时（队列中微任务长度为 0），才会将观察者注册的回调（在初始化 MutationObserver 时传入）作为微任务调度到任务队列上。这样可以保证记录队列的内容不会被回调处理两次。

不过在回调的微任务异步执行期间，有可能又会发生更多变化事件。因此被调用的回调会接收到一个 MutationRecord 实例的数组，顺序为它们进入记录队列的顺序。回调要负责处理这个数组的每一个实例，因为函数退出之后这些实现就不存在了。回调执行后，这些 MutationRecord 就用不着了，因此记录队列会被清空，其内容会被丢弃。

2. **takeRecords()方法**

调用 MutationObserver 实例的 takeRecords()方法可以清空记录队列，取出并返回其中的所有 MutationRecord 实例。看这个例子：

```js
let observer = new MutationObserver((mutationRecords) =>
  console.log(mutationRecords)
);
observer.observe(document.body, { attributes: true });
document.body.className = "foo";
document.body.className = "bar";
document.body.className = "baz";
console.log(observer.takeRecords());
console.log(observer.takeRecords());
// [MutationRecord, MutationRecord, MutationRecord]
// []
```

这在希望断开与观察目标的联系，但又希望处理由于调用 disconnect()而被抛弃的记录队列中的 MutationRecord 实例时比较有用。

### 14.3.4. 性能，内存与垃圾回收

DOM Level 2 规范中描述的 MutationEvent 定义了一组会在各种 DOM 变化时触发的事件。由于浏览器事件的实现机制，这个接口出现了严重的性能问题。因此，DOM Level 3 规定废弃了这些事件。MutationObserver 接口就是为替代这些事件而设计的更实用、性能更好的方案。

将变化回调委托给微任务来执行可以保证事件同步触发，同时避免随之而来的混乱。为 MutationObserver 而实现的记录队列，可以保证即使变化事件被爆发式地触发，也不会显著地拖慢浏览器。无论如何，使用 MutationObserver 仍然 **不是没有代价** 的。因此理解什么时候避免出现这种情况就很重要了。

1. **MutationObserver 的引用**

MutationObserver 实例与目标节点之间的引用关系是非对称的。MutationObserver 拥有对要观察的目标节点的弱引用。因为是弱引用，所以不会妨碍垃圾回收程序回收目标节点。

然而，目标节点却拥有对 MutationObserver 的强引用。如果目标节点从 DOM 中被移除，随后被垃圾回收，则关联的 MutationObserver 也会被垃圾回收。

2. **MutationRecord 的引用**

记录队列中的每个 MutationRecord 实例至少包含对已有 DOM 节点的一个引用。如果变化是 childList 类型，则会包含多个节点的引用。记录队列和回调处理的默认行为是耗尽这个队列，处理每个 MutationRecord，然后让它们超出作用域并被垃圾回收。

有时候可能需要保存某个观察者的完整变化记录。保存这些 MutationRecord 实例，也就会保存它们引用的节点，因而会妨碍这些节点被回收。如果需要尽快地释放内存，建议从每个 MutationRecord 中抽取出最有用的信息，然后保存到一个新对象中，最后抛弃 MutationRecord。
