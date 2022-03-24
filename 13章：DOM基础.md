- [1.1. 理解节点](#11-理解节点)
  - [1.1.1. Node 类型](#111-node-类型)
  - [1.1.2. Document 类型](#112-document-类型)
  - [1.1.3. Element 类型](#113-element-类型)
  - [1.1.4. Text 类型](#114-text-类型)
  - [1.1.5. Comment 类型](#115-comment-类型)
  - [1.1.6. CDATASection 类型](#116-cdatasection-类型)
  - [1.1.7. DocumentType 类型](#117-documenttype-类型)
  - [1.1.8. DocumentFragment 类型](#118-documentfragment-类型)
  - [1.1.9. Attr 类型](#119-attr-类型)
- [1.2. Slector API](#12-slector-api)
  - [1.2.1. querySelector()](#121-queryselector)
  - [1.2.2. querySelectorAll()](#122-queryselectorall)
  - [1.2.3. matches()](#123-matches)
- [1.3. 元素遍历](#13-元素遍历)
- [1.4. HTML 5](#14-html-5)
  - [1.4.1. CSS 类扩展](#141-css-类扩展)
  - [1.4.2. 焦点管理](#142-焦点管理)
  - [1.4.3. HTMLDocument 扩展](#143-htmldocument-扩展)
  - [1.4.4. 字符集属性](#144-字符集属性)
  - [1.4.5. 自定义数据属性](#145-自定义数据属性)
  - [1.4.6. 插入标记](#146-插入标记)
- [1.5. 专有扩展](#15-专有扩展)
  - [1.5.1. children 属性](#151-children-属性)
  - [1.5.2. contains()方法](#152-contains方法)
  - [1.5.3. 插入标记](#153-插入标记)
  - [1.5.4. 滚动](#154-滚动)

本章内容

- 理解节点
- selector API
- HTML5 扩展

**文档对象模型(DOM，Document Object Model)** 是 HTML 和 XML 文档的编程接口。DOM 表示由多层节点构成的文档，通过它开发者可以添加、删除和修改页面的各个部分。脱胎于网景和微软早期的动态 HTML（DHTML，Dynamic HTML），DOM 现在是真正跨平台、语言无关的表示和操作网页的方式。

DOM Level 1 在 1998 年成为 W3C 推荐标准，提供了基本文档结构和查询的接口。本章之所以介绍 DOM，主要因为它与浏览器中的 HTML 网页相关，并且在 JavaScript 中提供了 DOM API。

注意 IE8 及更低版本中的 DOM 是通过 COM 对象实现的。这意味着这些版本的 IE 中，DOM 对象跟原生 JavaScript 对象具有不同的行为和功能。

## 1.1. 理解节点

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

![12-1-DOM层次](/illustrations/12-1-DOM层次.png)

其中，document 节点表示每个文档的根节点。在这里，根节点的唯一子节点是`<html>`元素，我们称之为 **文档元素（documentElement）**。文档元素是文档最外层的元素，所有其他元素都存在于这个元素之内。每个文档只能有一个文档元素。在 HTML 页面中，文档元素始终是`<html>`元素。在 XML 文档中，则没有这样预定义的元素，任何元素都可能成为文档元素。

HTML 中的每段标记都可以表示为这个树形结构中的一个节点。元素节点表示 HTML 元素，属性节点表示属性，文档类型节点表示文档类型，注释节点表示注释。DOM 中总共有 12 种节点类型，这些类型都继承一种基本类型。

### 1.1.1. Node 类型

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

```javascript
if (someNode.nodeType == Node.ELEMENT_NODE) {
  alert('Node is an element.');
}
```

这个例子比较了 someNode.nodeType 与 Node.ELEMENT_NODE 常量。如果两者相等，则意味着 someNode 是一个元素节点。

浏览器并不支持所有节点类型。开发者最常用到的是元素节点和文本节点。本章后面会讨论每种节点受支持的程度及其用法。

1. **nodeName 与 nodeValue**

nodeName 与 nodeValue 保存着有关节点的信息。这两个属性的值完全取决于节点类型。在使用这两个属性前，最好先检测节点类型，如下所示：

```javascript
if (someNode.nodeType == 1) {
  value = someNode.nodeName; // 会显示元素的标签名
}
```

在这个例子中，先检查了节点是不是元素。如果是，则将其 nodeName 的值赋给一个变量。对元素而言，nodeName 始终等于元素的标签名，而 nodeValue 则始终为 null。

2. **节点关系**

文档中的所有节点都与其他节点有关系。这些关系可以形容为家族关系，相当于把文档树比作家谱。在 HTML 中，`<body>`元素是`<html>`元素的子元素，而`<html>`元素则是`<body>`元素的父元素。`<head>`元素是`<body>`元素的同胞元素，因为它们有共同的父元素`<html>`。

每个节点都有一个 childNodes 属性，其中包含一个 NodeList 的实例。NodeList 是一个类数组对象，用于存储可以按位置存取的有序节点。注意，NodeList 并不是 Array 的实例，但可以使用中括号访问它的值，而且它也有 length 属性。NodeList 对象独特的地方在于，它其实是一个对 DOM 结构的查询，因此 DOM 结构的变化会自动地在 NodeList 中反映出来。我们通常说 NodeList 是实时的活动对象，而不是第一次访问时所获得内容的快照。

下面的例子展示了如何使用中括号或使用 item()方法访问 NodeList 中的元素：

```javascript
let firstChild = someNode.childNodes[0];
let secondChild = someNode.childNodes.item(1);
let count = someNode.childNodes.length;
```

无论是使用中括号还是 item()方法都是可以的，但多数开发者倾向于使用中括号，因为它是一个类数组对象。注意，length 属性表示那一时刻 NodeList 中节点的数量。使用...可以像前面介绍 arguments 时一样把 NodeList 对象转换为数组。比如：

```javascript
let arrayOfNodes = [...someNode.childNodes];
```

每个节点都有一个 parentNode 属性，指向其 DOM 树中的父元素。childNodes 中的所有节点都有同一个父元素，因此它们的 parentNode 属性都指向同一个节点。此外，childNodes 列表中的每个节点都是同一列表中其他节点的同胞节点。而使用 previousSibling 和 nextSibling 可以在这个列表的节点间导航。这个列表中第一个节点的 previousSibling 属性是 null，最后一个节点的 nextSibling 属性也是 null，如下所示：

```javascript
if (someNode.nextSibling === null) {
  alert("Last node in the parent's childNodes list.");
} else if (someNode.previousSibling === null) {
  alert("First node in the parent's childNodes list.");
}
```

注意，如果 childNodes 中只有一个节点，则它的 previousSibling 和 nextSibling 属性都是 null。

父节点和它的第一个及最后一个子节点也有专门属性：firstChild 和 lastChild 分别指向 childNodes 中的第一个和最后一个子节点。someNode.firstChild 的值始终等于 someNode.childNodes[0]，而 someNode.lastChild 的值始终等于 someNode.childNodes[someNode.childNodes.length-1]。如果只有一个子节点，则 firstChild 和 lastChild 指向同一个节点。如果没有子节点，则 firstChild 和 lastChild 都是 null。上述这些节点之间的关系为在文档树的节点之间导航提供了方便。下图形象地展示了这些关系。

![12-2-节点关系](/illustrations/12-2-节点关系.png)

有了这些关系，childNodes 属性的作用远远不止是必备属性那么简单了。这是因为利用这些关系指针，几乎可以访问到文档树中的任何节点，而这种便利性是 childNodes 的最大亮点。还有一个便利的方法是 hasChildNodes()，这个方法如果返回 true 则说明节点有一个或多个子节点。相比查询 childNodes 的 length 属性，这个方法无疑更方便。

最后还有一个所有节点都共享的关系。ownerDocument 属性是一个指向代表整个文档的文档节点的指针。所有节点都被创建它们（或自己所在）的文档所拥有，因为一个节点不可能同时存在于两个或者多个文档中。这个属性为迅速访问文档节点提供了便利，因为无需在文档结构中逐层上溯了。

注意 虽然所有节点类型都继承了 Node，但并非所有节点都有子节点。本章后面会讨论不同节点类型的差异。

3. **操纵节点**

因为所有关系指针都是只读的，所以 DOM 又提供了一些操纵节点的方法。最常用的方法是 appendChild()，用于在 childNodes 列表末尾添加节点。添加新节点会更新相关的关系指针，包括父节点和之前的最后一个子节点。appendChild()方法返回新添加的节点，如下所示：

```javascript
let returnedNode = someNode.appendChild(newNode);
alert(returnedNode == newNode); // true
alert(someNode.lastChild == newNode); // true
```

如果把文档中已经存在的节点传给 appendChild()，则这个节点会从之前的位置被转移到新位置。即使 DOM 树通过各种关系指针维系，一个节点也不会在文档中同时出现在两个或更多个地方。因此，如果调用 appendChild()传入父元素的第一个子节点，则这个节点会成为父元素的最后一个子节点，如下所示：

```javascript
// 假设someNode 有多个子节点
let returnedNode = someNode.appendChild(someNode.firstChild);
alert(returnedNode == someNode.firstChild); // false
alert(returnedNode == someNode.lastChild); // true
```

如果想把节点放到 childNodes 中的特定位置而不是末尾，则可以使用 insertBefore()方法。这个方法接收两个参数：要插入的节点和参照节点。调用这个方法后，要插入的节点会变成参照节点的前一个同胞节点，并被返回。如果参照节点是 null，则 insertBefore()与 appendChild()效果相
同，如下面的例子所示：

```javascript
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

```javascript
// 替换第一个子节点
let returnedNode = someNode.replaceChild(newNode, someNode.firstChild);
// 替换最后一个子节点
returnedNode = someNode.replaceChild(newNode, someNode.lastChild);
```

使用 replaceChild()插入一个节点后，所有关系指针都会从被替换的节点复制过来。虽然被替换的节点从技术上说仍然被同一个文档所拥有，但文档中已经没有它的位置。

要移除节点而不是替换节点，可以使用 removeChild()方法。这个方法接收一个参数，即要移除的节点。被移除的节点会被返回，如下面的例子所示：

```javascript
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

```javascript
let deepList = myList.cloneNode(true);
alert(deepList.childNodes.length); // 3（IE9 之前的版本）或7（其他浏览器）
let shallowList = myList.cloneNode(false);
alert(shallowList.childNodes.length); // 0
```

在这个例子中，deepList 保存着 myList 的副本。这意味着 deepList 有 3 个列表项，每个列表项又各自包含文本。变量 shallowList 则保存着 myList 的浅副本， 因此没有子节点。deepList.childNodes.length 的值会因 IE8 及更低版本和其他浏览器对空格的处理方式而不同。IE9
之前的版本不会为空格创建节点。

注意 cloneNode()方法不会复制添加到 DOM 节点的 JavaScript 属性，比如事件处理程序。这个方法只复制 HTML 属性，以及可选地复制子节点。除此之外则一概不会复制。IE 在很长时间内会复制事件处理程序，这是一个 bug，所以推荐在复制前先删除事件处理程序。

本节要介绍的最后一个方法是 normalize()。这个方法唯一的任务就是处理文档子树中的文本节点。由于解析器实现的差异或 DOM 操作等原因，可能会出现并不包含文本的文本节点，或者文本节点之间互为同胞关系。在节点上调用 normalize()方法会检测这个节点的所有后代，从中搜索上述两种情形。如果发现空文本节点，则将其删除；如果两个同胞节点是相邻的，则将其合并为一个文本节点。这个方法将在本章后面进一步讨论。

### 1.1.2. Document 类型

Document 类型是 JavaScript 中表示文档节点的类型。在浏览器中，文档对象 document 是 HTMLDocument 的实例（HTMLDocument 继承 Document），表示整个 HTML 页面。document 是 window 对象的属性，因此是一个全局对象。Document 类型的节点有以下特征：

- nodeType 等于 9；
- nodeName 值为'#document'；
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

```javascript
let html = document.documentElement; // 取得对<html>的引用
alert(html === document.childNodes[0]); // true
alert(html === document.firstChild); // true
```

作为 HTMLDocument 的实例，document 对象还有一个 body 属性，直接指向`<body>`元素。因为这个元素是开发者使用最多的元素，所以 JavaScript 代码中经常可以看到 document.body，比如：

```javascript
let body = document.body; // 取得对<body>的引用
```

所有主流浏览器都支持 document.documentElement 和 document.body。

Document 类型另一种可能的子节点是 DocumentType。<!doctype>标签是文档中独立的部分，其信息可以通过 doctype 属性（在浏览器中是 document.doctype）来访问，比如：

```javascript
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

```javascript
// 读取文档标题
let originalTitle = document.title;
// 修改文档标题
document.title = 'New page title';
```

接下来要介绍的 3 个属性是 URL、domain 和 referrer。其中，URL 包含当前页面的完整 URL（地址栏中的 URL），domain 包含页面的域名，而 referrer 包含链接到当前页面的那个页面的 URL。如果当前页面没有来源，则 referrer 属性包含空字符串。所有这些信息都可以在请求的 HTTP 头部信息中获取，只是在 JavaScript 中通过这几个属性暴露出来而已，如下面的例子所示：

```javascript
// 取得完整的URL
let url = document.URL;
// 取得域名
let domain = document.domain;
// 取得来源
let referrer = document.referrer;
```

URL 跟域名是相关的。比如，如果 document.URL 是http://www.google.com/something，则document.domain 就是www.google.com。

在这些属性中，只有 domain 属性是可以设置的。出于安全考虑，给 domain 属性设置的值是有限制的。如果 URL 包含子域名如 topics.google.com，则可以将 domain 设置为'google.com'（URL 包含“www”时也一样，比如www.google.com）。不能给这个属性设置URL 中不包含的值，比如：

```javascript
// 页面来自topics.google.com
document.domain = 'google.com'; // 成功
document.domain = 'baidu.com'; // 出错！
```

当页面中包含来自某个不同子域的窗格（`<frame>`）或内嵌窗格（`<iframe>`）时，设置 document.domain 是有用的。因为跨源通信存在安全隐患，所以不同子域的页面间无法通过 JavaScript 通信。此时，在每个页面上把 document.domain 设置为相同的值，这些页面就可以访问对方的 JavaScript 对象了。比如，一个加载自www.google.com 的页面中包含一个内嵌窗格，其中的页面加载自 topics.google.com。这两个页面的 document.domain 包含不同的字符串，内部和外部页面相互之间不能访问对方的 JavaScript 对象。如果每个页面都把 document.domain 设置为 google.com，那这两个页面之间就可以通信了。

浏览器对 domain 属性还有一个限制， 即这个属性一旦放松就不能再收紧。比如， 把 document.domain 设置为'google.com'之后，就不能再将其设置回'topics.google.com'，后者会导致错误，比如：

```javascript
// 页面来自topics.google.com
document.domain = 'google.com'; // 放松，成功
document.domain = 'topics.google.com'; // 收紧，错误！
```

3. **定位元素**

使用 DOM 最常见的情形可能就是获取某个或某组元素的引用，然后对它们执行某些操作。document 对象上暴露了一些方法，可以实现这些操作。getElementById()和 getElementsByTagName()就是 Document 类型提供的两个方法。

getElementById()方法接收一个参数，即要获取元素的 ID，如果找到了则返回这个元素，如果没找到则返回 null。参数 ID 必须跟元素在页面中的 id 属性值完全匹配，包括大小写。比如页面中有以下元素：

```html
<div id="myDiv">Some text</div>
```

可以使用如下代码取得这个元素：

```javascript
let div = document.getElementById('myDiv'); // 取得对这个<div>元素的引用
```

但参数大小写不匹配会返回 null：

```javascript
let div = document.getElementById('mydiv'); // null
```

如果页面中存在多个具有相同 ID 的元素，则 getElementById()返回在文档中出现的第一个元素。

getElementsByTagName()是另一个常用来获取元素引用的方法。这个方法接收一个参数，即要获取元素的标签名，返回包含零个或多个元素的 NodeList。在 HTML 文档中，这个方法返回一个 HTMLCollection 对象。考虑到二者都是“实时”列表，HTMLCollection 与 NodeList 是很相似的。例如，下面的代码会取得页面中所有的`<img>`元素并返回包含它们的 HTMLCollection：

```javascript
let images = document.getElementsByTagName('img');
```

这里把返回的 HTMLCollection 对象保存在了变量 images 中。与 NodeList 对象一样，也可以使用中括号或 item()方法从 HTMLCollection 取得特定的元素。而取得元素的数量同样可以通过 length 属性得知，如下所示：

```javascript
alert(images.length); // 图片数量
alert(images[0].src); // 第一张图片的src 属性
alert(images.item(0).src); // 同上
```

HTMLCollection 对象还有一个额外的方法 namedItem()，可通过标签的 name 属性取得某一项的引用。例如，假设页面中包含如下的`<img>`元素：

```html
<img src="myimage.gif" name="myImage" />
```

那么也可以像这样从 images 中取得对这个`<img>`元素的引用：

```javascript
let myImage = images.namedItem('myImage');
```

这样，HTMLCollection 就提供了除索引之外的另一种获取列表项的方式，从而为取得元素提供了便利。对于 name 属性的元素，还可以直接使用中括号来获取，如下面的例子所示：

```javascript
let myImage = images['myImage'];
```

对 HTMLCollection 对象而言，中括号既可以接收数值索引，也可以接收字符串索引。而在后台，数值索引会调用 item()，字符串索引会调用 namedItem()。

要取得文档中的所有元素，可以给 getElementsByTagName()传入*。在 JavaScript 和 CSS 中，*一般被认为是匹配一切的字符。来看下面的例子：

```
let allElements = document.getElementsByTagName('*');
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

这里所有的单选按钮都有名为'color'的 name 属性，但它们的 ID 都不一样。这是因为 ID 是为了匹配对应的`<label>`元素，而 name 相同是为了保证只将三个中的一个值发送给服务器。然后就可以像下面这样取得所有单选按钮：

```javascript
let radios = document.getElementsByName('color');
```

与 getElementsByTagName()一样，getElementsByName()方法也返回 HTMLCollection。不过在这种情况下，namedItem()方法只会取得第一项（因为所有项的 name 属性都一样）。

4. **特殊集合**

document 对象上还暴露了几个特殊集合，这些集合也都是 HTMLCollection 的实例。这些集合是访问文档中公共部分的快捷方式，列举如下。

- document.anchors 包含文档中所有带 name 属性的`<a>`元素。
- document.forms 包含文档中所有`<form>`元素（与 document.getElementsByTagName('form')返回的结果相同）。
- document.images 包含文档中所有`<img>`元素（与 document.getElementsByTagName('img')返回的结果相同）。
- document.links 包含文档中所有带 href 属性的`<a>`元素。

这些特殊集合始终存在于 HTMLDocument 对象上，而且与所有 HTMLCollection 对象一样，其内容也会实时更新以符合当前文档的内容。

5. **DOM 兼容性检测**

由于 DOM 有多个 Level 和多个部分，因此确定浏览器实现了 DOM 的哪些部分是很必要的。document.implementation 属性是一个对象，其中提供了与浏览器 DOM 实现相关的信息和能力。DOM Level 1 在 document.implementation 上只定义了一个方法，即 hasFeature()。这个方法接收两个参数：特性名称和 DOM 版本。如果浏览器支持指定的特性和版本，则 hasFeature()方法返回 true，如下面的例子所示：

```javascript
let hasXmlDom = document.implementation.hasFeature('XML', '1.0');
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
        document.write('<strong>' + new Date().toString() + '</strong>');
      </script>
    </p>
  </body>
</html>
```

这个例子会在页面加载过程中输出当前日期和时间。日期放在了`<strong>`元素中，如同它们之前就包含在 HTML 页面中一样。这意味着会创建一个 DOM 元素，以后也可以访问。通过 write()和 writeln()输出的任何 HTML 都会以这种方式来处理。

write()和 writeln()方法经常用于动态包含外部资源，如 JavaScript 文件。在包含 JavaScript 文件时，记住不能像下面的例子中这样直接包含字符串'`</script>`'，因为这个字符串会被解释为脚本块的结尾，导致后面的代码不能执行：

```html
<html>
<head>
  <title>document.write() Example</title>
</head>
<body>
<script type='text/javascript'>
document.write('<script type=\'text/javascript\' src=\'file.js\'>' +
'</script>');
</script>
</body>
</html>
```

虽然这样写看起来没错，但输出之后的'`</script>`'会匹配最外层的`<script>`标签，导致页面中显示出');。为避免出现这个问题，需要对前面的例子稍加修改：

```html
<html>
  <head>
    <title>document.write() Example</title>
  </head>
  <body>
    <script type="text/javascript">
      document.write(
        '<script type='text/javascript' src='file.js'>' + '<\/script>'
      );
    </script>
  </body>
</html>
```

这里的字符串'<\/script>'不会再匹配最外层的`<script>`标签，因此不会在页面中输出额外内容。

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
        document.write('Hello world!');
      };
    </script>
  </body>
</html>
```

这个例子使用了 window.onload 事件处理程序，将调用 document.write()的函数推迟到页面加载完毕后执行。执行之后，字符串'Hello world!'会重写整个页面内容。

open()和 close()方法分别用于打开和关闭网页输出流。在调用 write()和 writeln()时，这两个方法都不是必需的。

注意 严格的 XHTML 文档不支持文档写入。对于内容类型为 application/xml+xhtml 的页面，这些方法不起作用。

### 1.1.3. Element 类型

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

```javascript
const myDiv = document.getElementById('myDiv');
console.log(myDiv.nodeName); // DIV
console.log(myDIv.tagName); // DIV
```

例子中的元素标签名为 div，ID 为'myDiv'。注意，div.tagName 实际上返回的是'DIV'而不是'div'。在 HTML 中，元素标签名始终以全大写表示；在 XML（包括 XHTML）中，标签名始终与源代码中的大小写一致。如果不确定脚本是在 HTML 文档还是 XML 文档中运行，最好将标签名转换为小写形式，以便于比较：

```javascript
if (element.tagName === 'div') {
  // 不要这样做，可能出错！
  // do something here
}
if (element.tagName.toLowerCase() === 'div') {
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
- dir，语言的书写方向（'ltr'表示从左到右，'rtl'表示从右到左，同样很少用）；
- className，相当于 class 属性，用于指定元素的 CSS 类（因为 class 是 ECMAScript 关键字，所以不能直接用这个名字）。

所有这些都可以用来获取对应的属性值，也可以用来修改相应的值。比如有下面的 HTML 元素：

```html
<div id="myDiv" class="bd" title="Body text" lang="en" dir="ltr"></div>
```

这个元素中的所有属性都可以使用下列 JavaScript 代码读取：

```javascript
let div = document.getElementById('myDiv');
console.log(div.id); // 'myDiv'
console.log(div.className); // 'bd'
console.log(div.title); // 'Body text'
console.log(div.lang); // 'en'
console.log(div.dir); // 'ltr'
```

而且，可以使用下列代码修改元素的属性：

```javascript
div.id = 'someOtherId';
div.className = 'ft';
div.title = 'Some other text';
div.lang = 'fr';
div.dir = 'rtl';
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

```javascript
let div = document.getElementById('myDiv');
console.log(div.getAttribute('id')); // 'myDiv'
console.log(div.getAttribute('class')); // 'bd'
console.log(div.getAttribute('title')); // 'Body text'
console.log(div.getAttribute('lang')); // 'en'
console.log(div.getAttribute('dir')); // 'ltr'
```

注意传给 getAttribute()的属性名与它们实际的属性名是一样的，因此这里要传'class'而非'className'（className 是作为对象属性时才那么拼写的）。如果给定的属性不存在，则 getAttribute()返回 null。

getAttribute()方法也能取得不是 HTML 语言正式属性的自定义属性的值。比如下面的元素：

```html
<div id="myDiv" my_special_attribute="hello!"></div>
```

这个元素有一个自定义属性 my_special_attribute，值为'hello!'。可以像其他属性一样使用 getAttribute()取得这个属性的值：

```javascript
let value = div.getAttribute('my_special_attribute');
```

注意，属性名不区分大小写，因此'ID'和'id'被认为是同一个属性。另外，根据 HTML5 规范的要求，自定义属性名应该前缀 data-以方便验证。

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

```javascript
div.setAttribute('id', 'someOtherId');
div.setAttribute('class', 'ft');
div.setAttribute('title', 'Some other text');
div.setAttribute('lang', 'fr');
div.setAttribute('dir', 'rtl');
```

setAttribute()适用于 HTML 属性，也适用于自定义属性。另外，使用 setAttribute()方法设置的属性名会规范为小写形式，因此'ID'会变成'id'。

因为元素属性也是 DOM 对象属性，所以直接给 DOM 对象的属性赋值也可以设置元素属性的值，如下所示：

```javascript
div.id = 'someOtherId';
div.align = 'left';
```

注意，在 DOM 对象上添加自定义属性，如下面的例子所示，不会自动让它变成元素的属性：

```javascript
div.mycolor = 'red';
console.log(div.getAttribute('mycolor')); // null（IE 除外）
```

这个例子添加了一个自定义属性 mycolor 并将其值设置为'red'。在多数浏览器中，这个属性不会自动变成元素属性。因此调用 getAttribute()取得 mycolor 的值会返回 null。

最后一个方法 removeAttribute()用于从元素中删除属性。这样不单单是清除属性的值，而是会把整个属性完全从元素中去掉，如下所示：

```javascript
div.removeAttribute('class');
```

这个方法用得并不多，但在序列化 DOM 元素时可以通过它控制要包含的属性。

4. **attributes 属性**

Element 类型是唯一使用 attributes 属性的 DOM 节点类型。attributes 属性包含一个 NamedNodeMap 实例，是一个类似 NodeList 的“实时”集合。元素的每个属性都表示为一个 Attr 节点，并保存在这个 NamedNodeMap 对象中。NamedNodeMap 对象包含下列方法：

- getNamedItem(name)，返回 nodeName 属性等于 name 的节点；
- removeNamedItem(name)，删除 nodeName 属性等于 name 的节点；
- setNamedItem(node)，向列表中添加 node 节点，以其 nodeName 为索引；
- item(pos)，返回索引位置 pos 处的节点。

attributes 属性中的每个节点的 nodeName 是对应属性的名字，nodeValue 是属性的值。比如，要取得元素 id 属性的值，可以使用以下代码：

```javascript
let id = element.attributes.getNamedItem('id').nodeValue;
```

下面是使用中括号访问属性的简写形式：

```javascript
let id = element.attributes['id'].nodeValue;
```

同样，也可以用这种语法设置属性的值，即先取得属性节点，再将其 nodeValue 设置为新值，如下所示：

```javascript
element.attributes['id'].nodeValue = 'someOtherId';
```

removeNamedItem()方法与元素上的 removeAttribute()方法类似，也是删除指定名字的属性。下面的例子展示了这两个方法唯一的不同之处，就是 removeNamedItem()返回表示被删除属性的 Attr 节点：

```javascript
let oldAttr = element.attributes.removeNamedItem('id');
```

setNamedItem()方法很少使用，它接收一个属性节点，然后给元素添加一个新属性，如下所示：

```javascript
element.attributes.setNamedItem(newAttr);
```

一般来说，因为使用起来更简便，通常开发者更喜欢使用 getAttribute()、removeAttribute()和 setAttribute()方法，而不是刚刚介绍的 NamedNodeMap 对象的方法。

attributes 属性最有用的场景是需要迭代元素上所有属性的时候。这时候往往是要把 DOM 结构序列化为 XML 或 HTML 字符串。比如，以下代码能够迭代一个元素上的所有属性并以 attribute1='value1' attribute2='value2'的形式生成格式化字符串：

```javascript
const outputAttributes = function (element) {
  let pairs = [];
  for (let i = 0, len = element.attributes.length; i < len; ++i) {
    const attribute = element.attributes[i];
    pairs.push(`${attribute.nodeName}='${attribute.nodeValue}'`);
  }
  return pairs.join(' ');
};
```

这个函数使用数组存储每个名/值对，迭代完所有属性后，再将这些名/值对用空格拼接在一起。（这个技术常用于序列化为长字符串。）这个函数中的 for 循环使用 attributes.length 属性迭代每个属性，将每个属性的名字和值输出为字符串。不同浏览器返回的 attributes 中的属性顺序也可能不一样。HTML 或 XML 代码中属性出现的顺序不一定与 attributes 中的顺序一致。

5. **创建元素**

可以使用 document.createElement()方法创建新元素。这个方法接收一个参数，即要创建元素的标签名。在 HTML 文档中，标签名是不区分大小写的，而 XML 文档（包括 XHTML）是区分大小写的。要创建`<div>`元素，可以使用下面的代码：

```javascript
let div = document.createElement('div');
```

使用 createElement()方法创建新元素的同时也会将其 ownerDocument 属性设置为 document。此时，可以再为其添加属性、添加更多子元素。比如：

```javascript
div.id = 'myNewDiv';
div.className = 'box';
```

在新元素上设置这些属性只会附加信息。因为这个元素还没有添加到文档树，所以不会影响浏览器显示。要把元素添加到文档树，可以使用 appendChild()、insertBefore()或 replaceChild()。比如，以下代码会把刚才创建的元素添加到文档的`<body>`元素中：

```javascript
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

```javascript
for (let i = 0, len = element.childNodes.length; i < len; ++i) {
  if (element.childNodes[i].nodeType == 1) {
    // 执行某个操作
  }
}
```

以上代码会遍历某个元素的子节点，并且只在 nodeType 等于 1（即 Element 节点）时执行某个操作。

要取得某个元素的子节点和其他后代节点，可以使用元素的 getElementsByTagName()方法。在元素上调用这个方法与在文档上调用是一样的，只不过搜索范围限制在当前元素之内，即只会返回当前元素的后代。对于本节前面`<ul>`的例子，可以像下面这样取得其所有的`<li>`元素：

```javascript
let ul = document.getElementById('myList');
let items = ul.getElementsByTagName('li');
```

这里例子中的`<ul>`元素只有一级子节点，如果它包含更多层级，则所有层级中的`<li>`元素都会返回。

### 1.1.4. Text 类型

Text 节点由 Text 类型表示，包含按字面解释的纯文本，也可能包含转义后的 HTML 字符，但不含 HTML 代码。Text 类型的节点具有以下特征：

- nodeType 等于 3；
- nodeName 值为'#text'；
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

示例中的第一个`<div>`元素中不包含内容，因此不会产生文本节点。只要开始标签和结束标签之间有内容，就会创建一个文本节点，因此第二个`<div>`元素会有一个文本节点的子节点，虽然它只包含空格。这个文本节点的 nodeValue 就是一个空格。第三个`<div>`元素也有一个文本节点的子节点，其 nodeValue 的值为'Hello World!'。下列代码可以用来访问这个文本节点：

```javascript
let textNode = div.firstChild; // 或div.childNodes[0]
```

取得文本节点的引用后，可以像这样来修改它：

```javascript
div.firstChild.nodeValue = 'Some other message';
```

只要节点在当前的文档树中，这样的修改就会马上反映出来。修改文本节点还有一点要注意，就是 HTML 或 XML 代码（取决于文档类型）会被转换成实体编码，即小于号、大于号或引号会被转义，如下所示：

```javascript
// 输出为'Some &lt;strong&gt;other&lt;/strong&gt; message'
div.firstChild.nodeValue = 'Some <strong>other</strong> message';
```

这实际上是在将 HTML 字符串插入 DOM 文档前进行编码的有效方式。

1. **创建文本节点**

document.createTextNode()可以用来创建新文本节点，它接收一个参数，即要插入节点的文本。跟设置已有文本节点的值一样，这些要插入的文本也会应用 HTML 或 XML 编码，如下面的例子所示：

```javascript
let textNode = document.createTextNode('<strong>Hello</strong> world!');
```

创建新文本节点后，其 ownerDocument 属性会被设置为 document。但在把这个节点添加到文档树之前，我们不会在浏览器中看到它。以下代码创建了一个`<div>`元素并给它添加了一段文本消息：

```javascript
let element = document.createElement('div');
element.className = 'message';
let textNode = document.createTextNode('Hello world!');
element.appendChild(textNode);
document.body.appendChild(element);
```

这个例子首先创建了一个`<div>`元素并给它添加了值为'message'的 class 属性，然后又创建了一个文本节点并添加到该元素。最后一步是把这个元素添加到文档的主体上，这样元素及其包含的文本会出现在浏览器中。

一般来说一个元素只包含一个文本子节点。不过，也可以让元素包含多个文本子节点，如下面的例子所示：

```javascript
let element = document.createElement('div');
element.className = 'message';
let textNode = document.createTextNode('Hello world!');
element.appendChild(textNode);
let anotherTextNode = document.createTextNode('Yippee!');
element.appendChild(anotherTextNode);
document.body.appendChild(element);
```

在将一个文本节点作为另一个文本节点的同胞插入后，两个文本节点的文本之间不会包含空格。

2. **规范化文本节点**

DOM 文档中的同胞文本节点可能导致困惑，因为一个文本节点足以表示一个文本字符串。同样，DOM 文档中也经常会出现两个相邻文本节点。为此，有一个方法可以合并相邻的文本节点。这个方法叫 normalize()，是在 Node 类型中定义的（因此所有类型的节点上都有这个方法）。在包含两个或多
个相邻文本节点的父节点上调用 normalize()时，所有同胞文本节点会被合并为一个文本节点，这个文本节点的 nodeValue 就等于之前所有同胞节点 nodeValue 拼接在一起得到的字符串。来看下面的例子：

```javascript
let element = document.createElement('div');
element.className = 'message';
let textNode = document.createTextNode('Hello world!');
element.appendChild(textNode);
let anotherTextNode = document.createTextNode('Yippee!');
element.appendChild(anotherTextNode);
document.body.appendChild(element);
console.log(element.childNodes.length); // 2
element.normalize();
console.log(element.childNodes.length); // 1
console.log(element.firstChild.nodeValue); // 'Hello world!Yippee!'
```

浏览器在解析文档时，永远不会创建同胞文本节点。同胞文本节点只会出现在 DOM 脚本生成的文档树中。

3. **拆分文本节点**

Text 类型定义了一个与 normalize()相反的方法——splitText()。这个方法可以在指定的偏移位置拆分 nodeValue，将一个文本节点拆分成两个文本节点。拆分之后，原来的文本节点包含开头到偏移位置前的文本，新文本节点包含剩下的文本。这个方法返回新的文本节点，具有与原来的文本节点
相同的 parentNode。来看下面的例子：

```javascript
let element = document.createElement('div');
element.className = 'message';
let textNode = document.createTextNode('Hello world!');
element.appendChild(textNode);
document.body.appendChild(element);
let newNode = element.firstChild.splitText(5);
console.log(element.firstChild.nodeValue); // 'Hello'
console.log(newNode.nodeValue); // ' world!'
console.log(element.childNodes.length); // 2
```

在这个例子中，包含'Hello world!'的文本节点被从位置 5 拆分成两个文本节点。位置 5 对应'Hello'和'world!'之间的空格，因此原始文本节点包含字符串'Hello'，而新文本节点包含文本'world!'（包含空格）。

拆分文本节点最常用于从文本节点中提取数据的 DOM 解析技术。

### 1.1.5. Comment 类型

DOM 中的注释通过 Comment 类型表示。Comment 类型的节点具有以下特征：

- nodeType 等于 8；
- nodeName 值为'#comment'；
- nodeValue 值为注释的内容；
- parentNode 值为 Document 或 Element 对象；
- 不支持子节点。

Comment 类型与 Text 类型继承同一个基类（CharacterData），因此拥有除 splitText()之外 Text 节点所有的字符串操作方法。与 Text 类型相似，注释的实际内容可以通过 nodeValue 或 data 属性获得。

注释节点可以作为父节点的子节点来访问。比如下面的 HTML 代码：

```html
<div id="myDiv"><!-- A comment --></div>
```

这里的注释是`<div>`元素的子节点，这意味着可以像下面这样访问它：

```javascript
let div = document.getElementById('myDiv');
let comment = div.firstChild;
console.log(comment.data); // 'A comment'
```

可以使用 document.createComment()方法创建注释节点，参数为注释文本，如下所示：

```javascript
let comment = document.createComment('A comment');
```

显然，注释节点很少通过 JavaScrpit 创建和访问，因为注释几乎不涉及算法逻辑。此外，浏览器不承认结束的`</html>`标签之后的注释。如果要访问注释节点，则必须确定它们是`<html>`元素的后代。

### 1.1.6. CDATASection 类型

CDATASection 类型表示 XML 中特有的 CDATA 区块。CDATASection 类型继承 Text 类型，因此拥有包括 splitText()在内的所有字符串操作方法。CDATASection 类型的节点具有以下特征：

- nodeType 等于 4；
- nodeName 值为'#cdata-section'；
- nodeValue 值为 CDATA 区块的内容；
- parentNode 值为 Document 或 Element 对象；
- 不支持子节点。

CDATA 区块只在 XML 文档中有效，因此某些浏览器比较陈旧的版本会错误地将 CDATA 区块解析为 Comment 或 Element。比如下面这行代码：

```html
<div id="myDiv"><![CDATA[This is some content.]]></div>
```

这里`<div>`的第一个子节点应该是 CDATASection 节点。但主流的四大浏览器没有一个将其识别为 CDATASection。即使在有效的 XHTML 文档中，这些浏览器也不能恰当地支持嵌入的 CDATA 区块。

在真正的 XML 文档中，可以使用 document.createCDataSection()并传入节点内容来创建 CDATA 区块。

### 1.1.7. DocumentType 类型

DocumentType 类型的节点包含文档的文档类型（doctype）信息，具有以下特征：

- nodeType 等于 10；
- nodeName 值为文档类型的名称；
- nodeValue 值为 null；
- parentNode 值为 Document 对象；
- 不支持子节点。

DocumentType 对象在 DOM Level 1 中不支持动态创建，只能在解析文档代码时创建。对于支持这个类型的浏览器，DocumentType 对象保存在 document.doctype 属性中。DOM Level 1 规定了 DocumentType 对象的 3 个属性：name、entities 和 notations。其中，name 是文档类型的名称，entities 是这个文档类型描述的实体的 NamedNodeMap，而 notations 是这个文档类型描述的表示法的 NamedNodeMap。因为浏览器中的文档通常是 HTML 或 XHTML 文档类型，所以 entities 和 notations 列表为空。（这个对象只包含行内声明的文档类型。）无论如何，只有 name 属性是有用的。这个属性包含文档类型的名称，即紧跟在`<!DOCTYPE` 后面的那串文本。比如下面的 HTML 4.01 严格文档类型：

```html
<!DOCTYPE html PUBLIC '-// W3C// DTD HTML 4.01// EN' 'http:// www.w3.org/TR/html4/strict.dtd'>
```

对于这个文档类型，name 属性的值是'html'：

```javascript
console.log(document.doctype.name); // 'html'
```

### 1.1.8. DocumentFragment 类型

在所有节点类型中，DocumentFragment 类型是唯一一个在标记中没有对应表示的类型。DOM 将文档片段定义为“轻量级”文档，能够包含和操作节点，却没有完整文档那样额外的消耗。DocumentFragment 节点具有以下特征：

- nodeType 等于 11；
- nodeName 值为'#document-fragment'；
- nodeValue 值为 null；
- parentNode 值为 null；
- 子节点可以是 Element、ProcessingInstruction、Comment、Text、CDATASection 或 EntityReference。

不能直接把文档片段添加到文档。相反，文档片段的作用是充当其他要被添加到文档的节点的仓库。可以使用 document.createDocumentFragment()方法像下面这样创建文档片段：

```javascript
let fragment = document.createDocumentFragment();
```

文档片段从 Node 类型继承了所有文档类型具备的可以执行 DOM 操作的方法。如果文档中的一个节点被添加到一个文档片段，则该节点会从文档树中移除，不会再被浏览器渲染。添加到文档片段的新节点同样不属于文档树，不会被浏览器渲染。可以通过 appendChild()或 insertBefore()方法将文
档片段的内容添加到文档。在把文档片段作为参数传给这些方法时，这个文档片段的所有子节点会被添加到文档中相应的位置。文档片段本身永远不会被添加到文档树。以下面的 HTML 为例：

```html
<ul id="myList"></ul>
```

假设想给这个`<ul>`元素添加 3 个列表项。如果分 3 次给这个元素添加列表项，浏览器就要重新渲染 3 次页面，以反映新添加的内容。为避免多次渲染，下面的代码示例使用文档片段创建了所有列表项，然后一次性将它们添加到了`<ul>`元素：

```javascript
let fragment = document.createDocumentFragment();
let ul = document.getElementById('myList');
for (let i = 0; i < 3; ++i) {
  let li = document.createElement('li');
  li.appendChild(document.createTextNode(`Item ${i + 1}`));
  fragment.appendChild(li);
}
ul.appendChild(fragment);
```

这个例子先创建了一个文档片段，然后取得了`<ul>`元素的引用。接着通过 for 循环创建了 3 个列表项，每一项都包含表明自己身份的文本。为此先创建`<li>`元素，再创建文本节点并添加到该元素。然后通过 appendChild()把`<li>`元素添加到文档片段。循环结束后，通过把文档片段传给 appendChild()将所有列表项添加到了`<ul>`元素。此时，文档片段的子节点全部被转移到了`<ul>`元素。

### 1.1.9. Attr 类型

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

```javascript
let attr = document.createAttribute('align');
attr.value = 'left';
element.setAttributeNode(attr);
console.log(element.attributes['align'].value); // 'left'
console.log(element.getAttributeNode('align').value); // 'left'
console.log(element.getAttribute('align')); // 'left'
```

在这个例子中，首先创建了一个新属性。调用 createAttribute()并传入'align'为新属性设置了 name 属性，因此就不用再设置了。随后，value 属性被赋值为'left'。为把这个新属性添加到元素上，可以使用元素的 setAttributeNode()方法。添加这个属性后，可以通过不同方式访问它，包括 attributes 属性、getAttributeNode()和 getAttribute()方法。其中，attributes 属性和 getAttributeNode()方法都返回属性对应的 Attr 节点，而 getAttribute()方法只返回属性的值。

注意 将属性作为节点来访问多数情况下并无必要。推荐使用 getAttribute()、removeAttribute()和 setAttribute()方法操作属性，而不是直接操作属性节点。

## 1.2. Slector API

JavaScript 库中最流行的一种能力就是根据 CSS 选择符的模式匹配 DOM 元素。比如，jQuery 就完全以 CSS 选择符查询 DOM 获取元素引用，而不是使用 getElementById()和 getElementsByTagName()。

Selectors API（参见 W3C 网站上的 Selectors API Level 1）是 W3C 推荐标准，规定了浏览器原生支持的 CSS 查询 API。支持这一特性的所有 JavaScript 库都会实现一个基本的 CSS 解析器，然后使用已有的 DOM 方法搜索文档并匹配目标节点。虽然库开发者在不断改进其性能，但 JavaScript 代码能做到的毕竟有限。通过浏览器原生支持这个 API，解析和遍历 DOM 树可以通过底层编译语言实现，性能也有了数量级的提升。

Selectors API Level 1 的核心是两个方法：querySelector()和 querySelectorAll()。在兼容浏览器中，Document 类型和 Element 类型的实例上都会暴露这两个方法。

Selectors API Level 2 规范在 Element 类型上新增了更多方法，比如 matches()、find()和 findAll()。不过，目前还没有浏览器实现或宣称实现 find()和 findAll()。

### 1.2.1. querySelector()

querySelector()方法接收 CSS 选择符参数，返回匹配该模式的第一个后代元素，如果没有匹配项则返回 null。下面是一些例子：

```javascript
// 取得 <body> 元素
const body = document.querySelector('body');

// 取得 ID 为 'myDiv' 的元素
const myDiv = document.querySelector('#myDiv');

// 取得类名为 'selected' 的第一个元素
const selected = document.querySelector('.selected');

// 取得类名为 'button' 的图片
const img = document.body.querySelector('img.button');
```

在 Document 上使用 querySelector()方法时，会从文档元素开始搜索；在 Element 上使用 querySelector()方法时，则只会从当前元素的后代中查询。

用于查询模式的 CSS 选择符可繁可简，依需求而定。如果选择符有语法错误或碰到不支持的选择符，则 querySelector()方法会抛出错误。

### 1.2.2. querySelectorAll()

querySelectorAll()方法跟 querySelector()一样，也接收一个用于查询的参数，但它会返回所有匹配的节点，而不止一个。这个方法返回的是一个 NodeList 的静态实例。

再强调一次，querySelectorAll()返回的 NodeList 实例一个属性和方法都不缺，但它是一个静态的“快照”，而非“实时”的查询。这样的底层实现避免了使用 NodeList 对象可能造成的性能问题。

以有效 CSS 选择符调用 querySelectorAll()都会返回 NodeList，无论匹配多少个元素都可以。如果没有匹配项，则返回空的 NodeList 实例。

与 querySelector()一样，querySelectorAll()也可以在 Document、DocumentFragment 和 Element 类型上使用。下面是几个例子：

```javascript
// 取得 ID 为 'myDiv' 的 <div> 元素中的所有 <em> 元素
const ems = document.getElementById('myDiv').querySelectorAll('em');

// 取得所有类名中包含 'selected' 的元素
const selecteds = document.querySelectorAll('.selected');

// 取得所有是 <p> 元素子元素的 <strong> 元素
const strongs = document.querySelectorAll('p strong');
```

返回的 NodeList 对象可以通过 for-of 循环、item()方法或中括号语法取得个别元素。比如：

```javascript
const strongElements = document.querySelectorAll('p strong');

// 以下3 个循环的效果一样
for (let strong of strongElements) {
  strong.className = 'important';
}

for (let i = 0; i < strongElements.length; ++i) {
  strongElements.item(i).className = 'important';
}

for (let i = 0; i < strongElements.length; ++i) {
  strongElements[i].className = 'important';
}
```

与 querySelector()方法一样，如果选择符有语法错误或碰到不支持的选择符，则 querySelectorAll()方法会抛出错误。

### 1.2.3. matches()

matches()方法（在规范草案中称为 matchesSelector()）接收一个 CSS 选择符参数，如果元素匹配则该选择符返回 true，否则返回 false。例如：

```javascript
if (document.body.matches('body.page1')) {
  // true
}
```

使用这个方法可以方便地检测某个元素会不会被 querySelector()或 querySelectorAll()方法返回。

所有主流浏览器都支持 matches()。Edge、Chrome、Firefox、Safari 和 Opera 完全支持，IE9~11 及一些移动浏览器支持带前缀的方法。

## 1.3. 元素遍历

IE9 之前的版本不会把元素间的空格当成空白节点，而其他浏览器则会。这样就导致了 childNodes 和 firstChild 等属性上的差异。为了弥补这个差异，同时不影响 DOM 规范，W3C 通过新的 ElementTraversal 规范定义了一组新属性。

Element Traversal API 为 DOM 元素添加了 5 个属性：

- childElementCount，返回子元素数量（不包含文本节点和注释）；
- firstElementChild，指向第一个 Element 类型的子元素（Element 版 firstChild）；
- lastElementChild，指向最后一个 Element 类型的子元素（Element 版 lastChild）；
- previousElementSibling ， 指向前一个 Element 类型的同胞元素（ Element 版 previousSibling）；
- nextElementSibling，指向后一个 Element 类型的同胞元素（Element 版 nextSibling）。

在支持的浏览器中，所有 DOM 元素都会有这些属性，为遍历 DOM 元素提供便利。这样开发者就不用担心空白文本节点的问题了。

举个例子，过去要以跨浏览器方式遍历特定元素的所有子元素，代码大致是这样写的：

```javascript
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

使用 Element Traversal 属性之后，以上代码可以简化如下：

```javascript
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

IE9 及以上版本，以及所有现代浏览器都支持 Element Traversal 属性。

## 1.4. HTML 5

HTML5 代表着与以前的 HTML 截然不同的方向。在所有以前的 HTML 规范中，从未出现过描述 JavaScript 接口的情形，HTML 就是一个纯标记语言。JavaScript 绑定的事，一概交给 DOM 规范去定义。

然而，HTML5 规范却包含了与标记相关的大量 JavaScript API 定义。其中有的 API 与 DOM 重合，定义了浏览器应该提供的 DOM 扩展。

注意 因为 HTML5 覆盖的范围极其广泛，所以本节主要讨论其影响所有 DOM 节点的部分。HTML5 的其他部分将在本书后面的相关章节中再讨论。

### 1.4.1. CSS 类扩展

自 HTML4 被广泛采用以来，Web 开发中一个主要的变化是 class 属性用得越来越多，其用处是为元素添加样式以及语义信息。自然地，JavaScript 与 CSS 类的交互就增多了，包括动态修改类名，以及根据给定的一个或一组类名查询元素，等等。为了适应开发者和他们对 class 属性的认可，HTML5 增加了一些特性以方便使用 CSS 类。

1. **getElementsByClassName()**

getElementsByClassName()是 HTML5 新增的最受欢迎的一个方法，暴露在 document 对象和所有 HTML 元素上。 这个方法脱胎于基于原有 DOM 特性实现该功能的 JavaScript 库，提供了性能高好的原生实现。

getElementsByClassName()方法接收一个参数，即包含一个或多个类名的字符串，返回类名中包含相应类的元素的 NodeList。如果提供了多个类名，则顺序无关紧要。下面是几个示例：

```javascript
// 取得所有类名中包含'username'和'current'元素
// 这两个类名的顺序无关紧要
let allCurrentUsernames = document.getElementsByClassName('username current');
// 取得ID 为'myDiv'的元素子树中所有包含'selected'类的元素
let selected = document
  .getElementById('myDiv')
  .getElementsByClassName('selected');
```

这个方法只会返回以调用它的对象为根元素的子树中所有匹配的元素。在 document 上调用 getElementsByClassName()返回文档中所有匹配的元素，而在特定元素上调用 getElementsByClassName()则返回该元素后代中匹配的元素。

如果要给包含特定类（而不是特定 ID 或标签）的元素添加事件处理程序，使用这个方法会很方便。不过要记住，因为返回值是 NodeList，所以使用这个方法会遇到跟使用 getElementsByTagName()和其他返回 NodeList 对象的 DOM 方法同样的问题。

IE9 及以上版本，以及所有现代浏览器都支持 getElementsByClassName()方法。

2. **classList 属性**

要操作类名，可以通过 className 属性实现添加、删除和替换。但 className 是一个字符串，所以每次操作之后都需要重新设置这个值才能生效，即使只改动了部分字符串也一样。以下面的 HTML 代码为例：

```html
<div class="bd user disabled">...</div>
```

这个`<div>`元素有 3 个类名。要想删除其中一个，就得先把 className 拆开，删除不想要的那个，再把包含剩余类的字符串设置回去。比如：

```javascript
// 要删除'user'类
let targetClass = 'user';
// 把类名拆成数组
let classNames = div.className.split(/\s+/);
// 找到要删除类名的索引
let idx = classNames.indexOf(targetClass);
// 如果有则删除
if (idx > -1) {
  classNames.splice(i, 1);
}
// 重新设置类名
div.className = classNames.join(' ');
```

这就是从`<div>`元素的类名中删除'user'类要写的代码。替换类名和检测类名也要涉及同样的算法。添加类名只涉及字符串拼接，但必须先检查一下以确保不会重复添加相同的类名。很多 JavaScript 库为这些操作实现了便利方法。

HTML5 通过给所有元素增加 classList 属性为这些操作提供了更简单也更安全的实现方式。classList 是一个新的集合类型 DOMTokenList 的实例。与其他 DOM 集合类型一样，DOMTokenList 也有 length 属性表示自己包含多少项，也可以通过 item()或中括号取得个别的元素。此外，DOMTokenList 还增加了以下方法。

- add(value)，向类名列表中添加指定的字符串值 value。如果这个值已经存在，则什么也不做。
- contains(value)，返回布尔值，表示给定的 value 是否存在。
- remove(value)，从类名列表中删除指定的字符串值 value。
- toggle(value)，如果类名列表中已经存在指定的 value，则删除；如果不存在，则添加。

这样以来，前面的例子中那么多行代码就可以简化成下面的一行：

```javascript
div.classList.remove('user');
```

这行代码可以在不影响其他类名的情况下完成删除。其他方法同样极大地简化了操作类名的复杂性，如下面的例子所示：

```javascript
// 删除'disabled'类
div.classList.remove('disabled');
// 添加'current'类
div.classList.add('current');
// 切换'user'类
div.classList.toggle('user');
// 检测类名
if (div.classList.contains('bd') && !div.classList.contains('disabled')){
// 执行操作
)
// 迭代类名
for (let class of div.classList){
doStuff(class);
}
```

添加了 classList 属性之后，除非是完全删除或完全重写元素的 class 属性，否则 className 属性就用不到了。IE10 及以上版本（部分）和其他主流浏览器（完全）实现了 classList 属性。

### 1.4.2. 焦点管理

HTML5 增加了辅助 DOM 焦点管理的功能。首先是 document.activeElement，始终包含当前拥有焦点的 DOM 元素。页面加载时，可以通过用户输入（按 Tab 键或代码中使用 focus()方法）让某个元素自动获得焦点。例如：

```javascript
let button = document.getElementById('myButton');
button.focus();
console.log(document.activeElement === button); // true
```

默认情况下，document.activeElement 在页面刚加载完之后会设置为 document.body。而在页面完全加载之前，document.activeElement 的值为 null。

其次是 document.hasFocus()方法，该方法返回布尔值，表示文档是否拥有焦点：

```javascript
let button = document.getElementById('myButton');
button.focus();
console.log(document.hasFocus()); // true
```

确定文档是否获得了焦点，就可以帮助确定用户是否在操作页面。

第一个方法可以用来查询文档，确定哪个元素拥有焦点，第二个方法可以查询文档是否获得了焦点，而这对于保证 Web 应用程序的无障碍使用是非常重要的。无障碍 Web 应用程序的一个重要方面就是焦点管理，而能够确定哪个元素当前拥有焦点（相比于之前的猜测）是一个很大的进步。

### 1.4.3. HTMLDocument 扩展

HTML5 扩展了 HTMLDocument 类型，增加了更多功能。与其他 HTML5 定义的 DOM 扩展一样，这些变化同样基于所有浏览器事实上都已经支持的专有扩展。为此，即使这些扩展的标准化相对较晚，很多浏览器也早就实现了相应的功能。

1. **readyState 属性**

readyState 是 IE4 最早添加到 document 对象上的属性，后来其他浏览器也都依葫芦画瓢地支持这个属性。最终，HTML5 将这个属性写进了标准。document.readyState 属性有 3 个可能的值：

- loading，表示文档正在加载。
- interactive，文档已被解析，“正在加载” 状态结束，但是诸如图像，样式表和框架之类的子资源仍在加载。
- complete，文档和所有子资源已完成加载。

实际开发中，最好是把 document.readState 当成一个指示器，以判断文档是否加载完毕。在这个属性得到广泛支持以前，通常要依赖 onload 事件处理程序设置一个标记，表示文档加载完了。这个属性的基本用法如下：

```javascript
if (document.readyState == 'complete') {
  // 执行操作
}
```

2. **compatMode 属性**

自从 IE6 提供了以标准或混杂模式渲染页面的能力之后，检测页面渲染模式成为一个必要的需求。IE 为 document 添加了 compatMode 属性，这个属性唯一的任务是指示浏览器当前处于什么渲染模式。如下面的例子所示，标准模式下 document.compatMode 的值是'CSS1Compat'，而在混杂模式下，document.compatMode 的值是'BackCompat'：

```javascript
if (document.compatMode == 'CSS1Compat') {
  console.log('Standards mode');
} else {
  console.log('Quirks mode');
}
```

HTML5 最终也把 compatMode 属性的实现标准化了。

3. **head 属性**

作为对 document.body（指向文档的`<body>`元素）的补充，HTML5 增加了 document.head 属性，指向文档的`<head>`元素。可以像下面这样直接取得`<head>`元素：

```javascript
const head = document.head;
```

### 1.4.4. 字符集属性

HTML5 增加了几个与文档字符集有关的新属性。其中，characterSet 属性表示文档实际使用的字符集，也可以用来指定新字符集。这个属性的默认值是'UTF-16'，但可以通过`<meta>`元素或响应头，以及新增的 characterSeet 属性来修改。下面是一个例子：

```javascript
console.log(document.characterSet); // 'UTF-16'
document.characterSet = 'UTF-8';
```

### 1.4.5. 自定义数据属性

HTML5 允许给元素指定非标准的属性，但要使用前缀 data-以便告诉浏览器，这些属性既不包含与渲染有关的信息，也不包含元素的语义信息。除了前缀，自定义属性对命名是没有限制的，data-后面跟什么都可以。下面是一个例子：

```html
<div id="myDiv" data-appId="12345" data-myname="Nicholas"></div>
```

定义了自定义数据属性后，可以通过元素的 dataset 属性来访问。dataset 属性是一个 DOMStringMap 的实例，包含一组键/值对映射。元素的每个 data-name 属性在 dataset 中都可以通过 data-后面的字符串作为键来访问（例如，属性 data-myname、data-myName 可以通过 myname 访问，但要注意 data-my-name、data-My-Name 要通过 myName 来访问）。下面是一个使用自定义数据属性的例子：

```javascript
// 本例中使用的方法仅用于示范
let div = document.getElementById('myDiv');
// 取得自定义数据属性的值
let appId = div.dataset.appId;
let myName = div.dataset.myname;
// 设置自定义数据属性的值
div.dataset.appId = 23456;
div.dataset.myname = 'Michael';
// 有'myname'吗？
if (div.dataset.myname) {
  console.log(`Hello, ${div.dataset.myname}`);
}
```

自定义数据属性非常适合需要给元素附加某些数据的场景，比如链接追踪和在聚合应用程序中标识页面的不同部分。另外，单页应用程序框架也非常多地使用了自定义数据属性。

### 1.4.6. 插入标记

DOM 虽然已经为操纵节点提供了很多 API，但向文档中一次性插入大量 HTML 时还是比较麻烦。相比先创建一堆节点，再把它们以正确的顺序连接起来，直接插入一个 HTML 字符串要简单（快速）得多。HTML5 已经通过以下 DOM 扩展将这种能力标准化了。

1. **innerHTML 属性**

在读取 innerHTML 属性时，会返回元素所有后代的 HTML 字符串，包括元素、注释和文本节点。而在写入 innerHTML 时，则会根据提供的字符串值以新的 DOM 子树替代元素中原来包含的所有节点。比如下面的 HTML 代码：

```html
<div id="content">
  <p>
    This is a
    <strong>paragraph</strong>
    with a list following it.
  </p>
  <ul>
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
  </ul>
</div>
```

对于这里的`<div>`元素而言，其 innerHTML 属性会返回以下字符串：

```html
<p>
  This is a
  <strong>paragraph</strong>
  with a list following it.
</p>
<ul>
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
</ul>
```

实际返回的文本内容会因浏览器而不同。IE 和 Opera 会把所有元素标签转换为大写，而 Safari、Chrome 和 Firefox 则会按照文档源代码的格式返回，包含空格和缩进。因此不要指望不同浏览器的 innerHTML 会返回完全一样的值。

在写入模式下，赋给 innerHTML 属性的值会被解析为 DOM 子树，并替代元素之前的所有节点。因为所赋的值默认为 HTML，所以其中的所有标签都会以浏览器处理 HTML 的方式转换为元素（同样，转换结果也会因浏览器不同而不同）。如果赋值中不包含任何 HTML 标签，则直接生成一个文本节点，如下所示：

```javascript
div.innerHTML = 'Hello world!';
```

因为浏览器会解析设置的值，所以给 innerHTML 设置包含 HTML 的字符串时，结果会大不一样。来看下面的例子：

```javascript
div.innerHTML = 'Hello & welcome, <b>'reader'!</b>';
```

这个操作的结果相当于：

```html
<div id="content">
  Hello &amp; welcome,
  <b>&quot;reader&quot;!</b>
</div>
```

设置完 innerHTML，马上就可以像访问其他节点一样访问这些新节点。

注意 设置 innerHTML 会导致浏览器将 HTML 字符串解析为相应的 DOM 树。这意味着设置 innerHTML 属性后马上再读出来会得到不同的字符串。这是因为返回的字符串是将原始字符串对应的 DOM 子树序列化之后的结果。

2. **旧 IE 中的 innerHTML**

在所有现代浏览器中，通过 innerHTML 插入的`<script>`标签是不会执行的。而在 IE8 及之前的版本中，只要这样插入的`<script>`元素指定了 defer 属性，且`<script>`之前是“受控元素”（scoped element），那就是可以执行的。`<script>`元素与`<style>`或注释一样，都是“非受控元素”（NoScope element），也就是在页面上看不到它们。IE 会把 innerHTML 中从非受控元素开始的内容都删掉，也就是说下面的例子是行不通的：

```javascript
// 行不通
div.innerHTML = '<script defer>console.log('hi');</script>';
```

在这个例子中，innerHTML 字符串以一个非受控元素开始，因此整个字符串都会被清空。为了达到目的，必须在`<script>`前面加上一个受控元素，例如文本节点或没有结束标签的元素（如`<input>`）。因此，下面的代码就是可行的：

```javascript
// 以下都可行
div.innerHTML = '_<script defer>console.log('hi');<\/script>';
div.innerHTML = '<div>&nbsp;</div><script defer>console.log('hi');<\/script>';
div.innerHTML = '<input type=\'hidden\'><script defer>console.
log('hi');<\/script>';
```

第一行会在`<script>`元素前面插入一个文本节点。为了不影响页面排版，可能稍后需要删掉这个文本节点。第二行与之类似，使用了包含空格的`<div>`元素。空`<div>`是不行的，必须包含一点内容，以强制创建一个文本节点。同样，这个`<div>`元素可能也需要事后删除，以免影响页面外观。第三行使用了一个隐藏的`<input>`字段来达成同样的目的。因为这个字段不影响页面布局，所以应该是最理想的方案。

在 IE 中，通过 innerHTML 插入`<style>`也会有类似的问题。多数浏览器支持使用 innerHTML 插入`<style>`元素：

```javascript
div.innerHTML = '<style type='text/css'>body {background-color: red; }</style>';
```

但在 IE8 及之前的版本中，`<style>`也被认为是非受控元素，所以必须前置一个受控元素：

```javascript
div.innerHTML =
  '_<style type='text/css'>body {background-color: red; }</style>';
div.removeChild(div.firstChild);
```

注意 Firefox 在内容类型为 application/xhtml+xml 的 XHTML 文档中对 innerHTML 更加严格。在 XHTML 文档中使用 innerHTML，必须使用格式良好的 XHTML 代码。否则，在 Firefox 中会静默失败。

3. **outerHTML 属性**

读取 outerHTML 属性时，会返回调用它的元素（及所有后代元素）的 HTML 字符串。在写入 outerHTML 属性时，调用它的元素会被传入的 HTML 字符串经解释之后生成的 DOM 子树取代。比如下面的 HTML 代码：

```html
<div id="content">
  <p>
    This is a
    <strong>paragraph</strong>
    with a list following it.
  </p>
  <ul>
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
  </ul>
</div>
```

在这个`<div>`元素上调用 outerHTML 会返回相同的字符串，包括`<div>`本身。注意，浏览器因解析和解释 HTML 代码的机制不同，返回的字符串也可能不同。（跟 innerHTML 的情况是一样的。）

如果使用 outerHTML 设置 HTML，比如：

```javascript
div.outerHTML = '<p>This is a paragraph.</p>';
```

则会得到与执行以下脚本相同的结果：`

```javascript
let p = document.createElement('p');
p.appendChild(document.createTextNode('This is a paragraph.'));
div.parentNode.replaceChild(p, div);
```

新的`<p>`元素会取代 DOM 树中原来的`<div>`元素。

4. **insertAdjacentHTML()与 insertAdjacentText()**

关于插入标签的最后两个新增方法是 insertAdjacentHTML()和 insertAdjacentText()。这两个方法最早源自 IE，它们都接收两个参数：要插入标记的位置和要插入的 HTML 或文本。第一个参数必须是下列值中的一个：

- 'beforebegin'，插入当前元素前面，作为前一个同胞节点；
- 'afterbegin'，插入当前元素内部，作为新的子节点或放在第一个子节点前面；
- 'beforeend'，插入当前元素内部，作为新的子节点或放在最后一个子节点后面；
- 'afterend'，插入当前元素后面，作为下一个同胞节点。

注意这几个值是不区分大小写的。第二个参数会作为 HTML 字符串解析（与 innerHTML 和 outerHTML 相同）或者作为纯文本解析（与 innerText 和 outerText 相同）。如果是 HTML，则会在解析出错时抛出错误。下面展示了基本用法：

```javascript
// 作为前一个同胞节点插入
element.insertAdjacentHTML('beforebegin', '<p>Hello world!</p>');
element.insertAdjacentText('beforebegin', 'Hello world!');
// 作为第一个子节点插入
element.insertAdjacentHTML('afterbegin', '<p>Hello world!</p>');
element.insertAdjacentText('afterbegin', 'Hello world!');
// 作为最后一个子节点插入
element.insertAdjacentHTML('beforeend', '<p>Hello world!</p>');
element.insertAdjacentText('beforeend', 'Hello world!');
// 作为下一个同胞节点插入
element.insertAdjacentHTML('afterend', '<p>Hello world!</p>');
element.insertAdjacentText('afterend', 'Hello world!');
```

5. **内存与性能问题**

使用本节介绍的方法替换子节点可能在浏览器（特别是 IE）中导致内存问题。比如，如果被移除的子树元素中之前有关联的事件处理程序或其他 JavaScript 对象（作为元素的属性），那它们之间的绑定关系会滞留在内存中。如果这种替换操作频繁发生，页面的内存占用就会持续攀升。在使用 innerHTML、outerHTML 和 insertAdjacentHTML()之前，最好手动删除要被替换的元素上关联的事件处理程序和 JavaScript 对象。

使用这些属性当然有其方便之处，特别是 innerHTML。一般来讲，插入大量的新 HTML 使用 innerHTML 比使用多次 DOM 操作创建节点再插入来得更便捷。这是因为 HTML 解析器会解析设置给 innerHTML（或 outerHTML）的值。解析器在浏览器中是底层代码（通常是 C++代码），比 JavaScript 快得多。不过，HTML 解析器的构建与解构也不是没有代价，因此最好限制使用 innerHTML 和 outerHTML 的次数。比如，下面的代码使用 innerHTML 创建了一些列表项：

```javascript
for (let value of values) {
  ul.innerHTML += '<li>${value}</li>'; // 别这样做！
}
```

这段代码效率低，因为每次迭代都要设置一次 innerHTML。不仅如此，每次循环还要先读取 innerHTML，也就是说循环一次要访问两次 innerHTML。为此，最好通过循环先构建一个独立的字符串，最后再一次性把生成的字符串赋值给 innerHTML，比如：

```javascript
let itemsHtml = '';
for (let value of values) {
  itemsHtml += '<li>${value}</li>';
}
ul.innerHTML = itemsHtml;
```

这样修改之后效率就高多了，因为只有对 innerHTML 的一次赋值。当然，像下面这样一行代码也可以搞定：

```javascript
ul.innerHTML = values.map((value) => '<li>${value}</li>').join('');
```

6. **跨站点脚本**

尽管 innerHTML 不会执行自己创建的`<script>`标签，但仍然向恶意用户暴露了很大的攻击面，因为通过它可以毫不费力地创建元素并执行 onclick 之类的属性。

如果页面中要使用用户提供的信息，则不建议使用 innerHTML。与使用 innerHTML 获得的方便相比，防止 XSS 攻击更让人头疼。此时一定要隔离要插入的数据，在插入页面前必须毫不犹豫地使用相关的库对它们进行转义。

7. **scrollIntoView()**

DOM 规范中没有涉及的一个问题是如何滚动页面中的某个区域。为填充这方面的缺失，不同浏览器实现了不同的控制滚动的方式。在所有这些专有方法中，HTML5 选择了标准化 scrollIntoView()。

scrollIntoView()方法存在于所有 HTML 元素上，可以滚动浏览器窗口或容器元素以便包含元素进入视口。这个方法的参数如下：

- alignToTop 是一个布尔值。
  - true：窗口滚动后元素的顶部与视口顶部对齐。
  - false：窗口滚动后元素的底部与视口底部对齐。
- scrollIntoViewOptions 是一个选项对象。
  - behavior：定义过渡动画，可取的值为'smooth'和'auto'，默认为'auto'。
  - block：定义垂直方向的对齐，可取的值为'start'、'center'、'end'和'nearest'，默认为 'start'。
  - inline：定义水平方向的对齐，可取的值为'start'、'center'、'end'和'nearest'，默认为 'nearest'。
- 不传参数等同于 alignToTop 为 true。

来看几个例子：

```javascript
// 确保元素可见
document.forms[0].scrollIntoView();
// 同上
document.forms[0].scrollIntoView(true);
document.forms[0].scrollIntoView({block: 'start'});
// 尝试将元素平滑地滚入视口
document.forms[0].scrollIntoView({behavior: 'smooth', block: 'start'});
```

这个方法可以用来在页面上发生某个事件时引起用户关注。把焦点设置到一个元素上也会导致浏览器将元素滚动到可见位置。

## 1.5. 专有扩展

尽管所有浏览器厂商都理解遵循标准的重要性，但它们也都有为弥补功能缺失而为 DOM 添加专有扩展的历史。虽然这表面上看是一件坏事，但专有扩展也为开发者提供了很多重要功能，而这些功能后来则有可能被标准化，比如进入 HTML5。

除了已经标准化的，各家浏览器还有很多未被标准化的专有扩展。这并不意味着它们将来不会被纳入标准，只不过在本书编写时，它们还只是由部分浏览器专有和采用。

### 1.5.1. children 属性

IE9 之前的版本与其他浏览器在处理空白文本节点上的差异导致了 children 属性的出现。children 属性是一个 HTMLCollection，只包含元素的 Element 类型的子节点。如果元素的子节点类型全部是元素类型，那 children 和 childNodes 中包含的节点应该是一样的。可以像下面这样使用 children 属性：

```javascript
let childCount = element.children.length;
let firstChild = element.children[0];
```

### 1.5.2. contains()方法

DOM 编程中经常需要确定一个元素是不是另一个元素的后代。IE 首先引入了 contains()方法，让开发者可以在不遍历 DOM 的情况下获取这个信息。contains()方法应该在要搜索的祖先元素上调用，参数是待确定的目标节点。

如果目标节点是被搜索节点的后代，contains()返回 true，否则返回 false。下面看一个例子：

```javascript
console.log(document.documentElement.contains(document.body)); // true
```

这个例子测试`<html>`元素中是否包含`<body>`元素，在格式正确的 HTML 中会返回 true。

另外，使用 DOM Level 3 的 compareDocumentPosition()方法也可以确定节点间的关系。这个方法会返回表示两个节点关系的位掩码。下表给出了这些位掩码的说明。

| 掩 码 | 节点关系                                      |
| ----- | --------------------------------------------- |
| 0x1   | 断开（传入的节点不在文档中）                  |
| 0x2   | 领先（传入的节点在 DOM 树中位于参考节点之前） |
| 0x4   | 随后（传入的节点在 DOM 树中位于参考节点之后） |
| 0x8   | 包含（传入的节点是参考节点的祖先）            |
| 0x10  | 被包含（传入的节点是参考节点的后代）          |

要模仿 contains()方法，就需要用到掩码 16（0x10）。compareDocumentPosition()方法的结果可以通过按位与来确定参考节点是否包含传入的节点，比如：

```javascript
let result = document.documentElement.compareDocumentPosition(document.body);
console.log(!!(result & 0x10));
```

以上代码执行后 result 的值为 20（或 0x14，其中 0x4 表示“随后”，加上 0x10“被包含”）。对 result 和 0x10 应用按位与会返回非零值，而两个叹号将这个值转换成对应的布尔值。

IE9 及之后的版本，以及所有现代浏览器都支持 contains()和 compareDocumentPosition()方法。

### 1.5.3. 插入标记

HTML5 将 IE 发明的 innerHTML 和 outerHTML 纳入了标准，但还有两个属性没有入选。这两个剩下的属性是 innerText 和 outerText。

1. **innnerText 属性**

innerText 属性对应元素中包含的所有文本内容，无论文本在子树中哪个层级。在用于读取值时，innerText 会按照深度优先的顺序将子树中所有文本节点的值拼接起来。在用于写入值时，innerText 会移除元素的所有后代并插入一个包含该值的文本节点。来看下面的 HTML 代码：

```html
<div id="content">
  <p>
    This is a
    <strong>paragraph</strong>
    with a list following it.
  </p>
  <ul>
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
  </ul>
</div>
```

对这个例子中的`<div>`而言，innerText 属性会返回以下字符串：

```javascript
This is a paragraph with a list following it.
Item 1
Item 2
Item 3
```

注意不同浏览器对待空格的方式不同，因此格式化之后的字符串可能包含也可能不包含原始 HTML 代码中的缩进。

下面再看一个使用 innerText 设置`<div>`元素内容的例子：

```javascript
div.innerText = 'Hello world!';
```

执行这行代码后，HTML 页面中的这个`<div>`元素实际上会变成这个样子：

```html
<div id="content">Hello world!</div>
```

设置 innerText 会移除元素之前所有的后代节点，完全改变 DOM 子树。此外，设置 innerText 也会编码出现在字符串中的 HTML 语法字符（小于号、大于号、引号及和号）。下面是一个例子：

```javascript
div.innerText = 'Hello & welcome, <b>'reader'!</b>';
```

执行之后的结果如下：

```html
<div id="content">
  Hello &amp; welcome, &lt;b&gt;&quot;reader&quot;!&lt;/b&gt;
</div>
```

因为设置 innerText 只能在容器元素中生成一个文本节点，所以为了保证一定是文本节点，就必须进行 HTML 编码。innerText 属性可以用于去除 HTML 标签。通过将 innerText 设置为等于 innerText，可以去除所有 HTML 标签而只剩文本，如下所示：

```javascript
div.innerText = div.innerText;
```

执行以上代码后，容器元素的内容只会包含原先的文本内容。

注意 Firefox 45（2016 年 3 月发布）以前的版本中只支持 textContent 属性，与 innerText 的区别是返回的文本中也会返回行内样式或脚本代码。innerText 目前已经得到所有浏览器支持，应该作为取得和设置文本内容的首选方法使用。

2. **outerText 属性**

outerText 与 innerText 是类似的，只不过作用范围包含调用它的节点。要读取文本值时，outerText 与 innerText 实际上会返回同样的内容。但在写入文本值时，outerText 就大不相同了。写入文本值时，outerText 不止会移除所有后代节点，而是会替换整个元素。比如：

```javascript
div.outerText = 'Hello world!';
```

这行代码的执行效果就相当于以下两行代码：

```javascript
let text = document.createTextNode('Hello world!');
div.parentNode.replaceChild(text, div);
```

本质上，这相当于用新的文本节点替代 outerText 所在的元素。此时，原来的元素会与文档脱离关系，因此也无法访问。

outerText 是一个非标准的属性，而且也没有被标准化的前景。因此，不推荐依赖这个属性实现重要的操作。除 Firefox 之外所有主流浏览器都支持 outerText。

### 1.5.4. 滚动

如前所述，滚动是 HTML5 之前 DOM 标准没有涉及的领域。虽然 HTML5 把 scrollIntoView()标准化了， 但不同浏览器中仍然有其他专有方法。比如， scrollIntoViewIfNeeded() 作为 HTMLElement 类型的扩展可以在所有元素上调用。scrollIntoViewIfNeeded(alingCenter)会在元素不可见的情况下，将其滚动到窗口或包含窗口中，使其可见；如果已经在视口中可见，则这个方法什么也不做。如果将可选的参数 alingCenter 设置为 true，则浏览器会尝试将其放在视口中央。Safari、Chrome 和 Opera 实现了这个方法。

下面使用 scrollIntoViewIfNeeded()方法的一个例子：

```javascript
// 如果不可见，则将元素可见
document.images[0].scrollIntoViewIfNeeded();
```

考虑到 scrollIntoView()是唯一一个所有浏览器都支持的方法，所以只用它就可以了。
