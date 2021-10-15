**目录：**

- [22. 处理 XML](#22-处理-xml)
  - [22.1. 浏览器对XML DOM 的支持](#221-浏览器对xml-dom-的支持)
    - [22.1.1. DOM Level 2 Core](#2211-dom-level-2-core)
    - [22.1.2. DOMParser 类型](#2212-domparser-类型)

# 22. 处理 XML

本章内容
- 浏览器对XML DOM 的支持
- 在JavaScript 中使用XPath
- 使用XSLT 处理器

XML 曾一度是在互联网上存储和传输结构化数据的标准。XML 的发展反映了Web 的发展，因为DOM 标准不仅是为了在浏览器中使用，而且还为了在桌面和服务器应用程序中处理XML 数据结构。在没有DOM 标准的时候，很多开发者使用JavaScript 编写自己的XML 解析器。自从有了DOM 标准，所有浏览器都开始原生支持XML、XML DOM及很多其他相关技术。

## 22.1. 浏览器对XML DOM 的支持

因为很多浏览器在正式标准问世之前就开始实现XML 解析方案，所以不同浏览器对标准的支持不仅有级别上的差异，也有实现上的差异。DOM Level 3 增加了解析和序列化能力。不过，在DOM Level 3制定完成时，大多数浏览器也已实现了自己的解析方案。

### 22.1.1. DOM Level 2 Core

正如第13 章所述，DOM Level 2 增加了document.implementation 的createDocument()方法。有读者可能还记得，可以像下面这样创建空XML 文档：

```javascript
const xmldom = document.implementation.createDocument(namespaceUri, root, doctype);
```

在JavaScript 中处理XML 时，root 参数通常只会使用一次，因为这个参数定义的是XML DOM中document 元素的标签名。namespaceUri 参数用得很少，因为在JavaScript 中很难管理命名空间。doctype 参数则更是少用。

要创建一个document 对象标签名为`<root>`的新XML 文档，可以使用以下代码：

```javascript
const xmldom = document.implementation.createDocument("", "root", null);
console.log(xmldom.documentElement.tagName);
// >> 'root'
const child = xmldom.createElement("child");
xmldom.documentElement.appendChild(child);
```

这个例子创建了一个XML DOM文档，该文档没有默认的命名空间和文档类型。注意，即使不指定命名空间和文档类型，参数还是要传的。命名空间传入空字符串表示不应用命名空间，文档类型传入null 表示没有文档类型。xmldom 变量包含DOM Level 2 Document 类型的实例，包括第13 章介绍的
所有DOM 方法和属性。在这个例子中，我们打印了document 元素的标签名，然后又为它创建并添加了一个新的子元素。

要检查浏览器是否支持DOM Level 2 XML，可以使用如下代码：

```javascript
const hasXmlDom = document.implementation.hasFeature("XML", "2.0");
```

实践中，很少需要凭空创建XML 文档，然后使用DOM 方法来系统创建XML 数据结构。更多是把XML文档解析为DOM结构，或者相反。因为DOM Level 2 并未提供这种功能，所以出现了一些事实标准。

### 22.1.2. DOMParser 类型

Firefox 专门为把XML 解析为DOM文档新增了DOMParser 类型，后来所有其他浏览器也实现了该类型。要使用DOMParser，需要先创建它的一个实例，然后再调用parseFromString()方法。这个方法接收两个参数：要解析的XML 字符串和内容类型（始终应该是"text/html"）。返回值是Document的实例。来看下面的例子：

```javascript
let parser = new DOMParser();
let xmldom = parser.parseFromString("<root><child/></root>", "text/xml");
console.log(xmldom.documentElement.tagName); // "root"
console.log(xmldom.documentElement.firstChild.tagName); // "child"
let anotherChild = xmldom.createElement("child");
xmldom.documentElement.appendChild(anotherChild);
let children = xmldom.getElementsByTagName("child");
console.log(children.length); // 2
```

