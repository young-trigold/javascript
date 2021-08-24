**目录：**
- [14. DOM](#14-dom)
  - [14.1. 节点层次](#141-节点层次)

# 14. DOM

本章内容
- 理解文档对象模型（DOM）的构成
- 节点类型
- 浏览器兼容性
- MutationObserver 接口

**文档对象模型（DOM，Document Object Model）** 是HTML 和XML 文档的编程接口。DOM 表示由多层节点构成的文档，通过它开发者可以添加、删除和修改页面的各个部分。脱胎于网景和微软早期的动态HTML（DHTML，Dynamic HTML），DOM 现在是真正跨平台、语言无关的表示和操作网页的方式。

DOM Level 1 在1998 年成为W3C 推荐标准，提供了基本文档结构和查询的接口。本章之所以介绍DOM，主要因为它与浏览器中的HTML 网页相关，并且在JavaScript 中提供了DOM API。

注意 IE8 及更低版本中的DOM是通过COM 对象实现的。这意味着这些版本的IE 中，DOM 对象跟原生JavaScript 对象具有不同的行为和功能。

## 14.1. 节点层次

任何HTML 或XML 文档都可以用DOM表示为一个由节点构成的层级结构。节点分很多类型，每种类型对应着文档中不同的信息和（或）标记，也都有自己不同的特性、数据和方法，而且与其他类型有某种关系。这些关系构成了层级，让标记可以表示为一个以特定节点为根的树形结构。以下面的HTML为例：

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

