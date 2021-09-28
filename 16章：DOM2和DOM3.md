**目录：**

- [16. DOM2 和 DOM3](#16-dom2-和-dom3)
  - [16.1. DOM 的演进](#161-dom-的演进)
    - [16.1.1. XML 命名空间](#1611-xml-命名空间)
    - [16.1.2. 其他变化](#1612-其他变化)
  - [16.2. 样式](#162-样式)
    - [16.2.1. 存取元素样式](#1621-存取元素样式)
    - [16.2.2. 操作样式表](#1622-操作样式表)
    - [16.2.3. 元素尺寸](#1623-元素尺寸)

# 16. DOM2 和 DOM3

本章内容

- DOM2 到 DOM3 的变化
- 操作样式的 DOM API
- DOM 遍历与范围

DOM1（DOM Level 1）主要定义了 HTML 和 XML 文档的底层结构。DOM2（DOM Level 2）和 DOM3（DOM Level 3）在这些结构之上加入更多交互能力，提供了更高级的 XML 特性。实际上，DOM2 和 DOM3 是按照模块化的思路来制定标准的，每个模块之间有一定关联，但分别针对某个 DOM 子集。这些模式如下所示。

- DOM Core：在 DOM1 核心部分的基础上，为节点增加方法和属性。
- DOM Views：定义基于样式信息的不同视图。
- DOM Events：定义通过事件实现 DOM 文档交互。
- DOM Style：定义以编程方式访问和修改 CSS 样式的接口。
- DOM Traversal and Range：新增遍历 DOM 文档及选择文档内容的接口。
- DOM HTML：在 DOM1 HTML 部分的基础上，增加属性、方法和新接口。
- DOM Mutation Observers：定义基于 DOM 变化触发回调的接口。这个模块是 DOM4 级模块，用于取代 Mutation Events。

本章介绍除 DOM Events 和 DOM Mutation Observers 之外的其他所有模块，第 17 章会专门介绍事件，而 DOM Mutation Observers 第 14 章已经介绍过了。DOM3 还有 XPath 模块和 Load and Save 模块，将在第 22 章介绍。

注意 比较老旧的浏览器（如 IE8）对本章内容支持有限。如果你的项目要兼容这些低版本浏览器，在使用本章介绍的 API 之前先确认浏览器的支持情况。推荐参考 Can I Use 网站。

## 16.1. DOM 的演进

DOM2 和 DOM3 Core 模块的目标是扩展 DOM API，满足 XML 的所有需求并提供更好的错误处理和特性检测。很大程度上，这意味着支持 XML 命名空间的概念。DOM2 Core 没有新增任何类型，仅仅在 DOM1 Core 基础上增加了一些方法和属性。DOM3 Core 则除了增强原有类型，也新增了一些新类型。

类似地，DOM View 和 HTML 模块也丰富了 DOM 接口，定义了新的属性和方法。这两个模块很小，因此本章将在讨论 JavaScript 对象的基本变化时将它们与 Core 模块放在一起讨论。

注意 本章只讨论浏览器实现的 DOM API，不会提及未被浏览器实现的。

### 16.1.1. XML 命名空间

XML 命名空间可以实现在一个格式规范的文档中混用不同的 XML 语言，而不必担心元素命名冲突。严格来讲，XML 命名空间在 XHTML 中才支持，HTML 并不支持。因此，本节的示例使用 XHTML。

命名空间是使用 xmlns 指定的。XHTML 的命名空间是'http://www.w3.org/1999/xhtml'，应该包含在任何格式规范的XHTML 页面的`<html>`元素中，如下所示：

```html
<html xmlns="http://www.w3.org/1999/xhtml">
  <head>
    <title>Example XHTML page</title>
  </head>
  <body>
    Hello world!
  </body>
</html>
```

对这个例子来说，所有元素都默认属于 XHTML 命名空间。可以使用 xmlns 给命名空间创建一个前缀，格式为“xmlns: 前缀”，如下面的例子所示：

```html
<xhtml:html xmlns:xhtml="http://www.w3.org/1999/xhtml">
  <xhtml:head>
    <xhtml:title>Example XHTML page</xhtml:title>
  </xhtml:head>
  <xhtml:body>
    Hello world!
  </xhtml:body>
</xhtml:html>
```

这里为 XHTML 命名空间定义了一个前缀 xhtml，同时所有 XHTML 元素都必须加上这个前缀。为避免混淆，属性也可以加上命名空间前缀，比如：

```html
<xhtml:html xmlns:xhtml="http://www.w3.org/1999/xhtml">
  <xhtml:head>
    <xhtml:title>Example XHTML page</xhtml:title>
  </xhtml:head>
  <xhtml:body xhtml:class="home">
    Hello world!
  </xhtml:body>
</xhtml:html>
```

这里的 class 属性被加上了 xhtml 前缀。如果文档中只使用一种 XML 语言，那么命名空间前缀其实是多余的，只有一个文档混合使用多种 XML 语言时才有必要。比如下面这个文档就使用了 XHTML 和 SVG 两种语言：

```html
<html xmlns="http://www.w3.org/1999/xhtml">
  <head>
    <title>Example XHTML page</title>
  </head>
  <body>
    <svg
      xmlns="http://www.w3.org/2000/svg"
      version="1.1"
      viewBox="0 0 100 100"
      style="width:100%; height:100%"
    >
      <rect x="0" y="0" width="100" height="100" style="fill:red" />
    </svg>
  </body>
</html>
```

在这个例子中，通过给`<svg>`元素设置自己的命名空间，将其标识为当前文档的外来元素。这样一来，`<svg>`元素及其属性，包括它的所有后代都会被认为属于'https://www.w3.org/2000/svg'命名空间。虽然这个文档从技术角度讲是XHTML 文档，但由于使用了命名空间，其中包含的 SVG 代码也是有效的。

对于这样的文档，如果调用某个方法与节点交互，就会出现一个问题。比如，创建了一个新元素，那这个元素属于哪个命名空间？查询特定标签名时，结果中应该包含哪个命名空间下的元素？DOM2 Core 为解决这些问题，给大部分 DOM1 方法提供了特定于命名空间的版本。

1. **Node 的变化**

在 DOM2 中，Node 类型包含以下特定于命名空间的属性：

- localName，不包含命名空间前缀的节点名；
- namespaceURI，节点的命名空间 URL，如果未指定则为 null；
- prefix，命名空间前缀，如果未指定则为 null。

在节点使用命名空间前缀的情况下，nodeName 等于 prefix + ':' + localName。比如下面这个例子：

```html
<html xmlns="http://www.w3.org/1999/xhtml">
  <head>
    <title>Example XHTML page</title>
  </head>
  <body>
    <s:svg
      xmlns:s="http://www.w3.org/2000/svg"
      version="1.1"
      viewBox="0 0 100 100"
      style="width:100%; height:100%"
    >
      <s:rect x="0" y="0" width="100" height="100" style="fill:red" />
    </s:svg>
  </body>
</html>
```

其中的`<html>`元素的 localName 和 tagName 都是'html'，namespaceURL 是'http://www.w3.org/1999/xhtml'，而prefix 是 null。对于`<s:svg>`元素，localName 是'svg'，tagName 是's:svg'，namespaceURI 是'https://www.w3.org/2000/svg'，而prefix 是's'。

DOM3 进一步增加了如下与命名空间相关的方法：

- isDefaultNamespace(namespaceURI)，返回布尔值，表示 namespaceURI 是否为节点的默
  认命名空间；
- lookupNamespaceURI(prefix)，返回给定 prefix 的命名空间 URI；
- lookupPrefix(namespaceURI)，返回给定 namespaceURI 的前缀。

对前面的例子，可以执行以下代码：

```js
console.log(document.body.isDefaultNamespace('http://www.w3.org/1999/xhtml')); // true
// 假设svg 包含对<s:svg>元素的引用
console.log(svg.lookupPrefix('http://www.w3.org/2000/svg')); // 's'
console.log(svg.lookupNamespaceURI('s')); // 'http://www.w3.org/2000/svg'
```

这些方法主要用于通过元素查询前面和命名空间 URI，以确定元素与文档的关系。

2. **Document 的变化**

DOM2 在 Document 类型上新增了如下命名空间特定的方法：

- createElementNS(namespaceURI, tagName)，以给定的标签名 tagName 创建指定命名空间 namespaceURI 的一个新元素；
- createAttributeNS(namespaceURI, attributeName)，以给定的属性名 attributeName 创建指定命名空间 namespaceURI 的一个新属性；
- getElementsByTagNameNS(namespaceURI, tagName)，返回指定命名空间 namespaceURI 中所有标签名为 tagName 的元素的 NodeList。
  使用这些方法都需要传入相应的命名空间 URI（不是命名空间前缀），如下面的例子所示：

```js
// 创建一个新SVG 元素
let svg = document.createElementNS('http://www.w3.org/2000/svg', 'svg');
// 创建一个任意命名空间的新属性
let att = document.createAttributeNS('http://www.somewhere.com', 'random');
// 获取所有XHTML 元素
let elems = document.getElementsByTagNameNS(
  'http://www.w3.org/1999/xhtml',
  '*',
);
```

这些命名空间特定的方法只在文档中包含两个或两个以上命名空间时才有用。

3. **Element 的变化**

DOM2 Core 对 Element 类型的更新主要集中在对属性的操作上。下面是新增的方法：

- getAttributeNS(namespaceURI, localName)，取得指定命名空间 namespaceURI 中名为 localName 的属性；
- getAttributeNodeNS(namespaceURI, localName)，取得指定命名空间 namespaceURI 中名为 localName 的属性节点；
- getElementsByTagNameNS(namespaceURI, tagName)，取得指定命名空间 namespaceURI 中标签名为 tagName 的元素的 NodeList；
- hasAttributeNS(namespaceURI, localName)，返回布尔值，表示元素中是否有命名空间 namespaceURI 下名为 localName 的属性（注意，DOM2 Core 也添加不带命名空间的 hasAttribute()方法）；
- removeAttributeNS(namespaceURI, localName)，删除指定命名空间 namespaceURI 中名为 localName 的属性；
- setAttributeNS(namespaceURI, qualifiedName, value)，设置指定命名空间 namespaceURI 中名为 qualifiedName 的属性为 value；
- setAttributeNodeNS(attNode)，为元素设置（添加）包含命名空间信息的属性节点 attNode。

这些方法与 DOM1 中对应的方法行为相同，除 setAttributeNodeNS()之外都只是多了一个命名空间参数。

4. **NamedNodeMap 的变化**

NamedNodeMap 也增加了以下处理命名空间的方法。因为 NamedNodeMap 主要表示属性，所以这些方法大都适用于属性：

- getNamedItemNS(namespaceURI, localName)，取得指定命名空间 namespaceURI 中名为 localName 的项；
- removeNamedItemNS(namespaceURI, localName)，删除指定命名空间 namespaceURI 中名为 localName 的项；
- setNamedItemNS(node)，为元素设置（添加）包含命名空间信息的节点。
  这些方法很少使用，因为通常都是使用元素来访问属性。

### 16.1.2. 其他变化

除命名空间相关的变化，DOM2 Core 还对 DOM 的其他部分做了一些更新。这些变化与 XML 命名空间无关，主要关注 DOM API 的完整性与可靠性。

1. **DocumentType 的变化**

DocumentType 新增了 3 个属性：publicId、systemId 和 internalSubset。publicId、systemId 属性表示文档类型声明中有效但无法使用 DOM1 API 访问的数据。比如下面这个 HTML 文档类型声明：

```html
<!DOCTYPE html PUBLIC '-// W3C// DTD HTML 4.01// EN' 'http://www.w3.org/TR/html4/strict.dtd'>
```

其 publicId 是'-// W3C// DTD HTML 4.01// EN'，而 systemId 是'http://www.w3.org/TR/html4/strict.dtd'。支持DOM2 的浏览器应该可以运行以下 JavaScript 代码：

```js
console.log(document.doctype.publicId);
console.log(document.doctype.systemId);
```

通常在网页中很少需要访问这些信息。
internalSubset 用于访问文档类型声明中可能包含的额外定义，如下面的例子所示：

```html
<!DOCTYPE html PUBLIC '-// W3C// DTD XHTML 1.0 Strict// EN' 'http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd' [<!ELEMENT name (#PCDATA)>
] >
```

对于以上声明，document.doctype.internalSubset 会返回'<!ELEMENT name (#PCDATA)>'。HTML 文档中几乎不会涉及文档类型的内部子集，XML 文档中稍微常用一些。

2. **Document 的变化**

Document 类型的更新中唯一跟命名空间无关的方法是 importNode()。这个方法的目的是从其他文档获取一个节点并导入到新文档，以便将其插入新文档。每个节点都有一个 ownerDocument 属性，表示所属文档。如果调用 appendChild()方法时传入节点的 ownerDocument 不是指向当前文档，则
会发生错误。而调用 importNode()导入其他文档的节点会返回一个新节点，这个新节点的 ownerDocument 属性是正确的。

importNode()方法跟 cloneNode()方法类似，同样接收两个参数：要复制的节点和表示是否同时复制子树的布尔值，返回结果是适合在当前文档中使用的新节点。下面看一个例子：

```js
let newNode = document.importNode(oldNode, true); // 导入节点及所有后代
document.body.appendChild(newNode);
```

这个方法在 HTML 中使用得并不多，在 XML 文档中的使用会更多一些（第 22 章会深入讨论）。

DOM2 View 给 Document 类型增加了新属性 defaultView，是一个指向拥有当前文档的窗口（或窗格<frame>）的指针。这个规范中并没有明确视图何时可用，因此这是添加的唯一一个属性。defaultView 属性得到了除 IE8 及更早版本之外所有浏览器的支持。IE8 及更早版本支持等价的 parentWindow 属性，Opera 也支持这个属性。因此要确定拥有文档的窗口，可以使用以下代码：

```js
let parentWindow = document.defaultView || document.parentWindow;
```

除了上面这一个方法和一个属性，DOM2 Core 还针对 document.implementation 对象增加了两个新方法：createDocumentType()和 createDocument()。前者用于创建 DocumentType 类型的新节点，接收 3 个参数：文档类型名称、publicId 和 systemId。比如，以下代码可以创建一个新的 HTML4.01 严格型文档：

```js
let doctype = document.implementation.createDocumentType(
  'html',
  '-// W3C// DTD HTML 4.01// EN',
  'http://www.w3.org/TR/html4/strict.dtd',
);
```

已有文档的文档类型不可更改，因此 createDocumentType()只在创建新文档时才会用到，而创建新文档要使用 createDocument() 方法。createDocument() 接收 3 个参数： 文档元素的 namespaceURI、文档元素的标签名和文档类型。比如，下列代码可以创建一个空的 XML 文档：

```js
let doc = document.implementation.createDocument('', 'root', null);
```

这个空文档没有命名空间和文档类型，只指定了`<root>`作为文档元素。要创建一个 XHTML 文档，可以使用以下代码：

```js
let doctype = document.implementation.createDocumentType(
  'html',
  '-// W3C// DTD XHTML 1.0 Strict// EN',
  'http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd',
);
let doc = document.implementation.createDocument(
  'http://www.w3.org/1999/xhtml',
  'html',
  doctype,
);
```

这里使用了适当的命名空间和文档类型创建一个新 XHTML 文档。这个文档只有一个文档元素`<html>`，其他一切都需要另行添加。

DOM2 HTML 模块也为 document.implamentation 对象添加了 createHTMLDocument()方法。使用这个方法可以创建一个完整的 HTML 文档，包含`<html>`、`<head>`、`<title>`和`<body>`元素。这个方法只接收一个参数，即新创建文档的标题（放到`<title>`元素中），返回一个新的 HTML 文档。比如：

```js
let htmldoc = document.implementation.createHTMLDocument('New Doc');
console.log(htmldoc.title); // 'New Doc'
console.log(typeof htmldoc.body); // 'object'
```

createHTMLDocument()方法创建的对象是 HTMLDocument 类型的实例，因此包括该类型所有相关的方法和属性，包括 title 和 body 属性。

3. **Node 的变化**

DOM3 新增了两个用于比较节点的方法：isSameNode()和 isEqualNode()。这两个方法都接收一个节点参数，如果这个节点与参考节点相同或相等，则返回 true。节点相同，意味着引用同一个对象；节点相等，意味着节点类型相同，拥有相等的属性（nodeName、nodeValue 等），而且 attributes 和 childNodes 也相等（即同样的位置包含相等的值）。来看一个例子：

```js
let div1 = document.createElement('div');
div1.setAttribute('class', 'box');
let div2 = document.createElement('div');
div2.setAttribute('class', 'box');
console.log(div1.isSameNode(div1)); // true
console.log(div1.isEqualNode(div2)); // true
console.log(div1.isSameNode(div2)); // false
```

这里创建了包含相同属性的两个`<div>`元素。这两个元素相等，但不相同。

DOM3 也增加了给 DOM 节点附加额外数据的方法。setUserData()方法接收 3 个参数：键、值、处理函数，用于给节点追加数据。可以像下面这样把数据添加到一个节点：

```js
document.body.setUserData('name', 'Nicholas', function () {});
```

然后，可以通过相同的键再取得这个信息，比如：

```js
let value = document.body.getUserData('name');
```

setUserData()的处理函数会在包含数据的节点被复制、删除、重命名或导入其他文档的时候执行，可以在这时候决定如何处理用户数据。处理函数接收 5 个参数：表示操作类型的数值（1 代表复制，2 代表导入，3 代表删除，4 代表重命名）、数据的键、数据的值、源节点和目标节点。删除节点时，源节点为 null；除复制外，目标节点都为 null。

```js
let div = document.createElement('div');
div.setUserData(
  'name',
  'Nicholas',
  function (operation, key, value, src, dest) {
    if (operation == 1) {
      dest.setUserData(key, value, function () {});
    }
  },
);
let newDiv = div.cloneNode(true);
console.log(newDiv.getUserData('name')); // 'Nicholas'
```

这里先创建了一个`<div>`元素，然后给它添加了一些数据，包含用户的名字。在使用 cloneNode()复制这个元素时，就会调用处理函数，从而将同样的数据再附加给复制得到的目标节点。然后，在副本节点上调用 getUserData()能够取得附加到源节点上的数据。

4. **内嵌窗格的变化**

DOM2 HTML 给 HTMLIFrameElement（即`<iframe>`，内嵌窗格）类型新增了一个属性，叫 contentDocument。这个属性包含代表子内嵌窗格中内容的 document 对象的指针。下面的例子展示了如何使用这个属性：

```js
let iframe = document.getElementById('myIframe');
let iframeDoc = iframe.contentDocument;
```

contentDocument 属性是 Document 的实例，拥有所有文档属性和方法，因此可以像使用其他 HTML 文档一样使用它。还有一个属性 contentWindow，返回相应窗格的 window 对象，这个对象上有一个 document 属性。所有现代浏览器都支持 contentDocument 和 contentWindow 属性。

注意 跨源访问子内嵌窗格的 document 对象会受到安全限制。如果内嵌窗格中加载了不同域名（或子域名）的页面，或者该页面使用了不同协议，则访问其 document 对象会抛出错误。

## 16.2. 样式

HTML 中的样式有 3 种定义方式：外部样式表（通过`<link>`元素）、文档样式表（使用`<style>`元素）和元素特定样式（使用 style 属性）。DOM2 Style 为这 3 种应用样式的机制都提供了 API。

### 16.2.1. 存取元素样式

任何支持 style 属性的 HTML 元素在 JavaScript 中都会有一个对应的 style 属性。这个 style 属性是 CSSStyleDeclaration 类型的实例，其中包含通过 HTML style 属性为元素设置的所有样式信息，但不包含通过层叠机制从文档样式和外部样式中继承来的样式。HTML style 属性中的 CSS 属性在 JavaScript style 对象中都有对应的属性。因为 CSS 属性名使用连字符表示法（用连字符分隔两个单词，如 background-image），所以在 JavaScript 中这些属性必须转换为驼峰大小写形式（如 backgroundImage）。下表给出了几个常用的 CSS 属性与 style 对象中等价属性的对比。

| CSS 属性         | JavaScript 属性       |
| ---------------- | --------------------- |
| background-image | style.backgroundImage |
| color            | style.color           |
| display          | style.display         |
| font-family      | style.fontFamily      |

大多数属性名会这样直接转换过来。但有一个 CSS 属性名不能直接转换，它就是 float。因为 float 是 JavaScript 的保留字，所以不能用作属性名。DOM2 Style 规定它在 style 对象中对应的属性应该是 cssFloat。

任何时候，只要获得了有效 DOM 元素的引用，就可以通过 JavaScript 来设置样式。来看下面的例子：

```js
let myDiv = document.getElementById('myDiv');
setTimeout(() => {
  // 设置背景颜色
  myDiv.style.backgroundColor = 'red';
  // 修改大小
  myDiv.style.width = '100px';
  myDiv.style.height = '200px';
  // 设置边框
  myDiv.style.border = '1px solid black';
}, 2000);
```

像这样修改样式时，元素的外观会自动更新。

注意 在标准模式下，所有尺寸都必须包含单位。在混杂模式下，可以把 style.width 设置为'20'，相当于'20px'。如果是在标准模式下，把 style.width 设置为'20'会被忽略，因为没有单位。实践中，最好一直加上单位。

通过 style 属性设置的值也可以通过 style 对象获取。比如下面的 HTML：

```html
<div id="myDiv" style="background-color: blue; width: 10px; height: 25px"></div>
```

这个元素 style 属性的值可以像这样通过代码获取：

```js
console.log(myDiv.style.backgroundColor); // 'blue'
console.log(myDiv.style.width); // '10px'
console.log(myDiv.style.height); // '25px'
```

如果元素上没有 style 属性，则 style 对象包含所有可能的 CSS 属性的空值。

1. **DOM 样式属性和方法**

DOM2 Style 规范也在 style 对象上定义了一些属性和方法。这些属性和方法提供了元素 style 属性的信息并支持修改，列举如下。

- cssText，包含 style 属性中的 CSS 代码。
- length，应用给元素的 CSS 属性数量。
- parentRule，表示 CSS 信息的 CSSRule 对象（下一节会讨论 CSSRule 类型）。
- getPropertyCSSValue(propertyName)，返回包含 CSS 属性 propertyName 值的 CSSValue 对象（已废弃）。
- getPropertyPriority(propertyName)，如果 CSS 属性 propertyName 使用了!important 则返回'important'，否则返回空字符串。
- getPropertyValue(propertyName)，返回属性 propertyName 的字符串值。
- item(index)，返回索引为 index 的 CSS 属性名。
- removeProperty(propertyName)，从样式中删除 CSS 属性 propertyName。
- setProperty(propertyName, value, priority)，设置 CSS 属性 propertyName 的值为 value，priority 是'important'或空字符串。

通过 cssText 属性可以存取样式的 CSS 代码。在读模式下，cssText 返回 style 属性 CSS 代码在浏览器内部的表示。在写模式下，给 cssText 赋值会重写整个 style 属性的值，意味着之前通过 style 属性设置的属性都会丢失。比如，如果一个元素通过 style 属性设置了边框，而赋给 cssText
属性的值不包含边框，则元素的边框会消失。下面的例子演示了 cssText 的使用：

```js
myDiv.style.cssText = 'width: 25px; height: 100px; background-color: green';
console.log(myDiv.style.cssText);
```

设置 cssText 是一次性修改元素多个样式最快捷的方式，因为所有变化会同时生效。

length 属性是跟 item()方法一起配套迭代 CSS 属性用的。style 其实是一个类数组对象，也可以用中括号代替 item()取得相应位置的 CSS 属性名，如下所示：

```js
for (let i = 0, len = myDiv.style.length; i < len; i++) {
  console.log(myDiv.style[i]); // 或者用myDiv.style.item(i)
}
```

或者更简洁的：

```js
[...myDiv.style].forEach((prop) => console.log(prop));
```

使用中括号或者 item()都可以取得相应位置的 CSS 属性名（'background-color'，不是'backgroundColor'）。这个属性名可以传给 getPropertyValue()以取得属性的值，如下面的例子所示：

```js
console.log(
  [...myDiv.style].map(
    (prop) => `${prop}: ${myDiv.style.getPropertyValue(prop)}`,
  ),
);
```

removeProperty()方法用于从元素样式中删除指定的 CSS 属性。使用这个方法删除属性意味着会应用该属性的默认（从其他样式表层叠继承的）样式。例如，可以像下面这样删除 style 属性中设置的 border 样式：

```js
myDiv.style.removeProperty('border');
```

在不确定给定 CSS 属性的默认值是什么的时候，可以使用这个方法。只要从 style 属性中删除，就可以使用默认值。

2. **计算样式**

style 对象中包含支持 style 属性的元素为这个属性设置的样式信息，但不包含从其他样式表层叠继承的同样影响该元素的样式信息。DOM2 Style 在 document.defaultView 上增加了 getComputedStyle()方法。这个方法接收两个参数：要取得计算样式的元素和伪元素字符串（如':after'）。如果不需要查询伪元素，则第二个参数可以传 null。getComputedStyle()方法返回一个 CSSStyleDeclaration 对象（与 style 属性的类型一样），包含元素的计算样式。假设有如下 HTML 页面：

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Computed Styles Example</title>
    <style type="text/css">
      #myDiv {
        background-color: blue;
        width: 100px;
        height: 200px;
      }
    </style>
  </head>
  <body>
    <div
      id="myDiv"
      style="background-color: red; border: 1px solid black"
    ></div>
  </body>
</html>
```

这里的`<div>`元素从文档样式表（`<style>`元素）和自己的 style 属性获取了样式。此时，这个元素的 style 对象中包含 backgroundColor 和 border 属性，但不包含（通过样式表规则应用的）width 和 height 属性。下面的代码从这个元素获取了计算样式：

```js
let myDiv = document.getElementById('myDiv');
let computedStyle = document.defaultView.getComputedStyle(myDiv, null);
console.log(computedStyle.backgroundColor); // 'red'
console.log(computedStyle.width); // '100px'
console.log(computedStyle.height); // '200px'
console.log(computedStyle.border); // '1px solid black'（在某些浏览器中）
```

在取得这个元素的计算样式时，得到的背景颜色是'red'，宽度为'100px'，高度为'200px'。背景颜色不是'blue'，因为元素样式覆盖了它。border 属性不一定返回样式表中实际的 border 规则（某些浏览器会）。这种不一致性是因浏览器解释简写样式的方式造成的，比如 border 实际上会设置一组别的属性。在设置 border 时，实际上设置的是 4 条边的线条宽度、颜色和样式（border-left-width、border-top-color、border-bottom-style 等）。因此，即使 computedStyle.border 在所有浏览器中都不会返回值，computedStyle.borderLeftWidth 也一定会返回值。

注意 浏览器虽然会返回样式值，但返回值的格式不一定相同。比如，Firefox 和 Safari 会把所有颜色值转换为 RGB 格式（如红色会变成 rgb(255,0,0)），而 Opera 把所有颜色转换为十六进制表示法（如红色会变成#ff0000）。因此在使用 getComputedStyle()时一定要多测试几个浏览器。

关于计算样式要记住一点，在所有浏览器中计算样式都是只读的，不能修改 getComputedStyle()方法返回的对象。而且，计算样式还包含浏览器内部样式表中的信息。因此有默认值的 CSS 属性会出现在计算样式里。例如，visibility 属性在所有浏览器中都有默认值，但这个值因实现而不同。有些浏览器会把 visibility 的默认值设置为'visible'，而另一些将其设置为'inherit'。不能假设 CSS 属性的默认值在所有浏览器中都一样。如果需要元素具有特定的默认值，那么一定要在样式表中手动指定。

### 16.2.2. 操作样式表

CSSStyleSheet 类型表示 CSS 样式表，包括使用`<link>`元素和通过`<style>`元素定义的样式表。注意，这两个元素本身分别是 HTMLLinkElement 和 HTMLStyleElement。CSSStyleSheet 类型是一个通用样式表类型，可以表示以任何方式在 HTML 中定义的样式表。另外，元素特定的类型允许修改 HTML 属性，而 CSSStyleSheet 类型的实例则是一个只读对象（只有一个属性例外）。

CSSStyleSheet 类型继承 StyleSheet，后者可用作非 CSS 样式表的基类。以下是 CSSStyleSheet 从 StyleSheet 继承的属性。

- disabled，布尔值，表示样式表是否被禁用了（这个属性是可读写的，因此将它设置为 true 会禁用样式表）。
- href，如果是使用`<link>`包含的样式表，则返回样式表的 URL，否则返回 null。
- media，样式表支持的媒体类型集合，这个集合有一个 length 属性和一个 item()方法，跟所有 DOM 集合一样。同样跟所有 DOM 集合一样，也可以使用中括号访问集合中特定的项。如果样式表可用于所有媒体，则返回空列表。
- ownerNode，指向拥有当前样式表的节点，在 HTML 中要么是`<link>`元素要么是`<style>`元素（在 XML 中可以是处理指令）。如果当前样式表是通过@import 被包含在另一个样式表中，则这个属性值为 null。
- parentStyleSheet，如果当前样式表是通过@import 被包含在另一个样式表中，则这个属性指向导入它的样式表。
- title，ownerNode 的 title 属性。
- type，字符串，表示样式表的类型。对 CSS 样式表来说，就是'text/css'。上述属性里除了 disabled，其他属性都是只读的。除了上面继承的属性，CSSStyleSheet 类型还支持以下属性和方法。
- cssRules，当前样式表包含的样式规则的集合。
- ownerRule，如果样式表是使用@import 导入的，则指向导入规则；否则为 null。
- deleteRule(index)，在指定位置删除 cssRules 中的规则。
- insertRule(rule, index)，在指定位置向 cssRules 中插入规则。

document.styleSheets 表示文档中可用的样式表集合。这个集合的 length 属性保存着文档中样式表的数量，而每个样式表都可以使用中括号或 item()方法获取。来看这个例子：

```js
let sheet = null;
for (let i = 0, len = document.styleSheets.length; i < len; i++) {
  sheet = document.styleSheets[i];
  console.log(sheet.href);
}
```

document.styleSheets 返回的样式表可能会因浏览器而异。所有浏览器都会包含`<style>`元素和 rel 属性设置为'stylesheet'的`<link>`元素。IE、Opera、Chrome 也包含 rel 属性设置为'alternate stylesheet'的`<link>`元素。

通过`<link>`或`<style>`元素也可以直接获取 CSSStyleSheet 对象。DOM 在这两个元素上暴露了 sheet 属性，其中包含对应的 CSSStyleSheet 对象。

1. **CSS 规则**

CSSRule 类型表示样式表中的一条规则。这个类型也是一个通用基类，很多类型都继承它，但其中最常用的是表示样式信息的 CSSStyleRule（其他 CSS 规则还有@import、@font-face、@page 和@charset 等，不过这些规则很少需要使用脚本来操作）。以下是 CSSStyleRule 对象上可用的属性。

- cssText，返回整条规则的文本。这里的文本可能与样式表中实际的文本不一样，因为浏览器内部处理样式表的方式也不一样。Safari 始终会把所有字母都转换为小写。
- parentRule，如果这条规则被其他规则（如@media）包含，则指向包含规则，否则就是 null。
- parentStyleSheet，包含当前规则的样式表。
- selectorText，返回规则的选择符文本。这里的文本可能与样式表中实际的文本不一样，因为浏览器内部处理样式表的方式也不一样。这个属性在 Firefox、Safari、Chrome 和 IE 中是只读的，在 Opera 中是可以修改的。
- style，返回 CSSStyleDeclaration 对象，可以设置和获取当前规则中的样式。
- type，数值常量，表示规则类型。对于样式规则，它始终为 1。

在这些属性中，使用最多的是cssText、selectorText 和style。cssText 属性与style.cssText类似，不过并不完全一样。前者包含选择符文本和环绕样式声明的大括号，而后者则只包含样式声明（类似于元素上的style.cssText）。此外，cssText 是只读的，而style.cssText 可以被重写。

多数情况下，使用style 属性就可以实现操作样式规则的任务了。这个对象可以像每个元素上的style 对象一样，用来读取或修改规则的样式。比如下面这个CSS 规则：

```css
div.box {
  background-color: blue;
  width: 100px;
  height: 200px;
}
```

假设这条规则位于页面中的第一个样式表中，而且是该样式表中唯一一条CSS 规则，则下列代码可以获取它的所有信息：

```js
let sheet = document.styleSheets[0];
let rules = sheet.cssRules || sheet.rules; // 取得规则集合
let rule = rules[0]; // 取得第一条规则
console.log(rule.selectorText); // 'div.box'
console.log(rule.style.cssText); // 完整的CSS 代码
console.log(rule.style.backgroundColor); // 'blue'
console.log(rule.style.width); // '100px'
console.log(rule.style.height); // '200px'
```

使用这些接口，可以像确定元素style 对象中包含的样式一样，确定一条样式规则的样式信息。与元素的场景一样，也可以修改规则中的样式，如下所示：

```js
let sheet = document.styleSheets[0];
let rules = sheet.cssRules || sheet.rules; // 取得规则集合
let rule = rules[0]; // 取得第一条规则
rule.style.backgroundColor = 'red'
```

注意，这样修改规则会影响到页面上所有应用了该规则的元素。如果页面上有两个`<div>`元素有'box'类，则这两个元素都会受到这个修改的影响。

2. **创建规则**

DOM 规定，可以使用insertRule()方法向样式表中添加新规则。这个方法接收两个参数：规则的文本和表示插入位置的索引值。下面是一个例子：

```js
sheet.insertRule("body { background-color: silver }", 0); // 使用DOM 方法
```

这个例子插入了一条改变文档背景颜色的规则。这条规则是作为样式表的第一条规则（位置0）插入的，顺序对规则层叠是很重要的。

虽然可以这样添加规则，但随着要维护的规则增多，很快就会变得非常麻烦。这时候，更好的方式是使用第14 章介绍的动态样式加载技术。

3. **删除规则**

支持从样式表中删除规则的DOM 方法是deleteRule()，它接收一个参数：要删除规则的索引。要删除样式表中的第一条规则，可以这样做：

```js
sheet.deleteRule(0); // 使用DOM 方法
```

与添加规则一样，删除规则并不是Web 开发中常见的做法。考虑到可能影响CSS 层叠的效果，删除规则时要慎重。

### 16.2.3. 元素尺寸

本节介绍的属性和方法并不是DOM2 Style 规范中定义的，但与HTML 元素的样式有关。DOM 一直缺乏页面中元素实际尺寸的规定。IE 率先增加了一些属性，向开发者暴露元素的尺寸信息。这些属性现在已经得到所有主流浏览器支持。

1. **偏移尺寸**

第一组属性涉及 **偏移尺寸(offset dimensions)**，包含元素在屏幕上占用的所有视觉空间。元素在页面上的视觉空间由其高度和宽度决定，包括所有内边距、滚动条和边框（但不包含外边距）。以下4 个属性用于取得元素的偏移尺寸。

- offsetHeight，元素在垂直方向上占用的像素尺寸，包括它的高度、水平滚动条高度（如果可见）和上、下边框的高度。
- offsetLeft，元素左边框外侧距离包含元素左边框内侧的像素数。
- offsetTop，元素上边框外侧距离包含元素上边框内侧的像素数。
- offsetWidth，元素在水平方向上占用的像素尺寸，包括它的宽度、垂直滚动条宽度（如果可见）和左、右边框的宽度。

其中，offsetLeft 和offsetTop 是相对于包含元素的，包含元素保存在offsetParent 属性中。offsetParent 不一定是parentNode。比如，`<td>`元素的offsetParent 是作为其祖先的`<table>`元素，因为`<table>`是节点层级中第一个提供尺寸的元素。下图展示了这些属性代表的不同尺寸。

