```json
item : JavaScript 高级程序设计
priority: 2
span : 1 months
plan : 7 chapter / week
```

**目录：**

- [1. 什么是 JavaScript](#1-什么是-javascript)
  - [1.1. 简短的历史回顾](#11-简短的历史回顾)
  - [1.2. JavaScript 实现](#12-javascript-实现)
    - [1.2.1. ECMAScript](#121-ecmascript)
    - [1.2.2. DOM](#122-dom)
    - [1.2.3. BOM](#123-bom)
  - [1.3. JavaScript 版本](#13-javascript-版本)
- [2. HTML 中的 JavaScript](#2-html-中的-javascript)
  - [2.1. `<script>` 元素](#21-script-元素)
    - [2.1.1. 标签位置](#211-标签位置)
    - [2.1.2. 推迟执行脚本](#212-推迟执行脚本)
    - [2.1.3. 异步执行脚本](#213-异步执行脚本)
    - [2.1.4. 动态加载脚本](#214-动态加载脚本)
  - [2.2. 行内代码与外部文件](#22-行内代码与外部文件)
  - [2.3. 文档模式](#23-文档模式)
  - [2.4. `<noscript>` 元素](#24-noscript-元素)
- [3. 语言基础](#3-语言基础)
  - [3.1. 语法](#31-语法)
    - [3.1.1. 区分大小写](#311-区分大小写)
    - [3.1.2. 标识符](#312-标识符)
    - [3.1.3. 注释](#313-注释)
    - [3.1.4. 严格模式](#314-严格模式)
    - [3.1.5. 语句](#315-语句)
  - [3.2. 关键字和保留字](#32-关键字和保留字)
  - [3.3. 变量](#33-变量)
    - [3.3.1. var 关键字](#331-var-关键字)
    - [3.3.2. let 声明](#332-let-声明)
    - [3.3.3. const](#333-const)
    - [3.3.4. 声明风格与最佳实践](#334-声明风格与最佳实践)
  - [3.4. 数据类型](#34-数据类型)
    - [3.4.1. typeof 操作符](#341-typeof-操作符)
    - [3.4.2. Undefined 类型](#342-undefined-类型)
    - [3.4.3. Null 类型](#343-null-类型)
    - [3.4.4. Boolean 类型](#344-boolean-类型)
    - [3.4.5. Number 类型](#345-number-类型)
    - [3.4.6. String 类型](#346-string-类型)
    - [3.4.7. Symbol 类型](#347-symbol-类型)
  - [3.5. 操作符](#35-操作符)
    - [3.5.1. 一元操作符](#351-一元操作符)
    - [3.5.2. 位操作符](#352-位操作符)
    - [3.5.3. 布尔操作符](#353-布尔操作符)
    - [3.5.4. 乘性操作符](#354-乘性操作符)
    - [3.5.5. 指数操作符](#355-指数操作符)
    - [3.5.6. 加性操作符](#356-加性操作符)
    - [3.5.7. 关系操作符](#357-关系操作符)
    - [3.5.8. 相等操作符](#358-相等操作符)
    - [3.5.9. 条件操作符](#359-条件操作符)
    - [3.5.10. 赋值操作符](#3510-赋值操作符)
    - [3.5.11. 逗号操作符](#3511-逗号操作符)
  - [3.6. 语句](#36-语句)
    - [3.6.1. if 语句](#361-if-语句)
    - [3.6.2. do-while 语句](#362-do-while-语句)
    - [3.6.3. while 语句](#363-while-语句)
    - [3.6.4. for 语句](#364-for-语句)
    - [3.6.5. for-in 语句](#365-for-in-语句)
    - [3.6.6. for-of 语句](#366-for-of-语句)
    - [3.6.7. 标签语句](#367-标签语句)
    - [3.6.8. break 和 continue 语句](#368-break-和-continue-语句)
    - [3.6.9. with](#369-with)
    - [3.6.10. switch 语句](#3610-switch-语句)
  - [3.7. 函数](#37-函数)
- [4. 变量，作用域与内存](#4-变量作用域与内存)
  - [4.1. 原始值和引用值](#41-原始值和引用值)
    - [4.1.1. 动态属性](#411-动态属性)
    - [4.1.2. 复制值](#412-复制值)
    - [4.1.3. 传递参数](#413-传递参数)
    - [4.1.4. 确定类型](#414-确定类型)
  - [4.2. 执行上下文和作用域](#42-执行上下文和作用域)
    - [4.2.1. 作用域链增强](#421-作用域链增强)
    - [4.2.2. 变量声明](#422-变量声明)
  - [4.3. 垃圾回收](#43-垃圾回收)
    - [4.3.1. 标记清理](#431-标记清理)
    - [4.3.2. 引用计数](#432-引用计数)
    - [4.3.3. 性能](#433-性能)
    - [4.3.4. 内存管理](#434-内存管理)
- [5. 基本引用类型](#5-基本引用类型)
  - [5.1. Date](#51-date)
    - [5.1.1. 继承的方法](#511-继承的方法)
    - [5.1.2. 日期格式化方法](#512-日期格式化方法)
    - [5.1.3. 日期/时间组件方法](#513-日期时间组件方法)
  - [5.2. RegExp](#52-regexp)
    - [5.2.1. RegExp 实例属性](#521-regexp-实例属性)
    - [5.2.2. RegExp 实例方法](#522-regexp-实例方法)
    - [5.2.3. RegExp 构造函数属性](#523-regexp-构造函数属性)
    - [5.2.4. 模式局限](#524-模式局限)
  - [5.3. 原始值包装类型](#53-原始值包装类型)
    - [5.3.1. Boolean](#531-boolean)
    - [5.3.2. Number](#532-number)
    - [5.3.3. String](#533-string)
  - [5.4. 单例内置对象](#54-单例内置对象)
    - [5.4.1. Global](#541-global)
    - [5.4.2. Math](#542-math)
- [6. 集合引用类型](#6-集合引用类型)
  - [6.1. Object](#61-object)
  - [6.2. Array](#62-array)
    - [6.2.1. 创建数组](#621-创建数组)
    - [6.2.2. 数组空位](#622-数组空位)
    - [6.2.3. 数组索引](#623-数组索引)
    - [6.2.4. 检测数组](#624-检测数组)
    - [6.2.5. 迭代器方法](#625-迭代器方法)
    - [6.2.6. 复制和填充方法](#626-复制和填充方法)
    - [6.2.7. 转换方法](#627-转换方法)
    - [6.2.8. 栈方法](#628-栈方法)
    - [6.2.9. 队列方法](#629-队列方法)
    - [6.2.10. 排序方法](#6210-排序方法)
    - [6.2.11. 操作方法](#6211-操作方法)
    - [6.2.12. 搜索和位置方法](#6212-搜索和位置方法)
    - [6.2.13. 迭代方法](#6213-迭代方法)
    - [6.2.14. 归并方法](#6214-归并方法)
  - [6.3. 定型数组](#63-定型数组)
    - [6.3.1. 历史](#631-历史)
    - [6.3.2. ArrayBuffer](#632-arraybuffer)
    - [6.3.3. DataView](#633-dataview)
    - [6.3.4. 定型数组](#634-定型数组)
  - [6.4. Map](#64-map)
    - [6.4.1. 基本 API](#641-基本-api)
    - [6.4.2. 顺序与迭代](#642-顺序与迭代)
    - [6.4.3. 选择 Object 还是 Map](#643-选择-object-还是-map)
  - [6.5. WeakMap](#65-weakmap)
    - [6.5.1. 基本 API](#651-基本-api)
    - [6.5.2. 弱键](#652-弱键)
    - [6.5.3. 不可迭代键](#653-不可迭代键)
    - [6.5.4. 使用弱映射](#654-使用弱映射)
  - [6.6. Set](#66-set)
    - [6.6.1. 基本 API](#661-基本-api)
    - [6.6.2. 顺序与迭代](#662-顺序与迭代)
    - [6.6.3. 定义正式集合操作](#663-定义正式集合操作)
  - [6.7. WeakSet](#67-weakset)
    - [6.7.1. 基本 API](#671-基本-api)
    - [6.7.2. 弱值](#672-弱值)
    - [6.7.3. 不可迭代值](#673-不可迭代值)
    - [6.7.4. 使用弱集合](#674-使用弱集合)
  - [6.8. 迭代与扩展操作](#68-迭代与扩展操作)
- [7. 迭代器与生成器](#7-迭代器与生成器)
  - [7.1. 理解迭代](#71-理解迭代)
  - [7.2. 迭代器模式](#72-迭代器模式)
    - [7.2.1. 可迭代协议](#721-可迭代协议)
    - [7.2.2. 迭代器协议](#722-迭代器协议)
    - [7.2.3. 自定义迭代器](#723-自定义迭代器)
    - [7.2.4. 提前终止迭代器](#724-提前终止迭代器)
  - [7.3. 生成器](#73-生成器)
    - [7.3.1. 生成器基础](#731-生成器基础)
    - [7.3.2. 通过 yield 中断执行](#732-通过-yield-中断执行)
    - [7.3.3. 生成器作为默认迭代器](#733-生成器作为默认迭代器)
    - [7.3.4. 提前终止迭代器](#734-提前终止迭代器)
- [8. 对象、类与面向对象编程](#8-对象类与面向对象编程)
  - [8.1. 理解对象](#81-理解对象)
    - [8.1.1. 属性的类型](#811-属性的类型)
    - [8.1.2. 定义多个属性](#812-定义多个属性)
    - [8.1.3. 读取属性的特性](#813-读取属性的特性)
    - [8.1.4. 合并对象](#814-合并对象)
    - [8.1.5. 对象标识及相等判定](#815-对象标识及相等判定)
    - [8.1.6. 增强的对象语法](#816-增强的对象语法)
    - [8.1.7. 对象解构](#817-对象解构)

# 1. 什么是 JavaScript

本章内容

- JavaScript 历史回顾
- JavaScript 是什么
- JavaScript 与 ECMAScript 的关系
- JavaScript 的不同版本

1995 年，JavaScript 问世。当时，它的主要用途是代替 Perl 等服务器端语言处理输入验证。在此之前，要验证某个必填字段是否已填写，或者某个输入的值是否有效，需要与服务器的一次往返通信。网景公司希望通过在其 Navigator 浏览器中加入 JavaScript 来改变这个局面。在那个普遍通过电话拨号上网的年代，由客户端处理某些基本的验证是让人兴奋的新功能。缓慢的网速让页面每次刷新都考验着人们的耐心。

从那时起，JavaScript 逐渐成为市面上所有主流浏览器的标配。如今，JavaScript 的应用也不再局限于数据验证，而是渗透到浏览器窗口及其内容的方方面面。JavaScript 已被公认为主流的编程语言，能够实现复杂的计算与交互，包括闭包、匿名（lambda）函数，甚至元编程等特性。不仅是桌面浏览器，手机浏览器和屏幕阅读器也支持 JavaScript，其重要性可见一斑。就连拥有自家客户端脚本语言 VBScript 的微软公司，也在其 Internet Explorer（以下简称 IE）浏览器最初的版本中包含了自己的 JavaScript 实现。

从简单的输入验证脚本到强大的编程语言，JavaScript 的崛起没有任何人预测到。它很简单，学会用只要几分钟；它又很复杂，掌握它要很多年。要真正学好用好 JavaScript，理解其本质、历史及局限性是非常重要的。

## 1.1. 简短的历史回顾

随着 Web 日益流行，对客户端脚本语言的需求也越来越强烈。当时，大多数用户使用 28.8kbit/s 的调制解调器上网，但网页变得越来越大、越来越复杂。为验证简单的表单而需要大量与服务器的往返通信成为用户的痛点。想象一下，你填写完表单，单击“提交”按钮，等 30 秒处理，然后看到一条消息，告诉你有一个必填字段没填。网景在当时是引领技术革新的公司，它将开发一个客户端脚本语言来处理这种简单的数据验证提上了日程。

1995 年，网景公司一位名叫 Brendan Eich 的工程师，开始为即将发布的 Netscape Navigator 2 开发一个叫 Mocha（后来改名为 LiveScript）的脚本语言。当时的计划是在客户端和服务器端都使用它，它在服务器端叫 LiveWire。

为了赶上发布时间，网景与 Sun 公司结为开发联盟，共同完成 LiveScript 的开发。就在 Netscape Navigator 2 正式发布前，网景把 LiveScript 改名为 JavaScript，以便搭上媒体当时热烈炒作 Java 的顺风车。

由于 JavaScript 1.0 很成功，网景又在 Netscape Navigator 3 中发布了 1.1 版本。尚未成熟的 Web 的受欢迎程度达到了历史新高，而网景则稳居市场领导者的位置。这时候，微软决定向 IE 投入更多资源。就在 Netscape Navigator 3 发布后不久，微软发布了 IE3，其中包含自己名为 JScript（叫这个名字是为了避免与网景发生许可纠纷）的 JavaScript 实现。1996 年 8 月，微软重磅进入 Web 浏览器领域，这是网景永远的痛，但它代表 JavaScript 作为一门语言向前迈进了一大步。

微软的 JavaScript 实现意味着出现了两个版本的 JavaScript：Netscape Navigator 中的 JavaScript，以及 IE 中的 JScript。与 C 语言以及很多其他编程语言不同，JavaScript 还没有规范其语法或特性的标准， 两个版本并存让这个问题更加突出了。随着业界担忧日甚，JavaScript 终于踏上了标准化的征程。

1997 年，JavaScript 1.1 作为提案被提交给欧洲计算机制造商协会（Ecma）。第 39 技术委员会（TC39）承担了“标准化一门通用、跨平台、厂商中立的脚本语言的语法和语义”的任务（参见 TC39-ECMAScript）。 TC39 委员会由来自网景、Sun、微软、Borland、Nombas 和其他对这门脚本语言有兴趣的公司的工程师 组成。他们花了数月时间打造出 ECMA-262，也就是 ECMAScript（发音为“ek-ma-script”）这个新的脚本语言标准。

1998 年，国际标准化组织（ISO）和国际电工委员会（IEC）也将 ECMAScript 采纳为标准（ISO/ IEC-16262）。自此以后，各家浏览器均以 ECMAScript 作为自己 JavaScript 实现的依据，虽然具体实现各有不同。

## 1.2. JavaScript 实现

虽然 JavaScript 和 ECMAScript 基本上是同义词，但 JavaScript 远远不限于 ECMA-262 所定义的那样。没错，完整的 JavaScript 实现包含以下几个部分（见下图）：

- **核心（ECMAScript）**
- **文档对象模型（DOM）**
- **浏览器对象模型（BOM）**

![1-1-JavaScript组成](illustrations/1-1-JavaScript组成.png)

### 1.2.1. ECMAScript

ECMAScript，即 ECMA-262 定义的语言，并不局限于 Web 浏览器。事实上，这门语言没有输入和输出之类的方法。ECMA-262 将这门语言作为一个基准来定义，以便在它之上再构建更稳健的脚本语言。Web 浏览器只是 ECMAScript 实现可能存在的一种 **宿主环境(host environment)**。宿主环境提供 ECMAScript 的基准实现和与环境自身交互必需的扩展。扩展（比如 DOM）使用 ECMAScript 核心类型和语法，提供特定于环境的额外功能。其他宿主环境还有服务器端 JavaScript 平台 Node.js 和已经被淘汰的 Adobe Flash(2020 年后)。

如果不涉及浏览器的话，ECMA-262 到底定义了什么？在基本的层面，它描述这门语言的如下部分：

- 语法
- 类型
- 语句
- 关键字
- 保留字
- 操作符
- 全局对象

ECMAScript 只是对实现这个规范描述的所有方面的一门语言的称呼。JavaScript 实现了 ECMAScript，而 Adobe ActionScript 同样也实现了 ECMAScript。

1. **ECMAScript 版本**

ECMAScript 不同的版本以“edition”表示（也就是描述特定实现的 ECMA-262 的版本）。ECMA-262 最近的版本是第 12 版，发布于 2021 年 6 月。ECMA-262 的第 1 版本质上跟网景的 JavaScript 1.1 相同， 只不过删除了所有浏览器特定的代码，外加少量细微的修改。ECMA-262 要求支持 Unicode 标准（以支持多语言），而且对象要与平台无关（Netscape JavaScript 1.1 的对象不是这样，比如它的 Date 对象就依赖平台）。这也是 JavaScript 1.1 和 JavaScript 1.2 不符合 ECMA-262 第 1 版要求的原因。

ECMA-262 第 2 版只是做了一些编校工作，主要是为了更新之后严格符合 ISO/IEC-16262 的要求， 并没有增减或改变任何特性。ECMAScript 实现通常不使用第 2 版来衡量符合性（conformance）。

ECMA-262 第 3 版第一次真正对这个标准进行更新，更新了字符串处理、错误定义和数值输出。此外还增加了对正则表达式、新的控制语句、try/catch 异常处理的支持，以及为了更好地让标准国际化所做的少量修改。对很多人来说，这标志着 ECMAScript 作为一门真正的编程语言的时代终于到来了。

ECMA-262 第 4 版是对这门语言的一次彻底修订。作为对 JavaScript 在 Web 上日益成功的回应，开发者开始修订 ECMAScript 以满足全球 Web 开发日益增长的需求。为此，Ecma T39 再次被召集起来， 以决定这门语言的未来。结果，他们制定的规范几乎在第 3 版基础上完全定义了一门新语言。第 4 版包括强类型变量、新语句和数据结构、真正的类和经典的继承，以及操作数据的新手段。

与此同时，TC39 委员会的一个子委员会也提出了另外一份提案，叫作“ECMAScript 3.1”，只对这门语言进行了较少的改进。这个子委员会的人认为第 4 版对这门语言来说跳跃太大了。因此，他们提出了一个改动较小的提案，只要在现有 JavaScript 引擎基础上做一些增改就可以实现。最终，ES3.1 子委员会赢得了 TC39 委员会的支持，ECMA-262 第 4 版在正式发布之前被放弃。

ECMAScript 3.1 变成了 ECMA-262 的第 5 版，于 2009 年 12 月 3 日正式发布。第 5 版致力于厘清第 3 版存在的歧义，也增加了新功能。新功能包括原生的解析和序列化 JSON 数据的 JSON 对象、方便继承和高级属性定义的方法，以及新的增强 ECMAScript 引擎解释和执行代码能力的严格模式。第 5 版在 2011 年 6 月发布了一个维护性修订版，这个修订版只更正了规范中的错误，并未增加任何新的语言或库特性。

ECMA-262 第 6 版，俗称 ES6、ES2015 或 ES Harmony（和谐版），于 2015 年 6 月发布。这一版包含了大概这个规范有史以来最重要的一批增强特性。ES6 正式支持了类、模块、迭代器、生成器、箭头函数、期约、反射、代理和众多新的数据类型。

ECMA-262 第 7 版，也称为 ES7 或 ES2016，于 2016 年 6 月发布。这次修订只包含少量语法层面的增强，如 Array.prototype.includes 和指数操作符。

ECMA-262 第 8 版，也称为 ES8、ES2017，完成于 2017 年 6 月。这一版主要增加了异步函数（async/await）、SharedArrayBuffer 及 Atomics API，以及 Object.values()/Object.entries()/Object.getOwnPropertyDescriptors()和字符串填充方法，另外明确支持对象字面量最后的逗号。

ECMA-262 第 9 版，也称为 ES9、ES2018，发布于 2018 年 6 月。这次修订包括异步迭代、剩余和扩展属性、一组新的正则表达式特性、Promise finally()，以及模板字面量修订。

ECMA-262 第 10 版，也称为 ES10、ES2019，发布于 2019 年 6 月。这次修订增加了 Array.prototype. flat()/flatMap()、String.prototype.trimStart()/trimEnd()、Object.fromEntries()方法，以及 Symbol.prototype.description 属性，明确定义了 Function.prototype.toString() 的返回值并固定了 Array.prototype.sort()的顺序。另外，这次修订解决了与 JSON 字符串兼容的问题，并定义了 catch 子句的可选绑定。

第 11 版，即 ECMAScript 2020，于 2020 年 6 月发布。除了新的函数，该版本还引入了一个用于任意大小的整数的 BigInt 原始类型，nullish 组合运算符，以及 globalThis 对象。

最新(2021 年)第 12 版于 2021 年 6 月发布。第 12 版增添了字符串方法 replaceALL，逻辑赋值操作符(??==, &&==, ||==)，Promise.any 方法，一种新的错误类型 AggregateError 表示同时发生多个错误，等等。

2. **符合性**

ECMA-262 阐述了什么是 ECMAScript 符合性。要成为 ECMAScript 实现，必须满足下列条件：

- 支持 ECMA-262 中描述的所有“类型、值、对象、属性、函数，以及程序语法与语义”；
- 支持 Unicode 字符标准。
  此外，符合性实现还可以满足下列要求。
- 增加 ECMA-262 中未提及的“额外的类型、值、对象、属性和函数”。ECMA-262 所说的这些额外内容主要指规范中未给出的新对象或对象的新属性。
- 支持 ECMA-262 中没有定义的“程序和正则表达式语法”（意思是允许修改和扩展内置的正则表达式特性）。

以上条件为实现开发者基于 ECMAScript 开发语言提供了极大的权限和灵活度，也是其广受欢迎的原因之一。

3. **浏览器对 ECMAScipt 的支持**

1996 年，Netscape Navigator 3 发布时包含了 JavaScript 1.1。JavaScript 1.1 规范随后被提交给 Ecma， 作为对新的 ECMA-262 标准的建议。随着 JavaScript 迅速走红，网景非常愿意开发 1.2 版。可是有个问题：Ecma 尚未接受网景的建议。

Netscape Navigator 3 发布后不久，微软推出了 IE3。IE 的这个版本包含了 JScript 1.0，本意是提供与 JavaScript 1.1 相同的功能。不过，由于缺少很多文档，而且还有不少重复性功能，JScript 1.0 远远没有 JavaScript 1.1 那么强大。

JScript 的再次更新出现在 IE4 中的 JScript 3.0（2.0 版是在 Microsoft Internet Information Server 3.0 中发布的，但从未包含在浏览器中）。微软发新闻稿称 JScript 3.0 是世界上第一门真正兼容 Ecma 标准的脚本语言。当时 ECMA-262 还没制定完成，因此 JScript 3.0 遭受了与 JavaScript 1.2 同样的命运，它同样没有遵守最终的 ECMAScript 标准。

网景又在 Netscape Navigator 4.06 中将其 JavaScript 版本升级到 1.3，因此做到了与 ECMA-262 第 1 版完全兼容。JavaScript 1.3 增加了对 Unicode 标准的支持，并做到了所有对象都与平台无关，同时保留了 JavaScript 1.2 所有的特性。

后来，当网景以 Mozilla 项目的名义向公众发布其源代码时，人们都期待 Netscape Navigator 5 中会包含 JavaScript 1.4。可是，一个完全重新设计网景代码的激进决定导致了人们的希望落空。JavaScript 1.4 只在 Netscape Enterprise Server 中作为服务器端语言发布了，从来就没有进入浏览器。

到了 2008 年，五大浏览器（IE、Firefox、Safari、Chrome 和 Opera）全部兼容 ECMA-262 第 3 版。IE8 率先实现 ECMA-262 第 5 版，并在 IE9 中完整支持。Firefox 4 很快也做到了。下表列出了主要的浏览器版本对 ECMAScript 的支持情况。

| 浏览器                        | ECMAScript 符合性 |
| ----------------------------- | ----------------- |
| Netscape Navigator 2          | -                 |
| Netscape Navigator 3 -        | -                 |
| Netscape Navigator 4~4.05     | -                 |
| Netscape Navigator 4.06~4.79  | 第 1 版           |
| Netscape 6+（Mozilla 0.6.0+） | 第 3 版           |
| IE3                           | -                 |
| IE4                           | -                 |
| IE5                           | 第 1 版           |
| IE5.5~8                       | 第 3 版           |
| IE9                           | 第 5 版（部分）   |
| IE10~11                       | 第 5 版           |
| Edge 12+                      | 第 6 版           |
| Opera 6~7.1                   | 第 2 版           |
| Opera 7.2+                    | 第 3 版           |
| Opera 15~28                   | 第 5 版           |
| Opera 29~35                   | 第 6 版（部分）   |
| Opera 36+                     | 第 6 版           |
| Safari 1~2.0.x                | 第 3 版（部分）   |
| Safari 3.1~5.1                | 第 5 版（部分）   |
| Safari 6~8                    | 第 5 版           |
| Safari 9+                     | 第 6 版           |
| iOS Safari 3.2~5.1            | 第 5 版（部分）   |
| iOS Safari 6~8.4              | 第 5 版           |
| iOS Safari 9.2+               | 第 6 版           |
| Chrome 1~3                    | 第 3 版           |
| Chrome 4~22                   | 第 5 版（部分）   |
| Chrome 23+                    | 第 5 版           |
| Chrome 42~48                  | 第 6 版（部分）   |
| Chrome 49+                    | 第 6 版           |
| Firefox 1~2                   | 第 3 版           |
| Firefox 3.0.x~20              | 第 5 版（部分）   |
| Firefox 21~44                 | 第 5 版           |
| Firefox 45+                   | 第 6 版           |

### 1.2.2. DOM

文档对象模型（DOM，Document Object Model）是一个应用编程接口（API），用于在 HTML 中使用扩展的 XML。DOM 将整个页面抽象为一组分层节点。HTML 或 XML 页面的每个组成部分都是一种节点，包含不同的数据。比如下面的 HTML 页面：

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

这些代码通过 DOM 可以表示为一组分层节点，如下图所示：

![1-2-DOM](illustrations/1-2-DOM.png)

DOM 通过创建表示文档的树，让开发者可以随心所欲地控制网页的内容和结构。使用 DOM API， 可以轻松地删除、添加、替换、修改节点。

1. **为什么 DOM 是必需的**

在 IE4 和 Netscape Navigator 4 支持不同形式的动态 HTML（DHTML）的情况下，开发者首先可以做到不刷新页面而修改页面外观和内容。这代表了 Web 技术的一个巨大进步，但也暴露了很大的问题。由于网景和微软采用不同思路开发 DHTML，开发者写一个 HTML 页面就可以在任何浏览器中运行的好日子就此终结。

为了保持 Web 跨平台的本性，必须要做点什么。人们担心如果无法控制网景和微软各行其是，那么 Web 就会发生分裂，导致人们面向浏览器开发网页。就在这时，万维网联盟（W3C，World Wide Web Consortium）开始了制定 DOM 标准的进程。

2. **DOM 级别**

1998 年 10 月，DOM Level 1 成为 W3C 的推荐标准。这个规范由两个模块组成：DOM Core 和 DOM HTML。前者提供了一种映射 XML 文档，从而方便访问和操作文档任意部分的方式；后者扩展了前者，并增加了特定于 HTML 的对象和方法。

DOM Level 1 的目标是映射文档结构，而 DOM Level 2 的目标则宽泛得多。这个对最初 DOM 的扩展增加了对（DHTML 早就支持的）鼠标和用户界面事件、范围、遍历（迭代 DOM 节点的方法）的支持，而且通过对象接口支持了层叠样式表（CSS）。另外，DOM Level 1 中的 DOM Core 也被扩展以包含对 XML 命名空间的支持。

DOM Level 2 新增了以下模块，以支持新的接口：

- DOM 视图：描述追踪文档不同视图（如应用 CSS 样式前后的文档）的接口。
- DOM 事件：描述事件及事件处理的接口。
- DOM 样式：描述处理元素 CSS 样式的接口。
- DOM 遍历和范围：描述遍历和操作 DOM 树的接口。

DOM Level 3 进一步扩展了 DOM，增加了以统一的方式加载和保存文档的方法（包含在一个叫 DOM Load and Save 的新模块中），还有验证文档的方法（DOM Validation）。在 Level 3 中，DOM Core 经过扩展支持了所有 XML 1.0 的特性，包括 XML Infoset、XPath 和 XML Base。

目前，W3C 不再按照 Level 来维护 DOM 了，而是作为 DOM Living Standard 来维护，其快照称为 DOM4。DOM4 新增的内容包括替代 Mutation Events 的 Mutation Observers。

3. **其他 DOM**

除了 DOM Core 和 DOM HTML 接口，有些其他语言也发布了自己的 DOM 标准。下面列出的语言是基于 XML 的，每一种都增加了该语言独有的 DOM 方法和接口：

- 可伸缩矢量图（SVG，Scalable Vector Graphics）
- 数学标记语言（MathML，Mathematical Markup Language）
- 同步多媒体集成语言（SMIL，Synchronized Multimedia Integration Language）

此外，还有一些语言开发了自己的 DOM 实现，比如 Mozilla 的 XML 用户界面语言（XUL，XML User Interface Language）。不过，只有前面列表中的语言是 W3C 推荐标准。

4. **Web 浏览器对 DOM 的支持情况**

DOM 标准在 Web 浏览器实现它之前就已经作为标准发布了。IE 在第 5 版中尝试支持 DOM，但直到 5.5 版才开始真正支持，该版本实现了 DOM Level 1 的大部分。IE 在第 6 版和第 7 版中都没有实现新特性，第 8 版中修复了一些问题。

网景在 Netscape 6（Mozilla 0.6.0）之前都不支持 DOM。Netscape 7 之后，Mozilla 把开发资源转移到开发 Firefox 浏览器上。Firefox 3+支持全部的 Level 1、几乎全部的 Level 2，以及 Level 3 的某些部分。（Mozilla 开发团队的目标是打造百分之百兼容标准的浏览器，他们的工作也得到了应有的回报。）

| 浏览器                        | DOM 兼容                                      |
| ----------------------------- | --------------------------------------------- |
| Netscape Navigator 1~4.x      | -                                             |
| Netscape 6+（Mozilla 0.6.0+） | Level 1、Level 2（几乎全部）、Level 3（部分） |
| IE2~4.x                       | -                                             |
| IE5                           | Level 1（很少）                               |
| IE5.5~8                       | Level 1（几乎全部）                           |
| IE9+                          | Level 1、Level 2、Level 3                     |
| Edge                          | Level 1、Level 2、Level 3                     |
| Opera 1~6                     | -                                             |
| Opera 7~8.x                   | Level 1（几乎全部）、Level 2（部分）          |
| Opera 9~9.9                   | Level 1、Level 2（几乎全部）、Level 3（部分） |
| Opera 10+                     | Level 1、Level 2、Level 3（部分）             |
| Safari 1.0.x                  | Level 1                                       |
| Safari 2+                     | Level 1、Level 2（部分）、Level 3（部分）     |
| iOS Safari 3.2+               | Level 1、Level 2（部分）、Level 3（部分）     |
| Chrome 1+                     | Level 1、Level 2（部分）、Level 3（部分）     |
| Firefox 1+                    | Level 1、Level 2（部分）、Level 3（部分）     |

### 1.2.3. BOM

IE3 和 Netscape Navigator 3 提供了浏览器对象模型（BOM） API，用于支持访问和操作浏览器的窗口。使用 BOM，开发者可以操控浏览器显示页面之外的部分。而 BOM 真正独一无二的地方，当然也是问题最多的地方，就是它是唯一一个没有相关标准的 JavaScript 实现。HTML5 改变了这个局面，这个版本的 HTML 以正式规范的形式涵盖了尽可能多的 BOM 特性。由于 HTML5 的出现，之前很多与 BOM 有关的问题都迎刃而解了。

总体来说，BOM 主要针对浏览器窗口和子窗口（frame），不过人们通常会把任何特定于浏览器的扩展都归在 BOM 的范畴内。比如，下面就是这样一些扩展：

- 弹出新浏览器窗口的能力；
- 移动、缩放和关闭浏览器窗口的能力；
- navigator 对象，提供关于浏览器的详尽信息；
- location 对象，提供浏览器加载页面的详尽信息；
- screen 对象，提供关于用户屏幕分辨率的详尽信息；
- performance 对象，提供浏览器内存占用、导航行为和时间统计的详尽信息；
- 对 cookie 的支持；
- 其他自定义对象，如 XMLHttpRequest 和 IE 的 ActiveXObject。

因为在很长时间内都没有标准，所以每个浏览器实现的都是自己的 BOM。有一些所谓的事实标准， 比如对于 window 对象和 navigator 对象，每个浏览器都会给它们定义自己的属性和方法。现在有了 HTML5，BOM 的实现细节应该会日趋一致。关于 BOM，本书会在第 12 章再专门详细介绍。

## 1.3. JavaScript 版本

作为网景的继承者，Mozilla 是唯一仍在延续最初 JavaScript 版本编号的浏览器厂商。当初网景在将其源代码开源时（项目名为 Mozilla Project），JavaScript 在其浏览器中最后的版本是 1.3。（前面提到过，1.4 版是专门为服务器实现的。）因为 Mozilla Foundation 在持续开发 JavaScript，为它增加新特性、关键字和语法，所以 JavaScript 的版本号也在不断递增。下表展示了 Netscape/Mozilla 浏览器发布的历代 JavaScript 版本。

| 浏览器                        | JavaScript 版本 |
| ----------------------------- | --------------- |
| Netscape Navigator 2          | 1.0             |
| Netscape Navigator 3          | 1.1             |
| Netscape Navigator 4          | 1.2             |
| Netscape Navigator 4.06       | 1.3             |
| Netscape 6+（Mozilla 0.6.0+） | 1.5             |
| Firefox 1                     | 1.5             |
| Firefox 1.5                   | 1.6             |
| Firefox 2                     | 1.7             |
| Firefox 3                     | 1.8             |
| Firefox 3.5                   | 1.8.1           |
| Firefox 3.6                   | 1.8.2           |
| Firefox 4                     | 1.8.5           |

这种版本编号方式是根据 Firefox 4 要发布 JavaScript 2.0 决定的，在此之前版本号的每次递增，反映的是 JavaScript 实现逐渐接近 2.0 建议。虽然这是最初的计划，但 JavaScript 的发展让这个计划变得不可能。JavaScript 2.0 作为一个目标已经不存在了，而这种版本号编排方式在 Firefox 4 发布后就终止了。

# 2. HTML 中的 JavaScript

本章内容:

- 使用`<script>`元素
- 行内脚本与外部脚本的比较
- 文档模式对 JavaScript 有什么影响
- 确保 JavaScript 不可用时的用户体验

将 JavaScript 引入网页，首先要解决它与网页的主导语言 HTML 的关系问题。在 JavaScript 早期，网景公司的工作人员希望在将 JavaScript 引入 HTML 页面的同时，不会导致页面在其他浏览器中渲染出问题。通过反复试错和讨论，他们最终做出了一些决定，并达成了向网页中引入通用脚本能力的共识。当初他们的很多工作得到了保留，并且最终形成了 HTML 规范。

## 2.1. `<script>` 元素

将 JavaScript 插入 HTML 的主要方法是使用 `<script>` 元素。这个元素是由网景公司创造出来，并最早在 Netscape Navigator 2 中实现的。后来，这个元素被正式加入到 HTML 规范。`<script>` 元素有下列 8 个属性：

- async：可选。表示应该立即开始下载脚本，但不能阻止其他页面动作，比如下载资源或等待其他脚本加载。只对外部脚本文件有效。
- charset：可选。使用 src 属性指定的代码字符集。这个属性很少使用，因为大多数浏览器不在乎它的值。
- crossorigin：可选。配置相关请求的 CORS（跨源资源共享）设置。默认不使用 CORS。crossorigin= "anonymous" 配置文件请求不必设置凭据标志。crossorigin="use-credentials"设置凭据标志，意味着出站请求会包含凭据。
- defer：可选。表示脚本可以延迟到文档完全被解析和显示之后再执行。只对外部脚本文件有效。在 IE7 及更早的版本中，对行内脚本也可以指定这个属性。
- integrity：可选。允许比对接收到的资源和指定的加密签名以验证子资源完整性（SRI， Subresource Integrity）。如果接收到的资源的签名与这个属性指定的签名不匹配，则页面会报错，脚本不会执行。这个属性可以用于确保内容分发网络（CDN，Content Delivery Network）不会提供恶意内容。
- language：废弃。最初用于表示代码块中的脚本语言（如"JavaScript"、"JavaScript 1.2"或"VBScript"）。大多数浏览器都会忽略这个属性，不应该再使用它。
- src：可选。表示包含要执行的代码的外部文件。
- type：可选。代替 language，表示代码块中脚本语言的内容类型（也称 MIME 类型）。按照惯例，这个值始终都是"text/javascript"，尽管"text/javascript"和"text/ecmascript" 都已经废弃了。JavaScript 文件的 MIME 类型通常是"application/x-javascript"，不过给 type 属性这个值有可能导致脚本被忽略。在非 IE 的浏览器中有效的其他值还有"application/javascript"和"application/ecmascript"。如果这个值是 module，则代码会被当成 ES6 模块，而且只有这时候代码中才能出现 import 和 export 关键字。

使用 `<script>` 的方式有两种：通过它直接在网页中嵌入 JavaScript 代码，以及通过它在网页中包含外部 JavaScript 文件。

要嵌入行内 JavaScript 代码，直接把代码放在`<script>`元素中就行：

```html
<script>
  function sayHi() {
    console.log("Hi!");
  }
</script>
```

包含在`<script>`内的代码会被从上到下解释。在上面的例子中，被解释的是一个函数定义，并且该函数会被保存在解释器环境中。在`<script>`元素中的代码被计算完成之前，页面的其余内容不会被加载，也不会被显示。

在使用行内 JavaScript 代码时，要注意代码中不能出现字符串`</script>`。比如，下面的代码会导致浏览器报错：

```html
<script>
  function sayScript() {
    console.log("</script>");
  }
</script>
```

浏览器解析行内脚本的方式决定了它在看到字符串`</script>`时，会将其当成结束的`</script>`标签。想避免这个问题，只需要转义字符“\”即可：

```html
<script>
  function sayScript() {
    console.log("<\/script>");
  }
</script>
```

这样修改之后，代码就可以被浏览器完全解释，不会导致任何错误。

要包含外部文件中的 JavaScript，就必须使用 src 属性。这个属性的值是一个 URL，指向包含 JavaScript 代码的文件，比如：

```html
<script src="example.js"></script>
```

这个例子在页面中加载了一个名为 example.js 的外部文件。文件本身只需包含要放在`<script>`的起始及结束标签中间的 JavaScript 代码。与解释行内 JavaScript 一样，在解释外部 JavaScript 文件时，页面也会阻塞。（阻塞时间也包含下载文件的时间。）在 XHTML 文档中，可以忽略结束标签，比如：

```html
<script src="example.js" />
```

以上语法不能在 HTML 文件中使用，因为它是无效的 HTML，有些浏览器不能正常处理，比如 IE。

另外，使用了 src 属性的`<script>`元素不应该再在`<script`>和`</script>`标签中再包含其他 JavaScript 代码。如果两者都提供的话，则浏览器只会下载并执行脚本文件，从而忽略行内代码。

`<script>`元素的一个最为强大、同时也备受争议的特性是，它可以包含来自外部域的 JavaScript 文件。跟`<img>`元素很像，`<script>`元素的 src 属性可以是一个完整的 URL，而且这个 URL 指向的资源可以跟包含它的 HTML 页面不在同一个域中，比如这个例子：

```html
<script src="http://www.somewhere.com/afile.js"></script>
```

浏览器在解析这个资源时，会向 src 属性指定的路径发送一个 GET 请求，以取得相应资源，假定是一个 JavaScript 文件。这个初始的请求不受浏览器同源策略限制，但返回并被执行的 JavaScript 则受限制。当然，这个请求仍然受父页面 HTTP/HTTPS 协议的限制。

来自外部域的代码会被当成加载它的页面的一部分来加载和解释。这个能力可以让我们通过不同的域分发 JavaScript。不过，引用了放在别人服务器上的 JavaScript 文件时要格外小心，因为恶意的程序员随时可能替换这个文件。在包含外部域的 JavaScript 文件时，要确保该域是自己所有的，或者该域是一个可信的来源。`<script>`标签的 integrity 属性是防范这种问题的一个武器，但这个属性也不是所有浏览器都支持。

不管包含的是什么代码，浏览器都会按照`<script>`在页面中出现的顺序依次解释它们，前提是它们没有使用 defer 和 async 属性。第二个`<script>`元素的代码必须在第一个`<script>`元素的代码解释完毕才能开始解释，第三个则必须等第二个解释完，以此类推。

### 2.1.1. 标签位置

过去，所有`<script>`元素都被放在页面的`<head>`标签内，如下面的例子所示：

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Example HTML Page</title>
    <script src="example1.js"></script>
    <script src="example2.js"></script>
  </head>
  <body>
    <!-- 这里是页面内容 -->
  </body>
</html>
```

这种做法的主要目的是把外部的 CSS 和 JavaScript 文件都集中放到一起。不过，把所有 JavaScript 文件都放在`<head>`里，也就意味着必须把所有 JavaScript 代码都下载、解析和解释完成后，才能开始渲染页面（页面在浏览器解析到`<body>`的起始标签时开始渲染）。对于需要很多 JavaScript 的页面，这会导致页面渲染的明显延迟，在此期间浏览器窗口完全空白。为解决这个问题，现代 Web 应用程序通常将所有 JavaScript 引用放在`<body>`元素中的页面内容后面，如下面的例子所示：

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Example HTML Page</title>
  </head>
  <body>
    <!-- 这里是页面内容 -->
    <script src="example1.js"></script>
    <script src="example2.js"></script>
  </body>
</html>
```

这样一来，页面会在处理 JavaScript 代码之前完全渲染页面。用户会感觉页面加载更快了，因为浏览器显示空白页面的时间短了。

### 2.1.2. 推迟执行脚本

HTML 4.01 为`<script>`元素定义了一个叫 defer 的属性。这个属性表示脚本在执行的时候不会改变页面的结构。也就是说，脚本会被延迟到整个页面都解析完毕后再运行。因此，在`<script>`元素上设置 defer 属性，相当于告诉浏览器立即下载，但延迟执行。

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Example HTML Page</title>
    <script defer src="example1.js"></script>
    <script defer src="example2.js"></script>
  </head>
  <body>
    <!-- 这里是页面内容 -->
  </body>
</html>
```

虽然这个例子中的`<script>`元素包含在页面的`<head>`中，但它们会在浏览器解析到结束的`</html>`标签后才会执行。HTML5 规范要求脚本应该按照它们出现的顺序执行，因此第一个推迟的脚本会在第二个推迟的脚本之前执行，而且两者都会在 DOMContentLoaded 事件之前执行（关于事件，请参考第 17 章）。不过在实际当中，推迟执行的脚本不一定总会按顺序执行或者在 DOMContentLoaded 事件之前执行，因此最好只包含一个这样的脚本。

如前所述，defer 属性只对外部脚本文件才有效。这是 HTML5 中明确规定的，因此支持 HTML5 的浏览器会忽略行内脚本的 defer 属性。IE4~7 展示出的都是旧的行为，IE8 及更高版本则支持 HTML5 定义的行为。

对 defer 属性的支持是从 IE4、Firefox 3.5、Safari 5 和 Chrome 7 开始的。其他所有浏览器则会忽略这个属性，按照通常的做法来处理脚本。考虑到这一点，还是把要推迟执行的脚本放在页面底部比较好。

### 2.1.3. 异步执行脚本

HTML5 为`<script>`元素定义了 async 属性。从改变脚本处理方式上看，async 属性与 defer 类似。当然，它们两者也都只适用于外部脚本，都会告诉浏览器立即开始下载。不过，与 defer 不同的是，标记为 async 的脚本并不保证能按照它们出现的次序执行，比如：

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Example HTML Page</title>
    <script async src="example1.js"></script>
    <script async src="example2.js"></script>
  </head>
  <body>
    <!-- 这里是页面内容 -->
  </body>
</html>
```

在这个例子中，第二个脚本可能先于第一个脚本执行。因此，重点在于它们之间没有依赖关系。给脚本添加 async 属性的目的是告诉浏览器，不必等脚本下载和执行完后再加载页面，同样也不必等到该异步脚本下载和执行后再加载其他脚本。正因为如此，异步脚本不应该在加载期间修改 DOM。

异步脚本保证会在页面的 load 事件前执行，但可能会在 DOMContentLoaded（参见第 17 章）之前或之后。Firefox 3.6、Safari 5 和 Chrome 7 支持异步脚本。使用 async 也会告诉页面你不会使用 document.write，不过好的 Web 开发实践根本就不推荐使用这个方法。

### 2.1.4. 动态加载脚本

除了`<script>`标签，还有其他方式可以加载脚本。因为 JavaScript 可以使用 DOM API，所以通过向 DOM 中动态添加 script 元素同样可以加载指定的脚本。只要创建一个 script 元素并将其添加到 DOM 即可。

```js
let script = document.createElement("script");
script.src = "gibberish.js";
document.head.appendChild(script);
```

当然，在把 HTML 元素添加到 DOM 且执行到这段代码之前不会发送请求。默认情况下，以这种方式创建的`<script>`元素是以异步方式加载的，相当于添加了 async 属性。不过这样做可能会有问题，因为所有浏览器都支持 createElement()方法，但不是所有浏览器都支持 async 属性。因此，如果要统一动态脚本的加载行为，可以明确将其设置为同步加载：

```js
let script = document.createElement("script");
script.src = "gibberish.js";
script.async = false;
document.head.appendChild(script);
```

以这种方式获取的资源对浏览器预加载器是不可见的。这会严重影响它们在资源获取队列中的优先级。根据应用程序的工作方式以及怎么使用，这种方式可能会严重影响性能。要想让预加载器知道这些动态请求文件的存在，可以在文档头部显式声明它们：

```html
<link rel="preload" href="gibberish.js" />
```

## 2.2. 行内代码与外部文件

虽然可以直接在 HTML 文件中嵌入 JavaScript 代码，但通常认为最佳实践是尽可能将 JavaScript 代码放在外部文件中。不过这个最佳实践并不是明确的强制性规则。推荐使用外部文件的理由如下。

- **可维护性**。JavaScript 代码如果分散到很多 HTML 页面，会导致维护困难。而用一个目录保存所有 JavaScript 文件，则更容易维护，这样开发者就可以独立于使用它们的 HTML 页面来编辑代码。
- **缓存**。浏览器会根据特定的设置缓存所有外部链接的 JavaScript 文件，这意味着如果两个页面都用到同一个文件，则该文件只需下载一次。这最终意味着页面加载更快。
- **适应未来**。通过把 JavaScript 放到外部文件中，就不必考虑用 XHTML 或前面提到的注释黑科技。包含外部 JavaScript 文件的语法在 HTML 和 XHTML 中是一样的。

在配置浏览器请求外部文件时，要重点考虑的一点是它们会占用多少带宽。在 SPDY/HTTP2 中，预请求的消耗已显著降低，以轻量、独立 JavaScript 组件形式向客户端送达脚本更具优势。

比如，第一个页面包含如下脚本：

```html
<script src="mainA.js"></script>
<script src="component1.js"></script>
<script src="component2.js"></script>
<script src="component3.js"></script>
...
```

后续页面可能包含如下脚本：

```html
<script src="mainB.js"></script>
<script src="component3.js"></script>
<script src="component4.js"></script>
<script src="component5.js"></script>
...
```

在初次请求时，如果浏览器支持 SPDY/HTTP2，就可以从同一个地方取得一批文件，并将它们逐个放到浏览器缓存中。从浏览器角度看，通过 SPDY/HTTP2 获取所有这些独立的资源与获取一个大 JavaScript 文件的延迟差不多。

在第二个页面请求时，由于你已经把应用程序切割成了轻量可缓存的文件，第二个页面也依赖的某些组件此时已经存在于浏览器缓存中了。

当然，这里假设浏览器支持 SPDY/HTTP2，只有比较新的浏览器才满足。如果你还想支持那些比较老的浏览器，可能还是用一个大文件更合适。

## 2.3. 文档模式

IE5.5 发明了文档模式的概念，即可以使用 doctype 切换文档模式。最初的文档模式有两种：**混杂模式(quirks mode)** 和 **标准模式(standards mode)**。前者让 IE 像 IE5 一样（支持一些非标准的特性），后者让 IE 具有兼容标准的行为。虽然这两种模式的主要区别只体现在通过 CSS 渲染的内容方面，但对 JavaScript 也有一些关联影响，或称为副作用。本书会经常提到这些副作用。

IE 初次支持文档模式切换以后，其他浏览器也跟着实现了。随着浏览器的普遍实现，又出现了第三种文档模式：**准标准模式(almost standards mode)**。这种模式下的浏览器支持很多标准的特性，但是没有标准规定得那么严格。主要区别在于如何对待图片元素周围的空白（在表格中使用图片时最明显）。

混杂模式在所有浏览器中都以省略文档开头的 doctype 声明作为开关。这种约定并不合理，因为混杂模式在不同浏览器中的差异非常大，不使用黑科技基本上就没有浏览器一致性可言。

标准模式通过下列几种文档类型声明开启：

```html
<!-- HTML 4.01 Strict -->
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
<!-- XHTML 1.0 Strict -->
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<!-- HTML5 -->
<!DOCTYPE html>
```

准标准模式通过过渡性文档类型（Transitional）和框架集文档类型（Frameset）来触发：

```html
<!-- HTML 4.01 Transitional -->
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<!-- HTML 4.01 Frameset -->
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Frameset//EN" "http://www.w3.org/TR/html4/frameset.dtd">
<!-- XHTML 1.0 Transitional -->
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<!-- XHTML 1.0 Frameset -->
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Frameset//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-frameset.dtd">
```

准标准模式与标准模式非常接近，很少需要区分。人们在说到“标准模式”时，可能指其中任何一个。而对文档模式的检测（本书后面会讨论）也不会区分它们。本书后面所说的标准模式，指的就是除混杂模式以外的模式。

## 2.4. `<noscript>` 元素

针对早期浏览器不支持 JavaScript 的问题，需要一个页面优雅降级的处理方案。最终，`<noscript>`元素出现，被用于给不支持 JavaScript 的浏览器提供替代内容。虽然如今的浏览器已经 100%支持 JavaScript，但对于禁用 JavaScript 的浏览器来说，这个元素仍然有它的用处。

`<noscript>`元素可以包含任何可以出现在`<body>`中的 HTML 元素，`<script>`除外。在下列两种情况下，浏览器将显示包含在`<noscript>`中的内容：

- 浏览器不支持脚本；
- 浏览器对脚本的支持被关闭。

任何一个条件被满足，包含在`<noscript>`中的内容就会被渲染。否则，浏览器不会渲染`<noscript>`中的内容。

下面是一个例子：

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Example HTML Page</title>
    <script defer="defer" src="example1.js"></script>
    <script defer="defer" src="example2.js"></script>
  </head>
  <body>
    <noscript>
      <p>This page requires a JavaScript-enabled browser.</p>
    </noscript>
  </body>
</html>
```

# 3. 语言基础

本章内容：

- 语法
- 数据类型
- 流控制语句
- 理解函数

任何语言的核心所描述的都是这门语言在最基本的层面上如何工作，涉及语法、操作符、数据类型以及内置功能，在此基础之上才可以构建复杂的解决方案。如前所述，ECMA-262 以一个名为 ECMAScript 的伪语言的形式，定义了 JavaScript 的所有这些方面。

ECMA-262 第 5 版（ES5）定义的 ECMAScript，是目前为止实现得最为广泛（即受浏览器支持最好）的一个版本。第 6 版（ES6）在浏览器中的实现（即受支持）程度次之。到 2017 年底，大多数主流浏览器几乎或全部实现了这一版的规范。为此，本章接下来的内容主要基于 ECMAScript 第 6 版。

## 3.1. 语法

ECMAScript 的语法很大程度上借鉴了 C 语言和其他类 C 语言，如 Java 和 Perl。熟悉这些语言的开发者，应该很容易理解 ECMAScript 宽松的语法。

### 3.1.1. 区分大小写

首先要知道的是，ECMAScript 中一切都区分大小写。无论是变量、函数名还是操作符，都区分大小写。换句话说，变量 test 和变量 Test 是两个不同的变量。类似地，typeof 不能作为函数名，因为它是一个关键字（后面会介绍）。但 Typeof 是一个完全有效的函数名。

### 3.1.2. 标识符

所谓标识符，就是变量、函数、属性或函数参数的名称。标识符可以由一或多个下列字符组成：

- 第一个字符必须是一个字母、下划线（\_）或美元符号（$）；
- 剩下的其他字符可以是字母、下划线、美元符号或数字。

按照惯例，ECMAScript 标识符使用驼峰大小写形式，即第一个单词的首字母小写，后面每个单词的首字母大写，如：

```js
firstSecond;
myCar;
doSomethingImportant;
```

虽然这种写法并不是强制性的，但因为这种形式跟 ECMAScript 内置函数和对象的命名方式一致，所以算是最佳实践。

### 3.1.3. 注释

ECMAScript 采用 C 语言风格的注释，包括单行注释和块注释。单行注释以两个斜杠字符开头，如：

```js
// 单行注释
```

多行注释以一个斜杠和一个星号（/\*）开头，以它们的反向组合（\*/）结尾，如：

```js
/* 这是多行
注释 */
```

### 3.1.4. 严格模式

ECMAScript 5 增加了严格模式（strict mode）的概念。严格模式是一种不同的 JavaScript 解析和执行模型，ECMAScript 3 的一些不规范写法在这种模式下会被处理，对于不安全的活动将抛出错误。要对整个脚本启用严格模式，在脚本开头加上这一行：

```js
"use strict";
```

虽然看起来像个没有赋值给任何变量的字符串，但它其实是一个预处理指令。任何支持的 JavaScript 引擎看到它都会切换到严格模式。选择这种语法形式的目的是不破坏 ECMAScript 3 语法。

也可以单独指定一个函数在严格模式下执行，只要把这个预处理指令放到函数体开头即可：

```js
function doSomething() {
  "use strict";
  // 函数体
}
```

严格模式会影响 JavaScript 执行的很多方面，因此本书在用到它时会明确指出来。所有现代浏览器都支持严格模式。

### 3.1.5. 语句

ECMAScript 中的语句以分号结尾。省略分号意味着由解析器确定语句在哪里结尾，如下面的例子所示：

```js
let sum = a + b; // 没有分号也有效，但不推荐
let diff = a - b; // 加分号有效，推荐
```

即使语句末尾的分号不是必需的，也应该加上。记着加分号有助于防止省略造成的问题，比如可以避免输入内容不完整。此外，加分号也便于开发者通过删除空行来压缩代码（如果没有结尾的分号，只删除空行，则会导致语法错误）。加分号也有助于在某些情况下提升性能，因为解析器会尝试在合适的位置补上分号以纠正语法错误。

多条语句可以合并到一个 C 语言风格的代码块中。代码块由一个左花括号（{）标识开始，一个右花括号（}）标识结束：

```js
if (test) {
  test = false;
  console.log(test);
}
```

if 之类的控制语句只在执行多条语句时要求必须有代码块。不过，最佳实践是始终在控制语句中使用代码块，即使要执行的只有一条语句，如下例所示：

```js
// 有效，但容易导致错误，应该避免
if (test) console.log(test);
// 推荐
if (test) {
  console.log(test);
}
```

在控制语句中使用代码块可以让内容更清晰，在需要修改代码时也可以减少出错的可能性。

## 3.2. 关键字和保留字

ECMA-262 描述了一组保留的 **关键字**，这些关键字有特殊用途，比如表示控制语句的开始和结束，或者执行特定的操作。按照规定，保留的关键字不能用作标识符或属性名。ECMA-262 第 6 版规定的所有关键字如下：

```js
break do in typeof
case else instanceof var
catch export new void
class extends return while
const finally super with
continue for switch yield
debugger function this
default if throw
delete import try
```

规范中也描述了一组未来的保留字，同样不能用作标识符或属性名。虽然保留字在语言中没有特定用途，但它们是保留给将来做关键字用的。

以下是 ECMA-262 第 6 版为将来保留的所有词汇。

始终保留：

```js
enum;
```

严格模式下保留:

```js
implements package public
interface protected static
let private
```

模块代码中保留:

```js
await
```

这些词汇不能用作标识符，但现在还可以用作对象的属性名。一般来说，最好还是不要使用关键字和保留字作为标识符和属性名，以确保兼容过去和未来的 ECMAScript 版本。

## 3.3. 变量

ECMAScript 变量是松散类型的，意思是变量可以用于保存任何类型的数据。每个变量只不过是一个用于保存任意值的命名占位符。有 3 个关键字可以声明变量：var、const 和 let。其中，var 在 ECMAScript 的所有版本中都可以使用，而 const 和 let 只能在 ECMAScript 6 及更晚的版本中使用。

### 3.3.1. var 关键字

要定义变量，可以使用 var 操作符（注意 var 是一个关键字），后跟变量名（即标识符，如前所述）：

```js
var message;
```

这行代码定义了一个名为 message 的变量，可以用它保存任何类型的值。（不初始化的情况下，变量会保存一个特殊值 undefined，下一节讨论数据类型时会谈到。）ECMAScript 实现变量初始化，因此可以同时定义变量并设置它的值：

```js
var message = "hi";
```

这里，message 被定义为一个保存字符串值 hi 的变量。像这样初始化变量不会将它标识为字符串类型，只是一个简单的赋值而已。随后，不仅可以改变保存的值，也可以改变值的类型：

```js
var message = "hi";
message = 100; // 合法，但不推荐
```

在这个例子中，变量 message 首先被定义为一个保存字符串值 hi 的变量，然后又被重写为保存了数值 100。虽然不推荐改变变量保存值的类型，但这在 ECMAScript 中是完全有效的。

1. **var 声明作用域**

关键的问题在于，使用 var 操作符定义的变量会成为包含它的函数的局部变量。比如，使用 var 在一个函数内部定义一个变量，就意味着该变量将在函数退出时被销毁：

```js
function test() {
  var message = "hi"; // 局部变量
}
test();
console.log(message); // 出错！
```

这里，message 变量是在函数内部使用 var 定义的。函数叫 test()，调用它会创建这个变量并给它赋值。调用之后变量随即被销毁，因此示例中的最后一行会导致错误。不过，在函数内定义变量时省略 var 操作符，可以创建一个全局变量：

```js
function test() {
  message = "hi"; // 全局变量
}
test();
console.log(message); // "hi"
```

去掉之前的 var 操作符之后，message 就变成了全局变量。只要调用一次函数 test()，就会定义这个变量，并且可以在函数外部访问到。

虽然可以通过省略 var 操作符定义全局变量，但不推荐这么做。在局部作用域中定义的全局变量很难维护，也会造成困惑。这是因为不能一下子断定省略 var 是不是有意而为之。在严格模式下，如果像这样给未声明的变量赋值，则会导致抛出 ReferenceError。

如果需要定义多个变量，可以在一条语句中用逗号分隔每个变量（及可选的初始化）：

```js
var message = "hi",
  found = false,
  age = 29;
```

这里定义并初始化了 3 个变量。因为 ECMAScript 是松散类型的，所以使用不同数据类型初始化的变量可以用一条语句来声明。插入换行和空格缩进并不是必需的，但这样有利于阅读理解。

在严格模式下，不能定义名为 eval 和 arguments 的变量，否则会导致语法错误。

2. **声明提升**

使用 var 时，下面的代码不会报错。这是因为使用这个关键字声明的变量会自动提升到函数作用域顶部：

```js
function foo() {
  console.log(age);
  var age = 26;
}
foo(); // undefined
```

之所以不会报错，是因为 ECMAScript 运行时把它看成等价于如下代码：

```js
function foo() {
  var age;
  console.log(age);
  age = 26;
}
foo(); // undefined
```

这就是所谓的“提升”（hoist），也就是把所有变量声明都拉到函数作用域的顶部。此外，反复多次使用 var 声明同一个变量也没有问题：

```js
function foo() {
  var age = 16;
  var age = 26;
  var age = 36;
  console.log(age);
}
foo(); // 36
```

### 3.3.2. let 声明

let 跟 var 的作用差不多，但有着非常重要的区别。最明显的区别是，let 声明的范围是块作用域，而 var 声明的范围是函数作用域。

```js
if (true) {
  var name = "Matt";
  console.log(name); // Matt
}
console.log(name); // Matt
if (true) {
  let age = 26;
  console.log(age); // 26
}
console.log(age); // ReferenceError: age 没有定义
```

在这里，age 变量之所以不能在 if 块外部被引用，是因为它的作用域仅限于该块内部。块作用域是函数作用域的子集，因此适用于 var 的作用域限制同样也适用于 let。

let 也不允许同一个块作用域中出现冗余声明。这样会导致报错：

```js
var name;
var name;
let age;
let age; // SyntaxError；标识符age 已经声明过了
```

当然，JavaScript 引擎会记录用于变量声明的标识符及其所在的块作用域，因此嵌套使用相同的标识符不会报错，而这是因为同一个块中没有重复声明：

```js
var name = "Nicholas";
console.log(name); // 'Nicholas'
if (true) {
  var name = "Matt";
  console.log(name); // 'Matt'
}
let age = 30;
console.log(age); // 30
if (true) {
  let age = 26;
  console.log(age); // 26
}
```

对声明冗余报错不会因混用 let 和 var 而受影响。这两个关键字声明的并不是不同类型的变量，它们只是指出变量在相关作用域如何存在。

```js
var name;
let name; // SyntaxError
let age;
var age; // SyntaxError
```

1. **暂时性死区**

let 与 var 的另一个重要的区别，就是 let 声明的变量不会在作用域中被提升。

```js
// name 会被提升
console.log(name); // undefined
var name = "Matt";

// age 不会被提升
console.log(age); // ReferenceError：age 没有定义
let age = 26;
```

只要块级作用域内存在 let 命令，它所声明的变量就“绑定”（binding）这个区域，不再受外部的影响。

```js
let tmp = 123;

if (true) {
  tmp = "abc"; // ReferenceError
  let tmp;
}
```

上面代码中，存在全局变量 tmp，但是块级作用域内 let 又声明了一个局部变量 tmp，导致后者绑定这个块级作用域，所以在 let 声明变量前，对 tmp 赋值会报错。

ES6 明确规定，如果区块中存在 let 和 const 命令，这个区块对这些命令声明的变量，从一开始就形成了封闭作用域。凡是在声明之前就使用这些变量，就会报错。

总之，在代码块内，使用 let 命令声明变量之前，该变量都是不可用的。这在语法上，称为“暂时性死区”（temporal dead zone，简称 TDZ）。

```js
if (true) {
  // TDZ开始
  tmp = "abc"; // ReferenceError
  console.log(tmp); // ReferenceError

  let tmp; // TDZ结束
  console.log(tmp); // undefined

  tmp = 123;
  console.log(tmp); // 123
}
```

上面代码中，在 let 命令声明变量 tmp 之前，都属于变量 tmp 的“死区”。

“暂时性死区”也意味着 typeof 不再是一个百分之百安全的操作：

```js
console.log(typeof something); // undefined

console.log(typeof otherthing); // ReferenceError
let otherthing;
```

在没有 let 之前，typeof 运算符是百分之百安全的，永远不会报错。现在这一点不成立了。这样的设计是为了让大家养成良好的编程习惯，变量一定要在声明之后使用，否则就报错。

有些“死区”比较隐蔽，不太容易发现。

```js
function bar(x = y, y = 2) {
  return [x, y];
}

bar(); // 报错
```

上面代码中，调用 bar 函数之所以报错（某些实现可能不报错），是因为参数 x 默认值等于另一个参数 y，而此时 y 还没有声明，属于“死区”。如果 y 的默认值是 x，就不会报错，因为此时 x 已经声明了。

```js
function bar(x = 2, y = x) {
  return [x, y];
}
bar(); // [2, 2]
```

另外，下面的代码也会报错，与 var 的行为不同。

```js
// 不报错
var x = x;

// 报错
let x = x;
// ReferenceError: x is not defined
```

上面代码报错，也是因为暂时性死区。使用 let 声明变量时，只要变量在还没有声明完成前使用，就会报错。上面这行就属于这个情况，在变量 x 的声明语句还没有执行完成前，就去取 x 的值，导致报错“x 未定义”。

总之，暂时性死区的本质就是，只要一进入当前作用域，所要使用的变量就已经存在了，但是不可获取，只有等到声明变量的那一行代码出现，才可以获取和使用该变量

2. **全局声明**

与 var 关键字不同，使用 let 在全局作用域中声明的变量不会成为 window 对象的属性（var 声明的变量则会）。

```js
var name = "Matt";
console.log(window.name); // 'Matt'

let age = 26;
console.log(window.age); // undefined
```

不过，let 声明仍然是在全局作用域中发生的，相应变量会在页面的生命周期内存续。因此，为了避免 SyntaxError，必须确保页面不会重复声明同一个变量。

3. **条件声明**

在使用 var 声明变量时，由于声明会被提升，JavaScript 引擎会自动将多余的声明在作用域顶部合并为一个声明。因为 let 的作用域是块，所以不可能检查前面是否已经使用 let 声明过同名变量，同时也就不可能在没有声明的情况下声明它。

```html
<script>
  var name = "Nicholas";
  let age = 26;
</script>

<script>
  // 假设脚本不确定页面中是否已经声明了同名变量
  // 那它可以假设还没有声明过
  var name = "Matt";
  // 这里没问题，因为可以被作为一个提升声明来处理
  // 不需要检查之前是否声明过同名变量
  let age = 36;
  // 如果age 之前声明过，这里会报错
</script>
```

使用 try/catch 语句或 typeof 操作符也不能解决，因为条件块中 let 声明的作用域仅限于该块。

```html
<script>
  let name = "Nicholas";
  let age = 36;
</script>
<script>
  // 假设脚本不确定页面中是否已经声明了同名变量
  // 那它可以假设还没有声明过
  if (typeof name === "undefined") {
    let name;
  }
  // name 被限制在if {} 块的作用域内
  // 因此这个赋值形同全局赋值
  name = "Matt";
  try {
    console.log(age); // 如果age 没有声明过，则会报错
  } catch (error) {
    let age;
  }
  // age 被限制在catch {}块的作用域内
  // 因此这个赋值形同全局赋值
  age = 26;
</script>
```

为此，对于 let 这个新的 ES6 声明关键字，不能依赖条件声明模式。

4. **for 循环中的 let 声明**

在 let 出现之前，for 循环定义的迭代变量会渗透到循环体外部：

```js
for (var i = 0; i < 5; ++i) {
  // 循环逻辑
}
console.log(i); // 5
```

改成使用 let 之后，这个问题就消失了，因为迭代变量的作用域仅限于 for 循环块内部：

```js
for (let i = 0; i < 5; ++i) {
  // 循环逻辑
}
console.log(i); // ReferenceError: i 没有定义
```

在使用 var 的时候，最常见的问题就是对迭代变量的奇特声明和修改：

```js
for (var i = 0; i < 5; ++i) {
  setTimeout(() => console.log(i), 0);
}
// 你可能以为会输出0、1、2、3、4
// 实际上会输出5、5、5、5、5
```

之所以会这样，是因为在退出循环时，迭代变量保存的是导致循环退出的值：5。在之后执行超时逻辑时，所有的 i 都是同一个变量，因而输出的都是同一个最终值。

而在使用 let 声明迭代变量时，JavaScript 引擎在后台会为每个迭代循环声明一个新的迭代变量。每个 setTimeout 引用的都是不同的变量实例，所以 console.log 输出的是我们期望的值，也就是循环执行过程中每个迭代变量的值。

```js
for (let i = 0; i < 5; ++i) {
  setTimeout(() => console.log(i), 0);
}
// 会输出0、1、2、3、4
```

这种每次迭代声明一个独立变量实例的行为适用于所有风格的 for 循环，包括 for-in 和 for-of 循环。

### 3.3.3. const

const 的行为与 let 基本相同，唯一一个重要的区别是用它声明变量时必须同时初始化变量，且尝试修改 const 声明的变量会导致运行时错误。

```js
const age = 26;
age = 36; // TypeError: 给常量赋值
// const 也不允许重复声明
const name = "Matt";
const name = "Nicholas"; // SyntaxError
// const 声明的作用域也是块
const name = "Matt";
if (true) {
  const name = "Nicholas";
}
console.log(name); // Matt
```

const 声明的限制只适用于它指向的变量的引用。换句话说，如果 const 变量引用的是一个对象，那么修改这个对象内部的属性并不违反 const 的限制。

```js
const person = {};
person.name = "Matt"; // ok
```

JavaScript 引擎会为 for 循环中的 let 声明分别创建独立的变量实例，虽然 const 变量跟 let 变量很相似，但是不能用 const 来声明迭代变量（因为迭代变量会自增）：

```js
for (const i = 0; i < 10; ++i) {} // TypeError：给常量赋值
```

不过，如果你只想用 const 声明一个不会被修改的 for 循环变量，那也是可以的。也就是说，每次迭代只是创建一个新变量。这对 for-of 和 for-in 循环特别有意义：

```js
let i = 0;
for (const j = 7; i < 5; ++i) {
  console.log(j);
}
// 7, 7, 7, 7, 7
for (const key in { a: 1, b: 2 }) {
  console.log(key);
}
// a, b
for (const value of [1, 2, 3, 4, 5]) {
  console.log(value);
}
// 1, 2, 3, 4, 5
```

### 3.3.4. 声明风格与最佳实践

ECMAScript 6 增加 let 和 const 从客观上为这门语言更精确地声明作用域和语义提供了更好的支持。行为怪异的 var 所造成的各种问题，已经让 JavaScript 社区为之苦恼了很多年。随着这两个新关键字的出现，新的有助于提升代码质量的最佳实践也逐渐显现。

1. 不使用 var

有了 let 和 const，大多数开发者会发现自己不再需要 var 了。限制自己只使用 let 和 const 有助于提升代码质量，因为变量有了明确的作用域、声明位置，以及不变的值。

2. const 优先，let 次之

使用 const 声明可以让浏览器运行时强制保持变量不变，也可以让静态代码分析工具提前发现不合法的赋值操作。因此，很多开发者认为应该优先使用 const 来声明变量，只在提前知道未来会有修改时，再使用 let。这样可以让开发者更有信心地推断某些变量的值永远不会变，同时也能迅速发现因意外赋值导致的非预期行为。

## 3.4. 数据类型

ECMAScript 有 6 种简单数据类型（也称为 **原始类型**）：Undefined、Null、Boolean、Number、String 和 Symbol。Symbol（符号）是 ECMAScript 6 新增的。还有一种复杂数据类型叫 Object（对象）。Object 是一种无序名值对的集合。因为在 ECMAScript 中不能定义自己的数据类型，所有值都可以用上述 7 种数据类型之一来表示。只有 7 种数据类型似乎不足以表示全部数据。但 ECMAScript 的数据类型很灵活，一种数据类型可以当作多种数据类型来使用。

### 3.4.1. typeof 操作符

因为 ECMAScript 的类型系统是松散的，所以需要一种手段来确定任意变量的数据类型。typeof 操作符就是为此而生的。对一个值使用 typeof 操作符会返回下列字符串之一：

- "undefined"表示值未定义；
- "boolean"表示值为布尔值；
- "string"表示值为字符串；
- "number"表示值为数值；
- "object"表示值为对象（而不是函数）或 null；
- "function"表示值为函数；
- "symbol"表示值为符号。

下面是使用 typeof 操作符的例子：

```js
let message = "some string";
console.log(typeof message); // "string"
console.log(typeof message); // "string"
console.log(typeof 95); // "number"
```

在这个例子中，我们把一个变量（message）和一个数值字面量传给了 typeof 操作符。注意，因为 typeof 是一个操作符而不是函数，所以不需要参数（但可以使用参数）。

注意 typeof 在某些情况下返回的结果可能会让人费解，但技术上讲还是正确的。比如，调用 typeof null 返回的是"object"。这是因为特殊值 null 被认为是一个对空对象的引用。

注意 严格来讲，函数在 ECMAScript 中被认为是对象，并不代表一种数据类型。可是，函数也有自己特殊的属性。为此，就有必要通过 typeof 操作符来区分函数和其他对象。

### 3.4.2. Undefined 类型

Undefined 类型只有一个值，就是特殊值 undefined。当使用 var 或 let 声明了变量但没有初始化时，就相当于给变量赋予了 undefined 值：

```js
let message;
console.log(message == undefined); // true
```

在这个例子中，变量 message 在声明的时候并未初始化。而在比较它和 undefined 的字面值时，两者是相等的。这个例子等同于如下示例：

```js
let message = undefined;
console.log(message == undefined); // true
```

这里，变量 message 显式地以 undefined 来初始化。但这是不必要的，因为默认情况下，任何未经初始化的变量都会取得 undefined 值。

注意：一般来说，永远不用显式地给某个变量设置 undefined 值。字面值 undefined 主要用于比较，而且在 ECMA-262 第 3 版之前是不存在的。增加这个特殊值的目的就是为了正式明确空对象指针（null）和未初始化变量的区别。

注意，包含 undefined 值的变量跟未定义变量是有区别的。请看下面的例子：

```js
let message; // 这个变量被声明了，只是值为undefined

// 确保没有声明过这个变量
// let age

console.log(message); // "undefined"
console.log(age); // 报错
```

在上面的例子中，第一个 console.log 会指出变量 message 的值，即 "undefined"。而第二个 console.log 要输出一个未声明的变量 age 的值，因此会导致报错。对未声明的变量，只能执行一个有用的操作，就是对它调用 typeof。（对未声明的变量调用 delete 也不会报错，但这个操作没什么用，实际上在严格模式下会抛出错误。）

在对未初始化的变量调用 typeof 时，返回的结果是"undefined"，但对未声明的变量调用它时，返回的结果还是"undefined"，这就有点让人看不懂了。比如下面的例子：

```js
let message; // 这个变量被声明了，只是值为undefined

// 确保没有声明过这个变量
// let age

console.log(typeof message); // "undefined"
console.log(typeof age); // "undefined"
```

无论是声明还是未声明，typeof 返回的都是字符串"undefined"。逻辑上讲这是对的，因为虽然严格来讲这两个变量存在根本性差异，但它们都无法执行实际操作。

注意：即使未初始化的变量会被自动赋予 undefined 值，但我们仍然建议在声明变量的同时进行初始化。这样，当 typeof 返回"undefined"时，你就会知道那是因为给定的变量尚未声明，而不是声明了但未初始化。

要区别一个值是未声明还是未初始化，可以使用 try-catch，例如：

```js
// 确保没有声明过这个变量
// let age
if (typeof age == "undefined") {
  try {
    console.log(age); // 未初始化
  } catch (error) {
    console.log("age未声明！");
  }
}
```

undefined 是一个假值。因此，如果需要，可以用更简洁的方式检测它。不过要记住，也有很多其他可能的值同样是假值。所以一定要明确自己想检测的就是 undefined 这个字面值，而不仅仅是假值。

```js
let message; // 这个变量被声明了，只是值为undefined
// age 没有声明
if (message) {
  // 这个块不会执行
}
if (!message) {
  // 这个块会执行
}
if (age) {
  // 这里会报错
}
```

### 3.4.3. Null 类型

Null 类型同样只有一个值，即特殊值 null。逻辑上讲，null 值表示一个空对象指针，这也是给 typeof 传一个 null 会返回"object"的原因：

```js
let car = null;
console.log(typeof car); // "object"
```

在定义将来要保存对象值的变量时，建议使用 null 来初始化，不要使用其他值。这样，只要检查这个变量的值是不是 null 就可以知道这个变量是否在后来被重新赋予了一个对象的引用，比如：

```js
if (car != null) {
  // car 是一个对象的引用
}
```

undefined 值是由 null 值派生而来的，因此 ECMA-262 将它们定义为表面上相等，如下面的例子所示：

```js
console.log(null == undefined); // true
```

用等于操作符（==）比较 null 和 undefined 始终返回 true。但要注意，这个操作符会为了比较而转换它的操作数（本章后面将详细介绍）。

即使 null 和 undefined 有关系，它们的用途也是完全不一样的。如前所述，永远不必显式地将变量值设置为 undefined。但 null 不是这样的。任何时候，只要变量要保存对象，而当时又没有那个对象可保存，就要用 null 来填充该变量。这样就可以保持 null 是空对象指针的语义，并进一步将其与 undefined 区分开来。

null 是一个假值。因此，如果需要，可以用更简洁的方式检测它。不过要记住，也有很多其他可能的值同样是假值。所以一定要明确自己想检测的就是 null 这个字面值，而不仅仅是假值。

```js
let message = null;
let age;
if (message) {
  // 这个块不会执行
}
if (!message) {
  // 这个块会执行
}
if (age) {
  // 这个块不会执行
}
if (!age) {
  // 这个块会执行
}
```

### 3.4.4. Boolean 类型

Boolean（布尔值）类型是 ECMAScript 中使用最频繁的类型之一，有两个字面值：true 和 false。这两个布尔值不同于数值，因此 true 不等于 1，false 不等于 0。下面是给变量赋布尔值的例子：

```js
let found = true;
let lost = false;
```

注意，布尔值字面量 true 和 false 是区分大小写的，因此 True 和 False（及其他大小混写形式）是有效的标识符，但不是布尔值。

虽然布尔值只有两个，但所有其他 ECMAScript 类型的值都有相应布尔值的等价形式。要将一个其他类型的值转换为布尔值，可以调用特定的 Boolean()转型函数：

```js
let message = "Hello world!";
let messageAsBoolean = Boolean(message);
```

在这个例子中，字符串 message 会被转换为布尔值并保存在变量 messageAsBoolean 中。Boolean()转型函数可以在任意类型的数据上调用，而且始终返回一个布尔值。什么值能转换为 true 或 false 的规则取决于数据类型和实际的值。下表总结了不同类型与布尔值之间的转换规则。

| 数据类型  | 转换为 true 的值       | 转换为 false 的值            |
| --------- | ---------------------- | ---------------------------- |
| Boolean   | true                   | false                        |
| String    | 非空字符串             | ""（空字符串）               |
| Number    | 非零数值（包括无穷值） | 0、NaN（参见后面的相关内容） |
| Object    | 任意对象               | null                         |
| Undefined | N/A（不存在）          | undefined                    |

理解以上转换非常重要，因为像 if 等流控制语句会自动执行其他类型值到布尔值的转换，例如：

```js
let message = "Hello world!";
if (message) {
  console.log("Value is true");
}
```

在这个例子中，console.log 会输出字符串"Value is true"，因为字符串 message 会被自动转换为等价的布尔值 true。由于存在这种自动转换，理解流控制语句中使用的是什么变量就非常重要。错误地使用对象而不是布尔值会明显改变应用程序的执行流。

### 3.4.5. Number 类型

ECMAScript 中最有意思的数据类型或许就是 Number 了。Number 类型使用 IEEE 754 格式表示整数和浮点值（在某些语言中也叫双精度值）。不同的数值类型相应地也有不同的数值字面量格式。

最基本的数值字面量格式是十进制整数，直接写出来即可：

```js
let intNum = 55; // 整数
```

整数也可以用八进制（以 8 为基数）或十六进制（以 16 为基数）字面量表示。对于八进制字面量，第一个数字必须是零（0），然后是相应的八进制数字（数值 0~7）。如果字面量中包含的数字超出了应有的范围，就会忽略前缀的零，后面的数字序列会被当成十进制数，如下所示：

```js
let octalNum1 = 070; // 八进制的56
let octalNum2 = 079; // 无效的八进制值，当成79 处理
let octalNum3 = 08; // 无效的八进制值，当成8 处理
```

八进制字面量在严格模式下是无效的，会导致 JavaScript 引擎抛出语法错误。ECMAScript 2015 或 ES6 中的八进制值通过前缀 0o 来表示；严格模式下，前缀 0 会被视为语法错误，如果要表示八进制值，应该使用前缀 0o。

要创建十六进制字面量，必须让真正的数值前缀 0x（区分大小写），然后是十六进制数字（0-9 以及 A-F）。十六进制数字中的字母大小写均可。下面是几个例子：

```js
let hexNum1 = 0xa; // 十六进制10
let hexNum2 = 0x1f; // 十六进制31
```

使用八进制和十六进制格式创建的数值在所有数学操作中都被视为十进制数值。

1. **浮点数**

要定义浮点值，数值中必须包含小数点，而且小数点后面必须至少有一个数字。虽然小数点前面不是必须有整数，但推荐加上。下面是几个例子：

```js
let floatNum1 = 1.1;
let floatNum2 = 0.1;
let floatNum3 = 0.1; // 有效，但不推荐
```

因为存储浮点值使用的内存空间是存储整数值的两倍，所以 ECMAScript 总是想方设法把值转换为整数。在小数点后面没有数字的情况下，数值就会变成整数。类似地，如果数值本身就是整数，只是小数点后面跟着 0（如 1.0），那它也会被转换为整数，如下例所示：

```js
let floatNum1 = 1; // 小数点后面没有数字，当成整数1 处理
let floatNum2 = 10.0; // 小数点后面是零，当成整数10 处理
```

对于非常大或非常小的数值，浮点值可以用科学记数法来表示。科学记数法用于表示一个应该乘以 10 的给定次幂的数值。ECMAScript 中科学记数法的格式要求是一个数值（整数或浮点数）后跟一个大写或小写的字母 e，再加上一个要乘的 10 的多少次幂。比如：

```js
let floatNum = 3.125e7; // 等于31250000
```

在这个例子中，floatNum 等于 31 250 000，只不过科学记数法显得更简洁。这种表示法实际上相当于说：“以 3.125 作为系数，乘以 10 的 7 次幂。

科学记数法也可以用于表示非常小的数值，例如 0.000 000 000 000 000 03。这个数值用科学记数法可以表示为 3e-17。默认情况下，ECMAScript 会将小数点后至少包含 6 个零的浮点值转换为科学记数法（例如，0.000 000 3 会被转换为 3e-7）。

浮点值的精确度最高可达 17 位小数，但在算术计算中远不如整数精确。例如，0.1 加 0.2 得到的不是 0.3，而是 0.300 000 000 000 000 04。由于这种微小的舍入错误，导致很难测试特定的浮点值。比如下面的例子：

```js
if (a + b == 0.3) {
  // 别这么干！
  console.log("You got 0.3.");
}
```

这里检测两个数值之和是否等于 0.3。如果两个数值分别是 0.05 和 0.25，或者 0.15 和 0.15，那没问题。但如果是 0.1 和 0.2，如前所述，测试将失败。因此永远不要测试某个特定的浮点值。

2. **值的范围**

由于内存的限制，ECMAScript 并不支持表示这个世界上的所有数值。ECMAScript 可以表示的最小数值保存在 Number.MIN_VALUE 中，这个值在多数浏览器中是 5e-324；可以表示的最大数值保存在 Number.MAX_VALUE 中，这个值在多数浏览器中是 1.797 693 134 862 315 7e+308。如果某个计算得到的数值结果超出了 JavaScript 可以表示的范围，那么这个数值会被自动转换为一个特殊的 Infinity（无穷）值。任何无法表示的负数以-Infinity（负无穷大）表示，任何无法表示的正数以 Infinity（正无穷大）表示。

如果计算返回正 Infinity 或负 Infinity，则该值将不能再进一步用于任何计算。这是因为 Infinity 没有可用于计算的数值表示形式。要确定一个值是不是有限大（即介于 JavaScript 能表示的最小值和最大值之间），可以使用 isFinite()函数，如下所示：

```js
let result = Number.MAX_VALUE + Number.MAX_VALUE;
console.log(isFinite(result)); // false
```

虽然超出有限数值范围的计算并不多见，但总归还是有可能的。因此在计算非常大或非常小的数值时，有必要监测一下计算结果是否超出范围。

注意：使用 Number.NEGATIVE_INFINITY 和 Number.POSITIVE_INFINITY 也可以获取正、负 Infinity。没错，这两个属性包含的值分别就是-Infinity 和 Infinity。

3. **NaN**

有一个特殊的数值叫 NaN，意思是“不是数值”（Not a Number），用于表示本来要返回数值的操作失败了（而不是抛出错误）。比如，用 0 除任意数值在其他语言中通常都会导致错误，从而中止代码执行。但在 ECMAScript 中，0、+0 或-0 相除会返回 NaN：

```js
console.log(0 / 0); // NaN
console.log(-0 / +0); // NaN
```

如果分子是非 0 值，分母是有符号 0 或无符号 0，则会返回 Infinity 或-Infinity：

```js
console.log(5 / 0); // Infinity
console.log(5 / -0); // -Infinity
```

NaN 有几个独特的属性。首先，任何涉及 NaN 的操作始终返回 NaN（如 NaN/10），在连续多步计算时这可能是个问题。其次，NaN 不等于包括 NaN 在内的任何值。例如，下面的比较操作会返回 false：

```js
console.log(NaN == NaN); // false
```

利用 NaN 这个特性可以方便的判断一个值是不是 NaN，例如：

```js
let test = NaN;
console.log(test === test); // false
```

为此，ECMAScript 提供了 isNaN()函数。该函数接收一个参数，可以是任意数据类型，然后判断这个参数是否“不是数值”。把一个值传给 isNaN()后，该函数会尝试把它转换为数值。某些非数值的值可以直接转换成数值，如字符串"10"或布尔值。任何不能转换为数值的值都会导致这个函数返回 true。举例如下：

```js
console.log(isNaN(NaN)); // true
console.log(isNaN(10)); // false，10 是数值
console.log(isNaN("10")); // false，可以转换为数值10
console.log(isNaN("blue")); // true，不可以转换为数值
console.log(isNaN(true)); // false，可以转换为数值1
```

上述的例子测试了 5 个不同的值。首先测试的是 NaN 本身，显然会返回 true。接着测试了数值 10 和字符串"10"，都返回 false，因为它们的数值都是 10。字符串"blue"不能转换为数值，因此函数返回 true。布尔值 true 可以转换为数值 1，因此返回 false。

与 isNaN 不同，Number.isNaN() 不会强制转换参数的类型，因此也可以使用 Number.isNaN() 来检测一个值是否是 NaN：

```js
console.log(Number.isNaN(NaN)); // true
console.log(Number.isNaN(10)); // false
console.log(Number.isNaN("10")); // false
console.log(Number.isNaN("blue")); // false
console.log(Number.isNaN(true)); // false
```

4. **数值转换**

有 3 个函数可以将非数值转换为数值：Number()、parseInt()和 parseFloat()。Number()是转型函数，可用于任何数据类型。后两个函数主要用于将字符串转换为数值。对于同样的参数，这 3 个函数执行的操作也不同。

Number()函数基于如下规则执行转换。

- 布尔值，true 转换为 1，false 转换为 0。
- 数值，直接返回。
- null，返回 0。
- undefined，返回 NaN。
- 字符串，应用以下规则。

  - 如果字符串包含数值字符，包括数值字符前面带加、减号的情况，则转换为一个十进制数值。
    因此，Number("1")返回 1，Number("123")返回 123，Number("011")返回 11（忽略前面
    的零）。
  - 如果字符串包含有效的浮点值格式如"1.1"，则会转换为相应的浮点值（同样，忽略前面的零）。
  - 如果字符串包含有效的十六进制格式如"0xf"，则会转换为与该十六进制值对应的十进制整
    数值。
  - 如果是空字符串（不包含字符），则返回 0。
  - 如果字符串包含除上述情况之外的其他字符，则返回 NaN。

- 对象，调用 valueOf()方法，并按照上述规则转换返回的值。如果转换结果是 NaN，则调用 toString()方法，再按照转换字符串的规则转换。

从不同数据类型到数值的转换有时候会比较复杂，看一看 Number()的转换规则就知道了。下面是几个具体的例子：

```js
let num1 = Number("Hello world!"); // NaN
let num2 = Number(""); // 0
let num3 = Number("000011"); // 11
let num4 = Number(true); // 1
```

可以看到，字符串"Hello world"转换之后是 NaN，因为它找不到对应的数值。空字符串转换后是 0。字符串 000011 转换后是 11，因为前面的零被忽略了。最后，true 转换为 1。

考虑到用 Number()函数转换字符串时相对复杂且有点反常规，通常在需要得到整数时可以优先使用 parseInt()函数。parseInt()函数更专注于字符串是否包含数值模式。字符串最前面的空格会被忽略，从第一个非空格字符开始转换。如果第一个字符不是数值字符、加号或减号，parseInt()立即返回 NaN。这意味着空字符串也会返回 NaN（这一点跟 Number()不一样，它返回 0）。如果第一个字符是数值字符、加号或减号，则继续依次检测每个字符，直到字符串末尾，或碰到非数值字符。比如，"1234blue"会被转换为 1234，因为"blue"会被完全忽略。类似地，"22.5"会被转换为 22，因为小数点不是有效的整数字符。

假设字符串中的第一个字符是数值字符，parseInt()函数也能识别不同的整数格式（十进制、八进制、十六进制）。换句话说，如果字符串以"0x"开头，就会被解释为十六进制整数。如果字符串以"0"开头，且紧跟着数值字符，在非严格模式下会被某些实现解释为八进制整数。

下面几个转换示例有助于理解上述规则：

```js
let num1 = parseInt("1234blue"); // 1234
let num2 = parseInt(""); // NaN
let num3 = parseInt("0xA"); // 10，解释为十六进制整数
let num4 = parseInt(22.5); // 22
let num5 = parseInt("70"); // 70，解释为十进制值
let num6 = parseInt("0xf"); // 15，解释为十六进制整数
```

不同的数值格式很容易混淆，因此 parseInt()也接收第二个参数，用于指定底数（进制数）。如果知道要解析的值是十六进制，那么可以传入 16 作为第二个参数，以便正确解析：

```js
let num = parseInt("0xAF", 16); // 175
```

事实上，如果提供了十六进制参数，那么字符串前面的"0x"可以省掉：

```js
let num1 = parseInt("AF", 16); // 175
let num2 = parseInt("AF"); // NaN
```

在这个例子中，第一个转换是正确的，而第二个转换失败了。区别在于第一次传入了进制数作为参数，告诉 parseInt()要解析的是一个十六进制字符串。而第二个转换检测到第一个字符就是非数值字符，随即自动停止并返回 NaN。

通过第二个参数，可以极大扩展转换后获得的结果类型。比如:

```js
let num1 = parseInt("10", 2); // 2，按二进制解析
let num2 = parseInt("10", 8); // 8，按八进制解析
let num3 = parseInt("10", 10); // 10，按十进制解析
let num4 = parseInt("10", 16); // 16，按十六进制解析
```

因为不传底数参数相当于让 parseInt()自己决定如何解析，所以为避免解析出错，建议始终传给它第二个参数。

parseFloat()函数的工作方式跟 parseInt()函数类似，都是从位置 0 开始检测每个字符。同样，它也是解析到字符串末尾或者解析到一个无效的浮点数值字符为止。这意味着第一次出现的小数点是有效的，但第二次出现的小数点就无效了，此时字符串的剩余字符都会被忽略。因此，"22.34.5"将转换成 22.34。

parseFloat()函数的另一个不同之处在于，它始终忽略字符串开头的零。这个函数能识别前面讨论的所有浮点格式，以及十进制格式（开头的零始终被忽略）。十六进制数值始终会返回 0。因为 parseFloat()只解析十进制值，因此不能指定底数。最后，如果字符串表示整数（没有小数点或者小数点后面只有一个零），则 parseFloat()返回整数。下面是几个示例：

```js
let num1 = parseFloat("1234blue"); // 1234，按整数解析
let num2 = parseFloat("0xA"); // 0
let num3 = parseFloat("22.5"); // 22.5
let num4 = parseFloat("22.34.5"); // 22.34
let num5 = parseFloat("0908.5"); // 908.5
let num6 = parseFloat("3.125e7"); // 31250000
```

### 3.4.6. String 类型

String（字符串）数据类型表示零或多个 16 位 Unicode 字符序列。字符串可以使用双引号（"）、单引号（'）或反引号（`）标示，因此下面的代码都是合法的：

```js
let firstName = "John";
let lastName = "Jacob";
let lastName = `Jingleheimerschmidt`;
```

跟某些语言中使用不同的引号会改变对字符串的解释方式不同，ECMAScript 语法中表示字符串的引号没有区别。不过要注意的是，以某种引号作为字符串开头，必须仍然以该种引号作为字符串结尾。比如，下面的写法会导致语法错误：

```js
let firstName = 'Nicholas"; // 语法错误：开头和结尾的引号必须是同一种
```

1. **字符字面量**

字符串数据类型包含一些字符字面量，用于表示非打印字符或有其他用途的字符，如下表所示：

| 字面量 | 含义                                                                                             |
| ------ | ------------------------------------------------------------------------------------------------ |
| \n     | 换行                                                                                             |
| \t     | 制表                                                                                             |
| \b     | 退格                                                                                             |
| \r     | 回车                                                                                             |
| \f     | 换页                                                                                             |
| \\\    | 反斜杠（\）                                                                                      |
| \\'    | 单引号（'），在字符串以单引号标示时使用，例如'He said, \\'hey.\\''                               |
| \\"    | 双引号（"），在字符串以双引号标示时使用，例如"He said, \\"hey.\\""                               |
| \ \`   | 反引号（\ \`），在字符串以反引号标示时使用，例如\`He said, \ \`hey.\\ ``                         |
| \xnn   | 以十六进制编码 nn 表示的字符（其中 n 是十六进制数字 0~F），例如\x41 等于"A"                      |
| \unnnn | 以十六进制编码 nnnn 表示的 Unicode 字符（其中 n 是十六进制数字 0~F），例如\u03a3 等于希腊字符"Σ" |

这些字符字面量可以出现在字符串中的任意位置，且可以作为单个字符被解释：

```js
let text = "This is the letter sigma: \u03a3.";
```

在这个例子中，即使包含 6 个字符长的转义序列，变量 text 仍然是 28 个字符长。因为转义序列表示一个字符，所以只算一个字符。

字符串的长度可以通过其 length 属性获取：

```js
console.log(text.length); // 28
```

这个属性返回字符串中 16 位字符的个数。

2. **字符串的特点**

ECMAScript 中的字符串是不可变的（immutable），意思是一旦创建，它们的值就不能变了。要修改某个变量中的字符串值，必须先销毁原始的字符串，然后将包含新值的另一个字符串保存到该变量，如下所示：

```js
let lang = "Java";
lang = lang + "Script";
```

这里，变量 lang 一开始包含字符串"Java"。紧接着，lang 被重新定义为包含"Java"和"Script"的组合，也就是"JavaScript"。整个过程首先会分配一个足够容纳 10 个字符的空间，然后填充上"Java"和"Script"。最后销毁原始的字符串"Java"和字符串"Script"，因为这两个字符串都没有用
了。所有处理都是在后台发生的，而这也是一些早期的浏览器（如 Firefox 1.0 之前的版本和 IE6.0）在拼接字符串时非常慢的原因。这些浏览器在后来的版本中都有针对性地解决了这个问题。

3. **转换为字符串**

有两种方式把一个值转换为字符串。首先是使用几乎所有值都有的 toString()方法。这个方法唯一的用途就是返回当前值的字符串等价物。比如：

```js
let age = 11;
let ageAsString = age.toString(); // 字符串"11"
let found = true;
let foundAsString = found.toString(); // 字符串"true"
```

toString()方法可见于数值、布尔值、对象和字符串值。（没错，字符串值也有 toString()方法，该方法只是简单地返回自身的一个副本。）null 和 undefined 值没有 toString()方法。

多数情况下，toString()不接收任何参数。不过，在对数值调用这个方法时，toString()可以接收一个底数参数，即以什么底数来输出数值的字符串表示。默认情况下，toString()返回数值的十进制字符串表示。而通过传入参数，可以得到数值的二进制、八进制、十六进制，或者其他任何有效基数的字符串表示，比如：

```js
let num = 10;
console.log(num.toString()); // "10"
console.log(num.toString(2)); // "1010"
console.log(num.toString(8)); // "12"
console.log(num.toString(10)); // "10"
console.log(num.toString(16)); // "a"
```

这个例子展示了传入底数参数时，toString()输出的字符串值也会随之改变。数值 10 可以输出为任意数值格式。注意，默认情况下（不传参数）的输出与传入参数 10 得到的结果相同。

如果你不确定一个值是不是 null 或 undefined，可以使用 String()转型函数，它始终会返回表示相应类型值的字符串。String()函数遵循如下规则。

- 如果值有 toString()方法，则调用该方法（不传参数）并返回结果。
- 如果值是 null，返回"null"。
- 如果值是 undefined，返回"undefined"。

下面看几个例子：

```js
let value1 = 10;
let value2 = true;
let value3 = null;
let value4;

console.log(String(value1)); // "10"
console.log(String(value2)); // "true"
console.log(String(value3)); // "null"
console.log(String(value4)); // "undefined"
```

这里展示了将 4 个值转换为字符串的情况：一个数值、一个布尔值、一个 null 和一个 undefined。数值和布尔值的转换结果与调用 toString()相同。因为 null 和 undefined 没有 toString()方法，所以 String()方法就直接返回了这两个值的字面量文本。

4. **模板字面量**

ECMAScript 6 新增了使用模板字面量定义字符串的能力。与使用单引号或双引号不同，模板字面量保留换行字符，可以跨行定义字符串：

```js
let myMultiLineString = "first line\nsecond line";
let myMultiLineTemplateLiteral = `first line
second line`;

console.log(myMultiLineString);
// first line
// second line"
console.log(myMultiLineTemplateLiteral);
// first line
// second line
console.log(myMultiLineString === myMultiLinetemplateLiteral); // true
```

顾名思义，模板字面量在定义模板时特别有用，比如下面这个 HTML 模板：

```js
let pageHTML = `
<div>
  <a href="#">
    <span>Jake</span>
  </a>
</div>`;
```

由于模板字面量会保持反引号内部的空格，因此在使用时要格外注意。格式正确的模板字符串看起来可能会缩进不当：

```js
// 这个模板字面量在换行符之后有25 个空格符
let myTemplateLiteral = `first line
second line`;
console.log(myTemplateLiteral.length); // 47

// 这个模板字面量以一个换行符开头
let secondTemplateLiteral = `
first line
second line`;
console.log(secondTemplateLiteral[0] === "\n"); // true

// 这个模板字面量没有意料之外的字符
let thirdTemplateLiteral = `first line
second line`;
console.log(thirdTemplateLiteral);
// first line
// second line
```

5. **字符串插值**

模板字面量最常用的一个特性是支持字符串插值，也就是可以在一个连续定义中插入一个或多个值。技术上讲，模板字面量不是字符串，而是一种特殊的 JavaScript 句法表达式，只不过求值后得到的是字符串。模板字面量在定义时立即求值并转换为字符串实例，任何插入的变量也会从它们最接近的作用域中取值。

字符串插值通过在${}中使用一个 JavaScript 表达式实现：

```js
let value = 5;
let exponent = "second";
// 以前，字符串插值是这样实现的：
let interpolatedString =
  value + " to the " + exponent + " power is " + value * value;
// 现在，可以用模板字面量这样实现：
let interpolatedTemplateLiteral = `${value} to the ${exponent} power is ${
  value * value
}`;
console.log(interpolatedString); // 5 to the second power is 25
console.log(interpolatedTemplateLiteral); // 5 to the second power is 25
```

所有插入的值都会使用 toString()强制转型为字符串，而且任何 JavaScript 表达式都可以用于插值。嵌套的模板字符串无须转义：

```js
console.log(`Hello, ${`World`}!`); // Hello, World!
```

将表达式转换为字符串时会调用 toString()：

```js
let foo = { toString: () => "World" };
console.log(`Hello, ${foo}!`); // Hello, World!
```

在插值表达式中可以调用函数和方法：

```js
function capitalize(word) {
  return `${word[0].toUpperCase()}${word.slice(1)}`;
}
console.log(`${capitalize("hello")}, ${capitalize("world")}!`); // Hello, World!
```

此外，模板也可以插入自己之前的值：

```js
let value = "";
function append() {
  value = `${value}abc`;
  console.log(value);
}
append(); // abc
append(); // abcabc
append(); // abcabcabc
```

6. **模板字面量标签函数**

模板字面量也支持定义 **标签函数(tag function)**，而通过标签函数可以自定义插值行为。标签函数会接收被插值记号分隔后的模板和对每个表达式求值的结果。

标签函数本身是一个常规函数，通过前缀到模板字面量来应用自定义行为，如下例所示。标签函数接收到的参数依次是原始字符串数组和对每个表达式求值的结果。这个函数的返回值是对模板字面量求值得到的字符串。

最好通过一个例子来理解：

```js
let a = 6;
let b = 9;
function simpleTag(strings, aValExpression, bValExpression, sumExpression) {
  console.log(strings);
  console.log(aValExpression);
  console.log(bValExpression);
  console.log(sumExpression);
  return "foobar";
}
let untaggedResult = `${a} + ${b} = ${a + b}`;
let taggedResult = simpleTag`${a} + ${b} = ${a + b}`;
// ["", " + ", " = ", ""]
// 6
// 9
// 15
console.log(untaggedResult); // "6 + 9 = 15"
console.log(taggedResult); // "foobar"
```

因为表达式参数的数量是可变的，所以通常应该使用剩余操作符（rest operator）将它们收集到一个数组中：

```js
let a = 6;
let b = 9;
function simpleTag(strings, ...expressions) {
  console.log(strings);
  for (const expression of expressions) {
    console.log(expression);
  }
  return "foobar";
}
let taggedResult = simpleTag`${a} + ${b} = ${a + b}`;
// ["", " + ", " = ", ""]
// 6
// 9
// 15
console.log(taggedResult); // "foobar"
```

对于有 n 个插值的模板字面量，传给标签函数的表达式参数的个数始终是 n，而传给标签函数的第一个参数所包含的字符串个数则始终是 n+1。因此，如果你想把这些字符串和对表达式求值的结果拼接起来作为默认返回的字符串，可以这样做：

```js
let a = 6;
let b = 9;
function zipTag(strings, ...expressions) {
  return (
    strings[0] + expressions.map((e, i) => `${e}${strings[i + 1]}`).join("")
  );
}
let untaggedResult = `${a} + ${b} = ${a + b}`;
let taggedResult = zipTag`${a} + ${b} = ${a + b}`;
console.log(untaggedResult); // "6 + 9 = 15"
console.log(taggedResult); // "6 + 9 = 15"
```

7. **原始字符串**

使用模板字面量也可以直接获取原始的模板字面量内容（如换行符或 Unicode 字符），而不是被转换后的字符表示。为此，可以使用默认的 String.raw 标签函数：

```js
// Unicode 示例
// \u00A9 是版权符号
console.log(`\u00A9`); // ©
console.log(String.raw`\u00A9`); // \u00A9
// 换行符示例
console.log(`first line\nsecond line`);
// first line
// second line
console.log(String.raw`first line\nsecond line`); // "first line\nsecond line"
// 对实际的换行符来说是不行的
// 它们不会被转换成转义序列的形式
console.log(`first line
second line`);
// first line
// second line
console.log(String.raw`first line
second line`);
// first line
// second line
```

另外，也可以通过标签函数的第一个参数，即字符串数组的.raw 属性取得每个字符串的原始内容：

```js
function printRaw(strings) {
  console.log("Actual characters:");
  for (const string of strings) {
    console.log(string);
  }
  console.log("Escaped characters;");
  for (const rawString of strings.raw) {
    console.log(rawString);
  }
}
printRaw`\u00A9${"and"}\n`;
// Actual characters:
// ©
//（换行符）
// Escaped characters:
// \u00A9
// \n
```

### 3.4.7. Symbol 类型

Symbol（符号）是 ECMAScript 6 新增的数据类型。符号是原始值，且符号实例是唯一、不可变的。符号的用途是确保对象属性使用唯一标识符，不会发生属性冲突的危险。

尽管听起来跟私有属性有点类似，但符号并不是为了提供私有属性的行为才增加的（尤其是因为 Object API 提供了方法，可以更方便地发现符号属性）。相反，符号就是用来创建唯一记号，进而用作非字符串形式的对象属性。

1. **符号的基本用法**

符号需要使用 Symbol()函数初始化。因为符号本身是原始类型，所以 typeof 操作符对符号返回 symbol。

```js
let sym = Symbol();
console.log(typeof sym); // symbol
```

调用 Symbol()函数时，也可以传入一个字符串参数作为对符号的描述（description），将来可以通过这个字符串来调试代码。但是，这个字符串参数与符号定义或标识完全无关：

```js
let genericSymbol = Symbol();
let otherGenericSymbol = Symbol();

let fooSymbol = Symbol("foo");
let otherFooSymbol = Symbol("foo");

console.log(genericSymbol == otherGenericSymbol); // false
console.log(fooSymbol == otherFooSymbol); // false
```

符号没有字面量语法，这也是它们发挥作用的关键。按照规范，你只要创建 Symbol()实例并将其用作对象的新属性，就可以保证它不会覆盖已有的对象属性，无论是符号属性还是字符串属性。

```js
let genericSymbol = Symbol();
console.log(genericSymbol); // Symbol()

let fooSymbol = Symbol("foo");
console.log(fooSymbol); // Symbol(foo);
```

最重要的是，Symbol()函数不能与 new 关键字一起作为构造函数使用。这样做是为了避免创建符号包装对象，像使用 Boolean、String 或 Number 那样，它们都支持构造函数且可用于初始化包含原始值的包装对象：

```js
let myBoolean = new Boolean();
console.log(typeof myBoolean); // "object"

let myString = new String();
console.log(typeof myString); // "object"

let myNumber = new Number();
console.log(typeof myNumber); // "object"

let mySymbol = new Symbol(); // TypeError: Symbol is not a constructor
```

如果你确实想使用符号包装对象，可以借用 Object()函数：

```js
let mySymbol = Symbol();
let myWrappedSymbol = Object(mySymbol);
console.log(typeof myWrappedSymbol); // "object"
```

2. **使用全局符号注册表**

如果运行时的不同部分需要共享和重用符号实例，那么可以用一个字符串作为键，在全局符号注册表中创建并重用符号。

为此，需要使用 Symbol.for()方法：

```js
let fooGlobalSymbol = Symbol.for("foo");
console.log(typeof fooGlobalSymbol); // symbol
```

Symbol.for()对每个字符串键都执行幂等操作。第一次使用某个字符串调用时，它会检查全局运行时注册表，发现不存在对应的符号，于是就会生成一个新符号实例并添加到注册表中。后续使用相同字符串的调用同样会检查注册表，发现存在与该字符串对应的符号，然后就会返回该符号实例。

```js
let fooGlobalSymbol = Symbol.for("foo"); // 创建新符号
let otherFooGlobalSymbol = Symbol.for("foo"); // 重用已有符号

console.log(fooGlobalSymbol === otherFooGlobalSymbol); // true
```

即使采用相同的符号描述，在全局注册表中定义的符号跟使用 Symbol()定义的符号也并不等同：

```js
let localSymbol = Symbol("foo");
let globalSymbol = Symbol.for("foo");

console.log(localSymbol === globalSymbol); // false
```

全局注册表中的符号必须使用字符串键来创建，因此作为参数传给 Symbol.for()的任何值都会被转换为字符串。此外，注册表中使用的键同时也会被用作符号描述。

```js
let emptyGlobalSymbol = Symbol.for();
console.log(emptyGlobalSymbol); // Symbol(undefined)
```

还可以使用 Symbol.keyFor()来查询全局注册表，这个方法接收符号，返回该全局符号对应的字符串键。如果查询的不是全局符号，则返回 undefined。

```js
// 创建全局符号
let s = Symbol.for("foo");
console.log(Symbol.keyFor(s)); // foo

// 创建普通符号
let s2 = Symbol("bar");
console.log(Symbol.keyFor(s2)); // undefined
```

如果传给 Symbol.keyFor()的不是符号，则该方法抛出 TypeError：

```js
Symbol.keyFor(123); // TypeError: 123 is not a symbol
```

3. **使用符号作为属性**

凡是可以使用字符串或数值作为属性的地方，都可以使用符号。这就包括了对象字面量属性和 Object.defineProperty()/Object.defineProperties()定义的属性。对象字面量只能在计算属性语法中使用符号作为属性。

```js
let s1 = Symbol("foo"),
  s2 = Symbol("bar"),
  s3 = Symbol("baz"),
  s4 = Symbol("qux");
let o = {
  [s1]: "foo val",
};
// 这样也可以：o[s1] = 'foo val';
console.log(o);
// {Symbol(foo): foo val}

Object.defineProperty(o, s2, { value: "bar val" });
console.log(o);
// {Symbol(foo): foo val, Symbol(bar): bar val}

Object.defineProperties(o, {
  [s3]: { value: "baz val" },
  [s4]: { value: "qux val" },
});
console.log(o);
// {Symbol(foo): foo val, Symbol(bar): bar val,
// Symbol(baz): baz val, Symbol(qux): qux val}
```

类似于 Object.getOwnPropertyNames()返回对象实例的常规属性数组，Object.getOwnPropertySymbols()返回对象实例的符号属性数组。这两个方法的返回值彼此互斥。Object.getOwnPropertyDescriptors()会返回同时包含常规和符号属性描述符的对象。Reflect.ownKeys()会返回两种类型的键：

```js
let s1 = Symbol("foo"),
  s2 = Symbol("bar");
let o = {
  [s1]: "foo val",
  [s2]: "bar val",
  baz: "baz val",
  qux: "qux val",
};
console.log(Object.getOwnPropertySymbols(o));
// [Symbol(foo), Symbol(bar)]

console.log(Object.getOwnPropertyNames(o));
// ["baz", "qux"]

console.log(Reflect.ownKeys(o));
// ["baz", "qux", Symbol(foo), Symbol(bar)]

console.log(Object.getOwnPropertyDescriptors(o));
// {baz: {...}, qux: {...}, Symbol(foo): {...}, Symbol(bar): {...}}
```

因为符号属性是对内存中符号的一个引用，所以直接创建并用作属性的符号不会丢失。但是，如果没有显式地保存对这些属性的引用，那么必须遍历对象的所有符号属性才能找到相应的属性键：

```js
let o = {
  [Symbol("foo")]: "foo val",
  [Symbol("bar")]: "bar val",
};
console.log(o);
// {Symbol(foo): "foo val", Symbol(bar): "bar val"}

let barSymbol = Object.getOwnPropertySymbols(o).find((symbol) =>
  symbol.toString().match(/bar/)
);
console.log(barSymbol);
// Symbol(bar)
```

4. **常用内置符号**

ECMAScript 6 也引入了一批 **常用内置符号(well-known symbol)**，用于暴露语言内部行为，开发者可以直接访问、重写或模拟这些行为。这些内置符号都以 Symbol 工厂函数字符串属性的形式存在。

这些内置符号最重要的用途之一是重新定义它们，从而改变原生结构的行为。比如，我们知道 for-of 循环会在相关对象上使用 Symbol.iterator 属性，那么就可以通过在自定义对象上重新定义 Symbol.iterator 的值，来改变 for-of 在迭代该对象时的行为。

这些内置符号也没有什么特别之处，它们就是全局函数 Symbol 的普通字符串属性，指向一个符号的实例。所有内置符号属性都是不可写、不可枚举、不可配置的。

注意：在提到 ECMAScript 规范时，经常会引用符号在规范中的名称，前缀为@@。比如，@@iterator 指的就是 Symbol.iterator。

5. **Symbol.asyncIterator**

根据 ECMAScript 规范，这个符号作为一个属性表示“一个方法，该方法返回对象默认的 AsyncIterator。由 for-await-of 语句使用”。换句话说，这个符号表示实现异步迭代器 API 的函数。

for-await-of 循环会利用这个函数执行异步迭代操作。循环时，它们会调用以 Symbol.asyncIterator 为键的函数，并期望这个函数会返回一个实现迭代器 API 的对象。很多时候，返回的对象是实现该 API 的 AsyncGenerator：

```js
class Foo {
  async *[Symbol.asyncIterator]() {}
}
let f = new Foo();
console.log(f[Symbol.asyncIterator]());
// AsyncGenerator {<suspended>}
```

技术上，这个由 Symbol.asyncIterator 函数生成的对象应该通过其 next()方法陆续返回 Promise 实例。可以通过显式地调用 next()方法返回，也可以隐式地通过异步生成器函数返回：

```js
class Emitter {
  constructor(max) {
    this.max = max;
    this.asyncIdx = 0;
  }
  async *[Symbol.asyncIterator]() {
    while (this.asyncIdx < this.max) {
      yield new Promise((resolve) => resolve(this.asyncIdx++));
    }
  }
}
async function asyncCount() {
  let emitter = new Emitter(5);
  for await (const x of emitter) {
    console.log(x);
  }
}
asyncCount();
// 0
// 1
// 2
// 3
// 4
```

注意:Symbol.asyncIterator 是 ES2018 规范定义的，因此只有版本非常新的浏览器支持它。

6. **Symbol.hasInstance**

根据 ECMAScript 规范，这个符号作为一个属性表示“一个方法，该方法决定一个构造器对象是否认可一个对象是它的实例。由 instanceof 操作符使用”。instanceof 操作符可以用来确定一个对象实例的原型链上是否有原型。instanceof 的典型使用场景如下：

```js
function Foo() {}
let f = new Foo();
console.log(f instanceof Foo); // true
class Bar {}
let b = new Bar();
console.log(b instanceof Bar); // true
```

在 ES6 中，instanceof 操作符会使用 Symbol.hasInstance 函数来确定关系。以 Symbol.hasInstance 为键的函数会执行同样的操作，只是操作数对调了一下：

```js
function Foo() {}
let f = new Foo();
console.log(Foo[Symbol.hasInstance](f)); // true
class Bar {}
let b = new Bar();
console.log(Bar[Symbol.hasInstance](b)); // true
```

这个属性定义在 Function 的原型上，因此默认在所有函数和类上都可以调用。由于 instanceof 操作符会在原型链上寻找这个属性定义，就跟在原型链上寻找其他属性一样，因此可以在继承的类上通过静态方法重新定义这个函数：

```js
class Bar {}
class Baz extends Bar {
  static [Symbol.hasInstance]() {
    return false;
  }
}
let b = new Baz();
console.log(Bar[Symbol.hasInstance](b)); // true
console.log(b instanceof Bar); // true
console.log(Baz[Symbol.hasInstance](b)); // false
console.log(b instanceof Baz); // false
```

7. **Symbol.isConcatSpreadable**

根据 ECMAScript 规范，这个符号作为一个属性表示“一个布尔值，如果是 true，则意味着对象应该用 Array.prototype.concat()打平其数组元素”。ES6 中的 Array.prototype.concat()方法会根据接收到的对象类型选择如何将一个类数组对象拼接成数组实例。覆盖 Symbol.isConcatSpreadable 的值可以修改这个行为。

数组对象默认情况下会被打平到已有的数组，false 或假值会导致整个对象被追加到数组末尾。类数组对象默认情况下会被追加到数组末尾，true 或真值会导致这个类数组对象被打平到数组实例。其他不是类数组对象的对象在 Symbol.isConcatSpreadable 被设置为 true 的情况下将被忽略。

```js
let initial = ["foo"];
let array = ["bar"];
console.log(array[Symbol.isConcatSpreadable]); // undefined
console.log(initial.concat(array)); // ['foo', 'bar']
array[Symbol.isConcatSpreadable] = false;
console.log(initial.concat(array)); // ['foo', Array(1)]
let arrayLikeObject = { length: 1, 0: "baz" };
console.log(arrayLikeObject[Symbol.isConcatSpreadable]); // undefined
console.log(initial.concat(arrayLikeObject)); // ['foo', {...}]
arrayLikeObject[Symbol.isConcatSpreadable] = true;
console.log(initial.concat(arrayLikeObject)); // ['foo', 'baz']
let otherObject = new Set().add("qux");
console.log(otherObject[Symbol.isConcatSpreadable]); // undefined
console.log(initial.concat(otherObject)); // ['foo', Set(1)]
otherObject[Symbol.isConcatSpreadable] = true;
console.log(initial.concat(otherObject)); // ['foo']
```

8. **Symbol.iterator**

根据 ECMAScript 规范，这个符号作为一个属性表示“一个方法，该方法返回对象默认的迭代器。由 for-of 语句使用”。换句话说，这个符号表示实现迭代器 API 的函数。

for-of 循环这样的语言结构会利用这个函数执行迭代操作。循环时，它们会调用以 Symbol.iterator 为键的函数，并默认这个函数会返回一个实现迭代器 API 的对象。很多时候，返回的对象是实现该 API 的 Generator：

```js
class Foo {
  *[Symbol.iterator]() {}
}
let f = new Foo();
console.log(f[Symbol.iterator]());
// Generator {<suspended>}
```

技术上，这个由 Symbol.iterator 函数生成的对象应该通过其 next()方法陆续返回值。可以通过显式地调用 next()方法返回，也可以隐式地通过生成器函数返回：

```js
class Emitter {
  constructor(max) {
    this.max = max;
    this.idx = 0;
  }
  *[Symbol.iterator]() {
    while (this.idx < this.max) {
      yield this.idx++;
    }
  }
}
function count() {
  let emitter = new Emitter(5);
  for (const x of emitter) {
    console.log(x);
  }
}
count();
// 0
// 1
// 2
// 3
// 4
```

9. **Symbol.match**

根据 ECMAScript 规范，这个符号作为一个属性表示“一个正则表达式方法，该方法用正则表达式去匹配字符串。由 String.prototype.match()方法使用”。String.prototype.match()方法会使用以 Symbol.match 为键的函数来对正则表达式求值。正则表达式的原型上默认有这个函数的定义，因此所有正则表达式实例默认是这个 String 方法的有效参数：

```js
console.log(RegExp.prototype[Symbol.match]);
// ƒ [Symbol.match]() { [native code] }

console.log("foobar".match(/bar/));
// ["bar", index: 3, input: "foobar", groups: undefined]
```

给这个方法传入非正则表达式值会导致该值被转换为 RegExp 对象。如果想改变这种行为，让方法直接使用参数，则可以重新定义 Symbol.match 函数以取代默认对正则表达式求值的行为，从而让 match()方法使用非正则表达式实例。Symbol.match 函数接收一个参数，就是调用 match()方法的字符串实例。返回的值没有限制：

```js
class FooMatcher {
  static [Symbol.match](target) {
    return target.includes("foo");
  }
}
console.log("foobar".match(FooMatcher)); // true
console.log("barbaz".match(FooMatcher)); // false
class StringMatcher {
  constructor(str) {
    this.str = str;
  }
  [Symbol.match](target) {
    return target.includes(this.str);
  }
}
console.log("foobar".match(new StringMatcher("foo"))); // true
console.log("barbaz".match(new StringMatcher("qux"))); // false
```

10. **Symbol.replace**

根据 ECMAScript 规范，这个符号作为一个属性表示“一个正则表达式方法，该方法替换一个字符串中匹配的子串。由 String.prototype.replace()方法使用”。String.prototype.replace()方法会使用以 Symbol.replace 为键的函数来对正则表达式求值。正则表达式的原型上默认有这个函数的定义，因此所有正则表达式实例默认是这个 String 方法的有效参数：

```js
console.log(RegExp.prototype[Symbol.replace]);
// ƒ [Symbol.replace]() { [native code] }

console.log("foobarbaz".replace(/bar/, "qux"));
// 'fooquxbaz'
```

给这个方法传入非正则表达式值会导致该值被转换为 RegExp 对象。如果想改变这种行为，让方法直接使用参数，可以重新定义 Symbol.replace 函数以取代默认对正则表达式求值的行为，从而让 replace()方法使用非正则表达式实例。Symbol.replace 函数接收两个参数，即调用 replace()方法的字符串实例和替换字符串。返回的值没有限制：

```js
class FooReplacer {
  static [Symbol.replace](target, replacement) {
    return target.split("foo").join(replacement);
  }
}
console.log("barfoobaz".replace(FooReplacer, "qux"));
// "barquxbaz"
class StringReplacer {
  constructor(str) {
    this.str = str;
  }
  [Symbol.replace](target, replacement) {
    return target.split(this.str).join(replacement);
  }
}
console.log("barfoobaz".replace(new StringReplacer("foo"), "qux"));
// "barquxbaz"
```

11. **Symbol.search**

根据 ECMAScript 规范，这个符号作为一个属性表示“一个正则表达式方法，该方法返回字符串中匹配正则表达式的索引。由 String.prototype.search()方法使用”。String.prototype.search()方法会使用以 Symbol.search 为键的函数来对正则表达式求值。正则表达式的原型上默认有这个函数的定义，因此所有正则表达式实例默认是这个 String 方法的有效参数：

```js
console.log(RegExp.prototype[Symbol.search]);
// ƒ [Symbol.search]() { [native code] }

console.log("foobar".search(/bar/));
// 3
```

给这个方法传入非正则表达式值会导致该值被转换为 RegExp 对象。如果想改变这种行为，让方法直接使用参数，可以重新定义 Symbol.search 函数以取代默认对正则表达式求值的行为，从而让 search()方法使用非正则表达式实例。Symbol.search 函数接收一个参数，就是调用 match()方法的字符串实例。返回的值没有限制：

```js
class FooSearcher {
  static [Symbol.search](target) {
    return target.indexOf("foo");
  }
}
console.log("foobar".search(FooSearcher)); // 0
console.log("barfoo".search(FooSearcher)); // 3
console.log("barbaz".search(FooSearcher)); // -1
class StringSearcher {
  constructor(str) {
    this.str = str;
  }
  [Symbol.search](target) {
    return target.indexOf(this.str);
  }
}
console.log("foobar".search(new StringSearcher("foo"))); // 0
console.log("barfoo".search(new StringSearcher("foo"))); // 3
console.log("barbaz".search(new StringSearcher("qux"))); // -1
```

12. **Symbol.species**

根据 ECMAScript 规范，这个符号作为一个属性表示“一个函数值，该函数作为创建派生对象的构造函数”。这个属性在内置类型中最常用，用于对内置类型实例方法的返回值暴露实例化派生对象的方法。用 Symbol.species 定义静态的获取器（getter）方法，可以覆盖新创建实例的原型定义：

```js
class Bar extends Array {}
class Baz extends Array {
  static get [Symbol.species]() {
    return Array;
  }
}
let bar = new Bar();
console.log(bar instanceof Array); // true
console.log(bar instanceof Bar); // true
bar = bar.concat("bar");
console.log(bar instanceof Array); // true
console.log(bar instanceof Bar); // true
let baz = new Baz();
console.log(baz instanceof Array); // true
console.log(baz instanceof Baz); // true
baz = baz.concat("baz");
console.log(baz instanceof Array); // true
console.log(baz instanceof Baz); // false
```

13. **Symbol.split**

根据 ECMAScript 规范，这个符号作为一个属性表示“一个正则表达式方法，该方法在匹配正则表达式的索引位置拆分字符串。由 String.prototype.split()方法使用”。String.prototype.split()方法会使用以 Symbol.split 为键的函数来对正则表达式求值。正则表达式的原型上默认有这个函数的定义，因此所有正则表达式实例默认是这个 String 方法的有效参数：

```js
console.log(RegExp.prototype[Symbol.split]);
// ƒ [Symbol.split]() { [native code] }

console.log("foobarbaz".split(/bar/));
// ['foo', 'baz']
```

给这个方法传入非正则表达式值会导致该值被转换为 RegExp 对象。如果想改变这种行为，让方法直接使用参数，可以重新定义 Symbol.split 函数以取代默认对正则表达式求值的行为，从而让 split()方法使用非正则表达式实例。Symbol.split 函数接收一个参数，就是调用 match()方法的字符串实例。返回的值没有限制：

```js
class FooSplitter {
  static [Symbol.split](target) {
    return target.split("foo");
  }
}
console.log("barfoobaz".split(FooSplitter));
// ["bar", "baz"]
class StringSplitter {
  constructor(str) {
    this.str = str;
  }
  [Symbol.split](target) {
    return target.split(this.str);
  }
}
console.log("barfoobaz".split(new StringSplitter("foo")));
// ["bar", "baz"]
```

14. **Symbol.toPrimitive**

根据 ECMAScript 规范，这个符号作为一个属性表示“一个方法，该方法将对象转换为相应的原始值。由 ToPrimitive 抽象操作使用”。很多内置操作都会尝试强制将对象转换为原始值，包括字符串、数值和未指定的原始类型。对于一个自定义对象实例，通过在这个实例的 Symbol.toPrimitive 属性上定义一个函数可以改变默认行为。

根据提供给这个函数的参数（string、number 或 default），可以控制返回的原始值：

```js
class Foo {}
let foo = new Foo();
console.log(3 + foo); // "3[object Object]"
console.log(3 - foo); // NaN
console.log(String(foo)); // "[object Object]"
class Bar {
  constructor() {
    this[Symbol.toPrimitive] = function (hint) {
      switch (hint) {
        case "number":
          return 3;
        case "string":
          return "string bar";
        case "default":
        default:
          return "default bar";
      }
    };
  }
}
let bar = new Bar();
console.log(3 + bar); // "3default bar"
console.log(3 - bar); // 0
console.log(String(bar)); // "string bar"
```

15. **Symbol.toStringTag**

根据 ECMAScript 规范，这个符号作为一个属性表示“一个字符串，该字符串用于创建对象的默认字符串描述。由内置方法 Object.prototype.toString()使用”。

通过 toString()方法获取对象标识时，会检索由 Symbol.toStringTag 指定的实例标识符，默认为"Object"。内置类型已经指定了这个值，但自定义类实例还需要明确定义：

```js
let s = new Set();
console.log(s); // Set(0) {}
console.log(s.toString()); // [object Set]
console.log(s[Symbol.toStringTag]); // Set
class Foo {}
let foo = new Foo();
console.log(foo); // Foo {}
console.log(foo.toString()); // [object Object]
console.log(foo[Symbol.toStringTag]); // undefined
class Bar {
  constructor() {
    this[Symbol.toStringTag] = "Bar";
  }
}
let bar = new Bar();
console.log(bar); // Bar {}
console.log(bar.toString()); // [object Bar]
console.log(bar[Symbol.toStringTag]); // Bar
```

## 3.5. 操作符

ECMA-262 描述了一组可用于操作数据值的操作符，包括数学操作符（如加、减）、位操作符、关系操作符和相等操作符等。ECMAScript 中的操作符是独特的，因为它们可用于各种值，包括字符串、数值、布尔值，甚至还有对象。在应用给对象时，操作符通常会调用 valueOf()和/或 toString()方法来取得可以计算的值。

### 3.5.1. 一元操作符

只操作一个值的操作符叫 **一元操作符(unary operator)**。一元操作符是 ECMAScript 中最简单的操作符。

1. **递增/递减操作符**

递增和递减操作符直接照搬自 C 语言，但有两个版本：前缀版和后缀版。顾名思义，前缀版就是位于要操作的变量前头，后缀版就是位于要操作的变量后头。前缀递增操作符会给数值加 1，把两个加号（++）放到变量前头即可：

```js
let age = 29;
++age;
```

在这个例子中，前缀递增操作符把 age 的值变成了 30（给之前的值 29 加 1）。因此，它实际上等于如下表达式：

```js
let age = 29;
age = age + 1;
```

前缀递减操作符也类似，只不过是从一个数值减 1。使用前缀递减操作符，只要把两个减号（--）放到变量前头即可：

```js
let age = 29;
--age;
```

执行操作后，变量 age 的值变成了 28（从 29 减 1）。

后缀版递增/递减操作符和前缀版在语句上的功能是相同的。

```js
let age = 29;
age++;
console.log(age); // 30
age--;
console.log(age); // 29
```

注意 涉及递增/递减操作符的语句也是表达式。有时会带来意想不到的结果。请看下面的例子：

```js
let age = 29;
++age;
console.log(++age); // 31
console.log(age); // 31
age--;
console.log(age--); // 30
console.log(age); // 29
```

要理解上面的例子，我们需要理解 `++age` 不仅是一条语句，也是一个表达式。`++age` 在作为语句时的效果是将 age 的值增加 1，作为表达式时，`++age` 的值是 `age + 1`。

我们重新观察上面的例子，一开始声明了一个变量 age，并初始化为 29。之后，`++age`作为语句将 age 的值加 1，所以 age 变为 30。之后输出 `++age` 的值，也就是 31，但是同时这也是一条语句，它将 age 的值增加 1，因此后面的 age 为 31。

后缀版的递增/递减操作符则和前缀版的不同，具体来说，在作为语句时后缀版的和前缀版的效果相同。但作为表达式时，它的值为原先的值。

因此我们看到，之后，`age--` 将 age 的值减 1，age 的值变为 31-1=30。后面输出 `age--` 的值，它是原先的值 30，这和前缀版的不同，同时作为语句它将 age 的值减 1，age 变为 29，所以后面输出 age 为 29。

递增/递减操作符不仅限于操作数值类型的值。它在操作其他类型的值时，有以下规则：

- 对于字符串，如果是有效的数值形式，则转换为数值再应用改变。变量类型从字符串变成数值。
- 对于字符串，如果不是有效的数值形式，则将变量的值设置为 NaN 。变量类型从字符串变成数值。
- 对于布尔值，如果是 false，则转换为 0 再应用改变。变量类型从布尔值变成数值。
- 对于布尔值，如果是 true，则转换为 1 再应用改变。变量类型从布尔值变成数值。
- 对于浮点值，加 1 或减 1。
- 如果是对象，则调用其（第 5 章会详细介绍的）valueOf()方法取得可以操作的值。对得到的值应用上述规则。如果是 NaN，则调用 toString()并再次应用其他规则。变量类型从对象变成数值。

请看示例：

```js
let s1 = "2";
let s2 = "z";
let b = false;
let o = {
  valueOf() {
    return -1;
  },
};

console.log(++s1); // 3
console.log(s1); // 3
console.log(typeof s1); // number

console.log(++s2); // NaN
console.log(s2); // NaN
console.log(typeof s2); // number

console.log(b++); // 0
console.log(b); // 1
console.log(typeof b); // number

console.log(o--); // -1
console.log(o); // -2
console.log(typeof o); // number
```

2. **正/负操作符**

正/负操作符对大多数开发者来说并不陌生，它们在 ECMAScript 中跟在数学中的用途一样。正号由（+）表示，放在变量前头，对数值没有任何影响：

```js
let num = 25;
num = +num;
console.log(num); // 25
```

如果将正号应用到非数值，则会执行与使用 Number()转型函数一样的类型转换：布尔值 false 和 true 转换为 0 和 1，字符串根据特殊规则进行解析，对象会调用它们的 valueOf()和/或 toString()方法以得到可以转换的值。

下面的例子演示了正号在应用到不同数据类型时的行为：

```js
let s1 = "01";
let s2 = "1.1";
let s3 = "z";
let b = false;
let f = 1.1;
let o = {
  valueOf() {
    return -1;
  },
};
s1 = +s1; // 值变成数值1
s2 = +s2; // 值变成数值1.1
s3 = +s3; // 值变成NaN
b = +b; // 值变成数值0
f = +f; // 不变，还是1.1
o = +o; // 值变成数值-1
```

负号由一个（-）表示，放在变量前头，主要用于把数值变成负值，如把 1 转换为-1。示例如下：

```js
let num = 25;
num = -num;
console.log(num); // -25
```

对数值使用负号会将其变成相应的负值（如上面的例子所示）。在应用到非数值时，负号会遵循与一元加同样的规则，先对它们进行转换，然后再取负值：

```js
let s1 = "01";
let s2 = "1.1";
let s3 = "z";
let b = false;
let f = 1.1;
let o = {
  valueOf() {
    return -1;
  },
};
s1 = -s1; // 值变成数值-1
s2 = -s2; // 值变成数值-1.1
s3 = -s3; // 值变成NaN
b = -b; // 值变成数值0
f = -f; // 变成-1.1
o = -o; // 值变成数值1
```

正号和负号操作符主要用于基本的算术，但也可以像上面的例子那样，用于数据类型转换。

### 3.5.2. 位操作符

接下来要介绍的操作符用于数值的底层操作，也就是操作内存中表示数据的比特（位）。ECMAScript 中的所有数值都以 IEEE 754 64 位格式存储，但位操作并不直接应用到 64 位表示，而是先把值转换为 32 位整数，再进行位操作，之后再把结果转换为 64 位。对开发者而言，就好像只有 32 位整数一样，因为 64 位整数存储格式是不可见的。既然知道了这些，就只需要考虑 32 位整数即可。

有符号整数使用 32 位的前 31 位表示整数值。第 32 位表示数值的符号，如 0 表示正，1 表示负。这一位称为符号位(sign bit)，它的值决定了数值其余部分的格式。正值以真正的二进制格式存储，即 31 位中的每一位都代表 2 的幂。第一位（称为第 0 位）表示 2^0，第二位表示 2^1，依此类推。如果一个位是空的，则以 0 填充，相当于忽略不计。比如，数值 18 的二进制格式为 00000000000000000000000000010010，或更精简的 10010。后者是用到的 5 个有效位，决定了实际的值（如下图所示）。

![3-1-二进制表示](illustrations/3-1-二进制表示.png)

负值以一种称为二补数（或补码）的二进制编码存储。一个数值的二补数通过如下 3 个步骤计算得到：

1. 确定绝对值的二进制表示（如，对于-18，先确定 18 的二进制表示）；
2. 找到数值的一补数（或反码），换句话说，就是每个 0 都变成 1，每个 1 都变成 0；
3. 给结果加 1。

基于上述步骤确定- 18 的二进制表示，首先从 18 的二进制表示开始：

0000 0000 0000 0000 0000 0000 0001 0010

然后，计算补数，即反转每一位的二进制值：

1111 1111 1111 1111 1111 1111 1110 1101

最后，给一补数加 1：

```
1111 1111 1111 1111 1111 1111 1110 1101
                                      1
----------------------------------------------
1111 1111 1111 1111 1111 1111 1110 1110
```

那么，-18 的二进制表示就是 11111111111111111111111111101110。要注意的是，在处理有符号整数时，我们无法访问第 31 位。

ECMAScript 会帮我们记录这些信息。在把负值输出为一个二进制字符串时，我们会得到一个前面加了减号的绝对值，如下所示：

```js
let num = -18;
console.log(num.toString(2)); // "-10010"
```

在将-18 转换为二进制字符串时，结果得到 -10010。转换过程会求得二补数，然后再以更符合逻辑的形式表示出来。

在对 ECMAScript 中的数值应用位操作符时，后台会发生转换：64 位数值会转换为 32 位数值，然后执行位操作，最后再把结果从 32 位转换为 64 位存储起来。整个过程就像处理 32 位数值一样，这让二进制操作变得与其他语言中类似。但这个转换也导致了一个奇特的副作用，即特殊值 NaN 和 Infinity 在位操作中都会被当成 0 处理。

如果将位操作符应用到非数值，那么首先会使用 Number()函数将该值转换为数值（这个过程是自动的），然后再应用位操作。最终结果是数值。

1. **按位非**

按位非操作符用波浪符（~）表示，它的作用是返回数值的一补数。按位非是 ECMAScript 中为数不多的几个二进制数学操作符之一。看下面的例子：

```js
let num1 = 25; // 二进制00000000000000000000000000011001
let num2 = ~num1; // 二进制11111111111111111111111111100110
console.log(num2); // -26
```

这里，按位非操作符作用到了数值 25，得到的结果是 -26。由此可以看出，按位非的最终效果是对数值取负并减 1，就像执行如下操作的结果一样：

```js
let num1 = 25;
let num2 = -num1 - 1;
console.log(num2); // "-26"
```

实际上，尽管两者返回的结果一样，但位操作的速度快得多。这是因为位操作是在数值的底层表示上完成的。

两个按位非操作符效果上等同于 Math.trunc()，截断了小数部分：

```js
function test = (number) => ~~number === Math.trunc(number);
console.log(test(1.05)); // true
console.log(test(-1.05)); // true
```

但不同的是，Math.trunc(NaN) 返回 NaN，Math.trunc(Infinity) 返回 Infinity，而`~~`对于这 2 个数值返回 0。例如：

```js
console.log(Math.trunc(NaN)); // NaN
console.log(~~NaN); // 0
console.log(Math.trunc(Infinity)); // Infinity
console.log(~~Infinity); // 0
```

从某些方面来说，开发者更愿意使用 `~~`；

2. **按位与**

按位与操作符用和号（&）表示，有两个操作数。本质上，按位与就是将两个数的每一个位对齐，然后基于真值表中的规则，对每一位执行相应的与操作。

| 第一个数值的位 | 第二个数值的位 | 结果 |
| -------------- | -------------- | ---- |
| 1              | 1              | 1    |
| 1              | 0              | 0    |
| 0              | 1              | 0    |
| 0              | 0              | 0    |

按位与操作在两个位都是 1 时返回 1，在任何一位是 0 时返回 0。下面看一个例子，我们对数值 25 和 3 求与操作，如下所示：

```js
let result = 25 & 3;
console.log(result); // 1
```

25 和 3 的按位与操作的结果是 1。为什么呢？看下面的二进制计算过程：

```
25 = 0000 0000 0000 0000 0000 0000 0001 1001
3 = 0000 0000 0000 0000 0000 0000 0000 0011
---------------------------------------------
AND = 0000 0000 0000 0000 0000 0000 0000 0001
```

如上所示，25 和 3 的二进制表示中，只有第 0 位上的两个数都是 1。于是结果数值的所有其他位都会以 0 填充，因此结果就是 1。

3. **按位或**

按位或操作符用管道符（|）表示，同样有两个操作数。按位或遵循如下真值表：

| 第一个数值的位 | 第二个数值的位 | 结果 |
| -------------- | -------------- | ---- |
| 1              | 1              | 1    |
| 1              | 0              | 1    |
| 0              | 1              | 1    |
| 0              | 0              | 0    |

按位或操作在至少一位是 1 时返回 1，两位都是 0 时返回 0。仍然用按位与的示例，如果对 25 和 3 执行按位或，代码如下所示：

```js
let result = 25 | 3;
console.log(result); // 27
```

可见 25 和 3 的按位或操作的结果是 27：

```
25 = 0000 0000 0000 0000 0000 0000 0001 1001
3 = 0000 0000 0000 0000 0000 0000 0000 0011
---------------------------------------------
OR = 0000 0000 0000 0000 0000 0000 0001 1011
```

在参与计算的两个数中，有 4 位都是 1，因此它们直接对应到结果上。二进制码 11011 等于 27。

4. **按位异或**

按位异或用脱字符（^）表示，同样有两个操作数。下面是按位异或的真值表：

| 第一个数的位 | 第二个数的位 | 结果 |
| ------------ | ------------ | ---- |
| 1            | 1            | 0    |
| 1            | 0            | 1    |
| 0            | 1            | 1    |
| 0            | 0            | 0    |

按位异或与按位或的区别是，它只在一位上是 1 的时候返回 1（两位都是 1 或 0，则返回 0）。对数值 25 和 3 执行按位异或操作：

```js
let result = 25 ^ 3;
console.log(result); // 26
```

可见，25 和 3 的按位异或操作结果为 26，如下所示：

```
25 = 0000 0000 0000 0000 0000 0000 0001 1001
3 = 0000 0000 0000 0000 0000 0000 0000 0011
---------------------------------------------
XOR = 0000 0000 0000 0000 0000 0000 0001 1010
```

两个数在 4 位上都是 1，但两个数的第 0 位都是 1，因此那一位在结果中就变成了 0。其余位上的 1 在另一个数上没有对应的 1，因此会直接传递到结果中。二进制码 11010 等于 26。（注意，这比对同样两个值执行按位或操作得到的结果小 1。）

5. **左移**

左移操作符用两个小于号（<<）表示，会按照指定的位数将数值的所有位向左移动。比如，如果数值 2（二进制 10）向左移 5 位，就会得到 64（二进制 1000000），如下所示：

```js
let oldValue = 2; // 等于二进制10
let newValue = oldValue << 5; // 等于二进制1000000，即十进制64
```

注意在移位后，数值右端会空出 5 位。左移会以 0 填充这些空位，让结果是完整的 32 位数值（见下图）。

![3-2-位左移](illustrations/3-2-位左移.png)

注意，左移会保留它所操作数值的符号。比如，如果 -2 左移 5 位，将得到-64，而不是正 64。

6. **有符号右移**

有符号右移由两个大于号（>>）表示，会将数值的所有 32 位都向右移，同时保留符号（正或负）。有符号右移实际上是左移的逆运算。比如，如果将 64 右移 5 位，那就是 2：

```js
let oldValue = 64; // 等于二进制1000000
let newValue = oldValue >> 5; // 等于二进制10，即十进制2
```

同样，移位后就会出现空位。不过，右移后空位会出现在左侧，且在符号位之后（见下图）。ECMAScript 会用符号位的值来填充这些空位，以得到完整的数值。

![3-4-位右移](illustrations/3-4-位右移.png)

7. **无符号右移**

无符号右移用 3 个大于号表示（>>>），会将数值的所有 32 位都向右移。对于正数，无符号右移与有符号右移结果相同。仍然以前面有符号右移的例子为例，64 向右移动 5 位，会变成 2：

```js
let oldValue = 64; // 等于二进制1000000
let newValue = oldValue >>> 5; // 等于二进制10，即十进制2
```

对于负数，有时候差异会非常大。与有符号右移不同，无符号右移会给空位补 0，而不管符号位是什么。对正数来说，这跟有符号右移效果相同。但对负数来说，结果就差太多了。无符号右移操作符将负数的二进制表示当成正数的二进制表示来处理。因为负数是其绝对值的二补数，所以右移之后结果变得非常之大，如下面的例子所示：

```js
let oldValue = -64; // 等于二进制11111111111111111111111111000000
let newValue = oldValue >>> 5; // 等于十进制134217726
```

在对-64 无符号右移 5 位后，结果是 134 217 726。这是因为-64 的二进制表示是 11111111111111111111111111000000，无符号右移却将它当成正值，也就是 4 294 967 232。把这个值右移 5 位后，结果是 00000111111111111111111111111110，即 134 217 726。

### 3.5.3. 布尔操作符

对于编程语言来说，布尔操作符跟相等操作符几乎同样重要。如果没有能力测试两个值的关系，那么像 if-else 和循环这样的语句也没什么用了。布尔操作符一共有 3 个：逻辑非、逻辑与和逻辑或。

1. **逻辑非**

逻辑非操作符由一个叹号（!）表示，可应用给 ECMAScript 中的任何值。这个操作符始终返回布尔值，无论应用到的是什么数据类型。逻辑非操作符首先将操作数转换为布尔值，然后再对其取反。换句话说，逻辑非操作符会遵循如下规则。

- 如果操作数是对象，则返回 false。
- 如果操作数是空字符串，则返回 true。
- 如果操作数是非空字符串，则返回 false。
- 如果操作数是数值 0，则返回 true。
- 如果操作数是非 0 数值（包括 Infinity），则返回 false。
- 如果操作数是 null，则返回 true。
- 如果操作数是 NaN，则返回 true。
- 如果操作数是 undefined，则返回 true。

以下示例验证了上述行为：

```js
console.log(!false); // true
console.log(!"blue"); // false
console.log(!0); // true
console.log(!NaN); // true
console.log(!""); // true
console.log(!12345); // false
```

逻辑非操作符也可以用于把任意值转换为布尔值。同时使用两个叹号（!!），相当于调用了转型函数 Boolean()。无论操作数是什么类型，第一个叹号总会返回布尔值。第二个叹号对该布尔值取反，从而给出变量真正对应的布尔值。结果与对同一个值使用 Boolean()函数是一样的：

```js
console.log(!!"blue"); // true
console.log(!!0); // false
console.log(!!NaN); // false
console.log(!!""); // false
console.log(!!12345); // true
```

2. **逻辑与**

逻辑与操作符由两个和号（&&）表示，应用到两个值，如下所示：

```js
let result = true && false;
```

逻辑与操作符遵循如下真值表：

| 第一个操作数 | 第二个操作数 | 结果  |
| ------------ | ------------ | ----- |
| true         | true         | true  |
| true         | false        | false |
| false        | true         | false |
| false        | false        | false |

逻辑与操作符可用于任何类型的操作数，不限于布尔值。如果有操作数不是布尔值，则逻辑与并不一定会返回布尔值，而是遵循如下规则。

- 如果第一个操作数是对象，则返回第二个操作数。
- 如果第二个操作数是对象，则只有第一个操作数求值为 true 才会返回该对象。
- 如果两个操作数都是对象，则返回第二个操作数。
- 如果有一个操作数是 null，则返回 null。
- 如果有一个操作数是 NaN，则返回 NaN。
- 如果有一个操作数是 undefined，则返回 undefined。

逻辑与操作符是一种短路操作符，意思就是如果第一个操作数决定了结果，那么永远不会对第二个操作数求值。对逻辑与操作符来说，如果第一个操作数是 false，那么无论第二个操作数是什么值，结果也不可能等于 true。看下面的例子：

```js
let found = true;
let result = found && someUndeclaredVariable; // 这里会出错
console.log(result); // 不会执行这一行
```

上面的代码之所以会出错，是因为 someUndeclaredVariable 没有事先声明，所以当逻辑与操作符对它求值时就会报错。变量 found 的值是 true，逻辑与操作符会继续求值变量 someUndeclaredVariable。但是由于 someUndeclaredVariable 没有定义，不能对它应用逻辑与操作符，因此就报错了。假如变量 found 的值是 false，那么就不会报错了：

```js
let found = false;
let result = found && someUndeclaredVariable; // 不会出错
console.log(result); // 会执行
```

这里，console.log 会成功执行。即使变量 someUndeclaredVariable 没有定义，由于第一个操作数是 false，逻辑与操作符也不会对它求值，因为此时对&&右边的操作数求值是没有意义的。在使用逻辑与操作符时，一定别忘了它的这个短路的特性。

3. **逻辑或**

逻辑或操作符由两个管道符（||）表示，比如：

```js
let result = true || false;
```

逻辑或操作符遵循如下真值表：

| 第一个操作数 | 第二个操作数 | 结果  |
| ------------ | ------------ | ----- |
| true         | true         | true  |
| true         | false        | true  |
| false        | true         | true  |
| false        | false        | false |

与逻辑与类似，如果有一个操作数不是布尔值，那么逻辑或操作符也不一定返回布尔值。它遵循如下规则。

- 如果第一个操作数是对象，则返回第一个操作数。
- 如果第一个操作数求值为 false，则返回第二个操作数。
- 如果两个操作数都是对象，则返回第一个操作数。
- 如果两个操作数都是 null，则返回 null。
- 如果两个操作数都是 NaN，则返回 NaN。
- 如果两个操作数都是 undefined，则返回 undefined。

同样与逻辑与类似，逻辑或操作符也具有短路的特性。只不过对逻辑或而言，第一个操作数求值为 true，第二个操作数就不会再被求值了。看下面的例子：

```js
let found = true;
let result = found || someUndeclaredVariable; // 不会出错
console.log(result); // 会执行
```

跟前面的例子一样，变量 someUndeclaredVariable 也没有定义。但是，因为变量 found 的值为 true，所以逻辑或操作符不会对变量 someUndeclaredVariable 求值，而直接返回 true。假如把 found 的值改为 false，那就会报错了：

```js
let found = false;
let result = found || someUndeclaredVariable; // 这里会出错
console.log(result); // 不会执行这一行
```

利用这个行为，可以避免给变量赋值 null 或 undefined。比如：

```js
let myObject = preferredObject || backupObject;
```

在这个例子中，变量 myObject 会被赋予两个值中的一个。其中，preferredObject 变量包含首选的值，backupObject 变量包含备用的值。如果 preferredObject 不是 null，则它的值就会赋给 myObject；如果 preferredObject 是 null，则 backupObject 的值就会赋给 myObject。这种模式在 ECMAScript 代码中经常用于变量赋值，本书后面的代码示例中也会经常用到。

### 3.5.4. 乘性操作符

ECMAScript 定义了 3 个乘性操作符：乘法、除法和取模。这些操作符跟它们在 Java、C 语言及 Perl 中对应的操作符作用一样，但在处理非数值时，它们也会包含一些自动的类型转换。如果乘性操作符有不是数值的操作数，则该操作数会在后台被使用 Number()转型函数转换为数值。这意味着空字符串会被当成 0，而布尔值 true 会被当成 1。

1. **乘法操作符**

乘法操作符由一个星号（\*）表示，可以用于计算两个数值的乘积。其语法类似于 C 语言，比如：

```js
let result = 34 * 56;
```

不过，乘法操作符在处理特殊值时也有一些特殊的行为。

- 如果操作数都是数值，则执行常规的乘法运算，即两个正值相乘是正值，两个负值相乘也是正值，正负符号不同的值相乘得到负值。如果 ECMAScript 不能表示乘积，则返回 Infinity 或-Infinity。
- 如果有任一操作数是 NaN，则返回 NaN。如果是 Infinity 乘以 0，则返回 NaN。
- 如果是 Infinity 乘以非 0 的有限数值，则根据第二个操作数的符号返回 Infinity 或-Infinity。
- 如果是 Infinity 乘以 Infinity，则返回 Infinity。
- 如果有不是数值的操作数，则先在后台用 Number()将其转换为数值，然后再应用上述规则。

2. **除法操作符**

除法操作符由一个斜杠（/）表示，用于计算第一个操作数除以第二个操作数的商，比如：

```js
let result = 66 / 11;
```

跟乘法操作符一样，除法操作符针对特殊值也有一些特殊的行为。

- 如果操作数都是数值，则执行常规的除法运算，即两个正值相除是正值，两个负值相除也是正值，符号不同的值相除得到负值。如果 ECMAScript 不能表示商，则返回 Infinity 或-Infinity。
- 如果有任一操作数是 NaN，则返回 NaN。
- 如果是 Infinity 除以 Infinity，则返回 NaN。
- 如果是 0 除以 0，则返回 NaN。
- 如果是非 0 的有限值除以 0，则根据第一个操作数的符号返回 Infinity 或-Infinity。
- 如果是 Infinity 除以任何数值，则根据第二个操作数的符号返回 Infinity 或-Infinity。
- 如果有不是数值的操作数，则先在后台用 Number()函数将其转换为数值，然后再应用上述规则。

3. **取余操作符**

取余（余数）操作符由一个百分比符号（%）表示，比如：

```js
let result = 26 % 5; // 等于1
```

与其他乘性操作符一样，取模操作符对特殊值也有一些特殊的行为。

- 如果操作数是数值，则执行常规除法运算，返回余数。
- 如果被除数是无限值，除数是有限值，则返回 NaN。
- 如果被除数是有限值，除数是 0，则返回 NaN。
- 如果是 Infinity 除以 Infinity，则返回 NaN。
- 如果被除数是有限值，除数是无限值，则返回被除数。
- 如果被除数是 0，除数不是 0，则返回 0。
- 如果有不是数值的操作数，则先在后台用 Number()函数将其转换为数值，然后再应用上述规则。

### 3.5.5. 指数操作符

ECMAScript 7 新增了指数操作符，Math.pow()现在有了自己的操作符\*\*，结果是一样的：

```js
console.log(Math.pow(3, 2); // 9
console.log(3 ** 2); // 9
console.log(Math.pow(16, 0.5); // 4
console.log(16** 0.5); // 4
```

不仅如此，指数操作符也有自己的指数赋值操作符\*\*=，该操作符执行指数运算和结果的赋值操作：

```js
let squared = 3;
squared **= 2;
console.log(squared); // 9
let sqrt = 16;
sqrt **= 0.5;
console.log(sqrt); // 4
```

### 3.5.6. 加性操作符

加性操作符，即加法和减法操作符，一般都是编程语言中最简单的操作符。不过，在 ECMAScript 中，这两个操作符拥有一些特殊的行为。与乘性操作符类似，加性操作符在后台会发生不同数据类型的转换。只不过对这两个操作符来说，转换规则不是那么直观。

1. **加法操作符**

加法操作符（+）用于求两个数的和，比如：

```js
let result = 1 + 2;
```

如果两个操作数都是数值，加法操作符执行加法运算并根据如下规则返回结果：

- 如果有任一操作数是 NaN，则返回 NaN；
- 如果是 Infinity 加 Infinity，则返回 Infinity；
- 如果是-Infinity 加-Infinity，则返回-Infinity；
- 如果是 Infinity 加-Infinity，则返回 NaN；
- 如果是+0 加+0，则返回+0；
- 如果是-0 加+0，则返回+0；
- 如果是-0 加-0，则返回-0。不过，如果有一个操作数是字符串，则要应用如下规则：
- 如果两个操作数都是字符串，则将第二个字符串拼接到第一个字符串后面；
- 如果只有一个操作数是字符串，则将另一个操作数转换为字符串，再将两个字符串拼接在一起。

如果有任一操作数是对象、数值或布尔值，则调用它们的 toString()方法以获取字符串，然后再应用前面的关于字符串的规则。对于 undefined 和 null，则调用 String()函数，分别获取 "undefined"和"null"。

看下面的例子：

```js
let result1 = 5 + 5; // 两个数值
console.log(result1); // 10
let result2 = 5 + "5"; // 一个数值和一个字符串
console.log(result2); // "55"
```

以上代码展示了加法操作符的两种运算模式。正常情况下，5 + 5 等于 10（数值），如前两行代码所示。但是，如果将一个操作数改为字符串，比如"5"，则相加的结果就变成了"55"（原始字符串值），因为第一个操作数也会被转换为字符串。

ECMAScript 中最常犯的一个错误，就是忽略加法操作中涉及的数据类型。比如下面这个例子：

```js
let num1 = 5;
let num2 = 10;
let message = "5和10的和是" + num1 + num2;
console.log(message); // "5和10的和是510"
```

这里，变量 message 中保存的是一个字符串，是执行两次加法操作之后的结果。有人可能会认为最终得到的字符串是"5 和 10 的和是 15"。可是，实际上得到的是"5 和 10 的和是 510"。这是因为每次加法运算都是独立完成的。第一次加法的操作数是一个字符串和一个数值（5），结果还是一个字符串。第二次加法仍然是用一个字符串去加一个数值（10），同样也会得到一个字符串。如果想真正执行数学计算，然后把结果追加到字符串末尾，只要使用一对括号即可：

```js
let num1 = 5;
let num2 = 10;
let message = "5和10的和是" + (num1 + num2);
console.log(message); // "5和10的和是15"
```

在此，我们用括号把两个数值变量括了起来，意思是让解释器先执行两个数值的加法，然后再把结果追加给字符串。因此，最终得到的字符串变成了"5 和 10 的和是 15"。

2. **减法操作符**

减法操作符（-）也是使用很频繁的一种操作符，比如：

```js
let result = 2 - 1;
```

与加法操作符一样，减法操作符也有一组规则用于处理 ECMAScript 中不同类型之间的转换。

- 如果两个操作数都是数值，则执行数学减法运算并返回结果。
- 如果有任一操作数是 NaN，则返回 NaN。
- 如果是 Infinity 减 Infinity，则返回 NaN。
- 如果是-Infinity 减-Infinity，则返回 NaN。
- 如果是 Infinity 减-Infinity，则返回 Infinity。
- 如果是-Infinity 减 Infinity，则返回-Infinity。
- 如果是+0 减+0，则返回+0。
- 如果是+0 减-0，则返回-0。
- 如果是-0 减-0，则返回+0。
- 如果有任一操作数是字符串、布尔值、null 或 undefined，则先在后台使用 Number()将其转换为数值，然后再根据前面的规则执行数学运算。如果转换结果是 NaN，则减法计算的结果是 NaN。
- 如果有任一操作数是对象，则调用其 valueOf()方法取得表示它的数值。如果该值是 NaN，则减法计算的结果是 NaN。如果对象没有 valueOf()方法，则调用其 toString()方法，然后再将得到的字符串转换为数值。

以下示例演示了上面的规则：

```js
let result1 = 5 - true; // true 被转换为1，所以结果是4
let result2 = NaN - 1; // NaN
let result3 = 5 - 3; // 2
let result4 = 5 - ""; // ""被转换为0，所以结果是5
let result5 = 5 - "2"; // "2"被转换为2，所以结果是3
let result6 = 5 - null; // null 被转换为0，所以结果是5
```

### 3.5.7. 关系操作符

关系操作符执行比较两个值的操作，包括小于（<）、大于（>）、小于等于（<=）和大于等于（>=），用法跟数学课上学的一样。这几个操作符都返回布尔值，如下所示：

```js
let result1 = 5 > 3; // true
let result2 = 5 < 3; // false
```

与 ECMAScript 中的其他操作符一样，在将它们应用到不同数据类型时也会发生类型转换和其他行为。

- 如果操作数都是数值，则执行数值比较。
- 如果操作数都是字符串，则逐个比较字符串中对应字符的编码。
- 如果有任一操作数是数值，则将另一个操作数转换为数值，执行数值比较。
- 如果有任一操作数是对象，则调用其 valueOf()方法，取得结果后再根据前面的规则执行比较。
  如果没有 valueOf()操作符，则调用 toString()方法，取得结果后再根据前面的规则执行比较。
- 如果有任一操作数是布尔值，则将其转换为数值再执行比较。

在使用关系操作符比较两个字符串时，会发生一个有趣的现象。很多人认为小于意味着“字母顺序靠前”，而大于意味着“字母顺序靠后”，实际上不是这么回事。对字符串而言，关系操作符会比较字符串中对应字符的编码，而这些编码是数值。比较完之后，会返回布尔值。问题的关键在于，大写字母的编码都小于小写字母的编码，因此以下这种情况就会发生：

```js
let result = "Brick" < "alphabet"; // true
```

在这里，字符串"Brick"被认为小于字符串"alphabet"，因为字母 B 的编码是 66，字母 a 的编码是 97。要得到确实按字母顺序比较的结果，就必须把两者都转换为相同的大小写形式（全大写或全小写），然后再比较：

```js
let result = "Brick".toLowerCase() < "alphabet".toLowerCase(); // false
```

将两个操作数都转换为小写，就能保证按照字母表顺序判定"alphabet"在"Brick"前头。另一个奇怪的现象是在比较两个数值字符串的时候，比如下面这个例子：

```js
let result = "23" < "3"; // true
```

这里在比较字符串"23"和"3"时返回 true。因为两个操作数都是字符串，所以会逐个比较它们的字符编码（字符"2"的编码是 50，而字符"3"的编码是 51）。不过，如果有一个操作数是数值，那么比较的结果就对了：

```js
let result = "23" < 3; // false
```

因为这次会将字符串"23"转换为数值 23，然后再跟 3 比较，结果当然对了。只要是数值和字符串比较，字符串就会先被转换为数值，然后进行数值比较。对于数值字符串而言，这样能保证结果正确。但如果字符串不能转换成数值呢？比如下面这个例子：

```js
let result = "a" < 3; // 因为"a"会转换为NaN，所以结果是false
```

因为字符"a"不能转换成任何有意义的数值，所以只能转换为 NaN。这里有一个规则，即任何关系操作符在涉及比较 NaN 时都返回 false。这样一来，下面的例子有趣了：

```js
let result1 = NaN < 3; // false
let result2 = NaN >= 3; // false
```

在大多数比较的场景中，如果一个值不小于另一个值，那就一定大于或等于它。但在比较 NaN 时，无论是小于还是大于等于，比较的结果都会返回 false。

### 3.5.8. 相等操作符

判断两个变量是否相等是编程中最重要的操作之一。在比较字符串、数值和布尔值是否相等时，过程都很直观。但是在比较两个对象是否相等时，情形就比较复杂了。ECMAScript 中的相等和不相等操作符，原本在比较之前会执行类型转换，但很快就有人质疑这种转换是否应该发生。最终，ECMAScript 提供了两组操作符。第一组是等于和不等于，它们在比较之前执行转换。第二组是全等和不全等，它们在比较之前不执行转换。

1. **等于和不等于**

ECMAScript 中的等于操作符用两个等于号（==）表示，如果操作数相等，则会返回 true。不等于操作符用叹号和等于号（!=）表示，如果两个操作数不相等，则会返回 true。这两个操作符都会先进行类型转换（通常称为 **强制类型转换**）再确定操作数是否相等。

在转换操作数的类型时，相等和不相等操作符遵循如下规则。

- 如果任一操作数是布尔值，则将其转换为数值再比较是否相等。false 转换为 0，true 转换为 1。
- 如果一个操作数是字符串，另一个操作数是数值，则尝试将字符串转换为数值，再比较是否相等。
- 如果一个操作数是对象，另一个操作数不是，则调用对象的 valueOf()方法取得其原始值，再根据前面的规则进行比较。
  在进行比较时，这两个操作符会遵循如下规则。
- null 和 undefined 相等。
- null 和 undefined 不能转换为其他类型的值再进行比较。
- 如果有任一操作数是 NaN，则相等操作符返回 false，不相等操作符返回 true。记住：即使两个操作数都是 NaN，相等操作符也返回 false，因为按照规则，NaN 不等于 NaN。
- 如果两个操作数都是对象，则比较它们是不是同一个对象。如果两个操作数都指向同一个对象，则相等操作符返回 true。否则，两者不相等。

下表总结了一些特殊情况及比较的结果。

| 表 达 式          | 结 果 |
| ----------------- | ----- |
| null == undefined | true  |
| "NaN" == NaN      | false |
| 5 == NaN          | false |
| NaN == NaN        | false |
| NaN != NaN        | true  |
| false == 0        | true  |
| true == 1         | true  |
| true == 2         | false |
| undefined == 0    | false |
| null == 0         | false |
| "5" == 5          | true  |

2. **全等和不全等**

全等和不全等操作符与相等和不相等操作符类似，只不过它们在比较相等时不转换操作数。全等操作符由 3 个等于号（===）表示，只有两个操作数在不转换的前提下相等才返回 true，比如：

```js
let result1 = "55" == 55; // true，转换后相等
let result2 = "55" === 55; // false，不相等，因为数据类型不同
```

在这个例子中，第一个比较使用相等操作符，比较的是字符串"55"和数值 55。如前所述，因为字符串"55"会被转换为数值 55，然后再与数值 55 进行比较，所以返回 true。第二个比较使用全等操作符，因为没有转换，字符串和数值当然不能相等，所以返回 false。

不全等操作符用一个叹号和两个等于号（!==）表示，只有两个操作数在不转换的前提下不相等才返回 true。比如：

```js
let result1 = "55" != 55; // false，转换后相等
let result2 = "55" !== 55; // true，不相等，因为数据类型不同
```

这一次，第一个比较使用不相等操作符，它会把字符串"55"转换为数值 55，跟第二个操作数相等。既然转换后两个值相等，那就返回 false。第二个比较使用不全等操作符。这时候可以这么问：“字符串 55 和数值 55 有区别吗？”答案是“有”（true）

另外，虽然 null == undefined 是 true（因为这两个值类似），但 null === undefined 是 false，因为它们不是相同的数据类型。

注意 由于相等和不相等操作符存在类型转换问题，因此推荐使用全等和不全等操作符。这样有助于在代码中保持数据类型的完整性。

### 3.5.9. 条件操作符

条件操作符是 ECMAScript 中用途最为广泛的操作符之一，语法跟 Java 中一样：

```js
variable = boolean_expression ? true_value : false_value;
```

上面的代码执行了条件赋值操作，即根据条件表达式 boolean_expression 的值决定将哪个值赋给变量 variable 。如果 boolean_expression 是 true ， 则赋值 true_value ； 如果 boolean_expression 是 false，则赋值 false_value。比如：

```js
let max = num1 > num2 ? num1 : num2;
```

在这个例子中，max 将被赋予一个最大值。这个表达式的意思是，如果 num1 大于 num2（条件表达式为 true），则将 num1 赋给 max。否则，将 num2 赋给 max。

### 3.5.10. 赋值操作符

简单赋值用等于号（=）表示，将右手边的值赋给左手边的变量，如下所示：

```js
let num = 10;
```

复合赋值使用乘性、加性或位操作符后跟等于号（=）表示。这些赋值操作符是类似如下常见赋值操作的简写形式：

```js
let num = 10;
num = num + 10;
```

以上代码的第二行可以通过复合赋值来完成：

```js
let num = 10;
num += 10;
```

每个数学操作符以及其他一些操作符都有对应的复合赋值操作符：

- 乘后赋值（\*=）
- 除后赋值（/=）
- 取模后赋值（%=）
- 加后赋值（+=）
- 减后赋值（-=）
- 左移后赋值（<<=）
- 右移后赋值（>>=）
- 无符号右移后赋值（>>>=）

这些操作符仅仅是简写语法，使用它们不会提升性能。

### 3.5.11. 逗号操作符

逗号操作符可以用来在一条语句中执行多个操作，如下所示：

```js
let num1 = 1,
  num2 = 2,
  num3 = 3;
```

在一条语句中同时声明多个变量是逗号操作符最常用的场景。不过，也可以使用逗号操作符来辅助赋值。在赋值时使用逗号操作符分隔值，最终会返回表达式中最后一个值：

```js
let num = (5, 1, 4, 8, 0); // num 的值为0
```

在这个例子中，num 将被赋值为 0，因为 0 是表达式中最后一项。逗号操作符的这种使用场景并不多见，但这种行为的确存在。

## 3.6. 语句

ECMA-262 描述了一些语句（也称为流控制语句），而 ECMAScript 中的大部分语法都体现在语句中。语句通常使用一或多个关键字完成既定的任务。语句可以简单，也可以复杂。简单的如告诉函数退出，复杂的如列出一堆要重复执行的指令。

### 3.6.1. if 语句

if 语句是使用最频繁的语句之一，语法如下：

```js
if (condition) statement1 else statement2
```

这里的条件（condition）可以是任何表达式，并且求值结果不一定是布尔值。ECMAScript 会自动调用 Boolean()函数将这个表达式的值转换为布尔值。如果条件求值为 true，则执行语句 statement1；如果条件求值为 false，则执行语句 statement2。这里的语句可能是一行代码，也可能是一个代码块（即包含在一对花括号中的多行代码）。来看下面的例子：

```js
if (i > 25) console.log("Greater than 25.");
// 只有一行代码的语句
else {
  console.log("Less than or equal to 25."); // 一个语句块
}
```

这里的最佳实践是使用语句块，即使只有一行代码要执行也是如此。这是因为语句块可以避免对什么条件下执行什么产生困惑。

可以像这样连续使用多个 if 语句：

```js
if (condition1) statement1 else if (condition2) statement2 else statement3
```

下面是一个例子：

```js
if (i > 25) {
  console.log("Greater than 25.");
} else if (i < 0) {
  console.log("Less than 0.");
} else {
  console.log("Between 0 and 25, inclusive.");
}
```

### 3.6.2. do-while 语句

do-while 语句是一种后测试循环语句，即循环体中的代码执行后才会对退出条件进行求值。换句话说，循环体内的代码至少执行一次。do-while 的语法如下：

```js
do {
  statement;
} while (expression);
```

下面是一个例子：

```js
let i = 0;
do {
  i += 2;
} while (i < 10);
```

在这个例子中，只要 i 小于 10，循环就会重复执行。i 从 0 开始，每次循环递增 2。

注意 后测试循环经常用于这种情形：循环体内代码在退出前至少要执行一次。

### 3.6.3. while 语句

while 语句是一种先测试循环语句，即先检测退出条件，再执行循环体内的代码。因此，while 循环体内的代码有可能不会执行。下面是 while 循环的语法：

```js
while (expression) statement;
```

这是一个例子：

```js
let i = 0;
while (i < 10) {
  i += 2;
}
```

在这个例子中，变量 i 从 0 开始，每次循环递增 2。只要 i 小于 10，循环就会继续。

### 3.6.4. for 语句

for 语句也是先测试语句，只不过增加了进入循环之前的初始化代码，以及循环执行后要执行的表达式，语法如下：

```js
for (initialization; expression; post - loop - expression) statement;
```

下面是一个用例：

```js
let count = 10;
for (let i = 0; i < count; i++) {
  console.log(i);
}
```

以上代码在循环开始前定义了变量 i 的初始值为 0。然后求值条件表达式，如果求值结果为 true（i < count），则执行循环体。因此循环体也可能不会被执行。如果循环体被执行了，则循环后表达式也会执行，以便递增变量 i。for 循环跟下面的 while 循环是一样的：

```js
let count = 10;
let i = 0;
while (i < count) {
  console.log(i);
  i++;
}
```

无法通过 while 循环实现的逻辑，同样也无法使用 for 循环实现。因此 for 循环只是将循环相关的代码封装在了一起而已。

在 for 循环的初始化代码中，其实是可以不使用变量声明关键字的。不过，初始化定义的迭代器变量在循环执行完成后几乎不可能再用到了。因此，最清晰的写法是使用 let 声明迭代器变量，这样就可以将这个变量的作用域限定在循环中。

初始化、条件表达式和循环后表达式都不是必需的。因此，下面这种写法可以创建一个无穷循环：

```js
for (;;) {
  // 无穷循环
  doSomething();
}
```

如果只包含条件表达式，那么 for 循环实际上就变成了 while 循环：

```js
let count = 10;
let i = 0;
for (; i < count; ) {
  console.log(i);
  i++;
}
```

这种多功能性使得 for 语句在这门语言中使用非常广泛。

### 3.6.5. for-in 语句

for-in 语句是一种严格的迭代语句，用于枚举对象中的非符号键属性，语法如下：

```js
for (property in expression) statement;
```

下面是一个例子：

```js
for (const propName in window) {
  document.write(propName);
}
```

这个例子使用 for-in 循环显示了 BOM 对象 window 的所有属性。每次执行循环，都会给变量 propName 赋予一个 window 对象的属性作为值，直到 window 的所有属性都被枚举一遍。与 for 循环一样，这里控制语句中的 const 也不是必需的。但为了确保这个局部变量不被修改，推荐使用 const。

ECMAScript 中对象的属性是无序的，因此 for-in 语句不能保证返回对象属性的顺序。换句话说，所有可枚举的属性都会返回一次，但返回的顺序可能会因浏览器而异。

如果 for-in 循环要迭代的变量是 null 或 undefined，则不执行循环体。

### 3.6.6. for-of 语句

for-of 语句是一种严格的迭代语句，用于遍历可迭代对象的元素，语法如下：

```js
for (property of expression) statement;
```

下面是示例：

```js
for (const el of [2, 4, 6, 8]) {
  document.write(el);
}
```

在这个例子中，我们使用 for-of 语句显示了一个包含 4 个元素的数组中的所有元素。循环会一直持续到将所有元素都迭代完。与 for 循环一样，这里控制语句中的 const 也不是必需的。但为了确保这个局部变量不被修改，推荐使用 const。

for-of 循环会按照可迭代对象的 next()方法产生值的顺序迭代元素。关于可迭代对象，本书将在第 7 章详细介绍。

如果尝试迭代的变量不支持迭代，则 for-of 语句会抛出错误。

注意 ES2018 对 for-of 语句进行了扩展，增加了 for-await-of 循环，以支持生成期约（promise）的异步可迭代对象。相关内容将在附录 A 介绍。

### 3.6.7. 标签语句

标签语句用于给语句加标签，语法如下：

```js
label: statement;
```

下面是一个例子：

```js
start: for (let i = 0; i < count; i++) {
  console.log(i);
}
```

在这个例子中，start 是一个标签，可以在后面通过 break 或 continue 语句引用。标签语句的典型应用场景是嵌套循环。

### 3.6.8. break 和 continue 语句

break 和 continue 语句为执行循环代码提供了更严格的控制手段。其中，break 语句用于立即退出循环，强制执行循环后的下一条语句。而 continue 语句也用于立即退出循环，但会再次从循环顶部开始执行。下面看一个例子：

```js
let num = 0;
for (let i = 1; i < 10; i++) {
  if (i % 5 == 0) {
    break;
  }
  num++;
}
console.log(num); // 4
```

在上面的代码中，for 循环会将变量 i 由 1 递增到 10。而在循环体内，有一个 if 语句用于检查 i 能否被 5 整除（使用取余操作符）。如果是，则执行 break 语句，退出循环。变量 num 的初始值为 0，表示循环在退出前执行了多少次。当 break 语句执行后，下一行执行的代码是 console.log(num)，显示 4。之所以循环执行了 4 次，是因为当 i 等于 5 时，break 语句会导致循环退出，该次循环不会执行递增 num 的代码。如果将 break 换成 continue，则会出现不同的效果：

```js
let num = 0;
for (let i = 1; i < 10; i++) {
  if (i % 5 == 0) {
    continue;
  }
  num++;
}
console.log(num); // 8
```

这一次，console.log 显示 8，即循环被完整执行了 8 次。当 i 等于 5 时，循环会在递增 num 之前退出，但会执行下一次迭代，此时 i 是 6。然后，循环会一直执行到自然结束，即 i 等于 10。最终 num 的值是 8 而不是 9，是因为 continue 语句导致它少递增了一次。

break 和 continue 都可以与标签语句一起使用，返回代码中特定的位置。这通常是在嵌套循环中，如下面的例子所示：

```js
let num = 0;

outermost: for (let i = 0; i < 10; i++) {
  for (let j = 0; j < 10; j++) {
    if (i == 5 && j == 5) {
      break outermost;
    }
    num++;
  }
}
console.log(num); // 55
```

在这个例子中，outermost 标签标识的是第一个 for 语句。正常情况下，每个循环执行 10 次，意味着 num++语句会执行 100 次，而循环结束时 console.log 的结果应该是 100。但是，break 语句带来了一个变数，即要退出到的标签。添加标签不仅让 break 退出（使用变量 j 的）内部循环，也会退出（使用变量 i 的）外部循环。当执行到 i 和 j 都等于 5 时，循环停止执行，此时 num 的值是 55。continue 语句也可以使用标签，如下面的例子所示：

```js
outermost: for (let i = 0; i < 10; i++) {
  for (let j = 0; j < 10; j++) {
    if (i == 5 && j == 5) {
      continue outermost;
    }
    num++;
  }
}
console.log(num); // 95
```

这一次，continue 语句会强制循环继续执行，但不是继续执行内部循环，而是继续执行外部循环。当 i 和 j 都等于 5 时，会执行 continue，跳到外部循环继续执行，从而导致内部循环少执行 5 次，结果 num 等于 95。

组合使用标签语句和 break、continue 能实现复杂的逻辑，但也容易出错。注意标签要使用描述性强的文本，而嵌套也不要太深。

### 3.6.9. with

with 语句的用途是将代码作用域设置为特定的对象，其语法是：

```js
with (expression) statement;
```

使用 with 语句的主要场景是针对一个对象反复操作，这时候将代码作用域设置为该对象能提供便利，如下面的例子所示：

```js
let qs = location.search.substring(1);
let hostName = location.hostname;
let url = location.href;
```

上面代码中的每一行都用到了 location 对象。如果使用 with 语句，就可以少写一些代码：

```js
with (location) {
  let qs = search.substring(1);
  let hostName = hostname;
  let url = href;
}
```

这里，with 语句用于连接 location 对象。这意味着在这个语句内部，每个变量首先会被认为是一个局部变量。如果没有找到该局部变量，则会搜索 location 对象，看它是否有一个同名的属性。如果有，则该变量会被求值为 location 对象的属性。

严格模式不允许使用 with 语句，否则会抛出错误。

警告 由于 with 语句影响性能且难于调试其中的代码，通常不推荐在产品代码中使用 with 语句。

### 3.6.10. switch 语句

switch 语句是与 if 语句紧密相关的一种流控制语句，从其他语言借鉴而来。ECMAScript 中 switch 语句跟 C 语言中 switch 语句的语法非常相似，如下所示：

```js
switch (expression) {
  case value1:
    statement;
    break;
  case value2:
    statement;
    break;
  case value3:
    statement;
    break;
  case value4:
    statement;
    break;
  default:
    statement;
}
```

这里的每个 case（条件/分支）相当于：“如果表达式等于后面的值，则执行下面的语句。”break 关键字会导致代码执行跳出 switch 语句。如果没有 break，则代码会继续匹配下一个条件。default 关键字用于在任何条件都没有满足时指定默认执行的语句（相当于 else 语句）。

有了 switch 语句，开发者就用不着写类似这样的代码了：

```js
if (i == 25) {
  console.log("25");
} else if (i == 35) {
  console.log("35");
} else if (i == 45) {
  console.log("45");
} else {
  console.log("Other");
}
```

而是可以这样写：

```js
switch (i) {
  case 25:
    console.log("25");
    break;
  case 35:
    console.log("35");
    break;
  case 45:
    console.log("45");
    break;
  default:
    console.log("Other");
}
```

为避免不必要的条件判断，最好给每个条件后面都加上 break 语句。如果确实需要连续匹配几个条件，那么推荐写个注释表明是故意忽略了 break，如下所示：

```js
switch (i) {
  case 25:
  /*跳过*/
  case 35:
    console.log("25 or 35");
    break;
  case 45:
    console.log("45");
    break;
  default:
    console.log("Other");
}
```

虽然 switch 语句是从其他语言借鉴过来的，但 ECMAScript 为它赋予了一些独有的特性。首先，switch 语句可以用于所有数据类型（在很多语言中，它只能用于数值），因此可以使用字符串甚至对象。其次，条件的值不需要是常量，也可以是变量或表达式。看下面的例子：

```js
switch ("hello world") {
  case "hello" + " world":
    console.log("Greeting was found.");
    break;
  case "goodbye":
    console.log("Closing was found.");
    break;
  default:
    console.log("Unexpected message was found.");
}
```

这个例子在 switch 语句中使用了字符串。第一个条件实际上使用的是表达式，求值为两个字符串拼接后的结果。因为拼接后的结果等于 switch 的参数，所以 console.log 会输出"Greeting wasfound."。能够在条件判断中使用表达式，就可以在判断中加入更多逻辑:

```js
let num = 25;
switch (true) {
  case num < 0:
    console.log("Less than 0.");
    break;
  case num >= 0 && num <= 10:
    console.log("Between 0 and 10.");
    break;
  case num > 10 && num <= 20:
    console.log("Between 10 and 20.");
    break;
  default:
    console.log("More than 20.");
}
```

上面的代码首先在外部定义了变量 num，而传给 switch 语句的参数之所以是 true，就是因为每个条件的表达式都会返回布尔值。条件的表达式分别被求值，直到有表达式返回 true；否则，就会一直跳到 default 语句（这个例子正是如此）。

注意 switch 语句在比较每个条件的值时会使用全等操作符，因此不会强制转换数据类型（比如，字符串"10"不等于数值 10）。

## 3.7. 函数

函数对任何语言来说都是核心组件，因为它们可以封装语句，然后在任何地方、任何时间执行。ECMAScript 中的函数使用 function 关键字声明，后跟一组参数，然后是函数体。第 10 章会更详细地介绍函数。

以下是函数的基本语法：

```js
function functionName(arg0, arg1,...,argN) {
  statements
}
```

下面是一个例子：

```js
function sayHi(name, message) {
  console.log("Hello " + name + ", " + message);
}
```

可以通过函数名来调用函数，要传给函数的参数放在括号里（如果有多个参数，则用逗号隔开）。下面是调用函数 sayHi()的示例：

```js
sayHi("Nicholas", "how are you today?");
```

调用这个函数的输出结果是"Hello Nicholas, how are you today?"。参数 name 和 message 在函数内部作为字符串被拼接在了一起，最终通过 console.log 输出到控制台。

ECMAScript 中的函数不需要指定是否返回值。任何函数在任何时间都可以使用 return 语句来返回函数的值，用法是后跟要返回的值。比如：

```js
function sum(num1, num2) {
  return num1 + num2;
}
```

函数 sum()会将两个值相加并返回结果。注意，除了 return 语句之外没有任何特殊声明表明该函数有返回值。然后就可以这样调用它：

```js
const result = sum(5, 10);
```

要注意的是，只要碰到 return 语句，函数就会立即停止执行并退出。因此，return 语句后面的代码不会被执行。比如：

```js
function sum(num1, num2) {
  return num1 + num2;
  console.log("Hello world"); // 不会执行
}
```

在这个例子中，console.log 不会执行，因为它在 return 语句后面。

一个函数里也可以有多个 return 语句，像这样：

```js
function diff(num1, num2) {
  if (num1 < num2) {
    return num2 - num1;
  } else {
    return num1 - num2;
  }
}
```

这个 diff()函数用于计算两个数值的差。如果第一个数值小于第二个，则用第二个减第一个；否则，就用第一个减第二个。代码中每个分支都有自己的 return 语句，返回正确的差值。

return 语句也可以不带返回值。这时候，函数会立即停止执行并返回 undefined。这种用法最常用于提前终止函数执行，并不是为了返回值。比如在下面的例子中，console.log 不会执行：

```js
function sayHi(name, message) {
  return;
  console.log("Hello " + name + ", " + message); // 不会执行
}
```

注意 最佳实践是函数要么返回值，要么不返回值。只在某个条件下返回值的函数会带来麻烦，尤其是调试时。

严格模式对函数也有一些限制：

- 函数不能以 eval 或 arguments 作为名称；
- 函数的参数不能叫 eval 或 arguments；
- 两个命名参数不能拥有同一个名称。

如果违反上述规则，则会导致语法错误，代码也不会执行。

# 4. 变量，作用域与内存

本章内容

- 通过变量使用原始值与引用值
- 理解执行上下文
- 理解垃圾回收

相比于其他语言，JavaScript 中的变量可谓独树一帜。正如 ECMA-262 所规定的，JavaScript 变量是松散类型的，而且变量不过就是特定时间点一个特定值的名称而已。由于没有规则定义变量必须包含什么数据类型，变量的值和数据类型在脚本生命期内可以改变。这样的变量很有意思，很强大，当然也有不少问题。本章会剖析错综复杂的变量。

## 4.1. 原始值和引用值

ECMAScript 变量可以包含两种不同类型的数据：原始值和引用值。**原始值(primitive value)** 就是最简单的数据，**引用值(reference value)** 则是由多个值构成的对象。

在把一个值赋给变量时，JavaScript 引擎必须确定这个值是原始值还是引用值。上一章讨论了 6 种原始值：Undefined、Null、Boolean、Number、String 和 Symbol。保存原始值的变量是 **按值(by value)** 访问的，因为我们操作的就是存储在变量中的实际值。

引用值是保存在内存中的对象。与其他语言不同，JavaScript 不允许直接访问内存位置，因此也就不能直接操作对象所在的内存空间。在操作对象时，实际上操作的是对该对象的 **引用(reference)** 而非实际的对象本身。为此，保存引用值的变量是 **按引用(by reference)** 访问的。

注意 在很多语言中，字符串是使用对象表示的，因此被认为是引用类型。ECMAScript 打破了这个惯例。

### 4.1.1. 动态属性

原始值和引用值的定义方式很类似，都是创建一个变量，然后给它赋一个值。不过，在变量保存了这个值之后，可以对这个值做什么，则大有不同。对于引用值而言，可以随时添加、修改和删除其属性和方法。比如，看下面的例子：

```js
let person = new Object();
person.name = "Nicholas";
console.log(person.name); // "Nicholas"
```

这里，首先创建了一个对象，并把它保存在变量 person 中。然后，给这个对象添加了一个名为 name 的属性，并给这个属性赋值了一个字符串"Nicholas"。在此之后，就可以访问这个新属性，直到对象被销毁或属性被显式地删除。

原始值不能有属性，尽管尝试给原始值添加属性不会报错。比如：

```js
let name = "Nicholas";
name.age = 27;
console.log(name.age); // undefined
```

在此，代码想给字符串 name 定义一个 age 属性并给该属性赋值 27。紧接着在下一行，属性不见了。记住，只有引用值可以动态添加后面可以使用的属性。

注意，原始类型的初始化可以只使用原始字面量形式。如果使用的是 new 关键字，则 JavaScript 会创建一个 Object 类型的实例，但其行为类似原始值。下面来看看这两种初始化方式的差异：

```js
let name1 = "Nicholas";
let name2 = new String("Matt");
name1.age = 27;
name2.age = 26;
console.log(name1.age); // undefined
console.log(name2.age); // 26
console.log(typeof name1); // string
console.log(typeof name2); // object
```

### 4.1.2. 复制值

除了存储方式不同，原始值和引用值在通过变量复制时也有所不同。在通过变量把一个原始值赋值到另一个变量时，原始值会被复制到新变量的位置。请看下面的例子：

```js
let num1 = 5;
let num2 = num1;
```

这里，num1 包含数值 5。当把 num2 初始化为 num1 时，num2 也会得到数值 5。这个值跟存储在 num1 中的 5 是完全独立的，因为它是那个值的副本。

这两个变量可以独立使用，互不干扰。这个过程如下图所示。

![4-1-原始值复制](illustrations/4-1-原始值复制.png)

在把引用值从一个变量赋给另一个变量时，存储在变量中的值也会被复制到新变量所在的位置。区别在于，这里复制的值实际上是一个指针，它指向存储在堆内存中的对象。操作完成后，两个变量实际上指向同一个对象，因此一个对象上面的变化会在另一个对象上反映出来，如下面的例子所示：

```js
let obj1 = new Object();
let obj2 = obj1;
obj1.name = "Nicholas";
console.log(obj2.name); // "Nicholas"
```

在这个例子中，变量 obj1 保存了一个新对象的实例。然后，这个值被复制到 obj2，此时两个变量都指向了同一个对象。在给 obj1 创建属性 name 并赋值后，通过 obj2 也可以访问这个属性，因为它们都指向同一个对象。图 4-2 展示了变量与堆内存中对象之间的关系。

![4-2-引用值复制](illustrations/4-2-引用值复制.png)

### 4.1.3. 传递参数

ECMAScript 中所有函数的参数都是按值传递的。这意味着函数外的值会被复制到函数内部的参数中，就像从一个变量复制到另一个变量一样。如果是原始值，那么就跟原始值变量的复制一样，如果是引用值，那么就跟引用值变量的复制一样。对很多开发者来说，这一块可能会不好理解，毕竟变量有按值和按引用访问，而传参则只有按值传递。

在按值传递参数时，值会被复制到一个局部变量（即一个命名参数，或者用 ECMAScript 的话说，就是 arguments 对象中的一个槽位）。在按引用传递参数时，值在内存中的位置会被保存在一个局部变量，这意味着对本地变量的修改会反映到函数外部。（这在 ECMAScript 中是不可能的。）来看下面这个例子：

```js
function addTen(num) {
  num += 10;
  return num;
}
let count = 20;
let result = addTen(count);
console.log(count); // 20，没有变化
console.log(result); // 30
```

这里，函数 addTen()有一个参数 num，它其实是一个局部变量。在调用时，变量 count 作为参数传入。count 的值是 20，这个值被复制到参数 num 以便在 addTen()内部使用。在函数内部，参数 num 的值被加上了 10，但这不会影响函数外部的原始变量 count。参数 num 和变量 count 互不干扰，它们只不过碰巧保存了一样的值。如果 num 是按引用传递的，那么 count 的值也会被修改为 30。这个事实在使用数值这样的原始值时是非常明显的。但是，如果变量中传递的是对象，就没那么清楚了。比如，再看这个例子：

```js
function setName(obj) {
  obj.name = "Nicholas";
}
let person = new Object();
setName(person);
console.log(person.name); // "Nicholas"
```

这一次，我们创建了一个对象并把它保存在变量 person 中。然后，这个对象被传给 setName()方法，并被复制到参数 obj 中。在函数内部，obj 和 person 都指向同一个对象。结果就是，即使对象是按值传进函数的，obj 也会通过引用访问对象。当函数内部给 obj 设置了 name 属性时，函数外部的对象也会反映这个变化，因为 obj 指向的对象保存在全局作用域的堆内存上。很多开发者错误地认为，当在局部作用域中修改对象而变化反映到全局时，就意味着参数是按引用传递的。为证明对象是按值传递的，我们再来看看下面这个修改后的例子：

```js
function setName(obj) {
  obj.name = "Nicholas";
  obj = new Object();
  obj.name = "Greg";
}
let person = new Object();
setName(person);
console.log(person.name); // "Nicholas"
```

这个例子前后唯一的变化就是 setName()中多了两行代码，将 obj 重新定义为一个有着不同 name 的新对象。当 person 传入 setName()时，其 name 属性被设置为"Nicholas"。然后变量 obj 被设置为一个新对象且 name 属性被设置为"Greg"。如果 person 是按引用传递的，那么 person 应该自动将指针改为指向 name 为"Greg"的对象。可是，当我们再次访问 person.name 时，它的值是"Nicholas"，这表明函数中参数的值改变之后，原始的引用仍然没变。当 obj 在函数内部被重写时，它变成了一个指向本地对象的指针。而那个本地对象在函数执行结束时就被销毁了。

### 4.1.4. 确定类型

前一章提到的 typeof 操作符最适合用来判断一个变量是否为原始类型。更确切地说，它是判断一个变量是否为字符串、数值、布尔值或 undefined 的最好方式。如果值是对象或 null，那么 typeof 返回"object"，如下面的例子所示：

```js
let s = "Nicholas";
let b = true;
let i = 22;
let u;
let n = null;
let o = new Object();
console.log(typeof s); // string
console.log(typeof i); // number
console.log(typeof b); // boolean
console.log(typeof u); // undefined
console.log(typeof n); // object
console.log(typeof o); // object
```

typeof 虽然对原始值很有用，但它对引用值的用处不大。我们通常不关心一个值是不是对象，而是想知道它是什么类型的对象。为了解决这个问题，ECMAScript 提供了 instanceof 操作符，语法如下：

```js
result = variable instanceof constructor;
```

如果变量是给定引用类型（由其原型链决定，将在第 8 章详细介绍）的实例，则 instanceof 操作符返回 true。来看下面的例子：

```js
console.log(person instanceof Object); // 变量person 是Object 吗？
console.log(colors instanceof Array); // 变量colors 是Array 吗？
console.log(pattern instanceof RegExp); // 变量pattern 是RegExp 吗？
```

按照定义，所有引用值都是 Object 的实例，因此通过 instanceof 操作符检测任何引用值和 Object 构造函数都会返回 true。类似地，如果用 instanceof 检测原始值，则始终会返回 false，因为原始值不是对象。

注意 typeof 操作符在用于检测函数时也会返回"function"。当在 Safari（直到 Safari 5）和 Chrome（直到 Chrome 7）中用于检测正则表达式时，由于实现细节的原因，typeof 也会返回"function"。ECMA-262 规定，任何实现内部[[Call]]方法的对象都应该在 typeof 检测时返回"function"。因为上述浏览器中的正则表达式实现了这个方法，所以 typeof 对正则表达式也返回"function"。在 IE 和 Firefox 中，typeof 对正则表达式返回"object"。

## 4.2. 执行上下文和作用域

执行上下文（以下简称“上下文”）的概念在 JavaScript 中是颇为重要的。变量或函数的上下文决定了它们可以访问哪些数据，以及它们的行为。每个上下文都有一个关联的变量对象(variable object)，而这个上下文中定义的所有变量和函数都存在于这个对象上。虽然无法通过代码访问变量对象，但后台处理数据会用到它。

全局上下文是最外层的上下文。根据 ECMAScript 实现的宿主环境，表示全局上下文的对象可能不一样。在浏览器中，全局上下文就是我们常说的 window 对象（第 12 章会详细介绍），因此所有通过 var 定义的全局变量和函数都会成为 window 对象的属性和方法。使用 let 和 const 的顶级声明不会定义在全局上下文中，但在作用域链解析上效果是一样的。上下文在其所有代码都执行完毕后会被销毁，包括定义在它上面的所有变量和函数（全局上下文在应用程序退出前才会被销毁，比如关闭网页或退出浏览器）。

每个函数调用都有自己的上下文。当代码执行流进入函数时，函数的上下文被推到一个上下文栈上。在函数执行完之后，上下文栈会弹出该函数上下文，将控制权返还给之前的执行上下文。ECMAScript 程序的执行流就是通过这个上下文栈进行控制的。

上下文中的代码在执行的时候，会创建变量对象的一个 **作用域链(scope chain)**。这个作用域链决定了各级上下文中的代码在访问变量和函数时的顺序。代码正在执行的上下文的变量对象始终位于作用域链的最前端。如果上下文是函数，则其**活动对象(activation object)** 用作变量对象。活动对象最初只有一个定义变量：arguments。（全局上下文中没有这个变量。）作用域链中的下一个变量对象来自包含上下文，再下一个对象来自再下一个包含上下文。以此类推直至全局上下文；全局上下文的变量对象始终是作用域链的最后一个变量对象。

代码执行时的标识符解析是通过沿作用域链逐级搜索标识符名称完成的。搜索过程始终从作用域链的最前端开始，然后逐级往后，直到找到标识符。（如果没有找到标识符，那么通常会报错。）

看一看下面这个例子：

```js
var color = "blue";
function changeColor() {
  if (color === "blue") {
    color = "red";
  } else {
    color = "blue";
  }
}
changeColor();
```

对这个例子而言，函数 changeColor()的作用域链包含两个对象：一个是它自己的变量对象（就是定义 arguments 对象的那个），另一个是全局上下文的变量对象。这个函数内部之所以能够访问变量 color，就是因为可以在作用域链中找到它。

此外，局部作用域中定义的变量可用于在局部上下文中替换全局变量。看一看下面这个例子：

```js
var color = "blue";
function changeColor() {
  let anotherColor = "red";
  function swapColors() {
    let tempColor = anotherColor;
    anotherColor = color;
    color = tempColor;
    // 这里可以访问color、anotherColor 和tempColor
  }
  // 这里可以访问color 和anotherColor，但访问不到tempColor
  swapColors();
}
// 这里只能访问color
changeColor();
```

以上代码涉及 3 个上下文：全局上下文、changeColor()的局部上下文和 swapColors()的局部上下文。全局上下文中有一个变量 color 和一个函数 changeColor()。changeColor()的局部上下文中有一个变量 anotherColor 和一个函数 swapColors()，但在这里可以访问全局上下文中的变量 color。swapColors()的局部上下文中有一个变量 tempColor，只能在这个上下文中访问到。全局上下文和 changeColor()的局部上下文都无法访问到 tempColor。而在 swapColors()中则可以访问另外两个上下文中的变量，因为它们都是父上下文。下图展示了前面这个例子的作用域链。

![4-3-作用域链](illustrations/4-3-作用域链.png)

上图中的矩形表示不同的上下文。内部上下文可以通过作用域链访问外部上下文中的一切，但外部上下文无法访问内部上下文中的任何东西。上下文之间的连接是线性的、有序的。每个上下文都可以到上一级上下文中去搜索变量和函数，但任何上下文都不能到下一级上下文中去搜索。swapColors()局部上下文的作用域链中有 3 个对象：swapColors()的变量对象、changeColor()的变量对象和全局变量对象。swapColors()的局部上下文首先从自己的变量对象开始搜索变量和函数，搜不到就去搜索上一级变量对象。changeColor()上下文的作用域链中只有 2 个对象：它自己的变量对象和全局变量对象。因此，它不能访问 swapColors()的上下文。

注意 函数参数被认为是当前上下文中的变量，因此也跟上下文中的其他变量遵循相同的访问规则。

### 4.2.1. 作用域链增强

虽然执行上下文主要有全局上下文和函数上下文两种（eval()调用内部存在第三种上下文），但有其他方式来增强作用域链。某些语句会导致在作用域链前端临时添加一个上下文，这个上下文在代码执行后会被删除。通常在两种情况下会出现这个现象，即代码执行到下面任意一种情况时：

- try/catch 语句的 catch 块
- with 语句

这两种情况下，都会在作用域链前端添加一个变量对象。对 with 语句来说，会向作用域链前端添加指定的对象；对 catch 语句而言，则会创建一个新的变量对象，这个变量对象会包含要抛出的错误对象的声明。看下面的例子：

```js
function buildUrl() {
  let qs = "?debug=true";
  with (location) {
    let url = href + qs;
  }
  return url;
}
```

这里，with 语句将 location 对象作为上下文，因此 location 会被添加到作用域链前端。buildUrl()函数中定义了一个变量 qs。当 with 语句中的代码引用变量 href 时，实际上引用的是 location.href，也就是自己变量对象的属性。在引用 qs 时，引用的则是定义在 buildUrl()中的那个变量，它定义在函数上下文的变量对象上。而在 with 语句中使用 var 声明的变量 url 会成为函数上下文的一部分，可以作为函数的值被返回；但像这里使用 let 声明的变量 url，因为被限制在块级作用域（稍后介绍），所以在 with 块之外没有定义。

注意 IE 的实现在 IE8 之前是有偏差的，即它们会将 catch 语句中捕获的错误添加到执行上下文的变量对象上，而不是 catch 语句的变量对象上，导致在 catch 块外部都可以访问到错误。IE9 纠正了这个问题。

### 4.2.2. 变量声明

ES6 之后，JavaScript 的变量声明经历了翻天覆地的变化。直到 ECMAScript 5.1，var 都是声明变量的唯一关键字。ES6 不仅增加了 let 和 const 两个关键字，而且还让这两个关键字压倒性地超越 var 成为首选。

1. **使用 var 的函数作用域声明**

在使用 var 声明变量时，变量会被自动添加到最接近的上下文。在函数中，最接近的上下文就是函数的局部上下文。在 with 语句中，最接近的上下文也是函数上下文。如果变量未经声明就被初始化了，那么它就会自动被添加到全局上下文，如下面的例子所示：

```js
function add(num1, num2) {
  var sum = num1 + num2;
  return sum;
}
let result = add(10, 20); // 30
console.log(sum); // 报错：sum 在这里不是有效变量
```

这里，函数 add()定义了一个局部变量 sum，保存加法操作的结果。这个值作为函数的值被返回，但变量 sum 在函数外部是访问不到的。如果省略上面例子中的关键字 var，那么 sum 在 add()被调用之后就变成可以访问的了，如下所示：

```js
function add(num1, num2) {
  sum = num1 + num2;
  return sum;
}
let result = add(10, 20); // 30
console.log(sum); // 30
```

这一次，变量 sum 被用加法操作的结果初始化时并没有使用 var 声明。在调用 add()之后，sum 被添加到了全局上下文，在函数退出之后依然存在，从而在后面可以访问到。

注意 未经声明而初始化变量是 JavaScript 编程中一个非常常见的错误，会导致很多问题。为此，读者在初始化变量之前一定要先声明变量。在严格模式下，未经声明就初始化变量会报错。

var 声明会被拿到函数或全局作用域的顶部，位于作用域中所有代码之前。这个现象叫作“提升”（hoisting）。提升让同一作用域中的代码不必考虑变量是否已经声明就可以直接使用。可是在实践中，提升也会导致合法却奇怪的现象，即在变量声明之前使用变量。下面的例子展示了在全局作用域中两段等价的代码：

```js
var name = "Jake";
// 等价于：
name = "Jake";
var name;
```

下面是两个等价的函数：

```js
function fn1() {
  var name = "Jake";
}
// 等价于：
function fn2() {
  var name;
  name = "Jake";
}
```

通过在声明之前打印变量，可以验证变量会被提升。声明的提升意味着会输出 undefined 而不是 Reference Error：

```js
console.log(name); // undefined
var name = 'Jake';
function() {
  console.log(name); // undefined
  var name = 'Jake';
}
```

2. **使用 let 的块级作用域声明**

ES6 新增的 let 关键字跟 var 很相似，但它的作用域是块级的，这也是 JavaScript 中的新概念。块级作用域由最近的一对包含花括号{}界定。换句话说，if 块、while 块、function 块，甚至连单独的块也是 let 声明变量的作用域。

```js
if (true) {
  let a;
}
console.log(a); // ReferenceError: a 没有定义

while (true) {
  let b;
}
console.log(b); // ReferenceError: b 没有定义

function foo() {
  let c;
}
console.log(c); // ReferenceError: c 没有定义
// 这没什么可奇怪的
// var 声明也会导致报错

// 这不是对象字面量，而是一个独立的块
// JavaScript 解释器会根据其中内容识别出它来
{
  let d;
}
console.log(d); // ReferenceError: d 没有定义
```

let 与 var 的另一个不同之处是在同一作用域内不能声明两次。重复的 var 声明会被忽略，而重复的 let 声明会抛出 SyntaxError。

```js
var a;
var a;
// 不会报错

{
  let b;
  let b;
}
// SyntaxError: 标识符b 已经声明过了
```

let 的行为非常适合在循环中声明迭代变量。使用 var 声明的迭代变量会泄漏到循环外部，这种情况应该避免。来看下面两个例子：

```js
for (var i = 0; i < 10; ++i) {}
console.log(i); // 10

for (let j = 0; j < 10; ++j) {}
console.log(j); // ReferenceError: j 没有定义
```

严格来讲，let 在 JavaScript 运行时中也会被提升，但由于“暂时性死区”（temporal dead zone）的缘故，实际上不能在声明之前使用 let 变量。因此，从写 JavaScript 代码的角度说，let 的提升跟 var 是不一样的。

3. **使用 const 的常量声明**

除了 let，ES6 同时还增加了 const 关键字。使用 const 声明的变量必须同时初始化为某个值。一经声明，在其生命周期的任何时候都不能再重新赋予新值。

```js
const a; // SyntaxError: 常量声明时没有初始化

const b = 3;
console.log(b); // 3
b = 4; // TypeError: 给常量赋值
```

const 除了要遵循以上规则，其他方面与 let 声明是一样的：

```js
if (true) {
  const a = 0;
}
console.log(a); // ReferenceError: a 没有定义

while (true) {
  const b = 1;
}
console.log(b); // ReferenceError: b 没有定义

function foo() {
  const c = 2;
}
console.log(c); // ReferenceError: c 没有定义

{
  const d = 3;
}
console.log(d); // ReferenceError: d 没有定义
```

const 声明只应用到顶级原语或者对象。换句话说，赋值为对象的 const 变量不能再被重新赋值为其他引用值，但对象的键则不受限制。

```js
const o1 = {};
o1 = {}; // TypeError: 给常量赋值

const o2 = {};
o2.name = "Jake";
console.log(o2.name); // 'Jake'
```

如果想让整个对象都不能修改，可以使用 Object.freeze()，这样再给属性赋值时虽然不会报错，但会静默失败：

```js
const o3 = Object.freeze({});
o3.name = "Jake";
console.log(o3.name); // undefined
```

由于 const 声明暗示变量的值是单一类型且不可修改，JavaScript 运行时编译器可以将其所有实例都替换成实际的值，而不会通过查询表进行变量查找。谷歌的 V8 引擎就执行这种优化。

注意 开发实践表明，如果开发流程并不会因此而受很大影响，就应该尽可能地多使用 const 声明，除非确实需要一个将来会重新赋值的变量。这样可以从根本上保证提前发现重新赋值导致的 bug。

4. **标识符查找**

当在特定上下文中为读取或写入而引用一个标识符时，必须通过搜索确定这个标识符表示什么。搜索开始于作用域链前端，以给定的名称搜索对应的标识符。如果在局部上下文中找到该标识符，则搜索停止，变量确定；如果没有找到变量名，则继续沿作用域链搜索。（注意，作用域链中的对象也有一个原型链，因此搜索可能涉及每个对象的原型链。）这个过程一直持续到搜索至全局上下文的变量对象。如果仍然没有找到标识符，则说明其未声明。

为更好地说明标识符查找，我们来看一个例子：

```js
var color = "blue";
function getColor() {
  return color;
}
console.log(getColor()); // 'blue'
```

在这个例子中，调用函数 getColor()时会引用变量 color。为确定 color 的值会进行两步搜索。第一步，搜索 getColor()的变量对象，查找名为 color 的标识符。结果没找到，于是继续搜索下一个变量对象（来自全局上下文），然后就找到了名为 color 的标识符。因为全局变量对象上有 color 的定义，所以搜索结束。

对这个搜索过程而言，引用局部变量会让搜索自动停止，而不继续搜索下一级变量对象。也就是说，如果局部上下文中有一个同名的标识符，那就不能在该上下文中引用父上下文中的同名标识符，如下面的例子所示：

```js
var color = "blue";
function getColor() {
  let color = "red";
  return color;
}
console.log(getColor()); // 'red'
```

使用块级作用域声明并不会改变搜索流程，但可以给词法层级添加额外的层次：

```js
var color = "blue";
function getColor() {
  let color = "red";
  {
    let color = "green";
    return color;
  }
}
console.log(getColor()); // 'green'
```

在这个修改后的例子中，getColor()内部声明了一个名为 color 的局部变量。在调用这个函数时，变量会被声明。在执行到函数返回语句时，代码引用了变量 color。于是开始在局部上下文中搜索这个标识符，结果找到了值为'green'的变量 color。因为变量已找到，搜索随即停止，所以就使用这个局部变量。这意味着函数会返回'green'。在局部变量 color 声明之后的任何代码都无法访问全局变量 color，除非使用完全限定的写法 window.color。

注意 标识符查找并非没有代价。访问局部变量比访问全局变量要快，因为不用切换作用域。不过，JavaScript 引擎在优化标识符查找上做了很多工作，将来这个差异可能就微不足道了。

## 4.3. 垃圾回收

JavaScript 是使用垃圾回收的语言，也就是说执行环境负责在代码执行时管理内存。在 C 和 C++等语言中，跟踪内存使用对开发者来说是个很大的负担，也是很多问题的来源。JavaScript 为开发者卸下了这个负担，通过自动内存管理实现内存分配和闲置资源回收。基本思路很简单：确定哪个变量不会再使用，然后释放它占用的内存。这个过程是周期性的，即垃圾回收程序每隔一定时间（或者说在代码执行过程中某个预定的收集时间）就会自动运行。垃圾回收过程是一个近似且不完美的方案，因为某块内存是否还有用，属于“不可判定的”问题，意味着靠算法是解决不了的。

我们以函数中局部变量的正常生命周期为例。函数中的局部变量会在函数执行时存在。此时，栈（或堆）内存会分配空间以保存相应的值。函数在内部使用了变量，然后退出。此时，就不再需要那个局部变量了，它占用的内存可以释放，供后面使用。这种情况下显然不再需要局部变量了，但并不是所有时候都会这么明显。垃圾回收程序必须跟踪记录哪个变量还会使用，以及哪个变量不会再使用，以便回收内存。如何标记未使用的变量也许有不同的实现方式。不过，在浏览器的发展史上，用到过两种主要的标记策略：标记清理和引用计数。

### 4.3.1. 标记清理

JavaScript 最常用的垃圾回收策略是 **标记清理(mark-and-sweep)**。当变量进入上下文，比如在函数内部声明一个变量时，这个变量会被加上存在于上下文中的标记。而在上下文中的变量，逻辑上讲，永远不应该释放它们的内存，因为只要上下文中的代码在运行，就有可能用到它们。当变量离开上下文时，也会被加上离开上下文的标记。

给变量加标记的方式有很多种。比如，当变量进入上下文时，反转某一位；或者可以维护“在上下文中”和“不在上下文中”两个变量列表，可以把变量从一个列表转移到另一个列表。标记过程的实现并不重要，关键是策略。

垃圾回收程序运行的时候，会标记内存中存储的所有变量（记住，标记方法有很多种）。然后，它会将所有在上下文中的变量，以及被在上下文中的变量引用的变量的标记去掉。在此之后再被加上标记的变量就是待删除的了，原因是任何在上下文中的变量都访问不到它们了。随后垃圾回收程序做一次内存清理，销毁带标记的所有值并收回它们的内存。

到了 2008 年，IE、Firefox、Opera、Chrome 和 Safari 都在自己的 JavaScript 实现中采用标记清理（或其变体），只是在运行垃圾回收的频率上有所差异。

### 4.3.2. 引用计数

另一种没那么常用的垃圾回收策略是 **引用计数(reference counting)**。其思路是对每个值都记录它被引用的次数。声明变量并给它赋一个引用值时，这个值的引用数为 1。如果同一个值又被赋给另一个变量，那么引用数加 1。类似地，如果保存对该值引用的变量被其他值给覆盖了，那么引用数减 1。当一个值的引用数为 0 时，就说明没办法再访问到这个值了，因此可以安全地收回其内存了。垃圾回收程序下次运行的时候就会释放引用数为 0 的值的内存。

引用计数最早由 Netscape Navigator 3.0 采用，但很快就遇到了严重的问题：循环引用。所谓循环引用，就是对象 A 有一个指针指向对象 B，而对象 B 也引用了对象 A。比如：

```js
function problem() {
  let objectA = new Object();
  let objectB = new Object();

  objectA.someOtherObject = objectB;
  objectB.anotherObject = objectA;
}
```

在这个例子中，objectA 和 objectB 通过各自的属性相互引用，意味着它们的引用数都是 2。在标记清理策略下，这不是问题，因为在函数结束后，这两个对象都不在作用域中。而在引用计数策略下，objectA 和 objectB 在函数结束后还会存在，因为它们的引用数永远不会变成 0。如果函数被多次调用，则会导致大量内存永远不会被释放。为此，Netscape 在 4.0 版放弃了引用计数，转而采用标记清理。事实上，引用计数策略的问题还不止于此。

在 IE8 及更早版本的 IE 中，并非所有对象都是原生 JavaScript 对象。BOM 和 DOM 中的对象是 C++实现的组件对象模型（COM，Component Object Model）对象，而 COM 对象使用引用计数实现垃圾回收。因此，即使这些版本 IE 的 JavaScript 引擎使用标记清理，JavaScript 存取的 COM 对象依旧使用引用计数。换句话说，只要涉及 COM 对象，就无法避开循环引用问题。下面这个简单的例子展示了涉及 COM 对象的循环引用问题：

```js
let element = document.getElementById("some_element");
let myObject = new Object();
myObject.element = element;
element.someObject = myObject;
```

这个例子在一个 DOM 对象（element）和一个原生 JavaScript 对象（myObject）之间制造了循环引用。myObject 变量有一个名为 element 的属性指向 DOM 对象 element，而 element 对象有一个 someObject 属性指回 myObject 对象。由于存在循环引用，因此 DOM 元素的内存永远不会被回收，即使它已经被从页面上删除了也是如此。

为避免类似的循环引用问题，应该在确保不使用的情况下切断原生 JavaScript 对象与 DOM 元素之间的连接。比如，通过以下代码可以清除前面的例子中建立的循环引用：

```js
myObject.element = null;
element.someObject = null;
```

把变量设置为 null 实际上会切断变量与其之前引用值之间的关系。当下次垃圾回收程序运行时，这些值就会被删除，内存也会被回收。

为了补救这一点，IE9 把 BOM 和 DOM 对象都改成了 JavaScript 对象，这同时也避免了由于存在两套垃圾回收算法而导致的问题，还消除了常见的内存泄漏现象。

注意 还有其他一些可能导致循环引用的情形，本书后面会介绍到。

### 4.3.3. 性能

垃圾回收程序会周期性运行，如果内存中分配了很多变量，则可能造成性能损失，因此垃圾回收的时间调度很重要。尤其是在内存有限的移动设备上，垃圾回收有可能会明显拖慢渲染的速度和帧速率。开发者不知道什么时候运行时会收集垃圾，因此最好的办法是在写代码时就要做到：无论什么时候开始收集垃圾，都能让它尽快结束工作。

现代垃圾回收程序会基于对 JavaScript 运行时环境的探测来决定何时运行。探测机制因引擎而异，但基本上都是根据已分配对象的大小和数量来判断的。比如，根据 V8 团队 2016 年的一篇博文的说法：“在一次完整的垃圾回收之后，V8 的堆增长策略会根据活跃对象的数量外加一些余量来确定何时再次垃圾回收。”

由于调度垃圾回收程序方面的问题会导致性能下降，IE 曾饱受诟病。它的策略是根据分配数，比如分配了 256 个变量、4096 个对象/数组字面量和数组槽位（slot），或者 64KB 字符串。只要满足其中某个条件，垃圾回收程序就会运行。这样实现的问题在于，分配那么多变量的脚本，很可能在其整个生命周期内始终需要那么多变量，结果就会导致垃圾回收程序过于频繁地运行。由于对性能的严重影响，IE7 最终更新了垃圾回收程序。

IE7 发布后，JavaScript 引擎的垃圾回收程序被调优为动态改变分配变量、字面量或数组槽位等会触发垃圾回收的阈值。IE7 的起始阈值都与 IE6 的相同。如果垃圾回收程序回收的内存不到已分配的 15%，这些变量、字面量或数组槽位的阈值就会翻倍。如果有一次回收的内存达到已分配的 85%，则阈值重置为默认值。这么一个简单的修改，极大地提升了重度依赖 JavaScript 的网页在浏览器中的性能。

警告 在某些浏览器中是有可能（但不推荐）主动触发垃圾回收的。在 IE 中，window.CollectGarbage()方法会立即触发垃圾回收。在 Opera 7 及更高版本中，调用 window.opera.collect()也会启动垃圾回收程序。

### 4.3.4. 内存管理

在使用垃圾回收的编程环境中，开发者通常无须关心内存管理。不过，JavaScript 运行在一个内存管理与垃圾回收都很特殊的环境。分配给浏览器的内存通常比分配给桌面软件的要少很多，分配给移动浏览器的就更少了。这更多出于安全考虑而不是别的，就是为了避免运行大量 JavaScript 的网页耗尽系统内存而导致操作系统崩溃。这个内存限制不仅影响变量分配，也影响调用栈以及能够同时在一个线程中执行的语句数量。

将内存占用量保持在一个较小的值可以让页面性能更好。优化内存占用的最佳手段就是保证在执行代码时只保存必要的数据。如果数据不再必要，那么把它设置为 null，从而释放其引用。这也可以叫作 **解除引用**。这个建议最适合全局变量和全局对象的属性。局部变量在超出作用域后会被自动解除引用，如下面的例子所示：

```js
function createPerson(name) {
  let localPerson = new Object();
  localPerson.name = name;
  return localPerson;
}

let globalPerson = createPerson("Nicholas");

// 解除globalPerson 对值的引用
globalPerson = null;
```

在上面的代码中，变量 globalPerson 保存着 createPerson()函数调用返回的值。在 createPerson()内部，localPerson 创建了一个对象并给它添加了一个 name 属性。然后，localPerson 作为函数值被返回，并被赋值给 globalPerson。localPerson 在 createPerson()执行完成超出上下文后会自动被解除引用，不需要显式处理。但 globalPerson 是一个全局变量，应该在不再需要时手动解除其引用，最后一行就是这么做的。

不过要注意，解除对一个值的引用并不会自动导致相关内存被回收。解除引用的关键在于确保相关的值已经不在上下文里了，因此它在下次垃圾回收时会被回收。

1. **通过 const 和 let 声明提升性能**

ES6 增加这两个关键字不仅有助于改善代码风格，而且同样有助于改进垃圾回收的过程。因为 const 和 let 都以块（而非函数）为作用域，所以相比于使用 var，使用这两个新关键字可能会更早地让垃圾回收程序介入，尽早回收应该回收的内存。在块作用域比函数作用域更早终止的情况下，这就有可能发生。

2. **隐藏类和删除操作**

根据 JavaScript 所在的运行环境，有时候需要根据浏览器使用的 JavaScript 引擎来采取不同的性能优化策略。截至 2017 年，Chrome 是最流行的浏览器，使用 V8 JavaScript 引擎。V8 在将解释后的 JavaScript 代码编译为实际的机器码时会利用“隐藏类”。如果你的代码非常注重性能，那么这一点可能对你很重要。

运行期间，V8 会将创建的对象与隐藏类关联起来，以跟踪它们的属性特征。能够共享相同隐藏类的对象性能会更好，V8 会针对这种情况进行优化，但不一定总能够做到。比如下面的代码：

```js
function Article() {
  this.title = "Inauguration Ceremony Features Kazoo Band";
}

let a1 = new Article();
let a2 = new Article();
```

V8 会在后台配置，让这两个类实例共享相同的隐藏类，因为这两个实例共享同一个构造函数和原型。假设之后又添加了下面这行代码：

```js
a2.author = "Jake";
```

此时两个 Article 实例就会对应两个不同的隐藏类。根据这种操作的频率和隐藏类的大小，这有可能对性能产生明显影响。

当然，解决方案就是避免 JavaScript 的“先创建再补充”（ready-fire-aim）式的动态属性赋值，并在构造函数中一次性声明所有属性，如下所示：

```js
function Article(opt_author) {
  this.title = "Inauguration Ceremony Features Kazoo Band";
  this.author = opt_author;
}

let a1 = new Article();
let a2 = new Article("Jake");
```

这样，两个实例基本上就一样了（不考虑 hasOwnProperty 的返回值），因此可以共享一个隐藏类，从而带来潜在的性能提升。不过要记住，使用 delete 关键字会导致生成相同的隐藏类片段。看一下这个例子：

```js
function Article() {
  this.title = "Inauguration Ceremony Features Kazoo Band";
  this.author = "Jake";
}

let a1 = new Article();
let a2 = new Article();

delete a1.author;
```

在代码结束后，即使两个实例使用了同一个构造函数，它们也不再共享一个隐藏类。动态删除属性与动态添加属性导致的后果一样。最佳实践是把不想要的属性设置为 null。这样可以保持隐藏类不变和继续共享，同时也能达到删除引用值供垃圾回收程序回收的效果。比如：

```js
function Article() {
  this.title = "Inauguration Ceremony Features Kazoo Band";
  this.author = "Jake";
}

let a1 = new Article();
let a2 = new Article();

a1.author = null;
```

3. **内存泄漏**

写得不好的 JavaScript 可能出现难以察觉且有害的内存泄漏问题。在内存有限的设备上，或者在函数会被调用很多次的情况下，内存泄漏可能是个大问题。JavaScript 中的内存泄漏大部分是由不合理的引用导致的。

意外声明全局变量是最常见但也最容易修复的内存泄漏问题。下面的代码没有使用任何关键字声明变量：

```js
function setName() {
  name = "Jake";
}
```

此时，解释器会把变量 name 当作 window 的属性来创建（相当于 window.name = 'Jake'）。可想而知，在 window 对象上创建的属性，只要 window 本身不被清理就不会消失。这个问题很容易解决，只要在变量声明前头加上 var、let 或 const 关键字即可，这样变量就会在函数执行完毕后离开作用域。

定时器也可能会悄悄地导致内存泄漏。下面的代码中，定时器的回调通过闭包引用了外部变量：

```js
let name = "Jake";
setInterval(() => {
  console.log(name);
}, 100);
```

只要定时器一直运行，回调函数中引用的 name 就会一直占用内存。垃圾回收程序当然知道这一点，因而就不会清理外部变量。

使用 JavaScript 闭包很容易在不知不觉间造成内存泄漏。请看下面的例子：

```js
let outer = function () {
  let name = "Jake";
  return function () {
    return name;
  };
};
```

调用 outer()会导致分配给 name 的内存被泄漏。以上代码执行后创建了一个内部闭包，只要返回的函数存在就不能清理 name，因为闭包一直在引用着它。假如 name 的内容很大（不止是一个小字符串），那可能就是个大问题了。

4. **静态分配与对象池**

为了提升 JavaScript 性能，最后要考虑的一点往往就是压榨浏览器了。此时，一个关键问题就是如何减少浏览器执行垃圾回收的次数。开发者无法直接控制什么时候开始收集垃圾，但可以间接控制触发垃圾回收的条件。理论上，如果能够合理使用分配的内存，同时避免多余的垃圾回收，那就可以保住因释放内存而损失的性能。

浏览器决定何时运行垃圾回收程序的一个标准就是对象更替的速度。如果有很多对象被初始化，然后一下子又都超出了作用域，那么浏览器就会采用更激进的方式调度垃圾回收程序运行，这样当然会影响性能。看一看下面的例子，这是一个计算二维矢量加法的函数：

```js
function addVector(a, b) {
  let resultant = new Vector();
  resultant.x = a.x + b.x;
  resultant.y = a.y + b.y;
  return resultant;
}
```

调用这个函数时，会在堆上创建一个新对象，然后修改它，最后再把它返回给调用者。如果这个矢量对象的生命周期很短，那么它会很快失去所有对它的引用，成为可以被回收的值。假如这个矢量加法函数频繁被调用，那么垃圾回收调度程序会发现这里对象更替的速度很快，从而会更频繁地安排垃圾回收。

该问题的解决方案是不要动态创建矢量对象，比如可以修改上面的函数，让它使用一个已有的矢量对象：

```js
function addVector(a, b, resultant) {
  resultant.x = a.x + b.x;
  resultant.y = a.y + b.y;
  return resultant;
}
```

当然，这需要在其他地方实例化矢量参数 resultant，但这个函数的行为没有变。那么在哪里创建矢量可以不让垃圾回收调度程序盯上呢？

一个策略是使用对象池。在初始化的某一时刻，可以创建一个对象池，用来管理一组可回收的对象。应用程序可以向这个对象池请求一个对象、设置其属性、使用它，然后在操作完成后再把它还给对象池。由于没发生对象初始化，垃圾回收探测就不会发现有对象更替，因此垃圾回收程序就不会那么频繁地运行。下面是一个对象池的伪实现：

```js
// vectorPool 是已有的对象池
let v1 = vectorPool.allocate();
let v2 = vectorPool.allocate();
let v3 = vectorPool.allocate();
v1.x = 10;
v1.y = 5;
v2.x = -3;
v2.y = -6;
addVector(v1, v2, v3);
console.log([v3.x, v3.y]); // [7, -1]
vectorPool.free(v1);
vectorPool.free(v2);
vectorPool.free(v3);
// 如果对象有属性引用了其他对象
// 则这里也需要把这些属性设置为null
v1 = null;
v2 = null;
v3 = null;
```

如果对象池只按需分配矢量（在对象不存在时创建新的，在对象存在时则复用存在的），那么这个实现本质上是一种贪婪算法，有单调增长但为静态的内存。这个对象池必须使用某种结构维护所有对象，数组是比较好的选择。不过，使用数组来实现，必须留意不要招致额外的垃圾回收。比如下面这个例子：

```js
let vectorList = new Array(100);
let vector = new Vector();
vectorList.push(vector);
```

由于 JavaScript 数组的大小是动态可变的，引擎会删除大小为 100 的数组，再创建一个新的大小为 200 的数组。垃圾回收程序会看到这个删除操作，说不定因此很快就会跑来收一次垃圾。要避免这种动态分配操作，可以在初始化时就创建一个大小够用的数组，从而避免上述先删除再创建的操作。不过，必须事先想好这个数组有多大。

注意 静态分配是优化的一种极端形式。如果你的应用程序被垃圾回收严重地拖了后腿，可以利用它提升性能。但这种情况并不多见。大多数情况下，这都属于过早优化，因此不用考虑。

# 5. 基本引用类型

本章内容

- 理解对象
- 基本 JavaScript 数据类型
- 原始值与原始值包装类型

引用值（或者对象）是某个特定引用类型的实例。在 ECMAScript 中，引用类型是把数据和功能组织到一起的结构，经常被人错误地称作“类”。虽然从技术上讲 JavaScript 是一门面向对象语言，但 ECMAScript 缺少传统的面向对象编程语言所具备的某些基本结构，包括类和接口。引用类型有时候也被称为对象定义，因为它们描述了自己的对象应有的属性和方法。

注意 引用类型虽然有点像类，但跟类并不是一个概念。为避免混淆，本章后面不会使用术语“类”。

对象被认为是某个特定引用类型的实例。新对象通过使用 new 操作符后跟一个 **构造函数(constructor)** 来创建。构造函数就是用来创建新对象的函数，比如下面这行代码：

```js
let now = new Date();
```

这行代码创建了引用类型 Date 的一个新实例，并将它保存在变量 now 中。Date()在这里就是构造函数，它负责创建一个只有默认属性和方法的简单对象。ECMAScript 提供了很多像 Date 这样的原生引用类型，帮助开发者实现常见的任务。

注意 函数也是一种引用类型，但有关函数的内容太多了，一章放不下，所以本书专门用第 10 章来介绍函数。

## 5.1. Date

ECMAScript 的 Date 类型参考了 Java 早期版本中的 java.util.Date。为此，Date 类型将日期保存为自协调世界时（UTC，Universal Time Coordinated）时间 1970 年 1 月 1 日午夜（零时）至今所经过的毫秒数。使用这种存储格式，Date 类型可以精确表示 1970 年 1 月 1 日之前及之后 285 616 年的日期。

要创建日期对象，就使用 new 操作符来调用 Date 构造函数：

```js
let now = new Date();
```

在不给 Date 构造函数传参数的情况下，创建的对象将保存当前日期和时间。要基于其他日期和时间创建日期对象，必须传入其毫秒表示（UNIX 纪元 1970 年 1 月 1 日午夜之后的毫秒数）。ECMAScript 为此提供了两个辅助方法：Date.parse()和 Date.UTC()。

Date.parse()方法接收一个表示日期的字符串参数，尝试将这个字符串转换为表示该日期的毫秒数。ECMA-262 第 5 版定义了 Date.parse()应该支持的日期格式，填充了第 3 版遗留的空白。所有实现都必须支持下列日期格式：

- “月/日/年”，如"08/07/2021"；
- “月名 日, 年”，如"Aug 07, 2021"；
- “周几 月名 日 年 时:分:秒 时区”，如"Sat Aug 07 2021 00:00:00 GMT-0700"；
- ISO 8601 扩展格式“YYYY-MM-DDTHH:mm:ss.sssZ”，如 2021-08-07T00:00:00（只适用于
  兼容 ES5 的实现）。

比如，要创建一个表示“2021 年 08 月 07 日”的日期对象，可以使用以下代码：

```js
let someDate = new Date(Date.parse("Aug 07, 2021"));
```

如果传给 Date.parse()的字符串并不表示日期，则该方法会返回 NaN。如果直接把表示日期的字符串传给 Date 构造函数，那么 Date 会在后台调用 Date.parse()。换句话说，下面这行代码跟前面那行代码是等价的：

```js
let someDate = new Date("Aug 07, 2021");
```

这两行代码得到的日期对象相同。

注意 不同的浏览器对 Date 类型的实现有很多问题。比如，很多浏览器会选择用当前日期替代越界的日期，因此有些浏览器会将"January 32, 2019"解释为"February 1,2019"。Opera 则会插入当前月的当前日，返回"January 当前日, 2019"。就是说，如果是在 9 月 21 日运行代码，会返回"January 21, 2019"。

Date.UTC()方法也返回日期的毫秒表示，但使用的是跟 Date.parse()不同的信息来生成这个值。传给 Date.UTC()的参数是年、零起点月数（1 月是 0，2 月是 1，以此类推）、日（1~31）、时（0~23）、分、秒和毫秒。这些参数中，只有前两个（年和月）是必需的。如果不提供日，那么默认为 1 日。其他参数的默认值都是 0。下面是使用 Date.UTC()的两个例子：

```js
// GMT 时间2000 年1 月1 日零点
let y2k = new Date(Date.UTC(2000, 0));

// GMT 时间2005 年5 月5 日下午5 点55 分55 秒
let allFives = new Date(Date.UTC(2005, 4, 5, 17, 55, 55));
```

这个例子创建了两个日期 。第一个日期是 2000 年 1 月 1 日零点（GMT），2000 代表年，0 代表月（1 月）。因为没有其他参数（日取 1，其他取 0），所以结果就是该月第 1 天零点。第二个日期表示 2005 年 5 月 5 日下午 5 点 55 分 55 秒（GMT）。虽然日期里面涉及的都是 5，但月数必须用 4，因为月数是零起点的。小时也必须是 17，因为这里采用的是 24 小时制，即取值范围是 0~23。其他参数就都很直观了。

与 Date.parse()一样，Date.UTC()也会被 Date 构造函数隐式调用，但有一个区别：这种情况下创建的是本地日期，不是 GMT 日期。不过 Date 构造函数跟 Date.UTC()接收的参数是一样的。因此，如果第一个参数是数值，则构造函数假设它是日期中的年，第二个参数就是月，以此类推。前面的例子也可以这样来写：

```js
// 本地时间2000 年1 月1 日零点
let y2k = new Date(2000, 0);

// 本地时间2005 年5 月5 日下午5 点55 分55 秒
let allFives = new Date(2005, 4, 5, 17, 55, 55);
```

以上代码创建了与前面例子中相同的两个日期，但这次的两个日期是（由于系统设置决定的）本地时区的日期。

ECMAScript 还提供了 Date.now()方法，返回表示方法执行时日期和时间的毫秒数。这个方法可以方便地用在代码分析中：

```js
// 起始时间
let start = Date.now();

// 调用函数
doSomething();

// 结束时间
let stop = Date.now(),
  result = stop - start;
```

### 5.1.1. 继承的方法

与其他类型一样，Date 类型重写了 toLocaleString()、toString()和 valueOf()方法。但与其他类型不同，重写后这些方法的返回值不一样。Date 类型的 toLocaleString()方法返回与浏览器运行的本地环境一致的日期和时间。这通常意味着格式中包含针对时间的 AM（上午）或 PM（下午），但不包含时区信息（具体格式可能因浏览器而不同）。toString()方法通常返回带时区信息的日期和时间，而时间也是以 24 小时制（0~23）表示的。下面给出了 toLocaleString()和 toString()返回的 2019 年 2 月 1 日零点的示例（地区为"en-US"的 PST，即 Pacific Standard Time，太平洋标准时间）：

toLocaleString() - 2/1/2019 12:00:00 AM
toString() - Thu Feb 1 2019 00:00:00 GMT-0800 (Pacific Standard Time)

现代浏览器在这两个方法的输出上已经趋于一致。在比较老的浏览器上，每个方法返回的结果可能在每个浏览器上都是不同的。这些差异意味着 toLocaleString()和 toString()可能只对调试有用，不能用于显示。

Date 类型的 valueOf()方法根本就不返回字符串，这个方法被重写后返回的是日期的毫秒表示。因此，操作符（如小于号和大于号）可以直接使用它返回的值。比如下面的例子：

```js
let date1 = new Date(2019, 0, 1); // 2019 年1 月1 日
let date2 = new Date(2019, 1, 1); // 2019 年2 月1 日

console.log(date1 < date2); // true
console.log(date1 > date2); // false
```

日期 2019 年 1 月 1 日在 2019 年 2 月 1 日之前，所以说前者小于后者没问题。因为 2019 年 1 月 1 日的毫秒表示小于 2019 年 2 月 1 日的毫秒表示，所以用小于号比较这两个日期时会返回 true。这也是确保日期先后的一个简单方式。

### 5.1.2. 日期格式化方法

Date 类型有几个专门用于格式化日期的方法，它们都会返回字符串：

- toDateString()显示日期中的周几、月、日、年（格式特定于实现）；
- toTimeString()显示日期中的时、分、秒和时区（格式特定于实现）；
- toLocaleDateString()显示日期中的周几、月、日、年（格式特定于实现和地区）；
- toLocaleTimeString()显示日期中的时、分、秒（格式特定于实现和地区）；
- toUTCString()显示完整的 UTC 日期（格式特定于实现）。

这些方法的输出与 toLocaleString()和 toString()一样，会因浏览器而异。因此不能用于在用户界面上一致地显示日期。

注意 还有一个方法叫 toGMTString()，这个方法跟 toUTCString()是一样的，目的是为了向后兼容。不过，规范建议新代码使用 toUTCString()。

### 5.1.3. 日期/时间组件方法

Date 类型剩下的方法（见下表）直接涉及取得或设置日期值的特定部分。注意表中“UTC 日期”，指的是没有时区偏移（将日期转换为 GMT）时的日期。

| 方 法                                       | 说 明                                                                                                      |
| ------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| getTime()                                   | 返回日期的毫秒表示；与 valueOf()相同                                                                       |
| setTime(milliseconds)                       | 设置日期的毫秒表示，从而修改整个日期                                                                       |
| getFullYear()                               | 返回 4 位数年（即 2019 而不是 19）                                                                         |
| getUTCFullYear()                            | 返回 UTC 日期的 4 位数年                                                                                   |
| setFullYear(year)                           | 设置日期的年（year 必须是 4 位数）                                                                         |
| setUTCFullYear(year)                        | 设置 UTC 日期的年（year 必须是 4 位数）                                                                    |
| getMonth()                                  | 返回日期的月（0 表示 1 月，11 表示 12 月）                                                                 |
| getUTCMonth()                               | 返回 UTC 日期的月（0 表示 1 月，11 表示 12 月）                                                            |
| setMonth(month)                             | 设置日期的月（month 为大于 0 的数值，大于 11 加年）                                                        |
| setUTCMonth(month)                          | 设置 UTC 日期的月（month 为大于 0 的数值，大于 11 加年）                                                   |
| getDate()                                   | 返回日期中的日（1~31）                                                                                     |
| getUTCDate()                                | 返回 UTC 日期中的日（1~31）                                                                                |
| setDate(date)                               | 设置日期中的日（如果 date 大于该月天数，则加月）                                                           |
| setUTCDate(date)                            | 设置 UTC 日期中的日（如果 date 大于该月天数，则加月）                                                      |
| getDay()                                    | 返回日期中表示周几的数值（0 表示周日，6 表示周六）                                                         |
| getUTCDay()                                 | 返回 UTC 日期中表示周几的数值（0 表示周日，6 表示周六）                                                    |
| getHours() 返回日期中的时（0~23）           |
| getUTCHours()                               | 返回 UTC 日期中的时（0~23）                                                                                |
| setHours(hours)                             | 设置日期中的时（如果 hours 大于 23，则加日）                                                               |
| setUTCHours(hours)                          | 设置 UTC 日期中的时（如果 hours 大于 23，则加日）                                                          |
| getMinutes()                                | 返回日期中的分（0~59）                                                                                     |
| getUTCMinutes() 返回 UTC 日期中的分（0~59） |
| setMinutes(minutes)                         | 设置日期中的分（如果 minutes 大于 59，则加时）                                                             |
| setUTCMinutes(minutes)                      | 设置 UTC 日期中的分（如果 minutes 大于 59，则加时）                                                        |
| getSeconds()                                | 返回日期中的秒（0~59）                                                                                     |
| getUTCSeconds()                             | 返回 UTC 日期中的秒（0~59）                                                                                |
| setSeconds(seconds)                         | 设置日期中的秒（如果 seconds 大于 59，则加分）                                                             |
| setUTCSeconds(seconds)                      | 设置 UTC 日期中的秒（如果 seconds 大于 59，则加分）                                                        |
| getMilliseconds()                           | 返回日期中的毫秒                                                                                           |
| getUTCMilliseconds()                        | 返回 UTC 日期中的毫秒                                                                                      |
| setMilliseconds(milliseconds)               | 设置日期中的毫秒                                                                                           |
| setUTCMilliseconds(milliseconds)            | 设置 UTC 日期中的毫秒                                                                                      |
| getTimezoneOffset()                         | 返回以分钟计的 UTC 与本地时区的偏移量（如美国 EST 即“东部标准时间”返回 300，进入夏令时的地区可能有所差异） |

下面是一个演示：

```js
function getTime(date) {
  return `${date.getFullYear()}-${
    date.getMonth() + 1
  }-${date.getDate()} ${date.getHours()}:${date.getMinutes()}:${date.getSeconds()} ${date.getMilliseconds()}ms`;
}
console.log(getTime(new Date())); // 2021-8-7 17:55:40 837ms
```

## 5.2. RegExp

ECMAScript 通过 RegExp 类型支持正则表达式。正则表达式使用类似 Perl 的简洁语法来创建：

```js
let expression = /pattern/flags;
```

这个正则表达式的 pattern（模式）可以是任何简单或复杂的正则表达式，包括字符类、限定符、分组、向前查找和反向引用。每个正则表达式可以带零个或多个 flags（标记），用于控制正则表达式的行为。下面给出了表示匹配模式的标记。

- g：全局模式，表示查找字符串的全部内容，而不是找到第一个匹配的内容就结束。
- i：不区分大小写，表示在查找匹配时忽略 pattern 和字符串的大小写。
- m：多行模式，表示查找到一行文本末尾时会继续查找。
- y：粘附模式，表示只查找从 lastIndex 开始及之后的字符串。
- u：Unicode 模式，启用 Unicode 匹配。
- s：dotAll 模式，表示元字符.匹配任何字符（包括\n 或\r）。

使用不同模式和标记可以创建出各种正则表达式，比如：

```js
// 匹配字符串中的所有"at"
let pattern1 = /at/g;

// 匹配第一个"bat"或"cat"，忽略大小写
let pattern2 = /[bc]at/i;

// 匹配所有以"at"结尾的三字符组合，忽略大小写
let pattern3 = /.at/gi;
```

与其他语言中的正则表达式类似，所有元字符在模式中也必须转义，包括：

( [ { \ ^ $ | ) ] } ? \* + .

元字符在正则表达式中都有一种或多种特殊功能，所以要匹配上面这些字符本身，就必须使用反斜杠来转义。下面是几个例子：

```js
// 匹配第一个"bat"或"cat"，忽略大小写
let pattern1 = /[bc]at/i;

// 匹配第一个"[bc]at"，忽略大小写
let pattern2 = /\[bc\]at/i;

// 匹配所有以"at"结尾的三字符组合，忽略大小写
let pattern3 = /.at/gi;

// 匹配所有".at"，忽略大小写
let pattern4 = /\.at/gi;
```

这里的 pattern1 匹配"bat"或"cat"，不区分大小写。要直接匹配"\[bc\]at"，左右中括号都必须像 pattern2 中那样使用反斜杠转义。在 pattern3 中，点号表示"at"前面的任意字符都可以匹配。如果想匹配".at"，那么要像 pattern4 中那样对点号进行转义。

前面例子中的正则表达式都是使用字面量形式定义的。正则表达式也可以使用 RegExp 构造函数来创建，它接收两个参数：模式字符串和（可选的）标记字符串。任何使用字面量定义的正则表达式也可以通过构造函数来创建，比如：

```js
// 匹配第一个"bat"或"cat"，忽略大小写
let pattern1 = /[bc]at/i;

// 跟pattern1 一样，只不过是用构造函数创建的
let pattern2 = new RegExp("[bc]at", "i");
```

这里的 pattern1 和 pattern2 是等效的正则表达式。注意，RegExp 构造函数的两个参数都是字符串。因为 RegExp 的模式参数是字符串，所以在某些情况下需要二次转义。所有元字符都必须二次转义，包括转义字符序列，如\n（\转义后的字符串是\\，在正则表达式字符串中则要写成\\\\）。下表展示了几个正则表达式的字面量形式，以及使用 RegExp 构造函数创建时对应的模式字符串。

| 字面量模式         | 对应的字符串            |
| ------------------ | ----------------------- |
| `/\[bc\]at/`       | `"\\[bc\\]at"`          |
| `/\.at/ `          | `"\\.at"`               |
| `/name\/age/`      | `"name\\/age"`          |
| `/\d.\d{1,2}/`     | `"\\d.\\d{1,2}"`        |
| `/\w\\hello\\123/` | `"\\w\\\\hello\\\\123"` |

此外，使用 RegExp 也可以基于已有的正则表达式实例，并可选择性地修改它们的标记：

```js
const re1 = /cat/g;
console.log(re1); // "/cat/g"

const re2 = new RegExp(re1);
console.log(re2); // "/cat/g"

const re3 = new RegExp(re1, "i");
console.log(re3); // "/cat/i"
```

### 5.2.1. RegExp 实例属性

每个 RegExp 实例都有下列属性，提供有关模式的各方面信息。

- global：布尔值，表示是否设置了 g 标记。
- ignoreCase：布尔值，表示是否设置了 i 标记。
- unicode：布尔值，表示是否设置了 u 标记。
- sticky：布尔值，表示是否设置了 y 标记。
- lastIndex：整数，表示在源字符串中下一次搜索的开始位置，始终从 0 开始。
- multiline：布尔值，表示是否设置了 m 标记。
- dotAll：布尔值，表示是否设置了 s 标记。
- source：正则表达式的字面量字符串（不是传给构造函数的模式字符串），没有开头和结尾的斜杠。
- flags：正则表达式的标记字符串。始终以字面量而非传入构造函数的字符串模式形式返回（没有前后斜杠）。

通过这些属性可以全面了解正则表达式的信息，不过实际开发中用得并不多，因为模式声明中包含这些信息。下面是一个例子：

```js
let pattern1 = /\[bc\]at/i;

console.log(pattern1.global); // false
console.log(pattern1.ignoreCase); // true
console.log(pattern1.multiline); // false
console.log(pattern1.lastIndex); // 0
console.log(pattern1.source); // "\[bc\]at"
console.log(pattern1.flags); // "i"

let pattern2 = new RegExp("\\[bc\\]at", "i");

console.log(pattern2.global); // false
console.log(pattern2.ignoreCase); // true
console.log(pattern2.multiline); // false
console.log(pattern2.lastIndex); // 0
console.log(pattern2.source); // "\[bc\]at"
console.log(pattern2.flags); // "i"
```

注意，虽然第一个模式是通过字面量创建的，第二个模式是通过 RegExp 构造函数创建的，但两个模式的 source 和 flags 属性是相同的。source 和 flags 属性返回的是规范化之后可以在字面量中使用的形式。

### 5.2.2. RegExp 实例方法

RegExp 实例的主要方法是 exec()，主要用于配合捕获组使用。这个方法只接收一个参数，即要应用模式的字符串。如果找到了匹配项，则返回包含第一个匹配信息的数组；如果没找到匹配项，则返回 null。返回的数组虽然是 Array 的实例，但包含两个额外的属性：index 和 input。index 是字符串中匹配模式的起始位置，input 是要查找的字符串。这个数组的第一个元素是匹配整个模式的字符串，其他元素是与表达式中的捕获组匹配的字符串。如果模式中没有捕获组，则数组只包含一个元素。来看下面的例子：

```js
let text = "mom and dad and baby";
let pattern = /mom( and dad( and baby)?)?/gi;

let matches = pattern.exec(text);
console.log(matches.index); // 0
console.log(matches.input); // "mom and dad and baby"
console.log(matches[0]); // "mom and dad and baby"
console.log(matches[1]); // " and dad and baby"
console.log(matches[2]); // " and baby"
```

在这个例子中，模式包含两个捕获组：最内部的匹配项" and baby"，以及外部的匹配项" and dad"或" and dad and baby"。调用 exec()后找到了一个匹配项。因为整个字符串匹配模式，所以 matchs 数组的 index 属性就是 0。数组的第一个元素是匹配的整个字符串，第二个元素是匹配第一个捕获组的字符串，第三个元素是匹配第二个捕获组的字符串。

如果模式设置了全局标记，则每次调用 exec()方法会返回一个匹配的信息。如果没有设置全局标记，则无论对同一个字符串调用多少次 exec()，也只会返回第一个匹配的信息。

```js
let text = "cat, bat, sat, fat";
let pattern = /.at/;

let matches = pattern.exec(text);
console.log(matches.index); // 0
console.log(matches[0]); // cat
console.log(pattern.lastIndex); // 0

matches = pattern.exec(text);
console.log(matches.index); // 0
console.log(matches[0]); // cat
console.log(pattern.lastIndex); // 0
```

上面例子中的模式没有设置全局标记，因此调用 exec()只返回第一个匹配项（"cat"）。lastIndex 在非全局模式下始终不变。

如果在这个模式上设置了 g 标记，则每次调用 exec()都会在字符串中向前搜索下一个匹配项，如下面的例子所示：

```js
let text = "cat, bat, sat, fat";
let pattern = /.at/g;
let matches = pattern.exec(text);
console.log(matches.index); // 0
console.log(matches[0]); // cat
console.log(pattern.lastIndex); // 3

matches = pattern.exec(text);
console.log(matches.index); // 5
console.log(matches[0]); // bat
console.log(pattern.lastIndex); // 8

matches = pattern.exec(text);
console.log(matches.index); // 10
console.log(matches[0]); // sat
console.log(pattern.lastIndex); // 13
```

这次模式设置了全局标记，因此每次调用 exec()都会返回字符串中的下一个匹配项，直到搜索到字符串末尾。注意模式的 lastIndex 属性每次都会变化。在全局匹配模式下，每次调用 exec()都会更新 lastIndex 值，以反映上次匹配的最后一个字符的索引。

如果模式设置了粘附标记 y，则每次调用 exec()就只会在 lastIndex 的位置上寻找匹配项。粘附标记覆盖全局标记。

```js
let text = "cat, bat, sat, fat";
let pattern = /.at/y;
let matches = pattern.exec(text);
console.log(matches.index); // 0
console.log(matches[0]); // cat
console.log(pattern.lastIndex); // 3

// 以索引3 对应的字符开头找不到匹配项，因此exec()返回null
// exec()没找到匹配项，于是将lastIndex 设置为0
matches = pattern.exec(text);
console.log(matches); // null
console.log(pattern.lastIndex); // 0

// 向前设置lastIndex 可以让粘附的模式通过exec()找到下一个匹配项：
pattern.lastIndex = 5;
matches = pattern.exec(text);
console.log(matches.index); // 5
console.log(matches[0]); // bat
console.log(pattern.lastIndex); // 8
```

正则表达式的另一个方法是 test()，接收一个字符串参数。如果输入的文本与模式匹配，则参数返回 true，否则返回 false。这个方法适用于只想测试模式是否匹配，而不需要实际匹配内容的情况。test()经常用在 if 语句中：

```js
let text = "000-00-0000";
let pattern = /\d{3}-\d{2}-\d{4}/;

if (pattern.test(text)) {
  console.log("The pattern was matched.");
}
```

在这个例子中，正则表达式用于测试特定的数值序列。如果输入的文本与模式匹配，则显示匹配成功的消息。这个用法常用于验证用户输入，此时我们只在乎输入是否有效，不关心为什么无效。

无论正则表达式是怎么创建的，继承的方法 toLocaleString()和 toString()都返回正则表达式的字面量表示。比如：

```js
let pattern = new RegExp("\\[bc\\]at", "gi");
console.log(pattern.toString()); // /\[bc\]at/gi
console.log(pattern.toLocaleString()); // /\[bc\]at/gi
```

这里的模式是通过 RegExp 构造函数创建的，但 toLocaleString()和 toString()返回的都是其字面量的形式。

注意 正则表达式的 valueOf()方法返回正则表达式本身。

### 5.2.3. RegExp 构造函数属性

RegExp 构造函数本身也有几个属性。（在其他语言中，这种属性被称为静态属性。）这些属性适用于作用域中的所有正则表达式，而且会根据最后执行的正则表达式操作而变化。这些属性还有一个特点，就是可以通过两种不同的方式访问它们。换句话说，每个属性都有一个全名和一个简写。下表列出了 RegExp 构造函数的属性。

| 全 名        | 简 写                                        | 说 明 |
| ------------ | -------------------------------------------- | ----- |
| input        | $\_ 最后搜索的字符串（非标准特性）           |
| lastMatch    | $& 最后匹配的文本                            |
| lastParen    | $+ 最后匹配的捕获组（非标准特性）            |
| leftContext  | $` input 字符串中出现在 lastMatch 前面的文本 |
| rightContext | $' input 字符串中出现在 lastMatch 后面的文本 |

通过这些属性可以提取出与 exec()和 test()执行的操作相关的信息。来看下面的例子：

```js
let text = "this has been a short summer";
let pattern = /(.)hort/g;

if (pattern.test(text)) {
  console.log(RegExp.input); // this has been a short summer
  console.log(RegExp.leftContext); // this has been a
  console.log(RegExp.rightContext); // summer
  console.log(RegExp.lastMatch); // short
  console.log(RegExp.lastParen); // s
}
```

以上代码创建了一个模式，用于搜索任何后跟"hort"的字符，并把第一个字符放在了捕获组中。不同属性包含的内容如下。

- input 属性中包含原始的字符串。
- leftConext 属性包含原始字符串中"short"之前的内容，rightContext 属性包含"short"之后的内容。
- lastMatch 属性包含匹配整个正则表达式的上一个字符串，即"short"。
- lastParen 属性包含捕获组的上一次匹配，即"s"。

这些属性名也可以替换成简写形式，只不过要使用中括号语法来访问，如下面的例子所示，因为大多数简写形式都不是合法的 ECMAScript 标识符：

```js
let text = "this has been a short summer";
let pattern = /(.)hort/g;

/*
 * 注意：Opera 不支持简写属性名
 * IE 不支持多行匹配
 */
if (pattern.test(text)) {
  console.log(RegExp.$_); // this has been a short summer
  console.log(RegExp["$`"]); // this has been a
  console.log(RegExp["$'"]); // summer
  console.log(RegExp["$&"]); // short
  console.log(RegExp["$+"]); // s
}
```

RegExp 还有其他几个构造函数属性，可以存储最多 9 个捕获组的匹配项。这些属性通过 RegExp.$1~RegExp.$9 来访问，分别包含第 1~9 个捕获组的匹配项。在调用 exec()或 test()时，这些属性就会被填充，然后就可以像下面这样使用它们：

```js
let text = "this has been a short summer";
let pattern = /(..)or(.)/g;
if (pattern.test(text)) {
  console.log(RegExp.$1); // sh
  console.log(RegExp.$2); // t
}
```

在这个例子中，模式包含两个捕获组。调用 test()搜索字符串之后，因为找到了匹配项所以返回 true，而且可以打印出通过 RegExp 构造函数的$1 和$2 属性取得的两个捕获组匹配的内容。

注意 RegExp 构造函数的所有属性都没有任何 Web 标准出处，因此不要在生产环境中使用它们。

### 5.2.4. 模式局限

虽然 ECMAScript 对正则表达式的支持有了长足的进步，但仍然缺少 Perl 语言中的一些高级特性。下列特性目前还没有得到 ECMAScript 的支持（想要了解更多信息，可以参考 Regular-Expressions.info 网站）：

- \A 和\Z 锚（分别匹配字符串的开始和末尾）
- 联合及交叉类
- 原子组
- x（忽略空格）匹配模式
- 条件式匹配
- 正则表达式注释

虽然还有这些局限，但 ECMAScript 的正则表达式已经非常强大，可以用于大多数模式匹配任务。

## 5.3. 原始值包装类型

为了方便操作原始值，ECMAScript 提供了 3 种特殊的引用类型：Boolean、Number 和 String。这些类型具有本章介绍的其他引用类型一样的特点，但也具有与各自原始类型对应的特殊行为。每当用到某个原始值的方法或属性时，后台都会创建一个相应原始包装类型的对象，从而暴露出操作原始值的各种方法。来看下面的例子：

```js
let s1 = "some text";
let s2 = s1.substring(2);
```

在这里，s1 是一个包含字符串的变量，它是一个原始值。第二行紧接着在 s1 上调用了 substring()方法，并把结果保存在 s2 中。我们知道，原始值本身不是对象，因此逻辑上不应该有方法。而实际上这个例子又确实按照预期运行了。这是因为后台进行了很多处理，从而实现了上述操作。具体来说，当第二行访问 s1 时，是以读模式访问的，也就是要从内存中读取变量保存的值。在以读模式访问字符串值的任何时候，后台都会执行以下 3 步：

1. 创建一个 String 类型的实例；
2. 调用实例上的特定方法；
3. 销毁实例。

可以把这 3 步想象成执行了如下 3 行 ECMAScript 代码：

```js
let s1 = new String("some text");
let s2 = s1.substring(2);
s1 = null;
```

这种行为可以让原始值拥有对象的行为。对布尔值和数值而言，以上 3 步也会在后台发生，只不过使用的是 Boolean 和 Number 包装类型而已。

引用类型与原始值包装类型的主要区别在于对象的生命周期。在通过 new 实例化引用类型后，得到的实例会在离开作用域时被销毁，而自动创建的原始值包装对象则只存在于访问它的那行代码执行期间。这意味着不能在运行时给原始值添加属性和方法。比如下面的例子：

```js
let s1 = "some text";
s1.color = "red";
console.log(s1.color); // undefined
```

这里的第二行代码尝试给字符串 s1 添加了一个 color 属性。可是，第三行代码访问 color 属性时，它却不见了。原因就是第二行代码运行时会临时创建一个 String 对象，而当第三行代码执行时，这个对象已经被销毁了。实际上，第三行代码在这里创建了自己的 String 对象，但这个对象没有 color 属性。

可以显式地使用 Boolean、Number 和 String 构造函数创建原始值包装对象。不过应该在确实必要时再这么做，否则容易让开发者疑惑，分不清它们到底是原始值还是引用值。在原始值包装类型的实例上调用 typeof 会返回"object"，所有原始值包装对象都会转换为布尔值 true。

另外，Object 构造函数作为一个工厂方法，能够根据传入值的类型返回相应原始值包装类型的实例。比如：

```js
let obj = new Object("some text");
console.log(obj instanceof String); // true
```

如果传给 Object 的是字符串，则会创建一个 String 的实例。如果是数值，则会创建 Number 的实例。布尔值则会得到 Boolean 的实例。

注意，使用 new 调用原始值包装类型的构造函数，与调用同名的转型函数并不一样。例如：

```js
let value = "25";
let number = Number(value); // 转型函数
console.log(typeof number); // "number"
let obj = new Number(value); // 构造函数
console.log(typeof obj); // "object"
```

在这个例子中，变量 number 中保存的是一个值为 25 的原始数值，而变量 obj 中保存的是一个 Number 的实例。

虽然不推荐显式创建原始值包装类型的实例，但它们对于操作原始值的功能是很重要的。每个原始值包装类型都有相应的一套方法来方便数据操作。

### 5.3.1. Boolean

Boolean 是对应布尔值的引用类型。要创建一个 Boolean 对象，就使用 Boolean 构造函数并传入 true 或 false，如下例所示：

```js
let booleanObject = new Boolean(true);
```

Boolean 的实例会重写 valueOf()方法，返回一个原始值 true 或 false。toString()方法被调用时也会被覆盖，返回字符串"true"或"false"。不过，Boolean 对象在 ECMAScript 中用得很少。不仅如此，它们还容易引起误会，尤其是在布尔表达式中使用 Boolean 对象时，比如：

```js
let falseObject = new Boolean(false);
let result = falseObject && true;
console.log(result); // true

let falseValue = false;
result = falseValue && true;
console.log(result); // false
```

在这段代码中，我们创建一个值为 false 的 Boolean 对象。然后，在一个布尔表达式中通过&&操作将这个对象与一个原始值 true 组合起来。在布尔算术中，false && true 等于 false。可是，这个表达式是对 falseObject 对象而不是对它表示的值（false）求值。前面刚刚说过，所有对象在布尔表达式中都会自动转换为 true，因此 falseObject 在这个表达式里实际上表示一个 true 值。那么 true && true 当然是 true。

除此之外，原始值和引用值（Boolean 对象）还有几个区别。首先，typeof 操作符对原始值返回"boolean"，但对引用值返回"object"。同样，Boolean 对象是 Boolean 类型的实例，在使用 instaceof 操作符时返回 true，但对原始值则返回 false，如下所示：

```js
console.log(typeof falseObject); // object
console.log(typeof falseValue); // boolean
console.log(falseObject instanceof Boolean); // true
console.log(falseValue instanceof Boolean); // false
```

理解原始布尔值和 Boolean 对象之间的区别非常重要，强烈建议永远不要使用后者。

### 5.3.2. Number

Number 是对应数值的引用类型。要创建一个 Number 对象，就使用 Number 构造函数并传入一个数值，如下例所示：

```js
let numberObject = new Number(10);
```

与 Boolean 类型一样，Number 类型重写了 valueOf()、toLocaleString()和 toString()方法。valueOf()方法返回 Number 对象表示的原始数值，另外两个方法返回数值字符串。toString()方法可选地接收一个表示基数的参数，并返回相应基数形式的数值字符串，如下所示：

```js
let num = 10;
console.log(num.toString()); // "10"
console.log(num.toString(2)); // "1010"
console.log(num.toString(8)); // "12"
console.log(num.toString(10)); // "10"
console.log(num.toString(16)); // "a"
```

除了继承的方法，Number 类型还提供了几个用于将数值格式化为字符串的方法。

toFixed()方法返回包含指定小数点位数的数值字符串，如：

```js
let num = 10;
console.log(num.toFixed(2)); // "10.00"
```

这里的 toFixed()方法接收了参数 2，表示返回的数值字符串要包含两位小数。结果返回值为"10.00"，小数位填充了 0。如果数值本身的小数位超过了参数指定的位数，则四舍五入到最接近的小数位：

```js
let num = 10.005;
console.log(num.toFixed(2)); // "10.01"
```

toFixed()自动舍入的特点可以用于处理货币。不过要注意的是，多个浮点数值的数学计算不一定得到精确的结果。比如，0.1 + 0.2 = 0.30000000000000004。

注意 toFixed()方法可以表示有 0~20 个小数位的数值。某些浏览器可能支持更大的范围，但这是通常被支持的范围。

另一个用于格式化数值的方法是 toExponential()，返回以科学记数法（也称为指数记数法）表示的数值字符串。与 toFixed()一样，toExponential()也接收一个参数，表示结果中小数的位数。来看下面的例子：

```js
let num = 10;
console.log(num.toExponential(1)); // "1.0e+1"
```

这段代码的输出为"1.0e+1"。一般来说，这么小的数不用表示为科学记数法形式。如果想得到数值最适当的形式，那么可以使用 toPrecision()。

toPrecision()方法会根据情况返回最合理的输出结果，可能是固定长度，也可能是科学记数法形式。这个方法接收一个参数，表示结果中数字的总位数（不包含指数）。来看几个例子：

```js
let num = 99;
console.log(num.toPrecision(1)); // "1e+2"
console.log(num.toPrecision(2)); // "99"
console.log(num.toPrecision(3)); // "99.0"
```

在这个例子中，首先要用 1 位数字表示数值 99，得到"1e+2"，也就是 100。因为 99 不能只用 1 位数字来精确表示，所以这个方法就将它舍入为 100，这样就可以只用 1 位数字（及其科学记数法形式）来表示了。用 2 位数字表示 99 得到"99"，用 3 位数字则是"99.0"。本质上，toPrecision()方法会根据数值和精度来决定调用 toFixed()还是 toExponential()。为了以正确的小数位精确表示数值，这 3 个方法都会向上或向下舍入。

与 Boolean 对象类似，Number 对象也为数值提供了重要能力。但是，考虑到两者存在同样的潜在问题，因此并不建议直接实例化 Number 对象。在处理原始数值和引用数值时，typeof 和 instacnceof 操作符会返回不同的结果，如下所示：

```js
let numberObject = new Number(10);
let numberValue = 10;
console.log(typeof numberObject); // "object"
console.log(typeof numberValue); // "number"
console.log(numberObject instanceof Number); // true
console.log(numberValue instanceof Number); // false
```

原始数值在调用 typeof 时始终返回"number"，而 Number 对象则返回"object"。类似地，Number 对象是 Number 类型的实例，而原始数值不是。

**isInteger()方法与安全整数**

ES6 新增了 Number.isInteger()方法，用于辨别一个数值是否保存为整数。有时候，小数位的 0 可能会让人误以为数值是一个浮点值：

```js
console.log(Number.isInteger(1)); // true
console.log(Number.isInteger(1.0)); // true
console.log(Number.isInteger(1.01)); // false
```

IEEE 754 数值格式有一个特殊的数值范围，在这个范围内二进制值可以表示一个整数值。这个数值范围从 Number.MIN_SAFE_INTEGER（-2^53 + 1）到 Number.MAX_SAFE_INTEGER（2^53 - 1）。对超出这个范围的数值，即使尝试保存为整数，IEEE 754 编码格式也意味着二进制值可能会表示一个完全不同的数值。例如：

```js
let test = 2 ** 53 === 2 ** 53 + 1;
console.log(test); // true
```

为了鉴别整数是否在这个范围内，可以使用 Number.isSafeInteger()方法：

```js
console.log(Number.isSafeInteger(-1 * 2 ** 53)); // false
console.log(Number.isSafeInteger(-1 * 2 ** 53 + 1)); // true
console.log(Number.isSafeInteger(2 ** 53)); // false
console.log(Number.isSafeInteger(2 ** 53 - 1)); // true
```

### 5.3.3. String

String 是对应字符串的引用类型。要创建一个 String 对象，使用 String 构造函数并传入一个数值，如下例所示：

```js
let stringObject = new String("hello world");
```

String 对象的方法可以在所有字符串原始值上调用。3 个继承的方法 valueOf()、toLocaleString()和 toString()都返回对象的原始字符串值。

每个 String 对象都有一个 length 属性，表示字符串中字符的数量。来看下面的例子：

```js
let stringValue = "hello world";
console.log(stringValue.length); // "11"
```

这个例子输出了字符串"hello world"中包含的字符数量：11。注意，即使字符串中包含双字节字符（而不是单字节的 ASCII 字符），也仍然会按单字符来计数。

String 类型提供了很多方法来解析和操作字符串。

1. **JavaScript 字符**

JavaScript 字符串由 16 位码元（code unit）组成。对多数字符来说，每 16 位码元对应一个字符。换句话说，字符串的 length 属性表示字符串包含多少 16 位码元：

```js
let message = "abcde";
console.log(message.length); // 5
```

此外，charAt()方法返回给定索引位置的字符，由传给方法的整数参数指定。具体来说，这个方法查找指定索引位置的 16 位码元，并返回该码元对应的字符：

```js
let message = "abcde";
console.log(message.charAt(2)); // "c"
```

JavaScript 字符串使用了两种 Unicode 编码混合的策略：UCS-2 和 UTF-16。对于可以采用 16 位编码的字符（U+0000~U+FFFF），这两种编码实际上是一样的。

注意 要深入了解关于字符编码的内容，推荐 Joel Spolsky 写的博客文章：“The Absolute Minimum Every Software Developer Absolutely, Positively Must Know About Unicode and Character Sets (No Excuses!)”。另一个有用的资源是 Mathias Bynens 的博文：“JavaScript’s Internal Character Encoding: UCS-2 or UTF-16?”。

使用 charCodeAt()方法可以查看指定码元的字符编码。这个方法返回指定索引位置的码元值，索引以整数指定。比如：

```js
let message = "abcde";

// Unicode "小写拉丁字母 C"的编码是U+0063
console.log(message.charCodeAt(2)); // 99

// 十进制99 等于十六进制63
console.log(99 === 0x63); // true
```

fromCharCode()方法用于根据给定的 UTF-16 码元创建字符串中的字符。这个方法可以接受任意多个数值，并返回将所有数值对应的字符拼接起来的字符串：

```js
// Unicode "小写拉丁字母 A"的编码是U+0061
// Unicode "小写拉丁字母 B"的编码是U+0062
// Unicode "小写拉丁字母 C"的编码是U+0063
// Unicode "小写拉丁字母 D"的编码是U+0064
// Unicode "小写拉丁字母 E"的编码是U+0065
console.log(String.fromCharCode(0x61, 0x62, 0x63, 0x64, 0x65)); // "abcde"
// 0x0061 === 97
// 0x0062 === 98
// 0x0063 === 99
// 0x0064 === 100
// 0x0065 === 101
console.log(String.fromCharCode(97, 98, 99, 100, 101)); // "abcde"
```

对于 U+0000~U+FFFF 范围内的字符，length、charAt()、charCodeAt()和 fromCharCode()返回的结果都跟预期是一样的。这是因为在这个范围内，每个字符都是用 16 位表示的，而这几个方法也都基于 16 位码元完成操作。只要字符编码大小与码元大小一一对应，这些方法就能如期工作。

这个对应关系在扩展到 Unicode 增补字符平面时就不成立了。问题很简单，即 16 位只能唯一表示 65 536 个字符。这对于大多数语言字符集是足够了，在 Unicode 中称为 **基本多语言平面(BMP)**。为了表示更多的字符，Unicode 采用了一个策略，即每个字符使用另外 16 位去选择一个增补平面。这种每个字符使用两个 16 位码元的策略称为 **代理对**。

在涉及增补平面的字符时，前面讨论的字符串方法就会出问题。比如，下面的例子中使用了一个笑脸表情符号，也就是一个使用代理对编码的字符：

```js
// "smiling face with smiling eyes" 表情符号的编码是U+1F60A
// 0x1F60A === 128522

let message = "ab☺de";
console.log(message.length); // 6
console.log(message.charAt(1)); // b
console.log(message.charAt(2)); // <?>
console.log(message.charAt(3)); // <?>
console.log(message.charAt(4)); // d
console.log(message.charCodeAt(1)); // 98
console.log(message.charCodeAt(2)); // 55357
console.log(message.charCodeAt(3)); // 56842
console.log(message.charCodeAt(4)); // 100
console.log(String.fromCodePoint(0x1f60a)); // ☺
console.log(String.fromCharCode(97, 98, 55357, 56842, 100, 101)); // ab☺de
```

这些方法仍然将 16 位码元当作一个字符，事实上索引 2 和索引 3 对应的码元应该被看成一个代理对，只对应一个字符。fromCharCode()方法仍然返回正确的结果，因为它实际上是基于提供的二进制表示直接组合成字符串。浏览器可以正确解析代理对（由两个码元构成），并正确地将其识别为一个 Unicode 笑脸字符。

为正确解析既包含单码元字符又包含代理对字符的字符串，可以使用 codePointAt()来代替 charCodeAt()。跟使用 charCodeAt()时类似，codePointAt()接收 16 位码元的索引并返回该索引位置上的码点（code point）。码点是 Unicode 中一个字符的完整标识。比如，"c"的码点是 0x0063，而"☺"的码点是 0x1F60A。码点可能是 16 位，也可能是 32 位，而 codePointAt()方法可以从指定码元位置识别完整的码点。

```js
let message = "ab☺de";
console.log(message.codePointAt(1)); // 98
console.log(message.codePointAt(2)); // 128522
console.log(message.codePointAt(3)); // 56842
console.log(message.codePointAt(4)); // 100
```

注意，如果传入的码元索引并非代理对的开头，就会返回错误的码点。这种错误只有检测单个字符的时候才会出现，可以通过从左到右按正确的码元数遍历字符串来规避。迭代字符串可以智能地识别代理对的码点：

```js
console.log([..."ab☺de"]); // ["a", "b", "☺", "d", "e"]
```

与 charCodeAt()有对应的 codePointAt()一样，fromCharCode()也有一个对应的 fromCodePoint()。这个方法接收任意数量的码点，返回对应字符拼接起来的字符串：

```js
console.log(String.fromCharCode(97, 98, 55357, 56842, 100, 101)); // ab☺de
console.log(String.fromCodePoint(97, 98, 128522, 100, 101)); // ab☺de
```

2. **normalize 方法**

某些 Unicode 字符可以有多种编码方式。有的字符既可以通过一个 BMP 字符表示，也可以通过一个代理对表示。比如：

```js
// U+00C5：上面带圆圈的大写拉丁字母A
console.log(String.fromCharCode(0x00c5)); // Å
// U+212B：长度单位“埃”
console.log(String.fromCharCode(0x212b)); // Å
// U+004：大写拉丁字母A
// U+030A：上面加个圆圈
console.log(String.fromCharCode(0x0041, 0x030a)); // Å
```

比较操作符不在乎字符看起来是什么样的，因此这 3 个字符互不相等。

```js
let a1 = String.fromCharCode(0x00c5),
  a2 = String.fromCharCode(0x212b),
  a3 = String.fromCharCode(0x0041, 0x030a);

console.log(a1, a2, a3); // Å, Å, Å
console.log(a1 === a2); // false
console.log(a1 === a3); // false
console.log(a2 === a3); // false
```

为解决这个问题，Unicode 提供了 4 种规范化形式，可以将类似上面的字符规范化为一致的格式，无论底层字符的代码是什么。这 4 种规范化形式是：NFD（Normalization Form D）、NFC（Normalization Form C）、NFKD（Normalization Form KD）和 NFKC（Normalization Form KC）。可以使用 normalize()方法对字符串应用上述规范化形式，使用时需要传入表示哪种形式的字符串："NFD"、"NFC"、"NFKD"或"NFKC"。

注意 这 4 种规范化形式的具体细节超出了本书范围，有兴趣的读者可以自行参考 UAX15#: Unicode Normalization Forms 中的 1.2 节“Normalization Forms”。

通过比较字符串与其调用 normalize()的返回值，就可以知道该字符串是否已经规范化了：

```js
let a1 = String.fromCharCode(0x00c5),
  a2 = String.fromCharCode(0x212b),
  a3 = String.fromCharCode(0x0041, 0x030a);
// U+00C5 是对0+212B 进行NFC/NFKC 规范化之后的结果
console.log(a1 === a1.normalize("NFD")); // false
console.log(a1 === a1.normalize("NFC")); // true
console.log(a1 === a1.normalize("NFKD")); // false
console.log(a1 === a1.normalize("NFKC")); // true
// U+212B 是未规范化的
console.log(a2 === a2.normalize("NFD")); // false
console.log(a2 === a2.normalize("NFC")); // false
console.log(a2 === a2.normalize("NFKD")); // false
console.log(a2 === a2.normalize("NFKC")); // false
// U+0041/U+030A 是对0+212B 进行NFD/NFKD 规范化之后的结果
console.log(a3 === a3.normalize("NFD")); // true
console.log(a3 === a3.normalize("NFC")); // false
console.log(a3 === a3.normalize("NFKD")); // true
console.log(a3 === a3.normalize("NFKC")); // false
```

选择同一种规范化形式可以让比较操作符返回正确的结果：

```js
let a1 = String.fromCharCode(0x00c5),
  a2 = String.fromCharCode(0x212b),
  a3 = String.fromCharCode(0x0041, 0x030a);
console.log(a1.normalize("NFD") === a2.normalize("NFD")); // true
console.log(a2.normalize("NFKC") === a3.normalize("NFKC")); // true
console.log(a1.normalize("NFC") === a3.normalize("NFC")); // true
```

3. **字符串操作方法**

本节介绍几个操作字符串值的方法。首先是 concat()，用于将一个或多个字符串拼接成一个新字符串。来看下面的例子：

```js
let stringValue = "hello ";
let result = stringValue.concat("world");
console.log(result); // "hello world"
console.log(stringValue); // "hello"
```

在这个例子中，对 stringValue 调用 concat()方法的结果是得到"hello world"，但 stringValue 的值保持不变。concat()方法可以接收任意多个参数，因此可以一次性拼接多个字符串，如下所示：

```js
let stringValue = "hello ";
let result = stringValue.concat("world", "!");
console.log(result); // "hello world!"
console.log(stringValue); // "hello"
```

这个修改后的例子将字符串"world"和"!"追加到了"hello "后面。虽然 concat()方法可以拼接字符串，但更常用的方式是使用加号操作符（+）。而且多数情况下，对于拼接多个字符串来说，使用加号更方便。

ECMAScript 提供了 3 个从字符串中提取子字符串的方法：slice()、substr()和 substring()。这 3 个方法都返回调用它们的字符串的一个子字符串，而且都接收一或两个参数。第一个参数表示子字符串开始的位置，第二个参数表示子字符串结束的位置。对 slice()和 substring()而言，第二个参数是提取结束的位置（即该位置之前的字符会被提取出来）。对 substr()而言，第二个参数表示返回的子字符串数量。任何情况下，省略第二个参数都意味着提取到字符串末尾。与 concat()方法一样，slice()、substr()和 substring()也不会修改调用它们的字符串，而只会返回提取到的原始新字符串值。来看下面的例子：

```js
let stringValue = "hello world";
console.log(stringValue.slice(3)); // "lo world"
console.log(stringValue.substring(3)); // "lo world"
console.log(stringValue.substr(3)); // "lo world"
console.log(stringValue.slice(3, 7)); // "lo w"
console.log(stringValue.substring(3, 7)); // "lo w"
console.log(stringValue.substr(3, 7)); // "lo worl"
```

在这个例子中，slice()、substr()和 substring()是以相同方式被调用的，而且多数情况下返回的值也相同。如果只传一个参数 3，则所有方法都将返回"lo world"，因为"hello"中"l"位置为 3。如果传入两个参数 3 和 7，则 slice()和 substring()返回"lo w"（因为"world"中"o"在位置 7，不包含），而 substr()返回"lo worl"，因为第二个参数对它而言表示返回的字符数。

当某个参数是负值时，这 3 个方法的行为又有不同。比如，slice()方法将所有负值参数都当成字符串长度加上负参数值。

而 substr()方法将第一个负参数值当成字符串长度加上该值，将第二个负参数值转换为 0。substring()方法会将所有负参数值都转换为 0。看下面的例子：

```js
let stringValue = "hello world";
console.log(stringValue.slice(-3)); // "rld"
console.log(stringValue.substring(-3)); // "hello world"
console.log(stringValue.substr(-3)); // "rld"
console.log(stringValue.slice(3, -4)); // "lo w"
console.log(stringValue.substring(3, -4)); // "hel"
console.log(stringValue.substr(3, -4)); // "" (empty string)
```

这个例子明确演示了 3 个方法的差异。在给 slice()和 substr()传入负参数时，它们的返回结果相同。这是因为-3 会被转换为 8（长度加上负参数），实际上调用的是 slice(8)和 substr(8)。而 substring()方法返回整个字符串，因为-3 会转换为 0。

在第二个参数是负值时，这 3 个方法各不相同。slice()方法将第二个参数转换为 7，实际上相当于调用 slice(3, 7)，因此返回"lo w"。而 substring()方法会将第二个参数转换为 0，相当于调用 substring(3, 0)，等价于 substring(0, 3)，这是因为这个方法会将较小的参数作为起点，将较大的参数作为终点。对 substr()来说，第二个参数会被转换为 0，意味着返回的字符串包含零个字符，因而会返回一个空字符串。

4. **字符串位置方法**

有两个方法用于在字符串中定位子字符串：indexOf()和 lastIndexOf()。这两个方法从字符串中搜索传入的字符串，并返回位置（如果没找到，则返回-1）。两者的区别在于，indexOf()方法从字符串开头开始查找子字符串，而 lastIndexOf()方法从字符串末尾开始查找子字符串。来看下面的例子：

```js
let stringValue = "hello world";
console.log(stringValue.indexOf("o")); // 4
console.log(stringValue.lastIndexOf("o")); // 7
```

这里，字符串中第一个"o"的位置是 4，即"hello"中的"o"。最后一个"o"的位置是 7，即"world"中的"o"。如果字符串中只有一个"o"，则 indexOf()和 lastIndexOf()返回同一个位置。

这两个方法都可以接收可选的第二个参数，表示开始搜索的位置。这意味着，indexOf()会从这个参数指定的位置开始向字符串末尾搜索，忽略该位置之前的字符；lastIndexOf()则会从这个参数指定的位置开始向字符串开头搜索，忽略该位置之后直到字符串末尾的字符。下面看一个例子：

```js
let stringValue = "hello world";
console.log(stringValue.indexOf("o", 6)); // 7
console.log(stringValue.lastIndexOf("o", 6)); // 4
```

在传入第二个参数 6 以后，结果跟前面的例子恰好相反。这一次，indexOf()返回 7，因为它从位置 6（字符"w"）开始向后搜索字符串，在位置 7 找到了"o"。而 lastIndexOf()返回 4，因为它从位置 6 开始反向搜索至字符串开头，因此找到了"hello"中的"o"。像这样使用第二个参数并循环调用 indexOf()或 lastIndexOf()，就可以在字符串中找到所有的目标子字符串，如下所示：

```js
let stringValue = "Lorem ipsum dolor sit amet, consectetur adipisicing elit";
let positions = new Array();
let pos = stringValue.indexOf("e");
while (pos > -1) {
  positions.push(pos);
  pos = stringValue.indexOf("e", pos + 1);
}
console.log(positions); // [3,24,32,35,52]
```

这个例子逐步增大开始搜索的位置，通过 indexOf()遍历了整个字符串。首先取得第一个"e"的位置，然后进入循环，将上一次的位置加 1 再传给 indexOf()，确保搜索到最后一个子字符串实例之后。每个位置都保存在 positions 数组中，可供以后使用。

5. **字符串包含方法**

ECMAScript 6 增加了 3 个用于判断字符串中是否包含另一个字符串的方法：startsWith()、endsWith()和 includes()。这些方法都会从字符串中搜索传入的字符串，并返回一个表示是否包含的布尔值。它们的区别在于，startsWith()检查开始于索引 0 的匹配项，endsWith()检查开始于索引(string.length - substring.length)的匹配项，而 includes()检查整个字符串：

```js
let message = "foobarbaz";
console.log(message.startsWith("foo")); // true
console.log(message.startsWith("bar")); // false
console.log(message.endsWith("baz")); // true
console.log(message.endsWith("bar")); // false
console.log(message.includes("bar")); // true
console.log(message.includes("qux")); // false
```

startsWith()和 includes()方法接收可选的第二个参数，表示开始搜索的位置。如果传入第二个参数，则意味着这两个方法会从指定位置向着字符串末尾搜索，忽略该位置之前的所有字符。下面是一个例子：

```js
let message = "foobarbaz";
console.log(message.startsWith("foo")); // true
console.log(message.startsWith("foo", 1)); // false
console.log(message.includes("bar")); // true
console.log(message.includes("bar", 4)); // false
```

endsWith()方法接收可选的第二个参数，表示应该当作字符串末尾的位置。如果不提供这个参数，那么默认就是字符串长度。如果提供这个参数，那么就好像字符串只有那么多字符一样：

```js
let message = "foobarbaz";
console.log(message.endsWith("bar")); // false
console.log(message.endsWith("bar", 6)); // true
```

6. **trim() 方法**

ECMAScript 在所有字符串上都提供了 trim()方法。这个方法会创建字符串的一个副本，删除前、后所有空格符，再返回结果。比如：

```js
let stringValue = " hello world ";
let trimmedStringValue = stringValue.trim();
console.log(stringValue); // " hello world "
console.log(trimmedStringValue); // "hello world"
```

由于 trim()返回的是字符串的副本，因此原始字符串不受影响，即原本的前、后空格符都会保留。另外，trimLeft()和 trimRight()方法分别用于从字符串开始和末尾清理空格符。

7. **repeat() 方法**

ECMAScript 在所有字符串上都提供了 repeat()方法。这个方法接收一个整数参数，表示要将字符串复制多少次，然后返回拼接所有副本后的结果。

```js
let stringValue = "na ";
console.log(stringValue.repeat(16) + "batman");
// na na na na na na na na na na na na na na na na batman
```

8. **padStart()和 padEnd()方法**

padStart()和 padEnd()方法会复制字符串，如果小于指定长度，则在相应一边填充字符，直至满足长度条件。这两个方法的第一个参数是长度，第二个参数是可选的填充字符串，默认为空格（U+0020）。

```js
let stringValue = "foo";
console.log(stringValue.padStart(6)); // " foo"
console.log(stringValue.padStart(9, ".")); // "......foo"
console.log(stringValue.padEnd(6)); // "foo "
console.log(stringValue.padEnd(9, ".")); // "foo......"
```

可选的第二个参数并不限于一个字符。如果提供了多个字符的字符串，则会将其拼接并截断以匹配指定长度。此外，如果长度小于或等于字符串长度，则会返回原始字符串。

```js
let stringValue = "foo";
console.log(stringValue.padStart(8, "bar")); // "barbafoo"
console.log(stringValue.padStart(2)); // "foo"
console.log(stringValue.padEnd(8, "bar")); // "foobarba"
console.log(stringValue.padEnd(2)); // "foo"
```

9. **字符串迭代与解构**

字符串的原型上暴露了一个@@iterator 方法，表示可以迭代字符串的每个字符。可以像下面这样手动使用迭代器：

```js
let message = "abc";
let stringIterator = message[Symbol.iterator]();
console.log(stringIterator.next()); // {value: "a", done: false}
console.log(stringIterator.next()); // {value: "b", done: false}
console.log(stringIterator.next()); // {value: "c", done: false}
console.log(stringIterator.next()); // {value: undefined, done: true}
```

在 for-of 循环中可以通过这个迭代器按序访问每个字符：

```js
for (const c of "abcde") {
  console.log(c);
}
// a
// b
// c
// d
// e
```

有了这个迭代器之后，字符串就可以通过解构操作符来解构了。比如，可以更方便地把字符串分割为字符数组：

```js
let message = "abcde";
console.log([...message]); // ["a", "b", "c", "d", "e"]
```

10. **字符串大小写转换**

下一组方法涉及大小写转换，包括 4 个方法：toLowerCase()、toLocaleLowerCase()、toUpperCase()和 toLocaleUpperCase()。toLowerCase()和 toUpperCase()方法是原来就有的方法，与 java.lang.String 中的方法同名。toLocaleLowerCase()和 toLocaleUpperCase()方法旨在基于特定地区实现。在很多地区，地区特定的方法与通用的方法是一样的。但在少数语言中（如土耳其语），Unicode 大小写转换需应用特殊规则，要使用地区特定的方法才能实现正确转换。下面是几个例子：

```js
let stringValue = "hello world";
console.log(stringValue.toLocaleUpperCase()); // "HELLO WORLD"
console.log(stringValue.toUpperCase()); // "HELLO WORLD"
console.log(stringValue.toLocaleLowerCase()); // "hello world"
console.log(stringValue.toLowerCase()); // "hello world"
```

这里，toLowerCase()和 toLocaleLowerCase()都返回 hello world，而 toUpperCase()和 toLocaleUpperCase()都返回 HELLO WORLD。通常，如果不知道代码涉及什么语言，则最好使用地区特定的转换方法。

11. **字符串模式匹配方法**

String 类型专门为在字符串中实现模式匹配设计了几个方法。第一个就是 match()方法，这个方法本质上跟 RegExp 对象的 exec()方法相同。match()方法接收一个参数，可以是一个正则表达式字符串，也可以是一个 RegExp 对象。来看下面的例子：

```js
let text = "cat, bat, sat, fat";
let pattern = /.at/;

// 等价于pattern.exec(text)
let matches = text.match(pattern);
console.log(matches.index); // 0
console.log(matches[0]); // "cat"
console.log(pattern.lastIndex); // 0
```

match()方法返回的数组与 RegExp 对象的 exec()方法返回的数组是一样的：第一个元素是与整个模式匹配的字符串，其余元素则是与表达式中的捕获组匹配的字符串（如果有的话）。

另一个查找模式的字符串方法是 search()。这个方法唯一的参数与 match()方法一样：正则表达式字符串或 RegExp 对象。这个方法返回模式第一个匹配的位置索引，如果没找到则返回-1。search()始终从字符串开头向后匹配模式。看下面的例子：

```js
let text = "cat, bat, sat, fat";
let pos = text.search(/at/);
console.log(pos); // 1
```

这里，search(/at/)返回 1，即"at"的第一个字符在字符串中的位置。

为简化子字符串替换操作，ECMAScript 提供了 replace()方法。这个方法接收两个参数，第一个参数可以是一个 RegExp 对象或一个字符串（这个字符串不会转换为正则表达式），第二个参数可以是一个字符串或一个函数。如果第一个参数是字符串，那么只会替换第一个子字符串。要想替换所有子字符串，第一个参数必须为正则表达式并且带全局标记，如下面的例子所示：

```js
let text = "cat, bat, sat, fat";
let result = text.replace("at", "ond");
console.log(result); // "cond, bat, sat, fat"
result = text.replace(/at/g, "ond");
console.log(result); // "cond, bond, sond, fond"
```

在这个例子中，字符串"at"先传给 replace()函数，而替换文本是"ond"。结果是"cat"被修改为"cond"，而字符串的剩余部分保持不变。通过将第一个参数改为带全局标记的正则表达式，字符串中的所有"at"都被替换成了"ond"。

第二个参数是字符串的情况下，有几个特殊的字符序列，可以用来插入正则表达式操作的值。ECMA-262 中规定了下表中的值。

| 字符序列 | 替换文本                                                                                                                                                       |
| -------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| $$       | $                                                                                                                                                              |
| $&       | 匹配整个模式的子字符串。与 RegExp.lastMatch 相同                                                                                                               |
| $'       | 匹配的子字符串之前的字符串。与 RegExp.rightContext 相同                                                                                                        |
| $`       | 匹配的子字符串之后的字符串。与 RegExp.leftContext 相同                                                                                                         |
| $n       | 匹配第 n 个捕获组的字符串，其中 n 是 0~9。比如，`$1` 是匹配第一个捕获组的字符串，`$2` 是匹配第二个捕获组的字符串，以此类推。如果没有捕获组，则值为空字符串     |
| $nn      | 匹配第 nn 个捕获组字符串，其中 nn 是 01~99。比如，`$01` 是匹配第一个捕获组的字符串，`$02` 是匹配第二个捕获组的字符串，以此类推。如果没有捕获组，则值为空字符串 |

使用这些特殊的序列，可以在替换文本中使用之前匹配的内容，如下面的例子所示：

```js
let text = "cat, bat, sat, fat";
result = text.replace(/(.at)/g, "word ($1)");
console.log(result); // word (cat), word (bat), word (sat), word (fat)
```

这里，每个以"at"结尾的词都会被替换成"word"后跟一对小括号，其中包含捕获组匹配的内容$1。

replace()的第二个参数可以是一个函数。在只有一个匹配项时，这个函数会收到 3 个参数：与整个模式匹配的字符串、匹配项在字符串中的开始位置，以及整个字符串。在有多个捕获组的情况下，每个匹配捕获组的字符串也会作为参数传给这个函数，但最后两个参数还是与整个模式匹配的开始位置和原始字符串。这个函数应该返回一个字符串，表示应该把匹配项替换成什么。使用函数作为第二个参数可以更细致地控制替换过程，如下所示：

```js
function htmlEscape(text) {
  return text.replace(/[<>"&]/g, function (match, pos, originalText) {
    switch (match) {
      case "<":
        return "&lt;";
      case ">":
        return "&gt;";
      case "&":
        return "&amp;";
      case '"':
        return "&quot;";
    }
  });
}
console.log(htmlEscape('<p class="greeting">Hello world!</p>'));
// "&lt;p class=&quot;greeting&quot;&gt;Hello world!</p>"
```

这里，函数 htmlEscape()用于将一段 HTML 中的 4 个字符替换成对应的实体：小于号、大于号、和号，还有双引号（都必须经过转义）。实现这个任务最简单的办法就是用一个正则表达式查找这些字符，然后定义一个函数，根据匹配的每个字符分别返回特定的 HTML 实体。

最后一个与模式匹配相关的字符串方法是 split()。这个方法会根据传入的分隔符将字符串拆分成数组。作为分隔符的参数可以是字符串，也可以是 RegExp 对象。（字符串分隔符不会被这个方法当成正则表达式。）还可以传入第二个参数，即数组大小，确保返回的数组不会超过指定大小。来看下面的例子：

```js
let colorText = "red,blue,green,yellow";
let colors1 = colorText.split(","); // ["red", "blue", "green", "yellow"]
let colors2 = colorText.split(",", 2); // ["red", "blue"]
let colors3 = colorText.split(/[^,]+/); // ["", ",", ",", ",", ""]
```

在这里，字符串 colorText 是一个逗号分隔的颜色名称符串。调用 split(",")会得到包含这些颜色名的数组，基于逗号进行拆分。要把数组元素限制为 2 个，传入第二个参数 2 即可。最后，使用正则表达式可以得到一个包含逗号的数组。注意在最后一次调用 split()时，返回的数组前后包含两个空
字符串。这是因为正则表达式指定的分隔符出现在了字符串开头（"red"）和末尾（"yellow"）。

12. **localeCompare()方法**

最后一个方法是 localeCompare()，这个方法比较两个字符串，返回如下 3 个值中的一个。

- 如果按照字母表顺序，字符串应该排在字符串参数前头，则返回负值。（通常是-1，具体还要看与实际值相关的实现。）
- 如果字符串与字符串参数相等，则返回 0。
- 如果按照字母表顺序，字符串应该排在字符串参数后头，则返回正值。（通常是 1，具体还要看与实际值相关的实现。）

下面是一个例子：

```js
let stringValue = "yellow";
console.log(stringValue.localeCompare("brick")); // 1
console.log(stringValue.localeCompare("yellow")); // 0
console.log(stringValue.localeCompare("zoo")); // -1
```

在这里，字符串"yellow"与 3 个不同的值进行了比较："brick"、"yellow"和"zoo"。"brick"按字母表顺序应该排在"yellow"前头，因此 localeCompare()返回 1。"yellow"等于"yellow"，因此"localeCompare()"返回 0。最后，"zoo"在"yellow"后面，因此 localeCompare()返回-1。强调一下，因为返回的具体值可能因具体实现而异，所以最好像下面的示例中一样使用 localeCompare()：

```js
function determineOrder(value) {
  let result = stringValue.localeCompare(value);
  if (result < 0) {
    console.log(`The string 'yellow' comes before the string '${value}'.`);
  } else if (result > 0) {
    console.log(`The string 'yellow' comes after the string '${value}'.`);
  } else {
    console.log(`The string 'yellow' is equal to the string '${value}'.`);
  }
}
determineOrder("brick");
determineOrder("yellow");
determineOrder("zoo");
```

这样一来，就可以保证在所有实现中都能正确判断字符串的顺序了。localeCompare()的独特之处在于，实现所在的地区（国家和语言）决定了这个方法如何比较字符串。在美国，英语是 ECMAScript 实现的标准语言，localeCompare()区分大小写，大写字母排在小写字母前面。但其他地区未必是这种情况。

13. **HTML 方法**

早期的浏览器开发商认为使用 JavaScript 动态生成 HTML 标签是一个需求。因此，早期浏览器扩展了规范，增加了辅助生成 HTML 标签的方法。下表总结了这些 HTML 方法。不过，这些方法基本上已经没有人使用了，因为结果通常不是语义化的标记。

| 方 法            | 输 出                               |
| ---------------- | ----------------------------------- |
| anchor(name)     | `<a name="name">string</a>`         |
| big()            | `<big>string</big>`                 |
| bold()           | `<b>string</b>`                     |
| fixed()          | `<tt>string</tt>`                   |
| fontcolor(color) | `<font color="color">string</font>` |
| fontsize(size)   | `<font size="size">string</font>`   |
| italics()        | `<i>string</i>`                     |
| link(url)        | `<a href="url">string</a>`          |
| small()          | `<small>string</small>`             |
| strike()         | `<strike>string</strike>`           |
| sub()            | `<sub>string</sub>`                 |
| sup()            | `<sup>string</sup>`                 |

## 5.4. 单例内置对象

ECMA-262 对内置对象的定义是“任何由 ECMAScript 实现提供、与宿主环境无关，并在 ECMAScript 程序开始执行时就存在的对象”。这就意味着，开发者不用显式地实例化内置对象，因为它们已经实例化好了。前面我们已经接触了大部分内置对象，包括 Object、Array 和 String。本节介绍 ECMA-262 定义的另外两个单例内置对象：Global 和 Math。

### 5.4.1. Global

Global 对象是 ECMAScript 中最特别的对象，因为代码不会显式地访问它。ECMA-262 规定 Global 对象为一种兜底对象，它所针对的是不属于任何对象的属性和方法。事实上，不存在全局变量或全局函数这种东西。在全局作用域中定义的变量和函数都会变成 Global 对象的属性 。本书前面介绍的函数，包括 isNaN()、isFinite()、parseInt()和 parseFloat()，实际上都是 Global 对象的方法。除了这些，Global 对象上还有另外一些方法。

1. **URL 编码方法**

encodeURI()和 encodeURIComponent()方法用于编码统一资源标识符（URI），以便传给浏览器。有效的 URI 不能包含某些字符，比如空格。使用 URI 编码方法来编码 URI 可以让浏览器能够理解它们，同时又以特殊的 UTF-8 编码替换掉所有无效字符。

ecnodeURI()方法用于对整个 URI 进行编码，比如"www.wrox.com/illegal value.js"。而 encodeURIComponent()方法用于编码 URI 中单独的组件，比如前面 URL 中的"illegal value.js"。这两个方法的主要区别是，encodeURI()不会编码属于 URL 组件的特殊字符，比如冒号、斜杠、问号、
井号，而 encodeURIComponent()会编码它发现的所有非标准字符。来看下面的例子：

```js
let uri = "http://www.wrox.com/illegal value.js#start";

// "http://www.wrox.com/illegal%20value.js#start"
console.log(encodeURI(uri));

// "http%3A%2F%2Fwww.wrox.com%2Fillegal%20value.js%23start"
console.log(encodeURIComponent(uri));
```

这里使用 encodeURI()编码后，除空格被替换为%20 之外，没有任何变化。而 encodeURIComponent()方法将所有非字母字符都替换成了相应的编码形式。这就是使用 encodeURI()编码整个 URI，但只使用 encodeURIComponent()编码那些会追加到已有 URI 后面的字符串的原因。

注意 一般来说，使用 encodeURIComponent()应该比使用 encodeURI()的频率更高，这是因为编码查询字符串参数比编码基准 URI 的次数更多。

与 encodeURI()和 encodeURIComponent()相对的是 decodeURI()和 decodeURIComponent()。decodeURI()只对使用 encodeURI()编码过的字符解码。例如，%20 会被替换为空格，但%23 不会被替换为井号（#），因为井号不是由 encodeURI()替换的。类似地，decodeURIComponent()解码所有被 encodeURIComponent()编码的字符，基本上就是解码所有特殊值。来看下面的例子：

```js
let uri = "http%3A%2F%2Fwww.wrox.com%2Fillegal%20value.js%23start";

// http%3A%2F%2Fwww.wrox.com%2Fillegal value.js%23start
console.log(decodeURI(uri));

// http:// www.wrox.com/illegal value.js#start
console.log(decodeURIComponent(uri));
```

这里，uri 变量中包含一个使用 encodeURIComponent()编码过的字符串。首先输出的是使用 decodeURI()解码的结果，可以看到只用空格替换了%20。然后是使用 decodeURIComponent()解码的结果，其中替换了所有特殊字符，并输出了没有包含任何转义的字符串。（这个字符串不是有效的 URL。）

注意 URI 方法 encodeURI()、encodeURIComponent()、decodeURI()和 decodeURIComponent()取代了 escape()和 unescape()方法，后者在 ECMA-262 第 3 版中就已经废弃了。URI 方法始终是首选方法，因为它们对所有 Unicode 字符进行编码，而原来的方法只能正确编码 ASCII 字符。不要在生产环境中使用 escape()和 unescape()。

2. **eval()方法**

最后一个方法可能是整个 ECMAScript 语言中最强大的了，它就是 eval()。这个方法就是一个完整的 ECMAScript 解释器，它接收一个参数，即一个要执行的 ECMAScript（JavaScript）字符串。来看一个例子：

```js
eval("console.log('hi')");
```

上面这行代码的功能与下一行等价：

```js
console.log("hi");
```

当解释器发现 eval()调用时，会将参数解释为实际的 ECMAScript 语句，然后将其插入到该位置。通过 eval()执行的代码属于该调用所在上下文，被执行的代码与该上下文拥有相同的作用域链。这意味着定义在包含上下文中的变量可以在 eval()调用内部被引用，比如下面这个例子：

```js
let msg = "hello world";
eval("console.log(msg)"); // "hello world"
```

这里，变量 msg 是在 eval()调用的外部上下文中定义的，而 console.log()显示了文本"hello world"。这是因为第二行代码会被替换成一行真正的函数调用代码。类似地，可以在 eval()内部定义一个函数或变量，然后在外部代码中引用，如下所示：

```js
eval("function sayHi() { console.log('hi'); }");
sayHi();
```

这里，函数 sayHi()是在 eval()内部定义的。因为该调用会被替换为真正的函数定义，所以才可能在下一行代码中调用 sayHi()。对于变量也是一样的：

```js
eval("let msg = 'hello world';");
console.log(msg); // Reference Error: msg is not defined
```

通过 eval()定义的任何变量和函数都不会被提升，这是因为在解析代码的时候，它们是被包含在一个字符串中的。它们只是在 eval()执行的时候才会被创建。

在严格模式下，在 eval()内部创建的变量和函数无法被外部访问。换句话说，最后两个例子会报错。同样，在严格模式下，赋值给 eval 也会导致错误：

```js
"use strict";
eval = "hi"; // 导致错误
```

注意 解释代码字符串的能力是非常强大的，但也非常危险。在使用 eval()的时候必须极为慎重，特别是在解释用户输入的内容时。因为这个方法会对 XSS 利用暴露出很大的攻击面。恶意用户可能插入会导致你网站或应用崩溃的代码。

3. **Global 对象属性**

Global 对象有很多属性，其中一些前面已经提到过了。像 undefined、NaN 和 Infinity 等特殊值都是 Global 对象的属性。此外，所有原生引用类型构造函数，比如 Object 和 Function，也都是 Global 对象的属性。下表列出了所有这些属性。

| 属 性          | 说 明                     |
| -------------- | ------------------------- |
| undefined      | 特殊值 undefined          |
| NaN            | 特殊值 NaN                |
| Infinity       | 特殊值 Infinity           |
| Object         | Object 的构造函数         |
| Array          | Array 的构造函数          |
| Function       | Function 的构造函数       |
| Boolean        | Boolean 的构造函数        |
| String         | String 的构造函数         |
| Number         | Number 的构造函数         |
| Date           | Date 的构造函数           |
| RegExp         | RegExp 的构造函数         |
| Symbol         | Symbol 的伪构造函数       |
| Error          | Error 的构造函数          |
| EvalError      | EvalError 的构造函数      |
| RangeError     | RangeError 的构造函数     |
| ReferenceError | ReferenceError 的构造函数 |
| SyntaxError    | SyntaxError 的构造函数    |
| TypeError      | TypeError 的构造函数      |
| URIError       | URIError 的构造函数       |

4. **window 对象**

虽然 ECMA-262 没有规定直接访问 Global 对象的方式，但浏览器将 window 对象实现为 Global 对象的代理。因此，所有全局作用域中声明的变量和函数都变成了 window 的属性。来看下面的例子：

```js
var color = "red";
function sayColor() {
  console.log(window.color);
}
window.sayColor(); // "red"
```

这里定义了一个名为 color 的全局变量和一个名为 sayColor()的全局函数。在 sayColor()内部，通过 window.color 访问了 color 变量，说明全局变量变成了 window 的属性。接着，又通过 window 对象直接调用了 window.sayColor()函数，从而输出字符串。

注意 window 对象在 JavaScript 中远不止实现了 ECMAScript 的 Global 对象那么简单。关于 window 对象的更多介绍，请参考第 12 章。

另一种获取 Global 对象的方式是使用如下的代码：

```js
let global = (function () {
  return this;
})();
```

这段代码创建一个立即调用的函数表达式，返回了 this 的值。如前所述，当一个函数在没有明确（通过成为某个对象的方法，或者通过 call()/apply()）指定 this 值的情况下执行时，this 值等于 Global 对象。因此，调用一个简单返回 this 的函数是在任何执行上下文中获取 Global 对象的通用方式。

### 5.4.2. Math

注意 Math 对象上提供的计算要比直接在 JavaScript 实现的快得多，因为 Math 对象上的计算使用了 JavaScript 引擎中更高效的实现和处理器指令。但使用 Math 计算的问题是精度会因浏览器、操作系统、指令集和硬件而异。

1. **Math 对象属性**

Math 对象有一些属性，主要用于保存数学中的一些特殊值。下表列出了这些属性。

| 属 性        | 说 明                 |
| ------------ | --------------------- |
| Math.E       | 自然对数的基数 e 的值 |
| Math.LN10    | 10 为底的自然对数     |
| Math.LN2     | 2 为底的自然对数      |
| Math.LOG2E   | 以 2 为底 e 的对数    |
| Math.LOG10E  | 以 10 为底 e 的对数   |
| Math.PI      | π 的值                |
| Math.SQRT1_2 | 1/2 的平方根          |
| Math.SQRT2   | 2 的平方根            |

这些值的含义和用法超出了本书的范畴，但都是 ECMAScript 规范定义的，并可以在你需要时使用。

2. **min()和 max()方法**

Math 对象也提供了很多辅助执行简单或复杂数学计算的方法。

min()和 max()方法用于确定一组数值中的最小值和最大值。这两个方法都接收任意多个参数，如下面的例子所示：

```js
let max = Math.max(3, 54, 32, 16);
console.log(max); // 54

let min = Math.min(3, 54, 32, 16);
console.log(min); // 3
```

在 3、54、32 和 16 中，Math.max()返回 54，Math.min()返回 3。使用这两个方法可以避免使用额外的循环和 if 语句来确定一组数值的最大最小值。

要知道数组中的最大值和最小值，可以像下面这样使用扩展操作符：

```js
let values = [1, 2, 3, 4, 5, 6, 7, 8];
let max = Math.max(...values);
```

3. **舍入方法**

接下来是用于把小数值舍入为整数的 4 个方法：Math.ceil()、Math.floor()、Math.round()和 Math.fround()。这几个方法处理舍入的方式如下所述。

- Math.ceil()方法始终向上舍入为最接近的整数。
- Math.floor()方法始终向下舍入为最接近的整数。
- Math.round()方法执行四舍五入。
- Math.fround()方法返回数值最接近的单精度（32 位）浮点值表示。

以下示例展示了这些方法的用法：

```js
console.log(Math.ceil(25.9)); // 26
console.log(Math.ceil(25.5)); // 26
console.log(Math.ceil(25.1)); // 26
console.log(Math.round(25.9)); // 26
console.log(Math.round(25.5)); // 26
console.log(Math.round(25.1)); // 25
console.log(Math.fround(0.4)); // 0.4000000059604645
console.log(Math.fround(0.5)); // 0.5
console.log(Math.fround(25.9)); // 25.899999618530273
console.log(Math.floor(25.9)); // 25
console.log(Math.floor(25.5)); // 25
console.log(Math.floor(25.1)); // 25
```

对于 25 和 26（不包含）之间的所有值，Math.ceil()都会返回 26，因为它始终向上舍入。Math.round()只在数值大于等于 25.5 时返回 26，否则返回 25。最后，Math.floor()对所有 25 和 26（不包含）之间的值都返回 25。

4. **random()方法**

Math.random()方法返回一个 0~1 范围内的随机数，其中包含 0 但不包含 1。对于希望显示随机名言或随机新闻的网页，这个方法是非常方便的。可以基于如下公式使用 Math.random()从一组整数中随机选择一个数：

```js
number = Math.floor(
  Math.random() * total_number_of_choices + first_possible_value
);
```

这里使用了 Math.floor()方法，因为 Math.random()始终返回小数，即便乘以一个数再加上一个数也是小数。因此，如果想从 1~10 范围内随机选择一个数，代码就是这样的：

```js
let num = Math.floor(Math.random() * 10 + 1);
```

这样就有 10 个可能的值（1~10），其中最小的值是 1。如果想选择一个 2~10 范围内的值，则代码就要写成这样：

```js
let num = Math.floor(Math.random() * 9 + 2);
```

2~10 只有 9 个数，所以可选总数（total_number_of_choices）是 9，而最小可能的值（first_possible_value）是 2。很多时候，通过函数来算出可选总数和最小可能的值可能更方便，比如：

```js
function selectFrom(lowerValue, upperValue) {
  let choices = upperValue - lowerValue + 1;
  return Math.floor(Math.random() * choices + lowerValue);
}
let num = selectFrom(2, 10);
console.log(num); // 2~10 范围内的值，其中包含2 和10
```

这里的函数 selectFrom()接收两个参数：应该返回的最小值和最大值。通过将这两个值相减再加 1 得到可选总数，然后再套用上面的公式。于是，调用 selectFrom(2,10)就可以从 2~10（包含）范围内选择一个值了。使用这个函数，从一个数组中随机选择一个元素就很容易，比如：

```js
let colors = ["red", "green", "blue", "yellow", "black", "purple", "brown"];
let color = colors[selectFrom(0, colors.length - 1)];
```

例如，生成一个随机的颜色码，即一个 6 位的 16 进制数，可以这样做：

```js
let maxValue = (0xffffff).toString(10);
console.log(maxValue); // 16777215

let colorCode = "#" + Math.floor(Math.random() * 16777216).toString(16);
console.log(colorCode); // #3684b4
```

注意 Math.random()方法在这里出于演示目的是没有问题的。如果是为了加密而需要生成随机数（传给生成器的输入需要较高的不确定性），那么建议使用 window.crypto.getRandomValues()。

5. **其他方法**

Math 对象还有很多涉及各种简单或高阶数运算的方法。讨论每种方法的具体细节或者它们的适用场景超出了本书的范畴。不过，下表还是总结了 Math 对象的其他方法。

| 方 法               | 说 明                            |
| ------------------- | -------------------------------- |
| Math.abs(x)         | 返回 x 的绝对值                  |
| Math.exp(x)         | 返回 Math.E 的 x 次幂            |
| Math.expm1(x)       | 等于 Math.exp(x) - 1             |
| Math.log(x)         | 返回 x 的自然对数                |
| Math.log1p(x)       | 等于 1 + Math.log(x)             |
| Math.pow(x, power)  | 返回 x 的 power 次幂             |
| Math.hypot(...nums) | 返回 nums 中每个数平方和的平方根 |
| Math.clz32(x)       | 返回 32 位整数 x 的前置零的数量  |
| Math.sign(x)        | 返回表示 x 符号的 1、0、-0 或-1  |
| Math.trunc(x)       | 返回 x 的整数部分，删除所有小数  |
| Math.sqrt(x)        | 返回 x 的平方根                  |
| Math.cbrt(x)        | 返回 x 的立方根                  |
| Math.acos(x)        | 返回 x 的反余弦                  |
| Math.acosh(x)       | 返回 x 的反双曲余弦              |
| Math.asin(x)        | 返回 x 的反正弦                  |
| Math.asinh(x)       | 返回 x 的反双曲正弦              |
| Math.atan(x)        | 返回 x 的反正切                  |
| Math.atanh(x)       | 返回 x 的反双曲正切              |
| Math.atan2(y, x)    | 返回 y/x 的反正切                |
| Math.cos(x)         | 返回 x 的余弦                    |
| Math.sin(x)         | 返回 x 的正弦                    |
| Math.tan(x)         | 返回 x 的正切                    |

即便这些方法都是由 ECMA-262 定义的，对正弦、余弦、正切等计算的实现仍然取决于浏览器，因为计算这些值的方式有很多种。结果，这些方法的精度可能因实现而异。

# 6. 集合引用类型

本章内容

- 对象
- 数组与定型数组
- Map、WeakMap、Set 以及 WeakSet 类型

## 6.1. Object

到目前为止，大多数引用值的示例使用的是 Object 类型。Object 是 ECMAScript 中最常用的类型之一。虽然 Object 的实例没有多少功能，但很适合存储和在应用程序间交换数据。

```js
let person = new Object();
person.name = "Nicholas";
person.age = 29;
```

另一种方式是使用 **对象字面量(object literal)** 表示法。对象字面量是对象定义的简写形式，目的是为了简化包含大量属性的对象的创建。比如，下面的代码定义了与前面示例相同的 person 对象，但使用的是对象字面量表示法：

```js
let person = {
  name: "Nicholas",
  age: 29,
};
```

在这个例子中，左大括号（{）表示对象字面量开始，因为它出现在一个 **表达式上下文(expression context)** 中。在 ECMAScript 中，表达式上下文指的是期待返回值的上下文。赋值操作符表示后面要期待一个值，因此左大括号表示一个表达式的开始。同样是左大括号，如果出现在 **语句上下文(statement context)** 中，比如 if 语句的条件后面，则表示一个语句块的开始。

接下来指定了 name 属性，后跟一个冒号，然后是属性的值。逗号用于在对象字面量中分隔属性，因此字符串"Nicholas"后面有一个逗号，而 29 后面没有，因为 age 是这个对象的最后一个属性。在最后一个属性后面加上逗号在非常老的浏览器中会导致报错，但所有现代浏览器都支持这种写法。在对象字面量表示法中，属性名可以是字符串或数值，比如：

```js
let person = {
  name: "Nicholas",
  age: 29,
  5: true,
};
```

这个例子会得到一个带有属性 name、age 和 5 的对象。注意，数值属性会自动转换为字符串。

当然也可以用对象字面量表示法来定义一个只有默认属性和方法的对象，只要使用一对大括号，中间留空就行了：

```js
let person = {}; // 与new Object()相同
person.name = "Nicholas";
person.age = 29;
```

这个例子跟本节开始的第一个例子是等效的，虽然看起来有点怪。对象字面量表示法通常只在为了让属性一目了然时才使用。

注意 在使用对象字面量表示法定义对象时，并不会实际调用 Object 构造函数。

虽然使用哪种方式创建 Object 实例都可以，但实际上开发者更倾向于使用对象字面量表示法。这是因为对象字面量代码更少，看起来也更有封装所有相关数据的感觉。事实上，对象字面量已经成为给函数传递大量可选参数的主要方式，比如：

```js
function displayInfo(args) {
  let output = "";
  if (typeof args.name == "string") {
    output += "Name: " + args.name + "\n";
  }
  if (typeof args.age == "number") {
    output += "Age: " + args.age + "\n";
  }
  console.log(output);
}
displayInfo({
  name: "Nicholas",
  age: 29,
});
displayInfo({
  name: "Greg",
});
```

这里，函数 displayInfo()接收一个名为 args 的参数。这个参数可能有属性 name 或 age，也可能两个属性都有或者都没有。函数内部会使用 typeof 操作符测试每个属性是否存在，然后根据属性有无构造并显示一条消息。然后，这个函数被调用了两次，每次都通过一个对象字面量传入了不同的数据。两种情况下，函数都正常运行。

注意 这种模式非常适合函数有大量可选参数的情况。一般来说，命名参数更直观，但在可选参数过多的时候就显得笨拙了。最好的方式是对必选参数使用命名参数，再通过一个对象字面量来封装多个可选参数。

虽然属性一般是通过点语法来存取的，这也是面向对象语言的惯例，但也可以使用中括号来存取属性。在使用中括号时，要在括号内使用属性名的字符串形式，比如：

```js
console.log(person["name"]); // "Nicholas"
console.log(person.name); // "Nicholas"
```

从功能上讲，这两种存取属性的方式没有区别。使用中括号的主要优势就是可以通过变量访问属性，就像下面这个例子中一样：

```js
let propertyName = "name";
console.log(person[propertyName]); // "Nicholas"
```

另外，如果属性名中包含可能会导致语法错误的字符，或者包含关键字/保留字时，也可以使用中括号语法。比如：

```js
person["first name"] = "Nicholas";
```

因为"first name"中包含一个空格，所以不能使用点语法来访问。不过，属性名中是可以包含非字母数字字符的，这时候只要用中括号语法存取它们就行了。

通常，点语法是首选的属性存取方式，除非访问属性时必须使用变量。

注意 第 8 章将更全面、深入地介绍 Object 类型。

## 6.2. Array

除了 Object，Array 应该就是 ECMAScript 中最常用的类型了。ECMAScript 数组跟其他编程语言的数组有很大区别。跟其他语言中的数组一样，ECMAScript 数组也是一组有序的数据，但跟其他语言不同的是，数组中每个槽位可以存储任意类型的数据。这意味着可以创建一个数组，它的第一个元素是字符串，第二个元素是数值，第三个是对象。ECMAScript 数组也是动态大小的，会随着数据添加而自动增长。

### 6.2.1. 创建数组

有几种基本的方式可以创建数组。一种是使用 Array 构造函数，比如：

```js
let colors = new Array();
```

如果知道数组中元素的数量，那么可以给构造函数传入一个数值，然后 length 属性就会被自动创建并设置为这个值。比如，下面的代码会创建一个初始 length 为 20 的数组：

```js
let colors = new Array(20);
```

也可以给 Array 构造函数传入要保存的元素。比如，下面的代码会创建一个包含 3 个字符串值的数组：

```js
let colors = new Array("red", "blue", "green");
```

创建数组时可以给构造函数传一个值。这时候就有点问题了，因为如果这个值是数值，则会创建一个长度为指定数值的数组；而如果这个值是其他类型的，则会创建一个只包含该特定值的数组。下面看一个例子：

```js
let colors = new Array(3); // 创建一个包含3 个元素的数组
let names = new Array("Greg"); // 创建一个只包含一个元素，即字符串"Greg"的数组
```

在使用 Array 构造函数时，也可以省略 new 操作符。结果是一样的，比如：

```js
let colors = Array(3); // 创建一个包含3 个元素的数组
let names = Array("Greg"); // 创建一个只包含一个元素，即字符串"Greg"的数组
```

另一种创建数组的方式是使用 **数组字面量(array literal)** 表示法。数组字面量是在中括号中包含以逗号分隔的元素列表，如下面的例子所示：

```js
let colors = ["red", "blue", "green"]; // 创建一个包含3 个元素的数组
let names = []; // 创建一个空数组
let values = [1, 2]; // 创建一个包含2 个元素的数组
```

在这个例子中，第一行创建一个包含 3 个字符串的数组。第二行用一对空中括号创建了一个空数组。第三行展示了在数组最后一个值后面加逗号的效果：values 是一个包含两个值（1 和 2）的数组。

注意 与对象一样，在使用数组字面量表示法创建数组不会调用 Array 构造函数。

Array 构造函数还有两个 ES6 新增的用于创建数组的静态方法：from()和 of()。from()用于将类数组结构转换为数组实例，而 of()用于将一组参数转换为数组实例。

Array.from()的第一个参数是一个类数组对象，即任何可迭代的结构，或者有一个 length 属性和可索引元素的结构。这种方式可用于很多场合：

```js
// 字符串会被拆分为单字符数组
console.log(Array.from("Matt")); // ["M", "a", "t", "t"]

// 可以使用from()将集合和映射转换为一个新数组
const m = new Map().set(1, 2).set(3, 4);
const s = new Set().add(1).add(2).add(3).add(4);

console.log(Array.from(m)); // [[1, 2], [3, 4]]
console.log(Array.from(s)); // [1, 2, 3, 4]

// Array.from()对现有数组执行浅复制
const a1 = [1, 2, 3, 4];
const a2 = Array.from(a1);

console.log(a1); // [1, 2, 3, 4]
console.log(a1 === a2); // false

// 可以使用任何可迭代对象
const iter = {
  *[Symbol.iterator]() {
    yield 1;
    yield 2;
    yield 3;
    yield 4;
  },
};
console.log(Array.from(iter)); // [1, 2, 3, 4]

// arguments 对象可以被轻松地转换为数组
function getArgsArray() {
  return Array.from(arguments);
}
console.log(getArgsArray(1, 2, 3, 4)); // [1, 2, 3, 4]

// from()也能转换带有必要属性的自定义对象
const arrayLikeObject = {
  0: 1,
  1: 2,
  2: 3,
  3: 4,
  length: 4,
};
console.log(Array.from(arrayLikeObject)); // [1, 2, 3, 4]
```

Array.from()还接收第二个可选的映射函数参数。这个函数可以直接增强新数组的值，而无须像调用 Array.from().map()那样先创建一个中间数组。还可以接收第三个可选参数，用于指定映射函数中 this 的值。但这个重写的 this 值在箭头函数中不适用。

```js
const a1 = [1, 2, 3, 4];
const a2 = Array.from(a1, (x) => x ** 2);
const a3 = Array.from(
  a1,
  function (x) {
    return x ** this.exponent;
  },
  { exponent: 2 }
);
console.log(a2); // [1, 4, 9, 16]
console.log(a3); // [1, 4, 9, 16]
```

Array.of()可以把一组参数转换为数组。这个方法用于替代在 ES6 之前常用的 Array.prototype.slice.call(arguments)，一种异常笨拙的将 arguments 对象转换为数组的写法：

```js
console.log(Array.of(1, 2, 3, 4)); // [1, 2, 3, 4]
console.log(Array.of(undefined)); // [undefined]
```

### 6.2.2. 数组空位

使用数组字面量初始化数组时，可以使用一串逗号来创建空位（hole）。ECMAScript 会将逗号之间相应索引位置的值当成空位，ES6 规范重新定义了该如何处理这些空位。

可以像下面这样创建一个空位数组：

```js
const options = [, , , , ,]; // 创建包含5 个元素的数组
console.log(options.length); // 5
console.log(options); // [,,,,,]
```

ES6 新增的方法和迭代器与早期 ECMAScript 版本中存在的方法行为不同。ES6 新增方法普遍将这些空位当成存在的元素，只不过值为 undefined：

```js
const options = [1, , , , 5];
for (const option of options) {
  console.log(option === undefined);
}
// false
// true
// true
// true
// false

const a = Array.from([, , ,]); // 使用ES6 的Array.from()创建的包含3 个空位的数组
for (const val of a) {
  console.log(val === undefined);
}
// true
// true
// true
console.log(Array.of(...[, , ,])); // [undefined, undefined, undefined]
for (const [index, value] of options.entries()) {
  console.log(value);
}
// 1
// undefined
// undefined
// undefined
// 5
```

ES6 之前的方法则会忽略这个空位，但具体的行为也会因方法而异：

```js
const options = [1, , , , 5];
// map()会跳过空位置
console.log(options.map(() => 6)); // [6, undefined, undefined, undefined, 6]
// join()视空位置为空字符串
console.log(options.join("-")); // "1----5"
```

注意 由于行为不一致和存在性能隐患，因此实践中要避免使用数组空位。如果确实需要空位，则可以显式地用 undefined 值代替。

### 6.2.3. 数组索引

要取得或设置数组的值，需要使用中括号并提供相应值的数字索引，如下所示：

```js
let colors = ["red", "blue", "green"]; // 定义一个字符串数组
console.log(colors[0]); // 显示第一项
colors[2] = "black"; // 修改第三项
colors[3] = "brown"; // 添加第四项
```

在中括号中提供的索引表示要访问的值。如果索引小于数组包含的元素数，则返回存储在相应位置的元素，就像示例中 colors[0]显示"red"一样。设置数组的值方法也是一样的，就是替换指定位置的值。如果把一个值设置给超过数组最大索引的索引，就像示例中的 colors[3]，则数组长度会自动扩展到该索引值加 1（示例中设置的索引 3，所以数组长度变成了 4）。

数组中元素的数量保存在 length 属性中，这个属性始终返回 0 或大于 0 的值，如下例所示：

```js
let colors = ["red", "blue", "green"]; // 创建一个包含3 个字符串的数组
let names = []; // 创建一个空数组
console.log(colors.length); // 3
console.log(names.length); // 0
```

数组 length 属性的独特之处在于，它不是只读的。通过修改 length 属性，可以从数组末尾删除或添加元素。来看下面的例子：

```js
let colors = ["red", "blue", "green"]; // 创建一个包含3 个字符串的数组
colors.length = 2;
console.log(colors[2]); // undefined
```

这里，数组 colors 一开始有 3 个值。将 length 设置为 2，就删除了最后一个（位置 2 的）值，因此 colors[2]就没有值了。如果将 length 设置为大于数组元素数的值，则新添加的元素都将以 undefined 填充，如下例所示：

```js
let colors = ["red", "blue", "green"]; // 创建一个包含3 个字符串的数组
colors.length = 4;
console.log(colors[3]); // undefined
```

这里将数组 colors 的 length 设置为 4，虽然数组只包含 3 个元素。位置 3 在数组中不存在，因此访问其值会返回特殊值 undefined。

使用 length 属性可以方便地向数组末尾添加元素，如下例所示：

```js
let colors = ["red", "blue", "green"]; // 创建一个包含3 个字符串的数组
colors[colors.length] = "black"; // 添加一种颜色（位置3）
colors[colors.length] = "brown"; // 再添加一种颜色（位置4）
```

数组中最后一个元素的索引始终是 length - 1，因此下一个新增槽位的索引就是 length。每次在数组最后一个元素后面新增一项，数组的 length 属性都会自动更新，以反映变化。这意味着第二行的 colors[colors.length]会在位置 3 添加一个新元素，下一行则会在位置 4 添加一个新元素。新的长度会在新增元素被添加到当前数组外部的位置上时自动更新。换句话说，就是 length 属性会更新为位置加上 1，如下例所示：

```js
let colors = ["red", "blue", "green"]; // 创建一个包含3 个字符串的数组
colors[99] = "black"; // 添加一种颜色（位置99）
console.log(colors.length); // 100
```

这里，colors 数组有一个值被插入到位置 99，结果新 length 就变成了 100（99 + 1）。这中间的所有元素，即位置 3~98，实际上并不存在，因此在访问时会返回 undefined。

注意 数组最多可以包含 4 294 967 295 个元素，这对于大多数编程任务应该足够了。如果尝试添加更多项，则会导致抛出错误。以这个最大值作为初始值创建数组，可能导致脚本运行时间过长的错误。

### 6.2.4. 检测数组

一个经典的 ECMAScript 问题是判断一个对象是不是数组。在只有一个网页（因而只有一个全局作用域）的情况下，使用 instanceof 操作符就足矣：

```js
if (value instanceof Array) {
  // 操作数组
}
```

使用 instanceof 的问题是假定只有一个全局执行上下文。如果网页里有多个框架，则可能涉及两个不同的全局执行上下文，因此就会有两个不同版本的 Array 构造函数。如果要把数组从一个框架传给另一个框架，则这个数组的构造函数将有别于在第二个框架内本地创建的数组。

为解决这个问题，ECMAScript 提供了 Array.isArray()方法。这个方法的目的就是确定一个值是否为数组，而不用管它是在哪个全局执行上下文中创建的。来看下面的例子：

```js
if (Array.isArray(value)) {
  // 操作数组
}
```

### 6.2.5. 迭代器方法

在 ES6 中，Array 的原型上暴露了 3 个用于检索数组内容的方法：keys()、values()和 entries()。keys()返回数组索引的迭代器，values()返回数组元素的迭代器，而 entries()返回索引/值对的迭代器：

```js
const a = ["foo", "bar", "baz", "qux"];
// 因为这些方法都返回迭代器，所以可以将它们的内容通过Array.from()直接转换为数组实例
const aKeys = Array.from(a.keys());
const aValues = Array.from(a.values());
const aEntries = Array.from(a.entries());
console.log(aKeys); // [0, 1, 2, 3]
console.log(aValues); // ["foo", "bar", "baz", "qux"]
console.log(aEntries); // [[0, "foo"], [1, "bar"], [2, "baz"], [3, "qux"]]
```

使用 ES6 的解构可以非常容易地在循环中拆分键/值对：

```js
const a = ["foo", "bar", "baz", "qux"];
for (const [idx, element] of a.entries()) {
  console.log(idx);
  console.log(element);
}
// 0
// foo
// 1
// bar
// 2
// baz
// 3
// qux
```

注意 虽然这些方法是 ES6 规范定义的，但在 2017 年底的时候仍有浏览器没有实现它们。

### 6.2.6. 复制和填充方法

ES6 新增了两个方法：批量复制方法 copyWithin()，以及填充数组方法 fill()。这两个方法的函数签名类似，都需要指定既有数组实例上的一个范围，包含开始索引，不包含结束索引。使用这个方法不会改变数组的大小。

使用 fill()方法可以向一个已有的数组中插入全部或部分相同的值。开始索引用于指定开始填充的位置，它是可选的。如果不提供结束索引，则一直填充到数组末尾。负值索引从数组末尾开始计算。也可以将负索引想象成数组长度加上它得到的一个正索引：

```js
const zeroes = [0, 0, 0, 0, 0];
// 用5 填充整个数组
zeroes.fill(5);
console.log(zeroes); // [5, 5, 5, 5, 5]
zeroes.fill(0); // 重置
// 用6 填充索引大于等于3 的元素
zeroes.fill(6, 3);
console.log(zeroes); // [0, 0, 0, 6, 6]
zeroes.fill(0); // 重置
// 用7 填充索引大于等于1 且小于3 的元素
zeroes.fill(7, 1, 3);
console.log(zeroes); // [0, 7, 7, 0, 0];
zeroes.fill(0); // 重置
// 用8 填充索引大于等于1 且小于4 的元素
// (-4 + zeroes.length = 1)
// (-1 + zeroes.length = 4)
zeroes.fill(8, -4, -1);
console.log(zeroes); // [0, 8, 8, 8, 0];
```

fill()静默忽略超出数组边界、零长度及方向相反的索引范围：

```js
const zeroes = [0, 0, 0, 0, 0];
// 索引过低，忽略
zeroes.fill(1, -10, -6);
console.log(zeroes); // [0, 0, 0, 0, 0]
// 索引过高，忽略
zeroes.fill(1, 10, 15);
console.log(zeroes); // [0, 0, 0, 0, 0]
// 索引反向，忽略
zeroes.fill(2, 4, 2);
console.log(zeroes); // [0, 0, 0, 0, 0]
// 索引部分可用，填充可用部分
zeroes.fill(4, 3, 10);
console.log(zeroes); // [0, 0, 0, 4, 4]
```

与 fill()不同，copyWithin()会按照指定范围浅复制数组中的部分内容，然后将它们插入到指定索引开始的位置。开始索引和结束索引则与 fill()使用同样的计算方法：

```js
let ints,
reset = () => ints = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];
reset();
// 从ints 中复制索引0 开始的内容，插入到索引5 开始的位置
// 在源索引或目标索引到达数组边界时停止
ints.copyWithin(5);
console.log(ints); // [0, 1, 2, 3, 4, 0, 1, 2, 3, 4]
reset();
// 从ints 中复制索引5 开始的内容，插入到索引0 开始的位置
ints.copyWithin(0, 5);
console.log(ints); // [5, 6, 7, 8, 9, 5, 6, 7, 8, 9]
reset();
// 从ints 中复制索引0 开始到索引3 结束的内容
// 插入到索引4 开始的位置
ints.copyWithin(4, 0, 3);
console.log(ints); // [0, 1, 2, 3, 0, 1, 2, 7, 8, 9]
reset();
// JavaScript 引擎在插值前会完整复制范围内的值
// 因此复制期间不存在重写的风险
ints.copyWithin(2, 0, 6);
console.log(ints); // [0, 1, 0, 1, 2, 3, 4, 5, 8, 9]
reset();
// 支持负索引值，与fill()相对于数组末尾计算正向索引的过程是一样的
ints.copyWithin(-4, -7, -3);
console.log(ints); // [0, 1, 2, 3, 4, 5, 3, 4, 5, 6]
copyWithin()静默忽略超出数组边界、零长度及方向相反的索引范围：
let ints,
reset = () => ints = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];
reset();
// 索引过低，忽略
ints.copyWithin(1, -15, -12);
console.log(ints); // [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];
reset()
// 索引过高，忽略
ints.copyWithin(1, 12, 15);
console.log(ints); // [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];
reset();
// 索引反向，忽略
ints.copyWithin(2, 4, 2);
console.log(ints); // [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];
reset();
// 索引部分可用，复制、填充可用部分
ints.copyWithin(4, 7, 10)
console.log(ints); // [0, 1, 2, 3, 7, 8, 9, 7, 8, 9];
```

### 6.2.7. 转换方法

前面提到过，所有对象都有 toLocaleString()、toString()和 valueOf()方法。其中，valueOf()返回的还是数组本身。而 toString()返回由数组中每个值的等效字符串拼接而成的一个逗号分隔的字符串。也就是说，对数组的每个值都会调用其 toString()方法，以得到最终的字符串。来看下面的例子：

```js
let colors = ["red", "blue", "green"]; // 创建一个包含3 个字符串的数组
console.log(colors.toString()); // red,blue,green
console.log(colors.valueOf()); // red,blue,green
```

显式调用的 toString()和 valueOf()方法，它们分别返回了数组的字符串表示，即将所有字符串组合起来，以逗号分隔。

toLocaleString()方法也可能返回跟 toString()和 valueOf()相同的结果，但也不一定。在调用数组的 toLocaleString()方法时，会得到一个逗号分隔的数组值的字符串。它与另外两个方法唯一的区别是，为了得到最终的字符串，会调用数组每个值的 toLocaleString()方法，而不是 toString()方法。看下面的例子：

```js
let person1 = {
  toLocaleString() {
    return "Nikolaos";
  },
  toString() {
    return "Nicholas";
  },
};
let person2 = {
  toLocaleString() {
    return "Grigorios";
  },
  toString() {
    return "Greg";
  },
};
let people = [person1, person2];
console.log(people); // Nicholas,Greg
console.log(people.toString()); // Nicholas,Greg
console.log(people.toLocaleString()); // Nikolaos,Grigorios
```

这里定义了两个对象 person1 和 person2，它们都定义了 toString()和 toLocaleString()方法，而且返回不同的值。然后又创建了一个包含这两个对象的数组 people。在将数组传给 console.log()时，输出的是"Nicholas,Greg"，这是因为会在数组每一项上调用 toString()方法（与下一行显式调用 toString()方法结果一样）。而在调用数组的 toLocaleString()方法时，结果变成了"Nikolaos,Grigorios"，这是因为调用了数组每一项的 toLocaleString()方法。

继承的方法 toLocaleString()以及 toString()都返回数组值的逗号分隔的字符串。如果想使用不同的分隔符，则可以使用 join()方法。join()方法接收一个参数，即字符串分隔符，返回包含所有项的字符串。来看下面的例子：

```js
let colors = ["red", "green", "blue"];
console.log(colors.join(",")); // red,green,blue
console.log(colors.join("||")); // red||green||blue
```

这里在 colors 数组上调用了 join()方法，得到了与调用 toString()方法相同的结果。传入逗号， 结果就是逗号分隔的字符串。最后一行给 join() 传入了双竖线， 得到了字符串"red||green||blue"。如果不给 join()传入任何参数，或者传入 undefined，则仍然使用逗号作为分隔符。

注意 如果数组中某一项是 null 或 undefined，则在 join()、toLocaleString()、toString()和 valueOf()返回的结果中会以空字符串表示。

### 6.2.8. 栈方法

ECMAScript 给数组提供几个方法，让它看起来像是另外一种数据结构。数组对象可以像栈一样，也就是一种限制插入和删除项的数据结构。栈是一种后进先出（LIFO，Last-In-First-Out）的结构，也就是最近添加的项先被删除。数据项的插入（称为 **推入，push**）和删除（称为 **弹出，pop**）只在栈的一个地方发生，即栈顶。ECMAScript 数组提供了 push()和 pop()方法，以实现类似栈的行为。

push()方法接收任意数量的参数，并将它们添加到数组末尾，返回数组的最新长度。pop()方法则用于删除数组的最后一项，同时减少数组的 length 值，返回被删除的项。来看下面的例子：

```js
let colors = new Array(); // 创建一个数组
let count = colors.push("red", "green"); // 推入两项
console.log(count); // 2
count = colors.push("black"); // 再推入一项
console.log(count); // 3
let item = colors.pop(); // 取得最后一项
console.log(item); // black
console.log(colors.length); // 2
```

这里创建了一个当作栈来使用的数组（注意不需要任何额外的代码，push()和 pop()都是数组的默认方法）。首先，使用 push()方法把两个字符串推入数组末尾，将结果保存在变量 count 中（结果为 2）。

然后，再推入另一个值，再把结果保存在 count 中。因为现在数组中有 3 个元素，所以 push()返回 3。在调用 pop()时，会返回数组的最后一项，即字符串"black"。此时数组还有两个元素。

栈方法可以与数组的其他任何方法一起使用，如下例所示：

```js
let colors = ["red", "blue"];
colors.push("brown"); // 再添加一项
colors[3] = "black"; // 添加一项
console.log(colors.length); // 4
let item = colors.pop(); // 取得最后一项
console.log(item); // black
```

这里先初始化了包含两个字符串的数组，然后通过 push()添加了第三个值，第四个值是通过直接在位置 3 上赋值添加的。调用 pop()时，返回了字符串"black"，也就是最后添加到数组的字符串。

### 6.2.9. 队列方法

就像栈是以 LIFO 形式限制访问的数据结构一样，队列以先进先出（FIFO，First-In-First-Out）形式限制访问。队列在列表末尾添加数据，但从列表开头获取数据。因为有了在数据末尾添加数据的 push()方法，所以要模拟队列就差一个从数组开头取得数据的方法了。这个数组方法叫 shift()，它会删除数组的第一项并返回它，然后数组长度减 1。使用 shift()和 push()，可以把数组当成队列来使用：

```js
let colors = new Array(); // 创建一个数组
let count = colors.push("red", "green"); // 推入两项
console.log(count); // 2
count = colors.push("black"); // 再推入一项
console.log(count); // 3
let item = colors.shift(); // 取得第一项
console.log(item); // red
console.log(colors.length); // 2
```

这个例子创建了一个数组并用 push()方法推入三个值。加粗的那行代码使用 shift()方法取得了数组的第一项，即"red"。删除这一项之后，"green"成为第一个元素，"black"成为第二个元素，数组此时就包含两项。

ECMAScript 也为数组提供了 unshift()方法。顾名思义，unshift()就是执行跟 shift()相反的操作：在数组开头添加任意多个值，然后返回新的数组长度。通过使用 unshift()和 pop()，可以在相反方向上模拟队列，即在数组开头添加新数据，在数组末尾取得数据，如下例所示：

```js
let colors = new Array(); // 创建一个数组
let count = colors.unshift("red", "green"); // 从数组开头推入两项
console.log(count); // 2
count = colors.unshift("black"); // 再推入一项
console.log(count); // 3
let item = colors.pop(); // 取得最后一项
console.log(item); // green
console.log(colors.length); // 2
```

这里，先创建一个数组，再通过 unshift()填充数组。首先，给数组添加"red"和"green"，再添加"black"，得到["black","red","green"]。调用 pop()时，删除最后一项"green"并返回它。

### 6.2.10. 排序方法

数组有两个方法可以用来对元素重新排序：reverse()和 sort()。顾名思义，reverse()方法就是将数组元素反向排列。比如：

```js
let values = [1, 2, 3, 4, 5];
values.reverse();
console.log(values); // 5,4,3,2,1
```

这里，数组 values 的初始状态为[1,2,3,4,5]。通过调用 reverse()反向排序，得到了[5,4,3,2,1]。这个方法很直观，但不够灵活，所以才有了 sort()方法。

默认情况下，sort()会按照升序重新排列数组元素，即最小的值在前面，最大的值在后面。为此，sort()会在每一项上调用 String()转型函数，然后比较字符串来决定顺序。即使数组的元素都是数值，也会先把数组转换为字符串再比较、排序。比如：

```js
let values = [0, 1, 5, 10, 15];
values.sort();
console.log(values); // 0,1,10,15,5
```

一开始数组中数值的顺序是正确的，但调用 sort()会按照这些数值的字符串形式重新排序。因此，即使 5 小于 10，但字符串"10"在字符串"5"的前头，所以 10 还是会排到 5 前面。很明显，这在多数情况下都不是最合适的。为此，sort()方法可以接收一个 **比较函数**，用于判断哪个值应该排在前面。

比较函数接收两个参数，如果第一个参数应该排在第二个参数前面，就返回负值；如果两个参数相等，就返回 0；如果第一个参数应该排在第二个参数后面，就返回正值。下面是使用简单比较函数的一个例子：

```js
function compare(value1, value2) {
  if (value1 < value2) {
    return -1;
  } else if (value1 > value2) {
    return 1;
  } else {
    return 0;
  }
}
```

这个比较函数可以适用于大多数数据类型，可以把它当作参数传给 sort()方法，如下所示：

```js
let values = [0, 1, 5, 10, 15];
values.sort(compare);
console.log(values); // 0,1,5,10,15
```

在给 sort()方法传入比较函数后，数组中的数值在排序后保持了正确的顺序。当然，比较函数也可以产生降序效果，只要把返回值交换一下即可：

```js
function compare(value1, value2) {
  if (value1 < value2) {
    return 1;
  } else if (value1 > value2) {
    return -1;
  } else {
    return 0;
  }
}
let values = [0, 1, 5, 10, 15];
values.sort(compare);
console.log(values); // 15,10,5,1,0
```

此外，这个比较函数还可简写为一个箭头函数：

```js
let values = [0, 1, 5, 10, 15];
values.sort((a, b) => (a < b ? 1 : a > b ? -1 : 0));
console.log(values); // 15,10,5,1,0
```

在这个修改版函数中，如果第一个值应该排在第二个值后面则返回 1，如果第一个值应该排在第二个值前面则返回-1。交换这两个返回值之后，较大的值就会排在前头，数组就会按照降序排序。当然，如果只是想反转数组的顺序，reverse()更简单也更快。

注意 reverse()和 sort()都返回调用它们的数组的引用。

如果数组的元素是数值，或者是其 valueOf()方法返回数值的对象（如 Date 对象），这个比较函数还可以写得更简单，因为这时可以直接用第二个值减去第一个值：

```js
function compare(value1, value2) {
  return value2 - value1;
}
```

比较函数就是要返回小于 0、0 和大于 0 的数值，因此减法操作完全可以满足要求。

### 6.2.11. 操作方法

对于数组中的元素，我们有很多操作方法。比如，concat()方法可以在现有数组全部元素基础上创建一个新数组。它首先会创建一个当前数组的副本，然后再把它的参数添加到副本末尾，最后返回这个新构建的数组。如果传入一个或多个数组，则 concat()会把这些数组的每一项都添加到结果数组。如果参数不是数组，则直接把它们添加到结果数组末尾。来看下面的例子：

```js
let colors = ["red", "green", "blue"];
let colors2 = colors.concat("yellow", ["black", "brown"]);
console.log(colors); // ["red", "green","blue"]
console.log(colors2); // ["red", "green", "blue", "yellow", "black", "brown"]
```

这里先创建一个包含 3 个值的数组 colors。然后 colors 调用 concat()方法，传入字符串"yellow"和一个包含"black"和"brown"的数组。保存在 colors2 中的结果就是["red", "green", "blue","yellow", "black", "brown"]。原始数组 colors 保持不变。

打平数组参数的行为可以重写，方法是在参数数组上指定一个特殊的符号：Symbol.isConcat-Spreadable。这个符号能够阻止 concat()打平参数数组。相反，把这个值设置为 true 可以强制打平类数组对象：

```js
let colors = ["red", "green", "blue"];
let newColors = ["black", "brown"];
let moreNewColors = {
  [Symbol.isConcatSpreadable]: true,
  length: 2,
  0: "pink",
  1: "cyan",
};
newColors[Symbol.isConcatSpreadable] = false;
// 强制不打平数组
let colors2 = colors.concat("yellow", newColors);
// 强制打平类数组对象
let colors3 = colors.concat(moreNewColors);
console.log(colors); // ["red", "green", "blue"]
console.log(colors2); // ["red", "green", "blue", "yellow", ["black", "brown"]]
console.log(colors3); // ["red", "green", "blue", "pink", "cyan"]
```

接下来，方法 slice()用于创建一个包含原有数组中一个或多个元素的新数组。slice()方法可以接收一个或两个参数：返回元素的开始索引和结束索引。如果只有一个参数，则 slice()会返回该索引到数组末尾的所有元素。如果有两个参数，则 slice()返回从开始索引到结束索引对应的所有元素，其中不包含结束索引对应的元素。记住，这个操作不影响原始数组。来看下面的例子：

```js
let colors = ["red", "green", "blue", "yellow", "purple"];
let colors2 = colors.slice(1);
let colors3 = colors.slice(1, 4);
console.log(colors2); // green,blue,yellow,purple
console.log(colors3); // green,blue,yellow
```

这里，colors 数组一开始有 5 个元素。调用 slice()传入 1 会得到包含 4 个元素的新数组。其中不包括"red"，这是因为拆分操作要从位置 1 开始，即从"green"开始。得到的 colors2 数组包含"green"、"blue"、"yellow"和"purple"。colors3 数组是通过调用 slice()并传入 1 和 4 得到的，即从位置 1 开始复制到位置 3。因此 colors3 包含"green"、"blue"和"yellow"。

或许最强大的数组方法就属 splice()了，使用它的方式可以有很多种。splice()的主要目的是在数组中间插入元素，但有 3 种不同的方式使用这个方法。

- 删除。需要给 splice()传 2 个参数：要删除的第一个元素的位置和要删除的元素数量。可以从数组中删除任意多个元素，比如 splice(0, 2)会删除前两个元素。
- 插入。需要给 splice()传 3 个参数：开始位置、0（要删除的元素数量）和要插入的元素，可以在数组中指定的位置插入元素。第三个参数之后还可以传第四个、第五个参数，乃至任意多个要插入的元素。比如，splice(2, 0, "red", "green")会从数组位置 2 开始插入字符串"red"和"green"。
- 替换。splice()在删除元素的同时可以在指定位置插入新元素，同样要传入 3 个参数：开始位置、要删除元素的数量和要插入的任意多个元素。要插入的元素数量不一定跟删除的元素数量一致。比如，splice(2, 1, "red", "green")会在位置 2 删除一个元素，然后从该位置开始向数组中插入"red"和"green"。

splice()方法始终返回这样一个数组，它包含从数组中被删除的元素（如果没有删除元素，则返回空数组）。以下示例展示了上述 3 种使用方式。

```js
let colors = ["red", "green", "blue"];
let removed = colors.splice(0, 1); // 删除第一项
console.log(colors); // green,blue
console.log(removed); // red，只有一个元素的数组
removed = colors.splice(1, 0, "yellow", "orange"); // 在位置1 插入两个元素
console.log(colors); // green,yellow,orange,blue
console.log(removed); // 空数组
removed = colors.splice(1, 1, "red", "purple"); // 插入两个值，删除一个元素
console.log(colors); // green,red,purple,orange,blue
console.log(removed); // yellow，只有一个元素的数组
```

这个例子中，colors 数组一开始包含 3 个元素。第一次调用 splice()时，只删除了第一项，colors 中还有"green"和"blue"。第二次调用 slice()时，在位置 1 插入两项，然后 colors 包含"green"、"yellow"、"orange"和"blue"。这次没删除任何项，因此返回空数组。最后一次调用 splice()时删除了位置 1 上的一项，同时又插入了"red"和"purple"。最后，colors 数组包含"green"、"red"、"purple"、"orange"和"blue"。

### 6.2.12. 搜索和位置方法

ECMAScript 提供两类搜索数组的方法：按严格相等搜索和按断言函数搜索。

1. **严格相等**

ECMAScript 提供了 3 个严格相等的搜索方法：indexOf()、lastIndexOf()和 includes()。其中，前两个方法在所有版本中都可用，而第三个方法是 ECMAScript 7 新增的。这些方法都接收两个参数：要查找的元素和一个可选的起始搜索位置。indexOf()和 includes()方法从数组前头（第一项）开始向后搜索，而 lastIndexOf()从数组末尾（最后一项）开始向前搜索。

indexOf()和 lastIndexOf()都返回要查找的元素在数组中的位置，如果没找到则返回-1。includes()返回布尔值，表示是否至少找到一个与指定元素匹配的项。在比较第一个参数跟数组每一项时，会使用全等（===）比较，也就是说两项必须严格相等。下面来看一些例子：

```js
let numbers = [1, 2, 3, 4, 5, 4, 3, 2, 1];
console.log(numbers.indexOf(4)); // 3
console.log(numbers.lastIndexOf(4)); // 5
console.log(numbers.includes(4)); // true
console.log(numbers.indexOf(4, 4)); // 5
console.log(numbers.lastIndexOf(4, 4)); // 3
console.log(numbers.includes(4, 7)); // false
let person = { name: "Nicholas" };
let people = [{ name: "Nicholas" }];
let morePeople = [person];
console.log(people.indexOf(person)); // -1
console.log(morePeople.indexOf(person)); // 0
console.log(people.includes(person)); // false
console.log(morePeople.includes(person)); // true
```

2. **断言函数**

ECMAScript 也允许按照定义的断言函数搜索数组，每个索引都会调用这个函数。断言函数的返回值决定了相应索引的元素是否被认为匹配。

断言函数接收 3 个参数：元素、索引和数组本身。其中元素是数组中当前搜索的元素，索引是当前元素的索引，而数组就是正在搜索的数组。断言函数返回布尔值，表示是否匹配。

find()和 findIndex()方法使用了断言函数。这两个方法都从数组的最小索引开始。find()返回第一个匹配的元素，findIndex()返回第一个匹配元素的索引。这两个方法也都接收第二个可选的参数，用于指定断言函数内部 this 的值。

```js
const people = [
  {
    name: "Matt",
    age: 27,
  },
  {
    name: "Nicholas",
    age: 29,
  },
];
console.log(people.find((element, index, array) => element.age < 28));
// {name: "Matt", age: 27}
console.log(people.findIndex((element, index, array) => element.age < 28));
// 0
```

找到匹配项后，这两个方法都不再继续搜索。

```js
const evens = [2, 4, 6];
// 找到匹配后，永远不会检查数组的最后一个元素
evens.find((element, index, array) => {
  console.log(element);
  console.log(index);
  console.log(array);
  return element === 4;
});
// 2
// 0
// [2, 4, 6]
// 4
// 1
// [2, 4, 6]
```

### 6.2.13. 迭代方法

ECMAScript 为数组定义了 5 个迭代方法。每个方法接收两个参数：以每一项为参数运行的函数，以及可选的作为函数运行上下文的作用域对象（影响函数中 this 的值）。传给每个方法的函数接收 3 个参数：数组元素、元素索引和数组本身。因具体方法而异，这个函数的执行结果可能会也可能不会影响方法的返回值。数组的 5 个迭代方法如下。

- every()：对数组每一项都运行传入的函数，如果对每一项函数都返回 true，则这个方法返回 true。
- filter()：对数组每一项都运行传入的函数，函数返回 true 的项会组成数组之后返回。
- forEach()：对数组每一项都运行传入的函数，没有返回值。
- map()：对数组每一项都运行传入的函数，返回由每次函数调用的结果构成的数组。
- some()：对数组每一项都运行传入的函数，如果有一项函数返回 true，则这个方法返回 true。

这些方法都不改变调用它们的数组。

在这些方法中，every()和 some()是最相似的，都是从数组中搜索符合某个条件的元素。对 every()来说，传入的函数必须对每一项都返回 true，它才会返回 true；否则，它就返回 false。而对 some()来说，只要有一项让传入的函数返回 true，它就会返回 true。下面是一个例子：

```js
let numbers = [1, 2, 3, 4, 5, 4, 3, 2, 1];
let everyResult = numbers.every((item, index, array) => item > 2);
console.log(everyResult); // false
let someResult = numbers.some((item, index, array) => item > 2);
console.log(someResult); // true
```

以上代码调用了 every()和 some()，传入的函数都是在给定项大于 2 时返回 true。every()返回 false 是因为并不是每一项都能达到要求。而 some()返回 true 是因为至少有一项满足条件。

下面再看一看 filter()方法。这个方法基于给定的函数来决定某一项是否应该包含在它返回的数组中。比如，要返回一个所有数值都大于 2 的数组，可以使用如下代码：

```js
let numbers = [1, 2, 3, 4, 5, 4, 3, 2, 1];
let filterResult = numbers.filter((item, index, array) => item > 2);
console.log(filterResult); // 3,4,5,4,3
```

这里，调用 filter()返回的数组包含 3、4、5、4、3，因为只有对这些项传入的函数才返回 true。这个方法非常适合从数组中筛选满足给定条件的元素。

接下来 map()方法也会返回一个数组。这个数组的每一项都是对原始数组中同样位置的元素运行传入函数而返回的结果。例如，可以将一个数组中的每一项都乘以 2，并返回包含所有结果的数组，如下所示：

```js
let numbers = [1, 2, 3, 4, 5, 4, 3, 2, 1];
let mapResult = numbers.map((item, index, array) => item * 2);
console.log(mapResult); // 2,4,6,8,10,8,6,4,2
```

以上代码返回了一个数组，包含原始数组中每个值乘以 2 的结果。这个方法非常适合创建一个与原始数组元素一一对应的新数组。

最后，再来看一看 forEach()方法。这个方法只会对每一项运行传入的函数，没有返回值。本质上，forEach()方法相当于使用 for 循环遍历数组。比如：

```js
let numbers = [1, 2, 3, 4, 5, 4, 3, 2, 1];
numbers.forEach((item, index, array) => {
  // 执行某些操作
});
```

数组的这些迭代方法通过执行不同操作方便了对数组的处理。

### 6.2.14. 归并方法

ECMAScript 为数组提供了两个归并方法：reduce()和 reduceRight()。这两个方法都会迭代数组的所有项，并在此基础上构建一个最终返回值。reduce()方法从数组第一项开始遍历到最后一项。而 reduceRight()从最后一项开始遍历至第一项。

这两个方法都接收两个参数：对每一项都会运行的归并函数，以及可选的以之为归并起点的初始值。传给 reduce()和 reduceRight()的函数接收 4 个参数：上一个归并值、当前项、当前项的索引和数组本身。这个函数返回的任何值都会作为下一次调用同一个函数的第一个参数。如果没有给这两个方法传入可选的第二个参数（作为归并起点值），则第一次迭代将从数组的第二项开始，因此传给归并函数的第一个参数是数组的第一项，第二个参数是数组的第二项。

可以使用 reduce()函数执行累加数组中所有数值的操作，比如：

```js
let values = [1, 2, 3, 4, 5];
let sum = values.reduce((prev, cur, index, array) => prev + cur);
console.log(sum); // 15
```

第一次执行归并函数时，prev 是 1，cur 是 2。第二次执行时，prev 是 3（1 + 2），cur 是 3（数组第三项）。如此递进，直到把所有项都遍历一次，最后返回归并结果。

reduceRight()方法与之类似，只是方向相反。来看下面的例子：

```js
let values = [1, 2, 3, 4, 5];
let sum = values.reduceRight(function (prev, cur, index, array) {
  return prev + cur;
});
console.log(sum); // 15
```

在这里，第一次调用归并函数时 prev 是 5，而 cur 是 4。当然，最终结果相同，因为归并操作都是简单的加法。

究竟是使用 reduce()还是 reduceRight()，只取决于遍历数组元素的方向。除此之外，这两个方法没什么区别。

## 6.3. 定型数组

定型数组（typed array）是 ECMAScript 新增的结构，目的是提升向原生库传输数据的效率。实际上，JavaScript 并没有“TypedArray”类型，它所指的其实是一种特殊的包含数值类型的数组。为理解如何使用定型数组，有必要先了解一下它的用途。

### 6.3.1. 历史

随着浏览器的流行，不难想象人们会满怀期待地通过它来运行复杂的 3D 应用程序。早在 2006 年，Mozilla、Opera 等浏览器提供商就实验性地在浏览器中增加了用于渲染复杂图形应用程序的编程平台，无须安装任何插件。其目标是开发一套 JavaScript API，从而充分利用 3D 图形 API 和 GPU 加速，以便在`<canvas>`元素上渲染复杂的图形。

1. **WebGL**

最后的 JavaScript API 是基于 OpenGL ES（OpenGL for Embedded Systems）2.0 规范的。OpenGL ES 是 OpenGL 专注于 2D 和 3D 计算机图形的子集。这个新 API 被命名为 WebGL（Web Graphics Library），于 2011 年发布 1.0 版。有了它，开发者就能够编写涉及复杂图形的应用程序，它会被兼容 WebGL 的浏览器原生解释执行。

在 WebGL 的早期版本中，因为 JavaScript 数组与原生数组之间不匹配，所以出现了性能问题。图形驱动程序 API 通常不需要以 JavaScript 默认双精度浮点格式传递给它们的数值，而这恰恰是 JavaScript 数组在内存中的格式。因此，每次 WebGL 与 JavaScript 运行时之间传递数组时，WebGL 绑定都需要在目标环境分配新数组，以其当前格式迭代数组，然后将数值转型为新数组中的适当格式，而这些要花费很多时间。

2. **定型数组**

这当然是难以接受的，Mozilla 为解决这个问题而实现了 CanvasFloatArray。这是一个提供 JavaScript 接口的、C 语言风格的浮点值数组。JavaScript 运行时使用这个类型可以分配、读取和写入数组。这个数组可以直接传给底层图形驱动程序 API，也可以直接从底层获取到。最终，CanvasFloatArray 变成了 Float32Array，也就是今天定型数组中可用的第一个“类型”。

### 6.3.2. ArrayBuffer

Float32Array 实际上是一种“视图”，可以允许 JavaScript 运行时访问一块名为 ArrayBuffer 的预分配内存。ArrayBuffer 是所有定型数组及视图引用的基本单位。

注意 SharedArrayBuffer 是 ArrayBuffer 的一个变体，可以无须复制就在执行上下文间传递它。关于这种类型，请参考第 27 章。

ArrayBuffer()是一个普通的 JavaScript 构造函数，可用于在内存中分配特定数量的字节空间。

```js
const buf = new ArrayBuffer(16); // 在内存中分配16 字节
console.log(buf.byteLength); // 16
```

ArrayBuffer 一经创建就不能再调整大小。不过，可以使用 slice()复制其全部或部分到一个新实例中：

```js
const buf1 = new ArrayBuffer(16);
const buf2 = buf1.slice(4, 12);
console.log(buf2.byteLength); // 8
```

ArrayBuffer 某种程度上类似于 C++的 malloc()，但也有几个明显的区别。

- malloc()在分配失败时会返回一个 null 指针。ArrayBuffer 在分配失败时会抛出错误。
- malloc()可以利用虚拟内存，因此最大可分配尺寸只受可寻址系统内存限制。ArrayBuffer 分配的内存不能超过 Number.MAX_SAFE_INTEGER（2^53 - 1）字节。
- malloc()调用成功不会初始化实际的地址。声明 ArrayBuffer 则会将所有二进制位初始化为 0。
- 通过 malloc()分配的堆内存除非调用 free()或程序退出，否则系统不能再使用。而通过声明 ArrayBuffer 分配的堆内存可以被当成垃圾回收，不用手动释放。

不能仅通过对 ArrayBuffer 的引用就读取或写入其内容。要读取或写入 ArrayBuffer，就必须通过视图。视图有不同的类型，但引用的都是 ArrayBuffer 中存储的二进制数据。

### 6.3.3. DataView

第一种允许你读写 ArrayBuffer 的视图是 DataView。这个视图专为文件 I/O 和网络 I/O 设计，其 API 支持对缓冲数据的高度控制，但相比于其他类型的视图性能也差一些。DataView 对缓冲内容没有任何预设，也不能迭代。

必须在对已有的 ArrayBuffer 读取或写入时才能创建 DataView 实例。这个实例可以使用全部或部分 ArrayBuffer，且维护着对该缓冲实例的引用，以及视图在缓冲中开始的位置。

```js
const buf = new ArrayBuffer(16);
// DataView 默认使用整个ArrayBuffer
const fullDataView = new DataView(buf);
console.log(fullDataView.byteOffset); // 0
console.log(fullDataView.byteLength); // 16
console.log(fullDataView.buffer === buf); // true
// 构造函数接收一个可选的字节偏移量和字节长度
// byteOffset=0 表示视图从缓冲起点开始
// byteLength=8 限制视图为前8 个字节
const firstHalfDataView = new DataView(buf, 0, 8);
console.log(firstHalfDataView.byteOffset); // 0
console.log(firstHalfDataView.byteLength); // 8
console.log(firstHalfDataView.buffer === buf); // true
// 如果不指定，则DataView 会使用剩余的缓冲
// byteOffset=8 表示视图从缓冲的第9 个字节开始
// byteLength 未指定，默认为剩余缓冲
const secondHalfDataView = new DataView(buf, 8);
console.log(secondHalfDataView.byteOffset); // 8
console.log(secondHalfDataView.byteLength); // 8
console.log(secondHalfDataView.buffer === buf); // true
```

要通过 DataView 读取缓冲，还需要几个组件。

- 首先是要读或写的字节偏移量。可以看成 DataView 中的某种“地址”。
- DataView 应该使用 ElementType 来实现 JavaScript 的 Number 类型到缓冲内二进制格式的转换。
- 最后是内存中值的字节序。默认为大端字节序。

1. **ElementType**

DataView 对存储在缓冲内的数据类型没有预设。它暴露的 API 强制开发者在读、写时指定一个 ElementType，然后 DataView 就会忠实地为读、写而完成相应的转换。

| ElementType | 字 节 | 说 明           | 等价的 C 类型  | 值的范围                     |
| ----------- | ----- | --------------- | -------------- | ---------------------------- |
| Int8        | 1     | 8 位有符号整数  | signed char    | -128~127                     |
| Uint8       | 1     | 8 位无符号整数  | unsigned char  | 0~255                        |
| Int16       | 2     | 16 位有符号整数 | short          | -32 768~32 767               |
| Uint16      | 2     | 16 位无符号整数 | unsigned short | 0~65 535                     |
| Int32       | 4     | 32 位有符号整数 | int            | -2 147 483 648~2 147 483 647 |
| Uint32      | 4     | 32 位无符号整数 | unsigned int   | 0~4 294 967 295              |
| Float32     | 4     | 32 位 IEEE-754  | 浮点数 float   | -3.4e+38~+3.4e+38            |
| Float64     | 8     | 64 位 IEEE-754  | 浮点数 double  | -1.7e+308~+1.7e+308          |

DataView 为上表中的每种类型都暴露了 get 和 set 方法，这些方法使用 byteOffset（字节偏移量）定位要读取或写入值的位置。类型是可以互换使用的，如下例所示：

```js
// 在内存中分配两个字节并声明一个DataView
const buf = new ArrayBuffer(2);
const view = new DataView(buf);
// 说明整个缓冲确实所有二进制位都是0
// 检查第一个和第二个字符
console.log(view.getInt8(0)); // 0
console.log(view.getInt8(1)); // 0
// 检查整个缓冲
console.log(view.getInt16(0)); // 0
// 将整个缓冲都设置为1
// 255 的二进制表示是11111111（2^8 - 1）
view.setUint8(0, 255);
// DataView 会自动将数据转换为特定的ElementType
// 255 的十六进制表示是0xFF
view.setUint8(1, 0xff);
// 现在，缓冲里都是1 了
// 如果把它当成二补数的有符号整数，则应该是-1
console.log(view.getInt16(0)); // -1
```

2. **字节序**

前面例子中的缓冲有意回避了字节序的问题。“字节序”指的是计算系统维护的一种字节顺序的约定。DataView 只支持两种约定：大端字节序和小端字节序。大端字节序也称为“网络字节序”，意思是最高有效位保存在第一个字节，而最低有效位保存在最后一个字节。小端字节序正好相反，即最低有效位保存在第一个字节，最高有效位保存在最后一个字节。

JavaScript 运行时所在系统的原生字节序决定了如何读取或写入字节，但 DataView 并不遵守这个约定。对一段内存而言，DataView 是一个中立接口，它会遵循你指定的字节序。DataView 的所有 API 方法都以大端字节序作为默认值，但接收一个可选的布尔值参数，设置为 true 即可启用小端字节序。

```js
// 在内存中分配两个字节并声明一个DataView
const buf = new ArrayBuffer(2);
const view = new DataView(buf);
// 填充缓冲，让第一位和最后一位都是1
view.setUint8(0, 0x80); // 设置最左边的位等于1
view.setUint8(1, 0x01); // 设置最右边的位等于1
// 缓冲内容（为方便阅读，人为加了空格）
// 0x8 0x0 0x0 0x1
// 1000 0000 0000 0001
// 按大端字节序读取Uint16
// 0x80 是高字节，0x01 是低字节
// 0x8001 = 2^15 + 2^0 = 32768 + 1 = 32769
console.log(view.getUint16(0)); // 32769
// 按小端字节序读取Uint16
// 0x01 是高字节，0x80 是低字节
// 0x0180 = 2^8 + 2^7 = 256 + 128 = 384
console.log(view.getUint16(0, true)); // 384
// 按大端字节序写入Uint16
view.setUint16(0, 0x0004);
// 缓冲内容（为方便阅读，人为加了空格）
// 0x0 0x0 0x0 0x4
// 0000 0000 0000 0100
console.log(view.getUint8(0)); // 0
console.log(view.getUint8(1)); // 4
// 按小端字节序写入Uint16
view.setUint16(0, 0x0002, true);
// 缓冲内容（为方便阅读，人为加了空格）
// 0x0 0x2 0x0 0x0
// 0000 0010 0000 0000
console.log(view.getUint8(0)); // 2
console.log(view.getUint8(1)); // 0
```

3. **边界情形**

DataView 完成读、写操作的前提是必须有充足的缓冲区，否则就会抛出 RangeError：

```js
const buf = new ArrayBuffer(6);
const view = new DataView(buf);
// 尝试读取部分超出缓冲范围的值
view.getInt32(4);
// RangeError
// 尝试读取超出缓冲范围的值
view.getInt32(8);
// RangeError
// 尝试读取超出缓冲范围的值
view.getInt32(-1);
// RangeError
// 尝试写入超出缓冲范围的值
view.setInt32(4, 123);
// RangeError
```

DataView 在写入缓冲里会尽最大努力把一个值转换为适当的类型，后备为 0。如果无法转换，则抛出错误：

```js
const buf = new ArrayBuffer(1);
const view = new DataView(buf);
view.setInt8(0, 1.5);
console.log(view.getInt8(0)); // 1
view.setInt8(0, [4]);
console.log(view.getInt8(0)); // 4
view.setInt8(0, "f");
console.log(view.getInt8(0)); // 0
view.setInt8(0, Symbol());
// TypeError
```

### 6.3.4. 定型数组

定型数组是另一种形式的 ArrayBuffer 视图。虽然概念上与 DataView 接近，但定型数组的区别在于，它特定于一种 ElementType 且遵循系统原生的字节序。相应地，定型数组提供了适用面更广的 API 和更高的性能。设计定型数组的目的就是提高与 WebGL 等原生库交换二进制数据的效率。由于定型数组的二进制表示对操作系统而言是一种容易使用的格式，JavaScript 引擎可以重度优化算术运算、按位运算和其他对定型数组的常见操作，因此使用它们速度极快。

创建定型数组的方式包括读取已有的缓冲、使用自有缓冲、填充可迭代结构，以及填充基于任意类型的定型数组。另外，通过`<ElementType>.from()`和`<ElementType>.of()`也可以创建定型数组：

```js
// 创建一个12 字节的缓冲
const buf = new ArrayBuffer(12);
// 创建一个引用该缓冲的Int32Array
const ints = new Int32Array(buf);
// 这个定型数组知道自己的每个元素需要4 字节
// 因此长度为3
console.log(ints.length); // 3
// 创建一个长度为6 的Int32Array
const ints2 = new Int32Array(6);
// 每个数值使用4 字节，因此ArrayBuffer 是24 字节
console.log(ints2.length); // 6
// 类似DataView，定型数组也有一个指向关联缓冲的引用
console.log(ints2.buffer.byteLength); // 24
// 创建一个包含[2, 4, 6, 8]的Int32Array
const ints3 = new Int32Array([2, 4, 6, 8]);
console.log(ints3.length); // 4
console.log(ints3.buffer.byteLength); // 16
console.log(ints3[2]); // 6
// 通过复制ints3 的值创建一个Int16Array
const ints4 = new Int16Array(ints3);
// 这个新类型数组会分配自己的缓冲
// 对应索引的每个值会相应地转换为新格式
console.log(ints4.length); // 4
console.log(ints4.buffer.byteLength); // 8
console.log(ints4[2]); // 6
// 基于普通数组来创建一个Int16Array
const ints5 = Int16Array.from([3, 5, 7, 9]);
console.log(ints5.length); // 4
console.log(ints5.buffer.byteLength); // 8
console.log(ints5[2]); // 7
// 基于传入的参数创建一个Float32Array
const floats = Float32Array.of(3.14, 2.718, 1.618);
console.log(floats.length); // 3
console.log(floats.buffer.byteLength); // 12
console.log(floats[2]); // 1.6180000305175781
```

定型数组的构造函数和实例都有一个 BYTES_PER_ELEMENT 属性，返回该类型数组中每个元素的大小：

```js
console.log(Int16Array.BYTES_PER_ELEMENT); // 2
console.log(Int32Array.BYTES_PER_ELEMENT); // 4
const ints = new Int32Array(1),
  floats = new Float64Array(1);
console.log(ints.BYTES_PER_ELEMENT); // 4
console.log(floats.BYTES_PER_ELEMENT); // 8
```

如果定型数组没有用任何值初始化，则其关联的缓冲会以 0 填充：

```js
const ints = new Int32Array(4);
console.log(ints[0]); // 0
console.log(ints[1]); // 0
console.log(ints[2]); // 0
console.log(ints[3]); // 0
```

1. **定型数组行为**

从很多方面看，定型数组与普通数组都很相似。定型数组支持如下操作符、方法和属性：

- []
- copyWithin()
- entries()
- every()
- fill()
- filter()
- find()
- findIndex()
- forEach()
- indexOf()
- join()
- keys()
- lastIndexOf()
- length
- map()
- reduce()
- reduceRight()
- reverse()
- slice()
- some()
- sort()
- toLocaleString()
- toString()
- values()

其中，返回新数组的方法也会返回包含同样元素类型（element type）的新定型数组：

```js
const ints = new Int16Array([1, 2, 3]);
const doubleints = ints.map((x) => 2 * x);
console.log(doubleints instanceof Int16Array); // true
```

定型数组有一个 Symbol.iterator 符号属性，因此可以通过 for..of 循环和扩展操作符来操作：

```js
const ints = new Int16Array([1, 2, 3]);
for (const int of ints) {
  console.log(int);
}
// 1
// 2
// 3
console.log(Math.max(...ints)); // 3
```

2. **合并、复制和修改定型数组**

定型数组同样使用数组缓冲来存储数据，而数组缓冲无法调整大小。因此，下列方法不适用于定型数组：

- concat()
- pop()
- push()
- shift()
- splice()
- unshift()

不过，定型数组也提供了两个新方法，可以快速向外或向内复制数据：set()和 subarray()。

set()从提供的数组或定型数组中把值复制到当前定型数组中指定的索引位置：

```js
// 创建长度为8 的int16 数组
const container = new Int16Array(8);
// 把定型数组复制为前4 个值
// 偏移量默认为索引0
container.set(Int8Array.of(1, 2, 3, 4));
console.log(container); // [1,2,3,4,0,0,0,0]
// 把普通数组复制为后4 个值
// 偏移量4 表示从索引4 开始插入
container.set([5, 6, 7, 8], 4);
console.log(container); // [1,2,3,4,5,6,7,8]
// 溢出会抛出错误
container.set([5, 6, 7, 8], 7);
// RangeError
```

subarray()执行与 set()相反的操作，它会基于从原始定型数组中复制的值返回一个新定型数组。复制值时的开始索引和结束索引是可选的：

```js
const source = Int16Array.of(2, 4, 6, 8);
// 把整个数组复制为一个同类型的新数组
const fullCopy = source.subarray();
console.log(fullCopy); // [2, 4, 6, 8]
// 从索引2 开始复制数组
const halfCopy = source.subarray(2);
console.log(halfCopy); // [6, 8]
// 从索引1 开始复制到索引3
const partialCopy = source.subarray(1, 3);
console.log(partialCopy); // [4, 6]
```

定型数组没有原生的拼接能力，但使用定型数组 API 提供的很多工具可以手动构建：

```js
// 第一个参数是应该返回的数组类型
// 其余参数是应该拼接在一起的定型数组
function typedArrayConcat(typedArrayConstructor, ...typedArrays) {
  // 计算所有数组中包含的元素总数
  const numElements = typedArrays.reduce((x, y) => (x.length || x) + y.length);
  // 按照提供的类型创建一个数组，为所有元素留出空间
  const resultArray = new typedArrayConstructor(numElements);
  // 依次转移数组
  let currentOffset = 0;
  typedArrays.map((x) => {
    resultArray.set(x, currentOffset);
    currentOffset += x.length;
  });
  return resultArray;
}
const concatArray = typedArrayConcat(
  Int32Array,
  Int8Array.of(1, 2, 3),
  Int16Array.of(4, 5, 6),
  Float32Array.of(7, 8, 9)
);
console.log(concatArray); // [1, 2, 3, 4, 5, 6, 7, 8, 9]
console.log(concatArray instanceof Int32Array); // true
```

3. **上溢和下溢**

定型数组中值的下溢和上溢不会影响到其他索引，但仍然需要考虑数组的元素应该是什么类型。定型数组对于可以存储的每个索引只接受一个相关位，而不考虑它们对实际数值的影响。以下代码演示了如何处理下溢和上溢：

```js
// 长度为2 的有符号整数数组
// 每个索引保存一个二补数形式的有符号整数
// 范围是-128（-1 * 2^7）~127（2^7 - 1）
const ints = new Int8Array(2);
// 长度为2 的无符号整数数组
// 每个索引保存一个无符号整数
// 范围是0~255（2^7 - 1）
const unsignedInts = new Uint8Array(2);
// 上溢的位不会影响相邻索引
// 索引只取最低有效位上的8 位
unsignedInts[1] = 256; // 0x100
console.log(unsignedInts); // [0, 0]
unsignedInts[1] = 511; // 0x1FF
console.log(unsignedInts); // [0, 255]
// 下溢的位会被转换为其无符号的等价值
// 0xFF 是以二补数形式表示的-1（截取到8 位）,
// 但255 是一个无符号整数
unsignedInts[1] = -1; // 0xFF (truncated to 8 bits)
console.log(unsignedInts); // [0, 255]
// 上溢自动变成二补数形式
// 0x80 是无符号整数的128，是二补数形式的-128
ints[1] = 128; // 0x80
console.log(ints); // [0, -128]
// 下溢自动变成二补数形式
// 0xFF 是无符号整数的255，是二补数形式的-1
ints[1] = 255; // 0xFF
console.log(ints); // [0, -1]
```

除了 8 种元素类型，还有一种“夹板”数组类型：Uint8ClampedArray，不允许任何方向溢出。超出最大值 255 的值会被向下舍入为 255，而小于最小值 0 的值会被向上舍入为 0。

```js
const clampedInts = new Uint8ClampedArray([-1, 0, 255, 256]);
console.log(clampedInts); // [0, 0, 255, 255]
```

按照 JavaScript 之父 Brendan Eich 的说法：“Uint8ClampedArray 完全是 HTML5canvas 元素的历史留存。除非真的做跟 canvas 相关的开发，否则不要使用它。”

## 6.4. Map

ECMAScript 6 以前，在 JavaScript 中实现“键/值”式存储可以使用 Object 来方便高效地完成，也就是使用对象属性作为键，再使用属性来引用值。但这种实现并非没有问题，为此 TC39 委员会专门为“键/值”存储定义了一个规范。

作为 ECMAScript 6 的新增特性，Map 是一种新的集合类型，为这门语言带来了真正的键/值存储机制。Map 的大多数特性都可以通过 Object 类型实现，但二者之间还是存在一些细微的差异。具体实践中使用哪一个，还是值得细细甄别。

### 6.4.1. 基本 API

使用 new 关键字和 Map 构造函数可以创建一个空映射：

```js
const m = new Map();
```

如果想在创建的同时初始化实例，可以给 Map 构造函数传入一个可迭代对象，需要包含键/值对数组。可迭代对象中的每个键/值对都会按照迭代顺序插入到新映射实例中：

```js
// 使用嵌套数组初始化映射
const m1 = new Map([
  ["key1", "val1"],
  ["key2", "val2"],
  ["key3", "val3"],
]);
console.log(m1.size); // 3

// 使用自定义迭代器初始化映射
const m2 = new Map({
  [Symbol.iterator]: function* () {
    yield ["key1", "val1"];
    yield ["key2", "val2"];
    yield ["key3", "val3"];
  },
});
console.log(m2.size); // 3

// 映射期待的键/值对，无论是否提供
const m3 = new Map([[]]);
console.log(m3.has(undefined)); // true
console.log(m3.get(undefined)); // undefined
```

初始化之后，可以使用 set()方法再添加键/值对。另外，可以使用 get()和 has()进行查询，可以通过 size 属性获取映射中的键/值对的数量，还可以使用 delete()和 clear()删除值。

```js
const m = new Map();
console.log(m.has("firstName")); // false
console.log(m.get("firstName")); // undefined
console.log(m.size); // 0

m.set("firstName", "Matt").set("lastName", "Frisbie");
console.log(m.has("firstName")); // true
console.log(m.get("firstName")); // Matt
console.log(m.size); // 2

m.delete("firstName"); // 只删除这一个键/值对
console.log(m.has("firstName")); // false
console.log(m.has("lastName")); // true
console.log(m.size); // 1

m.clear(); // 清除这个映射实例中的所有键/值对
console.log(m.has("firstName")); // false
console.log(m.has("lastName")); // false
console.log(m.size); // 0
```

set()方法返回映射实例，因此可以把多个操作连缀起来，包括初始化声明：

```js
const m = new Map().set("key1", "val1").set("key2", "val2").set("key3", "val3");

console.log(m.size); // 3
```

与 Object 只能使用数值、字符串或符号作为键不同，Map 可以使用任何 JavaScript 数据类型作为键。Map 内部使用 SameValueZero 比较操作（ECMAScript 规范内部定义，语言中不能使用），基本上相当于使用严格对象相等的标准来检查键的匹配性。与 Object 类似，映射的值是没有限制的。

```js
const m = new Map();

const functionKey = function () {};
const symbolKey = Symbol();
const objectKey = new Object();

m.set(functionKey, "functionValue");
m.set(symbolKey, "symbolValue");
m.set(objectKey, "objectValue");

console.log(m.get(functionKey)); // functionValue
console.log(m.get(symbolKey)); // symbolValue
console.log(m.get(objectKey)); // objectValue

// SameValueZero 比较意味着独立实例不冲突
console.log(m.get(function () {})); // undefined
```

与严格相等一样，在映射中用作键和值的对象及其他“集合”类型，在自己的内容或属性被修改时仍然保持不变：

```js
const m = new Map();

const objKey = {},
  objVal = {},
  arrKey = [],
  arrVal = [];

m.set(objKey, objVal);
m.set(arrKey, arrVal);

objKey.foo = "foo";
objVal.bar = "bar";
arrKey.push("foo");
arrVal.push("bar");

console.log(m.get(objKey)); // {bar: "bar"}
console.log(m.get(arrKey)); // ["bar"]
```

SameValueZero 比较也可能导致意想不到的冲突：

```js
const m = new Map();
const a = 0 / "", // NaN
  b = 0 / "", // NaN
  pz = +0,
  nz = -0;
console.log(a === b); // false
console.log(pz === nz); // true
m.set(a, "foo");
m.set(pz, "bar");
console.log(m.get(b)); // foo
console.log(m.get(nz)); // bar
```

注意 SameValueZero 是 ECMAScript 规范新增的相等性比较算法。关于 ECMAScript 的相等性比较，可以参考 MDN 文档中的文章“Equality Comparisons and Sameness”

### 6.4.2. 顺序与迭代

与 Object 类型的一个主要差异是，Map 实例会维护键值对的插入顺序，因此可以根据插入顺序执行迭代操作。

映射实例可以提供一个迭代器（Iterator），能以插入顺序生成[key, value]形式的数组。可以通过 entries()方法（或者 Symbol.iterator 属性，它引用 entries()）取得这个迭代器：

```js
const m = new Map([
  ["key1", "val1"],
  ["key2", "val2"],
  ["key3", "val3"],
]);
console.log(m.entries === m[Symbol.iterator]); // true
for (let pair of m.entries()) {
  console.log(pair);
}
// [key1,val1]
// [key2,val2]
// [key3,val3]
for (let pair of m[Symbol.iterator]()) {
  console.log(pair);
}
// [key1,val1]
// [key2,val2]
// [key3,val3]
```

因为 entries()是默认迭代器，所以可以直接对映射实例使用扩展操作，把映射转换为数组：

```js
const m = new Map([
  ["key1", "val1"],
  ["key2", "val2"],
  ["key3", "val3"],
]);
console.log([...m]); // [[key1,val1],[key2,val2],[key3,val3]]
```

如果不使用迭代器，而是使用回调方式，则可以调用映射的 forEach(callback, opt_thisArg)方法并传入回调，依次迭代每个键/值对。传入的回调接收可选的第二个参数，这个参数用于重写回调内部 this 的值：

```js
const m = new Map([
  ["key1", "val1"],
  ["key2", "val2"],
  ["key3", "val3"],
]);
m.forEach((val, key) => console.log(`${key} => ${val}`));
// key1 -> val1
// key2 -> val2
// key3 -> val3
```

keys()和 values()分别返回以插入顺序生成键和值的迭代器：

```js
const m = new Map([
  ["key1", "val1"],
  ["key2", "val2"],
  ["key3", "val3"],
]);
for (let key of m.keys()) {
  console.log(key);
}
// key1
// key2
// key3
for (let key of m.values()) {
  console.log(key);
}
// value1
// value2
// value3
```

键和值在迭代器遍历时是可以修改的，但映射内部的引用则无法修改。当然，这并不妨碍修改作为键或值的对象内部的属性，因为这样并不影响它们在映射实例中的身份：

```js
const m1 = new Map([["key1", "val1"]]);

// 作为键的字符串原始值是不能修改的
for (let key of m1.keys()) {
  key = "newKey";
  console.log(key); // newKey
  console.log(m1.get("key1")); // val1
}
const keyObj = { id: 1 };
const m = new Map([[keyObj, "val1"]]);

// 修改了作为键的对象的属性，但对象在映射内部仍然引用相同的值
for (let key of m.keys()) {
  key.id = "newKey";
  console.log(key); // {id: "newKey"}
  console.log(m.get(keyObj)); // val1
}
console.log(keyObj); // {id: "newKey"}
```

### 6.4.3. 选择 Object 还是 Map

对于多数 Web 开发任务来说，选择 Object 还是 Map 只是个人偏好问题，影响不大。不过，对于在乎内存和性能的开发者来说，对象和映射之间确实存在显著的差别。

1. 内存占用
   Object 和 Map 的工程级实现在不同浏览器间存在明显差异，但存储单个键/值对所占用的内存数量都会随键的数量线性增加。批量添加或删除键/值对则取决于各浏览器对该类型内存分配的工程实现。不同浏览器的情况不同，但给定固定大小的内存，Map 大约可以比 Object 多存储 50%的键/值对。
2. 插入性能
   向 Object 和 Map 中插入新键/值对的消耗大致相当，不过插入 Map 在所有浏览器中一般会稍微快一点儿。对这两个类型来说，插入速度并不会随着键/值对数量而线性增加。如果代码涉及大量插入操作，那么显然 Map 的性能更佳。
3. 查找速度
   与插入不同，从大型 Object 和 Map 中查找键/值对的性能差异极小，但如果只包含少量键/值对，则 Object 有时候速度更快。在把 Object 当成数组使用的情况下（比如使用连续整数作为属性），浏览器引擎可以进行优化，在内存中使用更高效的布局。这对 Map 来说是不可能的。对这两个类型而言，查找速度不会随着键/值对数量增加而线性增加。如果代码涉及大量查找操作，那么某些情况下可能选择 Object 更好一些。
4. 删除性能
   使用 delete 删除 Object 属性的性能一直以来饱受诟病，目前在很多浏览器中仍然如此。为此，出现了一些伪删除对象属性的操作，包括把属性值设置为 undefined 或 null。但很多时候，这都是一种讨厌的或不适宜的折中。而对大多数浏览器引擎来说，Map 的 delete()操作都比插入和查找更快。如果代码涉及大量删除操作，那么毫无疑问应该选择 Map。

## 6.5. WeakMap

ECMAScript 6 新增的“弱映射”（WeakMap）是一种新的集合类型，为这门语言带来了增强的键/值对存储机制。WeakMap 是 Map 的“兄弟”类型，其 API 也是 Map 的子集。WeakMap 中的“weak”（弱），描述的是 JavaScript 垃圾回收程序对待“弱映射”中键的方式。

### 6.5.1. 基本 API

可以使用 new 关键字实例化一个空的 WeakMap：

```js
const wm = new WeakMap();
```

弱映射中的键只能是 Object 或者继承自 Object 的类型，尝试使用非对象设置键会抛出 TypeError。值的类型没有限制。

如果想在初始化时填充弱映射，则构造函数可以接收一个可迭代对象，其中需要包含键/值对数组。可迭代对象中的每个键/值都会按照迭代顺序插入新实例中：

```js
const key1 = { id: 1 },
  key2 = { id: 2 },
  key3 = { id: 3 };

// 使用嵌套数组初始化弱映射
const wm1 = new WeakMap([
  [key1, "val1"],
  [key2, "val2"],
  [key3, "val3"],
]);
console.log(wm1.get(key1)); // val1
console.log(wm1.get(key2)); // val2
console.log(wm1.get(key3)); // val3
// 初始化是全有或全无的操作
// 只要有一个键无效就会抛出错误，导致整个初始化失败
const wm2 = new WeakMap([
  [key1, "val1"],
  ["BADKEY", "val2"],
  [key3, "val3"],
]);
// TypeError: Invalid value used as WeakMap key
typeof wm2;
// ReferenceError: wm2 is not defined
// 原始值可以先包装成对象再用作键
const stringKey = new String("key1");
const wm3 = new WeakMap([stringKey, "val1"]);
console.log(wm3.get(stringKey)); // "val1"
```

初始化之后可以使用 set()再添加键/值对，可以使用 get()和 has()查询，还可以使用 delete()删除：

```js
const wm = new WeakMap();
const key1 = { id: 1 },
  key2 = { id: 2 };
console.log(wm.has(key1)); // false
console.log(wm.get(key1)); // undefined
wm.set(key1, "Matt").set(key2, "Frisbie");
console.log(wm.has(key1)); // true
console.log(wm.get(key1)); // Matt
wm.delete(key1); // 只删除这一个键/值对
console.log(wm.has(key1)); // false
console.log(wm.has(key2)); // true
```

set()方法返回弱映射实例，因此可以把多个操作连缀起来，包括初始化声明：

```js
const key1 = { id: 1 },
  key2 = { id: 2 },
  key3 = { id: 3 };
const wm = new WeakMap().set(key1, "val1").set(key2, "val2").set(key3, "val3");

console.log(wm.get(key1)); // val1
console.log(wm.get(key2)); // val2
console.log(wm.get(key3)); // val3
```

### 6.5.2. 弱键

WeakMap 中“weak”表示弱映射的键是“弱弱地拿着”的。意思就是，这些键不属于正式的引用，不会阻止垃圾回收。但要注意的是，弱映射中值的引用可不是“弱弱地拿着”的。只要键存在，键/值对就会存在于映射中，并被当作对值的引用，因此就不会被当作垃圾回收。

来看下面的例子：

```js
const wm = new WeakMap();
wm.set({}, "val");
```

set()方法初始化了一个新对象并将它用作一个字符串的键。因为没有指向这个对象的其他引用，所以当这行代码执行完成后，这个对象键就会被当作垃圾回收。然后，这个键/值对就从弱映射中消失了，使其成为一个空映射。在这个例子中，因为值也没有被引用，所以这对键/值被破坏以后，值本身也会成为垃圾回收的目标。

再看一个稍微不同的例子：

```js
const wm = new WeakMap();
const container = {
  key: {},
};
wm.set(container.key, "val");
function removeReference() {
  container.key = null;
}
```

这一次，container 对象维护着一个对弱映射键的引用，因此这个对象键不会成为垃圾回收的目标。不过，如果调用了 removeReference()，就会摧毁键对象的最后一个引用，垃圾回收程序就可以把这个键/值对清理掉。

### 6.5.3. 不可迭代键

因为 WeakMap 中的键/值对任何时候都可能被销毁，所以没必要提供迭代其键/值对的能力。当然，也用不着像 clear()这样一次性销毁所有键/值的方法。WeakMap 确实没有这个方法。因为不可能迭代，所以也不可能在不知道对象引用的情况下从弱映射中取得值。即便代码可以访问 WeakMap 实例，也没办法看到其中的内容。

WeakMap 实例之所以限制只能用对象作为键，是为了保证只有通过键对象的引用才能取得值。如果允许原始值，那就没办法区分初始化时使用的字符串字面量和初始化之后使用的一个相等的字符串了。

### 6.5.4. 使用弱映射

WeakMap 实例与现有 JavaScript 对象有着很大不同，可能一时不容易说清楚应该怎么使用它。这个问题没有唯一的答案，但已经出现了很多相关策略。

1. **私有对象**

弱映射造就了在 JavaScript 中实现真正私有变量的一种新方式。前提很明确：私有变量会存储在弱映射中，以对象实例为键，以私有成员的字典为值。

下面是一个示例实现：

```js
const wm = new WeakMap();
class User {
  constructor(id) {
    this.idProperty = Symbol("id");
    this.setId(id);
  }
  setPrivate(property, value) {
    const privateMembers = wm.get(this) || {};
    privateMembers[property] = value;
    wm.set(this, privateMembers);
  }
  getPrivate(property) {
    return wm.get(this)[property];
  }
  setId(id) {
    this.setPrivate(this.idProperty, id);
  }
  getId() {
    return this.getPrivate(this.idProperty);
  }
}
const user = new User(123);
console.log(user.getId()); // 123
user.setId(456);
console.log(user.getId()); // 456
// 并不是真正私有的
console.log(wm.get(user)[user.idProperty]); // 456
```

慧眼独具的读者会发现，对于上面的实现，外部代码只需要拿到对象实例的引用和弱映射，就可以取得“私有”变量了。为了避免这种访问，可以用一个闭包把 WeakMap 包装起来，这样就可以把弱映射与外界完全隔离开了：

```js
const User = (() => {
  const wm = new WeakMap();
  class User {
    constructor(id) {
      this.idProperty = Symbol("id");
      this.setId(id);
    }
    setPrivate(property, value) {
      const privateMembers = wm.get(this) || {};
      privateMembers[property] = value;
      wm.set(this, privateMembers);
    }
    getPrivate(property) {
      return wm.get(this)[property];
    }
    setId(id) {
      this.setPrivate(this.idProperty, id);
    }
    getId(id) {
      return this.getPrivate(this.idProperty);
    }
  }
  return User;
})();
const user = new User(123);
console.log(user.getId()); // 123
user.setId(456);
console.log(user.getId()); // 456
```

这样，拿不到弱映射中的健，也就无法取得弱映射中对应的值。虽然这防止了前面提到的访问，但整个代码也完全陷入了 ES6 之前的闭包私有变量模式。

2. **DOM 节点元数据**

因为 WeakMap 实例不会妨碍垃圾回收，所以非常适合保存关联元数据。来看下面这个例子，其中使用了常规的 Map：

```js
const m = new Map();
const loginButton = document.querySelector("#login");
// 给这个节点关联一些元数据
m.set(loginButton, { disabled: true });
```

假设在上面的代码执行后，页面被 JavaScript 改变了，原来的登录按钮从 DOM 树中被删掉了。但由于映射中还保存着按钮的引用，所以对应的 DOM 节点仍然会逗留在内存中，除非明确将其从映射中删除或者等到映射本身被销毁。

如果这里使用的是弱映射，如以下代码所示，那么当节点从 DOM 树中被删除后，垃圾回收程序就可以立即释放其内存（假设没有其他地方引用这个对象）：

```js
const wm = new WeakMap();
const loginButton = document.querySelector("#login");
// 给这个节点关联一些元数据
wm.set(loginButton, { disabled: true });
```

## 6.6. Set

ECMAScript 6 新增的 Set 是一种新集合类型，为这门语言带来集合数据结构。Set 在很多方面都像是加强的 Map，这是因为它们的大多数 API 和行为都是共有的。

### 6.6.1. 基本 API

使用 new 关键字和 Set 构造函数可以创建一个空集合：

```js
const m = new Set();
```

如果想在创建的同时初始化实例，则可以给 Set 构造函数传入一个可迭代对象，其中需要包含插入到新集合实例中的元素：

```js
// 使用数组初始化集合
const s1 = new Set(["val1", "val2", "val3"]);
console.log(s1.size); // 3
// 使用自定义迭代器初始化集合
const s2 = new Set({
  [Symbol.iterator]: function* () {
    yield "val1";
    yield "val2";
    yield "val3";
  },
});
console.log(s2.size); // 3
```

初始化之后，可以使用 add()增加值，使用 has()查询，通过 size 取得元素数量，以及使用 delete()和 clear()删除元素：

```js
const s = new Set();
console.log(s.has("Matt")); // false
console.log(s.size); // 0
s.add("Matt").add("Frisbie");
console.log(s.has("Matt")); // true
console.log(s.size); // 2
s.delete("Matt");
console.log(s.has("Matt")); // false
console.log(s.has("Frisbie")); // true
console.log(s.size); // 1
s.clear(); // 销毁集合实例中的所有值
console.log(s.has("Matt")); // false
console.log(s.has("Frisbie")); // false
console.log(s.size); // 0
```

add()返回集合的实例，所以可以将多个添加操作连缀起来，包括初始化：

```js
const s = new Set().add("val1").add("val2").add("val3");
console.log(s.size); // 3
```

与 Map 类似，Set 可以包含任何 JavaScript 数据类型作为值。集合也使用 SameValueZero 操作（ECMAScript 内部定义，无法在语言中使用），基本上相当于使用严格对象相等的标准来检查值的匹配性。

```js
const s = new Set();
const functionVal = function () {};
const symbolVal = Symbol();
const objectVal = new Object();
s.add(functionVal);
s.add(symbolVal);
s.add(objectVal);
console.log(s.has(functionVal)); // true
console.log(s.has(symbolVal)); // true
console.log(s.has(objectVal)); // true
// SameValueZero 检查意味着独立的实例不会冲突
console.log(s.has(function () {})); // false
```

与严格相等一样，用作值的对象和其他“集合”类型在自己的内容或属性被修改时也不会改变：

```js
const s = new Set();
const objVal = {},
  arrVal = [];
s.add(objVal);
s.add(arrVal);
objVal.bar = "bar";
arrVal.push("bar");
console.log(s.has(objVal)); // true
console.log(s.has(arrVal)); // true
```

add()和 delete()操作是幂等的。delete()返回一个布尔值，表示集合中是否存在要删除的值：

```js
const s = new Set();
s.add("foo");
console.log(s.size); // 1
s.add("foo");
console.log(s.size); // 1
// 集合里有这个值
console.log(s.delete("foo")); // true
// 集合里没有这个值
console.log(s.delete("foo")); // false
```

### 6.6.2. 顺序与迭代

Set 会维护值插入时的顺序，因此支持按顺序迭代。

集合实例可以提供一个迭代器（Iterator），能以插入顺序生成集合内容。可以通过 values()方法及其别名方法 keys()（或者 Symbol.iterator 属性，它引用 values()）取得这个迭代器：

```js
const s = new Set(["val1", "val2", "val3"]);
console.log(s.values === s[Symbol.iterator]); // true
console.log(s.keys === s[Symbol.iterator]); // true
for (let value of s.values()) {
  console.log(value);
}
// val1
// val2
// val3
for (let value of s[Symbol.iterator]()) {
  console.log(value);
}
// val1
// val2
// val3
```

因为 values()是默认迭代器，所以可以直接对集合实例使用扩展操作，把集合转换为数组：

```js
const s = new Set(["val1", "val2", "val3"]);
console.log([...s]); // ["val1", "val2", "val3"]
```

集合的 entries()方法返回一个迭代器，可以按照插入顺序产生包含两个元素的数组，这两个元素是集合中每个值的重复出现：

```js
const s = new Set(["val1", "val2", "val3"]);
for (let pair of s.entries()) {
  console.log(pair);
}
// ["val1", "val1"]
// ["val2", "val2"]
// ["val3", "val3"]
```

如果不使用迭代器，而是使用回调方式，则可以调用集合的 forEach()方法并传入回调，依次迭代每个键/值对。传入的回调接收可选的第二个参数，这个参数用于重写回调内部 this 的值：

```js
const s = new Set(["val1", "val2", "val3"]);
s.forEach((val, dupVal) => console.log(`${val} -> ${dupVal}`));
// val1 -> val1
// val2 -> val2
// val3 -> val3
```

修改集合中值的属性不会影响其作为集合值的身份：

```js
const s1 = new Set(["val1"]);
// 字符串原始值作为值不会被修改
for (let value of s1.values()) {
  value = "newVal";
  console.log(value); // newVal
  console.log(s1.has("val1")); // true
}
const valObj = { id: 1 };
const s2 = new Set([valObj]);
// 修改值对象的属性，但对象仍然存在于集合中
for (let value of s2.values()) {
  value.id = "newVal";
  console.log(value); // {id: "newVal"}
  console.log(s2.has(valObj)); // true
}
console.log(valObj); // {id: "newVal"}
```

### 6.6.3. 定义正式集合操作

从各方面来看，Set 跟 Map 都很相似，只是 API 稍有调整。唯一需要强调的就是集合的 API 对自身的简单操作。很多开发者都喜欢使用 Set 操作，但需要手动实现：或者是子类化 Set，或者是定义一个实用函数库。要把两种方式合二为一，可以在子类上实现静态方法，然后在实例方法中使用这些静态方法。在实现这些操作时，需要考虑几个地方。

- 某些 Set 操作是有关联性的，因此最好让实现的方法能支持处理任意多个集合实例。
- Set 保留插入顺序，所有方法返回的集合必须保证顺序。
- 尽可能高效地使用内存。扩展操作符的语法很简洁，但尽可能避免集合和数组间的相互转换能够节省对象初始化成本。
- 不要修改已有的集合实例。union(a, b)或 a.union(b)应该返回包含结果的新集合实例。

```js
class XSet extends Set {
  union(...sets) {
    return XSet.union(this, ...sets);
  }
  intersection(...sets) {
    return XSet.intersection(this, ...sets);
  }
  difference(set) {
    return XSet.difference(this, set);
  }
  symmetricDifference(set) {
    return XSet.symmetricDifference(this, set);
  }
  cartesianProduct(set) {
    return XSet.cartesianProduct(this, set);
  }
  powerSet() {
    return XSet.powerSet(this);
  }
  // 返回两个或更多集合的并集
  static union(a, ...bSets) {
    const unionSet = new XSet(a);
    for (const b of bSets) {
      for (const bValue of b) {
        unionSet.add(bValue);
      }
    }
    return unionSet;
  }
  // 返回两个或更多集合的交集
  static intersection(a, ...bSets) {
    const intersectionSet = new XSet(a);
    for (const aValue of intersectionSet) {
      for (const b of bSets) {
        if (!b.has(aValue)) {
          intersectionSet.delete(aValue);
        }
      }
    }
    return intersectionSet;
  }
  // 返回两个集合的差集
  static difference(a, b) {
    const differenceSet = new XSet(a);
    for (const bValue of b) {
      if (a.has(bValue)) {
        differenceSet.delete(bValue);
      }
    }
    return differenceSet;
  }
  // 返回两个集合的对称差集
  static symmetricDifference(a, b) {
    // 按照定义，对称差集可以表达为
    return a.union(b).difference(a.intersection(b));
  }
  // 返回两个集合（数组对形式）的笛卡儿积
  // 必须返回数组集合，因为笛卡儿积可能包含相同值的对
  static cartesianProduct(a, b) {
    const cartesianProductSet = new XSet();
    for (const aValue of a) {
      for (const bValue of b) {
        cartesianProductSet.add([aValue, bValue]);
      }
    }
    return cartesianProductSet;
  }
  // 返回一个集合的幂集
  static powerSet(a) {
    const powerSet = new XSet().add(new XSet());
    for (const aValue of a) {
      for (const set of new XSet(powerSet)) {
        powerSet.add(new XSet(set).add(aValue));
      }
    }
    return powerSet;
  }
}
```

## 6.7. WeakSet

ECMAScript 6 新增的“弱集合”（WeakSet）是一种新的集合类型，为这门语言带来了集合数据结构。WeakSet 是 Set 的“兄弟”类型，其 API 也是 Set 的子集。WeakSet 中的“weak”（弱），描述的是 JavaScript 垃圾回收程序对待“弱集合”中值的方式。

### 6.7.1. 基本 API

可以使用 new 关键字实例化一个空的 WeakSet：

```js
const ws = new WeakSet();
```

弱集合中的值只能是 Object 或者继承自 Object 的类型，尝试使用非对象设置值会抛出 TypeError。

如果想在初始化时填充弱集合，则构造函数可以接收一个可迭代对象，其中需要包含有效的值。可迭代对象中的每个值都会按照迭代顺序插入到新实例中：

```js
const val1 = { id: 1 },
  val2 = { id: 2 },
  val3 = { id: 3 };
// 使用数组初始化弱集合
const ws1 = new WeakSet([val1, val2, val3]);
console.log(ws1.has(val1)); // true
console.log(ws1.has(val2)); // true
console.log(ws1.has(val3)); // true
// 初始化是全有或全无的操作
// 只要有一个值无效就会抛出错误，导致整个初始化失败
const ws2 = new WeakSet([val1, "BADVAL", val3]);
// TypeError: Invalid value used in WeakSet
typeof ws2;
// ReferenceError: ws2 is not defined
// 原始值可以先包装成对象再用作值
const stringVal = new String("val1");
const ws3 = new WeakSet([stringVal]);
console.log(ws3.has(stringVal)); // true
```

初始化之后可以使用 add()再添加新值，可以使用 has()查询，还可以使用 delete()删除：

```js
const ws = new WeakSet();
const val1 = { id: 1 },
  val2 = { id: 2 };
console.log(ws.has(val1)); // false
ws.add(val1).add(val2);
console.log(ws.has(val1)); // true
console.log(ws.has(val2)); // true
ws.delete(val1); // 只删除这一个值
console.log(ws.has(val1)); // false
console.log(ws.has(val2)); // true
```

add()方法返回弱集合实例，因此可以把多个操作连缀起来，包括初始化声明：

```js
const val1 = { id: 1 },
  val2 = { id: 2 },
  val3 = { id: 3 };
const ws = new WeakSet().add(val1);
ws.add(val2).add(val3);
console.log(ws.has(val1)); // true
console.log(ws.has(val2)); // true
console.log(ws.has(val3)); // true
```

### 6.7.2. 弱值

WeakSet 中“weak”表示弱集合的值是“弱弱地拿着”的。意思就是，这些值不属于正式的引用，不会阻止垃圾回收。

来看下面的例子：

```js
const ws = new WeakSet();
ws.add({});
```

add()方法初始化了一个新对象，并将它用作一个值。因为没有指向这个对象的其他引用，所以当这行代码执行完成后，这个对象值就会被当作垃圾回收。然后，这个值就从弱集合中消失了，使其成为一个空集合。

再看一个稍微不同的例子：

```js
const ws = new WeakSet();
const container = {
  val: {},
};
ws.add(container.val);
function removeReference() {
  container.val = null;
}
```

这一次，container 对象维护着一个对弱集合值的引用，因此这个对象值不会成为垃圾回收的目标。不过，如果调用了 removeReference()，就会摧毁值对象的最后一个引用，垃圾回收程序就可以把这个值清理掉。

### 6.7.3. 不可迭代值

因为 WeakSet 中的值任何时候都可能被销毁，所以没必要提供迭代其值的能力。当然，也用不着像 clear()这样一次性销毁所有值的方法。WeakSet 确实没有这个方法。因为不可能迭代，所以也不可能在不知道对象引用的情况下从弱集合中取得值。即便代码可以访问 WeakSet 实例，也没办法看到其中的内容。

WeakSet 之所以限制只能用对象作为值，是为了保证只有通过值对象的引用才能取得值。如果允许原始值，那就没办法区分初始化时使用的字符串字面量和初始化之后使用的一个相等的字符串了。

### 6.7.4. 使用弱集合

相比于 WeakMap 实例，WeakSet 实例的用处没有那么大。不过，弱集合在给对象打标签时还是有价值的。

来看下面的例子，这里使用了一个普通 Set：

```js
const disabledElements = new Set();
const loginButton = document.querySelector("#login");
// 通过加入对应集合，给这个节点打上“禁用”标签
disabledElements.add(loginButton);
```

这样，通过查询元素在不在 disabledElements 中，就可以知道它是不是被禁用了。不过，假如元素从 DOM 树中被删除了，它的引用却仍然保存在 Set 中，因此垃圾回收程序也不能回收它。

为了让垃圾回收程序回收元素的内存，可以在这里使用 WeakSet：

```js
const disabledElements = new WeakSet();
const loginButton = document.querySelector("#login");
// 通过加入对应集合，给这个节点打上“禁用”标签
disabledElements.add(loginButton);
```

这样，只要 WeakSet 中任何元素从 DOM 树中被删除，垃圾回收程序就可以忽略其存在，而立即释放其内存（假设没有其他地方引用这个对象）。

## 6.8. 迭代与扩展操作

ECMAScript 6 新增的迭代器和扩展操作符对集合引用类型特别有用。这些新特性让集合类型之间相互操作、复制和修改变得异常方便。

注意 第 7 章会更详细地介绍迭代器和生成器。

如本章前面所示，有 4 种原生集合类型定义了默认迭代器：

- Array
- 所有定型数组
- Map
- Set

很简单，这意味着上述所有类型都支持顺序迭代，都可以传入 for-of 循环：

```js
let iterableThings = [
  Array.of(1, 2),
  (typedArr = Int16Array.of(3, 4)),
  new Map([
    [5, 6],
    [7, 8],
  ]),
  new Set([9, 10]),
];
for (const iterableThing of iterableThings) {
  for (const x of iterableThing) {
    console.log(x);
  }
}
// 1
// 2
// 3
// 4
// [5, 6]
// [7, 8]
// 9
// 10
```

这也意味着所有这些类型都兼容扩展操作符。扩展操作符在对可迭代对象执行浅复制时特别有用，只需简单的语法就可以复制整个对象：

```js
let arr1 = [1, 2, 3];
let arr2 = [...arr1];
console.log(arr1); // [1, 2, 3]
console.log(arr2); // [1, 2, 3]
console.log(arr1 === arr2); // false
```

对于期待可迭代对象的构造函数，只要传入一个可迭代对象就可以实现复制：

```js
let map1 = new Map([
  [1, 2],
  [3, 4],
]);
let map2 = new Map(map1);
console.log(map1); // Map {1 => 2, 3 => 4}
console.log(map2); // Map {1 => 2, 3 => 4}
```

当然，也可以构建数组的部分元素：

```js
let arr1 = [1, 2, 3];
let arr2 = [0, ...arr1, 4, 5];
console.log(arr2); // [0, 1, 2, 3, 4, 5]
```

浅复制意味着只会复制对象引用：

```js
let arr1 = [{}];
let arr2 = [...arr1];
arr1[0].foo = "bar";
console.log(arr2[0]); // { foo: 'bar' }
```

上面的这些类型都支持多种构建方法，比如 Array.of()和 Array.from()静态方法。在与扩展操作符一起使用时，可以非常方便地实现互操作：

```js
let arr1 = [1, 2, 3];
// 把数组复制到定型数组
let typedArr1 = Int16Array.of(...arr1);
let typedArr2 = Int16Array.from(arr1);
console.log(typedArr1); // Int16Array [1, 2, 3]
console.log(typedArr2); // Int16Array [1, 2, 3]
// 把数组复制到映射
let map = new Map(arr1.map((x) => [x, "val" + x]));
console.log(map); // Map {1 => 'val 1', 2 => 'val 2', 3 => 'val 3'}
// 把数组复制到集合
let set = new Set(typedArr2);
console.log(set); // Set {1, 2, 3}
// 把集合复制回数组
let arr2 = [...set];
console.log(arr2); // [1, 2, 3]
```

# 7. 迭代器与生成器

本章内容

- 理解迭代
- 迭代器模式
- 生成器

迭代的英文“iteration”源自拉丁文 itero，意思是“重复”或“再来”。在软件开发领域，“迭代”的意思是按照顺序反复多次执行一段程序，通常会有明确的终止条件。ECMAScript 6 规范新增了两个高级特性：迭代器和生成器。使用这两个特性，能够更清晰、高效、方便地实现迭代。

## 7.1. 理解迭代

在 JavaScript 中，计数循环就是一种最简单的迭代：

```js
for (let i = 0; i <= 10; i++) {
  console.log(i);
}
```

循环是迭代机制的基础，这是因为它可以指定迭代的次数，以及每次迭代要执行什么操作。每次循环都会在下一次迭代开始之前完成，而每次迭代的顺序都是事先定义好的。

迭代会在一个有序集合上进行。（“有序”可以理解为集合中所有项都可以按照既定的顺序被遍历到，特别是开始和结束项有明确的定义。）数组是 JavaScript 中有序集合的最典型例子。

```js
let collection = ["foo", "bar", "baz"];
for (let index = 0; index < collection.length; index++) {
  console.log(collection[index]);
}
```

因为数组有已知的长度，且数组每一项都可以通过索引获取，所以整个数组可以通过递增索引来遍历。

由于如下原因，通过这种循环来执行例程并不理想。

- 迭代之前需要事先知道如何使用数据结构。数组中的每一项都只能先通过引用取得数组对象，然后再通过[]操作符取得特定索引位置上的项。这种情况并不适用于所有数据结构。
- 遍历顺序并不是数据结构固有的。通过递增索引来访问数据是特定于数组类型的方式，并不适用于其他具有隐式顺序的数据结构。

ES5 新增了 Array.prototype.forEach()方法，向通用迭代需求迈进了一步（但仍然不够理想）：

```js
let collection = ["foo", "bar", "baz"];
collection.forEach((item) => console.log(item));
// foo
// bar
// baz
```

这个方法解决了单独记录索引和通过数组对象取得值的问题。不过，没有办法标识迭代何时终止。因此这个方法只适用于数组，而且回调结构也比较笨拙。

在 ECMAScript 较早的版本中，执行迭代必须使用循环或其他辅助结构。随着代码量增加，代码会变得越发混乱。很多语言都通过原生语言结构解决了这个问题，开发者无须事先知道如何迭代就能实现迭代操作。这个解决方案就是迭代器模式。Python、Java、C++，还有其他很多语言都对这个模式提供了完备的支持。JavaScript 在 ECMAScript 6 以后也支持了迭代器模式。

## 7.2. 迭代器模式

迭代器模式（特别是在 ECMAScript 这个语境下）描述了一个方案，即可以把有些结构称为“可迭代对象”（iterable），因为它们实现了正式的 Iterable 接口，而且可以通过迭代器 Iterator 消费。

可迭代对象是一种抽象的说法。基本上，可以把可迭代对象理解成数组或集合这样的集合类型的对象。它们包含的元素都是有限的，而且都具有无歧义的遍历顺序：

```js
// 数组的元素是有限的
// 递增索引可以按序访问每个元素
let arr = [3, 1, 4];

// 集合的元素是有限的
// 可以按插入顺序访问每个元素
let set = new Set().add(3).add(1).add(4);
```

不过，可迭代对象不一定是集合对象，也可以是仅仅具有类似数组行为的其他数据结构，比如本章开头提到的计数循环。该循环中生成的值是暂时性的，但循环本身是在执行迭代。计数循环和数组都具有可迭代对象的行为。

注意 临时性可迭代对象可以实现为生成器，本章后面会讨论。

任何实现 Iterable 接口的数据结构都可以被实现 Iterator 接口的结构“消费”（consume）。迭代器（iterator）是按需创建的一次性对象。每个迭代器都会关联一个可迭代对象，而迭代器会暴露迭代其关联可迭代对象的 API。迭代器无须了解与其关联的可迭代对象的结构，只需要知道如何取得连续的值。这种概念上的分离正是 Iterable 和 Iterator 的强大之处。

### 7.2.1. 可迭代协议

实现 Iterable 接口（可迭代协议）要求同时具备两种能力：支持迭代的自我识别能力和创建实现 Iterator 接口的对象的能力。在 ECMAScript 中，这意味着必须暴露一个属性作为“默认迭代器”，而且这个属性必须使用特殊的 Symbol.iterator 作为键。这个默认迭代器属性必须引用一个迭代器工厂函数，调用这个工厂函数必须返回一个新迭代器。

很多内置类型都实现了 Iterable 接口：

- 字符串
- 数组
- 映射
- 集合
- arguments 对象
- NodeList 等 DOM 集合类型

检查是否存在默认迭代器属性可以暴露这个工厂函数：

```js
let num = 1;
let obj = {};
// 这两种类型没有实现迭代器工厂函数
console.log(num[Symbol.iterator]); // undefined
console.log(obj[Symbol.iterator]); // undefined

let str = "abc";
let arr = ["a", "b", "c"];
let map = new Map().set("a", 1).set("b", 2).set("c", 3);
let set = new Set().add("a").add("b").add("c");
let els = document.querySelectorAll("div");
// 这些类型都实现了迭代器工厂函数
console.log(str[Symbol.iterator]); // f values() { [native code] }
console.log(arr[Symbol.iterator]); // f values() { [native code] }
console.log(map[Symbol.iterator]); // f values() { [native code] }
console.log(set[Symbol.iterator]); // f values() { [native code] }
console.log(els[Symbol.iterator]); // f values() { [native code] }

// 调用这个工厂函数会生成一个迭代器
console.log(str[Symbol.iterator]()); // StringIterator {}
console.log(arr[Symbol.iterator]()); // ArrayIterator {}
console.log(map[Symbol.iterator]()); // MapIterator {}
console.log(set[Symbol.iterator]()); // SetIterator {}
console.log(els[Symbol.iterator]()); // ArrayIterator {}
```

实际写代码过程中，不需要显式调用这个工厂函数来生成迭代器。实现可迭代协议的所有类型都会自动兼容接收可迭代对象的任何语言特性。接收可迭代对象的原生语言特性包括：

- for-of 循环
- 数组解构
- 扩展操作符
- Array.from()
- 创建集合
- 创建映射
- Promise.all()接收由期约组成的可迭代对象
- Promise.race()接收由期约组成的可迭代对象
- yield\*操作符，在生成器中使用

这些原生语言结构会在后台调用提供的可迭代对象的这个工厂函数，从而创建一个迭代器：

```js
let arr = ["foo", "bar", "baz"];
// for-of 循环
for (let el of arr) {
  console.log(el);
}
// foo
// bar
// baz
// 数组解构
let [a, b, c] = arr;
console.log(a, b, c); // foo, bar, baz
// 扩展操作符
let arr2 = [...arr];
console.log(arr2); // ['foo', 'bar', 'baz']
// Array.from()
let arr3 = Array.from(arr);
console.log(arr3); // ['foo', 'bar', 'baz']
// Set 构造函数
let set = new Set(arr);
console.log(set); // Set(3) {'foo', 'bar', 'baz'}
// Map 构造函数
let pairs = arr.map((x, i) => [x, i]);
console.log(pairs); // [['foo', 0], ['bar', 1], ['baz', 2]]
let map = new Map(pairs);
console.log(map); // Map(3) { 'foo'=>0, 'bar'=>1, 'baz'=>2 }
```

如果对象原型链上的父类实现了 Iterable 接口，那这个对象也就实现了这个接口：

```js
class FooArray extends Array {}
let fooArr = new FooArray("foo", "bar", "baz");
for (let el of fooArr) {
  console.log(el);
}
// foo
// bar
// baz
```

### 7.2.2. 迭代器协议

迭代器是一种一次性使用的对象，用于迭代与其关联的可迭代对象。迭代器 API 使用 next()方法在可迭代对象中遍历数据。每次成功调用 next()，都会返回一个 IteratorResult 对象，其中包含迭代器返回的下一个值。若不调用 next()，则无法知道迭代器的当前位置。

next()方法返回的迭代器对象 IteratorResult 包含两个属性：done 和 value。done 是一个布尔值，表示是否还可以再次调用 next()取得下一个值；value 包含可迭代对象的下一个值（done 为 false），或者 undefined（done 为 true）。done: true 状态称为“耗尽”。可以通过以下简单的数组来演示：

```js
// 可迭代对象
let arr = ["foo", "bar"];
// 迭代器工厂函数
console.log(arr[Symbol.iterator]); // f values() { [native code] }
// 迭代器
let iter = arr[Symbol.iterator]();
console.log(iter); // ArrayIterator {}
// 执行迭代
console.log(iter.next()); // { value: 'foo', done: false }
console.log(iter.next()); // { value: 'bar', done: false }
console.log(iter.next()); // { value: undefined, done: true }
```

这里通过创建迭代器并调用next()方法按顺序迭代了数组，直至不再产生新值。迭代器并不知道怎么从可迭代对象中取得下一个值，也不知道可迭代对象有多大。只要迭代器到达done: true 状态，后续调用next()就一直返回同样的值了：

```js
let arr = ['foo'];
let iter = arr[Symbol.iterator]();
console.log(iter.next()); // { value: undefined, done: true }
console.log(iter.next()); // { value: undefined, done: true }
console.log(iter.next()); // { value: undefined, done: true }
console.log(iter.next()); // { value: undefined, done: true }
```

不过可以使用 done 的值来结束迭代，例如：

```js
let arr = ["foo", "bar", "baz"];
let iter = arr[Symbol.iterator]();
let done = false;
while (!done) {
  let result = iter.next();
  done = result.done;
  console.log(result);
}
// { value: 'foo', done: false }
// { value: 'bar', done: false }
// { value: 'baz', done: false }
// { value: undefined, done: true }
```

每个迭代器都表示对可迭代对象的一次性有序遍历。不同迭代器的实例相互之间没有联系，只会独立地遍历可迭代对象：

```js
let arr = ['foo', 'bar'];
let iter1 = arr[Symbol.iterator]();
let iter2 = arr[Symbol.iterator]();

console.log(iter1.next()); // { value: 'foo', done: false }
console.log(iter2.next()); // { value: 'foo', done: false }
console.log(iter2.next()); // { value: 'bar', done: false }
console.log(iter1.next()); // { value: 'bar', done: false }

console.log(arr[Symbol.iterator]().next()); // { value: 'foo', done: false }
console.log(arr[Symbol.iterator]().next()); // { value: 'foo', done: false }
console.log(arr[Symbol.iterator]().next()); // { value: 'foo', done: false }
console.log(arr[Symbol.iterator]().next()); // { value: 'foo', done: false }
```

迭代器并不与可迭代对象某个时刻的快照绑定，而仅仅是使用游标来记录遍历可迭代对象的历程。如果可迭代对象在迭代期间被修改了，那么迭代器也会反映相应的变化：

```js
let arr = ['foo', 'baz'];
let iter = arr[Symbol.iterator]();
console.log(iter.next()); // { value: 'foo', done: false }

// 在数组中间插入值
arr.splice(1, 0, 'bar');
console.log(iter.next()); // { value: 'bar', done: false }
console.log(iter.next()); // { value: 'baz', done: false }
console.log(iter.next()); // { value: undefined, done: true }
```

注意 迭代器维护着一个指向可迭代对象的引用，因此迭代器会阻止垃圾回收程序回收可迭代对象。

“迭代器”的概念有时候容易模糊，因为它可以指通用的迭代，也可以指接口，还可以指正式的迭代器类型。下面的例子比较了一个显式的迭代器实现和一个原生的迭代器实现。

```js
// 这个类实现了可迭代接口（Iterable）
// 调用默认的迭代器工厂函数会返回
// 一个实现迭代器接口（Iterator）的迭代器对象
class Foo {
  [Symbol.iterator]() {
    return {
      next() {
        return { value: 'foo', done: false };
      }
    }
  }
}
let f = new Foo();
// 打印出实现了迭代器接口的对象
console.log(f[Symbol.iterator]()); // { next: f() {} }

// Array 类型实现了可迭代接口（Iterable）
// 调用Array 类型的默认迭代器工厂函数
// 会创建一个ArrayIterator 的实例
let a = new Array();
// 打印出ArrayIterator 的实例
console.log(a[Symbol.iterator]()); // Array Iterator {}
```

### 7.2.3. 自定义迭代器

与Iterable 接口类似，任何实现Iterator 接口的对象都可以作为迭代器使用。下面这个例子中的Counter 类只能被迭代一定的次数：

```js
class Counter {
  // Counter 的实例应该迭代limit 次
  constructor(limit) {
    this.count = 1;
    this.limit = limit;
  }
  next() {
    if (this.count <= this.limit) {
      return { value: this.count++, done: false };
    } else {
      return { value: undefined, done: true };
    }
  }
  [Symbol.iterator]() {
    return this;
  }
}
let counter = new Counter(3);
for (let i of counter) {
  console.log(i);
} 
// 1
// 2
// 3
```

这个类实现了Iterator 接口，但不理想。这是因为它的每个实例只能被迭代一次：

```js
for (let i of counter) { console.log(i); }
// 1
// 2
// 3
for (let i of counter) { console.log(i); }
// (nothing logged)
```

为了让一个可迭代对象能够创建多个迭代器，必须每创建一个迭代器就对应一个新计数器。为此，可以把计数器变量放到闭包里，然后通过闭包返回迭代器：

```js
class Counter {
  constructor(limit) {
    this.limit = limit;
  }
  [Symbol.iterator]() {
    let count = 1,
    limit = this.limit;
    return {
      next() {
        if (count <= limit) {
          return { done: false, value: count++ };
        } else {
          return { done: true, value: undefined };
        }
      }
    };
  }
}
let counter = new Counter(3);
for (let i of counter) { console.log(i); }
// 1
// 2
// 3
for (let i of counter) { console.log(i); }
// 1
// 2
// 3
```

每个以这种方式创建的迭代器也实现了Iterable 接口。Symbol.iterator 属性引用的工厂函数会返回相同的迭代器：

```js
let arr = ['foo', 'bar', 'baz'];
let iter1 = arr[Symbol.iterator]();
console.log(iter1[Symbol.iterator]); // f values() { [native code] }
let iter2 = iter1[Symbol.iterator]();
console.log(iter1 === iter2); // true
```

因为每个迭代器也实现了Iterable 接口，所以它们可以用在任何期待可迭代对象的地方，比如for-of 循环：

```js
for (let item of arr ) { console.log(item); }
// 3
// 1
// 4
for (let item of iter ) { console.log(item); }
// 3
// 1
// 4
```

### 7.2.4. 提前终止迭代器

可选的return()方法用于指定在迭代器提前关闭时执行的逻辑。执行迭代的结构在想让迭代器知道它不想遍历到可迭代对象耗尽时，就可以“关闭”迭代器。可能的情况包括：

- for-of 循环通过break、continue、return 或throw 提前退出；
- 解构操作并未消费所有值。

return()方法必须返回一个有效的IteratorResult 对象。简单情况下，可以只返回{ done: true }。因为这个返回值只会用在生成器的上下文中，所以本章后面再讨论这种情况。

如下面的代码所示，内置语言结构在发现还有更多值可以迭代，但不会消费这些值时，会自动调用return()方法。

```js
class Counter {
constructor(limit) {
this.limit = limit;
}
[Symbol.iterator]() {
let count = 1,
limit = this.limit;
return {
next() {
if (count <= limit) {
return { done: false, value: count++ };
} else {
return { done: true };
}
},
return() {
console.log('Exiting early');
return { done: true };
}
};
}
}
let counter1 = new Counter(5);
for (let i of counter1) {
if (i > 2) {
break;
}
console.log(i);
}
// 1
// 2
// Exiting early
let counter2 = new Counter(5);
try {
for (let i of counter2) {
if (i > 2) {
throw 'err';
}
console.log(i);
}
} catch(e) {}
// 1
// 2
// Exiting early
let counter3 = new Counter(5);
let [a, b] = counter3;
// Exiting early
```

如果迭代器没有关闭，则还可以继续从上次离开的地方继续迭代。比如，数组的迭代器就是不能关闭的：

```js
let a = [1, 2, 3, 4, 5];
let iter = a[Symbol.iterator]();
for (let i of iter) {
  console.log(i);
  if (i > 2) {
    break
  }
}
// 1
// 2
// 3
for (let i of iter) {
console.log(i);
}
// 4
// 5
```

因为return()方法是可选的，所以并非所有迭代器都是可关闭的。要知道某个迭代器是否可关闭，可以测试这个迭代器实例的return 属性是不是函数对象。不过，仅仅给一个不可关闭的迭代器增加这个方法并不能让它变成可关闭的。这是因为调用return()不会强制迭代器进入关闭状态。即便如此，return()方法还是会被调用。

```js
let a = [1, 2, 3, 4, 5];
let iter = a[Symbol.iterator]();
iter.return = function() {
console.log('Exiting early');
return { done: true };
};
for (let i of iter) {
console.log(i);
if (i > 2) {
break
}
}
// 1
// 2
// 3
// 提前退出
for (let i of iter) {
console.log(i);
}
// 4
// 5
```

## 7.3. 生成器

生成器是ECMAScript 6 新增的一个极为灵活的结构，拥有在一个函数块内暂停和恢复代码执行的能力。这种新能力具有深远的影响，比如，使用生成器可以自定义迭代器和实现协程。

### 7.3.1. 生成器基础

生成器的形式是一个函数，函数名称前面加一个星号（*）表示它是一个生成器。只要是可以定义函数的地方，就可以定义生成器。

```js
// 生成器函数声明
function* generatorFn() {}

// 生成器函数表达式
let generatorFn = function* () {}

// 作为对象字面量方法的生成器函数
let foo = {
  * generatorFn() {}
}
// 作为类实例方法的生成器函数
class Foo {
  * generatorFn() {}
}
// 作为类静态方法的生成器函数
class Bar {
  static * generatorFn() {}
}
```

注意 箭头函数不能用来定义生成器函数。

标识生成器函数的星号不受两侧空格的影响：

```js
// 等价的生成器函数：
function* generatorFnA() {}
function *generatorFnB() {}
function * generatorFnC() {}
// 等价的生成器方法：
class Foo {
  *generatorFnD() {}
  * generatorFnE() {}
}
```

调用生成器函数会产生一个 **生成器对象**。生成器对象一开始处于暂停执行（suspended）的状态。与迭代器相似，生成器对象也实现了Iterator 接口，因此具有next()方法。调用这个方法会让生成器开始或恢复执行。

```js
function* generatorFn() {}
const g = generatorFn();
console.log(g); // generatorFn {<suspended>}
console.log(g.next); // f next() { [native code] }
```

next()方法的返回值类似于迭代器，有一个done 属性和一个value 属性。函数体为空的生成器函数中间不会停留，调用一次next()就会让生成器到达done: true 状态。

```js
function* generatorFn() {}
let generatorObject = generatorFn();
console.log(generatorObject); // generatorFn {<suspended>}
console.log(generatorObject.next()); // { done: true, value: undefined }
```

value 属性是生成器函数的返回值，默认值为undefined，可以通过生成器函数的返回值指定：

```js
function* generatorFn() {
  return 'foo';
}
let generatorObject = generatorFn();
console.log(generatorObject); // generatorFn {<suspended>}
console.log(generatorObject.next()); // { done: true, value: 'foo' }
```

生成器函数只会在初次调用next()方法后开始执行，如下所示：

```js
function* generatorFn() {
  console.log('foobar');
}
// 初次调用生成器函数并不会打印日志
let generatorObject = generatorFn();
generatorObject.next(); // foobar
```

生成器对象实现了Iterable 接口，它们默认的迭代器是自引用的：

```js
function* generatorFn() {}
console.log(generatorFn);
// f* generatorFn() {}
console.log(generatorFn()[Symbol.iterator]);
// f [Symbol.iterator]() {native code}
console.log(generatorFn());
// generatorFn {<suspended>}
console.log(generatorFn()[Symbol.iterator]());
// generatorFn {<suspended>}
const g = generatorFn();
console.log(g === g[Symbol.iterator]());
// true
```

### 7.3.2. 通过 yield 中断执行

yield 关键字可以让生成器停止和开始执行，也是生成器最有用的地方。生成器函数在遇到yield关键字之前会正常执行。遇到这个关键字后，执行会停止，函数作用域的状态会被保留。停止执行的生成器函数只能通过在生成器对象上调用next()方法来恢复执行：

```js
function* generatorFn() {
  yield;
}
let generatorObject = generatorFn();
console.log(generatorObject.next()); // { value: undefined, done: false }
console.log(generatorObject.next()); // { value: undefined, done: true }
```

此时的yield 关键字有点像函数的中间返回语句，它生成的值会出现在next()方法返回的对象里。通过yield 关键字退出的生成器函数会处在done: false 状态；通过return 关键字退出的生成器函数会处于done: true 状态。

```js
function* generatorFn() {
  yield 'foo';
  yield 'bar';
  return 'baz';
}
let generatorObject = generatorFn();
console.log(generatorObject.next()); // { done: false, value: 'foo' }
console.log(generatorObject.next()); // { done: false, value: 'bar' }
console.log(generatorObject.next()); // { done: true, value: 'baz' }
```

生成器函数内部的执行流程会针对每个生成器对象区分作用域。在一个生成器对象上调用next()不会影响其他生成器：

```js
function* generatorFn() {
  yield 'foo';
  yield 'bar';
  return 'baz';
}
let generatorObject1 = generatorFn();
let generatorObject2 = generatorFn();
console.log(generatorObject1.next()); // { done: false, value: 'foo' }
console.log(generatorObject2.next()); // { done: false, value: 'foo' }
console.log(generatorObject2.next()); // { done: false, value: 'bar' }
console.log(generatorObject1.next()); // { done: false, value: 'bar' }
```

yield 关键字只能在生成器函数内部使用，用在其他地方会抛出错误。类似函数的return 关键字，yield 关键字必须直接位于生成器函数定义中，出现在嵌套的非生成器函数中会抛出语法错误：

```js
// 有效
function* validGeneratorFn() {
  yield;
}
// 无效
function* invalidGeneratorFnA() {
  function a() {
    yield;
  }
}
// 无效
function* invalidGeneratorFnB() {
  const b = () => {
    yield;
  }
}
// 无效
function* invalidGeneratorFnC() {
  (() => {
    yield;
  })();
}
```

1. **生成器作为可迭代对象**

在生成器对象上显式调用next()方法的用处并不大。其实，如果把生成器对象当成可迭代对象，那么使用起来会更方便：

```js
function* generatorFn() {
  yield 1;
  yield 2;
  yield 3;
}
for (const x of generatorFn()) {
  console.log(x);
}
// 1
// 2
// 3
```

在需要自定义迭代对象时，这样使用生成器对象会特别有用。比如，我们需要定义一个可迭代对象，而它会产生一个迭代器，这个迭代器会执行指定的次数。使用生成器，可以通过一个简单的循环来实现：

```js
function* nTimes(n) {
  while(n--) {
    yield;
  }
}

for (let _ of nTimes(3)) {
  console.log('foo');
}
// foo
// foo
// foo
```

传给生成器的函数可以控制迭代循环的次数。在n 为0 时，while 条件为假，循环退出，生成器函数返回。

2. **使用yield 实现输入和输出**

除了可以作为函数的中间返回语句使用，yield 关键字还可以作为函数的中间参数使用。上一次让生成器函数暂停的yield 关键字会接收到传给next()方法的第一个值。这里有个地方不太好理解——第一次调用next()传入的值不会被使用，因为这一次调用是为了开始执行生成器函数：

```js
function* generatorFn(initial) {
  console.log(initial);
  console.log(yield);
  console.log(yield);
}
let generatorObject = generatorFn('foo');
generatorObject.next('bar'); // foo
generatorObject.next('baz'); // baz
generatorObject.next('qux'); // qux
```

yield 关键字可以同时用于输入和输出，如下例所示：

```js
function* generatorFn() {
  return yield 'foo';
}
let generatorObject = generatorFn();
console.log(generatorObject.next()); // { done: false, value: 'foo' }
console.log(generatorObject.next('bar')); // { done: true, value: 'bar' }
```

因为函数必须对整个表达式求值才能确定要返回的值，所以它在遇到yield 关键字时暂停执行并计算出要产生的值："foo"。下一次调用next()传入了"bar"，作为交给同一个yield 的值。然后这个值被确定为本次生成器函数要返回的值。

yield 关键字并非只能使用一次。比如，以下代码就定义了一个无穷计数生成器函数：

```js
function* generatorFn() {
  for (let i = 0;;++i) {
    yield i;
  }
}
let generatorObject = generatorFn();
console.log(generatorObject.next().value); // 0
console.log(generatorObject.next().value); // 1
console.log(generatorObject.next().value); // 2
console.log(generatorObject.next().value); // 3
console.log(generatorObject.next().value); // 4
console.log(generatorObject.next().value); // 5
```

假设我们想定义一个生成器函数，它会根据配置的值迭代相应次数并产生迭代的索引。初始化一个新数组可以实现这个需求，但不用数组也可以实现同样的行为：

```js
function* nTimes(n) {
  for (let i = 0; i < n; ++i) {
    yield i;
  }
}
for (let x of nTimes(3)) {
  console.log(x);
}
// 0
// 1
// 2
```

另外，使用while 循环也可以，而且代码稍微简洁一点：

```js
function* nTimes(n) {
  let i = 0;
  while(n--) {
    yield i++;
  }
}
for (let x of nTimes(3)) {
  console.log(x);
}
// 0
// 1
// 2
```

这样使用生成器也可以实现范围和填充数组：

```js
function* range(start, end) {
  while(end > start) {
    yield start++;
  }
}
for (const x of range(4, 7)) {
  console.log(x);
}
// 4
// 5
// 6
function* zeroes(n) {
  while(n--) {
    yield 0;
  }
}
console.log(Array.from(zeroes(8))); // [0, 0, 0, 0, 0, 0, 0, 0]
```

3. **产生可迭代对象**

可以使用星号增强yield 的行为，让它能够迭代一个可迭代对象，从而一次产出一个值：

```js
// 等价的generatorFn：
// function* generatorFn() {
// for (const x of [1, 2, 3]) {
// yield x;
// }
// }
function* generatorFn() {
  yield* [1, 2, 3];
}
let generatorObject = generatorFn();
for (const x of generatorFn()) {
  console.log(x);
}
// 1
// 2
// 3
```

与生成器函数的星号类似，yield 星号两侧的空格不影响其行为：

```js
function* generatorFn() {
  yield* [1, 2];
  yield *[3, 4];
  yield * [5, 6];
}
for (const x of generatorFn()) {
`console.log(x);`
}
// 1
// 2
// 3
// 4
// 5
// 6
```

因为yield*实际上只是将一个可迭代对象序列化为一连串可以单独产出的值，所以这跟把yield放到一个循环里没什么不同。下面两个生成器函数的行为是等价的：

```js
function* generatorFnA() {
  for (const x of [1, 2, 3]) {
    yield x;
  }
}
for (const x of generatorFnA()) {
  console.log(x);
}
// 1
// 2
// 3
function* generatorFnB() {
  yield* [1, 2, 3];
}
for (const x of generatorFnB()) {
  console.log(x);
}
// 1
// 2
// 3
```

yield*的值是关联迭代器返回done: true 时的value 属性。对于普通迭代器来说，这个值是undefined：

```js
function* generatorFn() {
  console.log('iter value:', yield* [1, 2, 3]);
}
for (const x of generatorFn()) {
  console.log('value:', x);
}
// value: 1
// value: 2
// value: 3
// iter value: undefined
```

对于生成器函数产生的迭代器来说，这个值就是生成器函数返回的值：

```js
function* innerGeneratorFn() {
  yield 'foo';
  return 'bar';
}
function* outerGeneratorFn(genObj) {
  console.log('iter value:', yield* innerGeneratorFn());
}
for (const x of outerGeneratorFn()) {
  console.log('value:', x);
}
// value: foo
// iter value: bar
```

4. **使用yield*实现递归算法**

yield*最有用的地方是实现递归操作，此时生成器可以产生自身。看下面的例子：

```js
function* nTimes(n) {
  if (n > 0) {
    yield* nTimes(n - 1);
    yield n - 1;
  }
}
for (const x of nTimes(3)) {
  console.log(x);
}
// 0
// 1
// 2
```

在这个例子中，每个生成器首先都会从新创建的生成器对象产出每个值，然后再产出一个整数。结果就是生成器函数会递归地减少计数器值，并实例化另一个生成器对象。从最顶层来看，这就相当于创建一个可迭代对象并返回递增的整数。

使用递归生成器结构和yield*可以优雅地表达递归算法。下面是一个图的实现，用于生成一个随机的双向图：

```js
class Node {
  constructor(id) {
    this.id = id;
    this.neighbors = new Set();
  }
  connect(node) {
    if (node !== this) {
      this.neighbors.add(node);
      node.neighbors.add(this);
    }
  }
}
class RandomGraph {
  constructor(size) {
    this.nodes = new Set();
    // 创建节点
    for (let i = 0; i < size; ++i) {
      this.nodes.add(new Node(i));
    }
    // 随机连接节点
    const threshold = 1 / size;
    for (const x of this.nodes) {
      for (const y of this.nodes) {
        if (Math.random() < threshold) {
          x.connect(y);
        }
      }
    }
  }
  // 这个方法仅用于调试
  print() {
    for (const node of this.nodes) {
      const ids = [...node.neighbors]
      .map((n) => n.id)
      .join(',');
      console.log(`${node.id}: ${ids}`);
    }
  }
}
const g = new RandomGraph(6);
g.print();
// 示例输出：
// 0: 2,3,5
// 1: 2,3,4,5
// 2: 1,3
// 3: 0,1,2,4
// 4: 2,3
// 5: 0,4
```

图数据结构非常适合递归遍历，而递归生成器恰好非常合用。为此，生成器函数必须接收一个可迭代对象，产出该对象中的每一个值，并且对每个值进行递归。这个实现可以用来测试某个图是否连通，即是否没有不可到达的节点。只要从一个节点开始，然后尽力访问每个节点就可以了。结果就得到了一个非常简洁的深度优先遍历：

```js
class Node {
  constructor(id) {
    ...
  }
  connect(node) {
    ...
  }
}
class RandomGraph {
  constructor(size) {
    ...
  }
  print() {
    ...
  }
  isConnected() {
    const visitedNodes = new Set();
    function* traverse(nodes) {
      for (const node of nodes) {
        if (!visitedNodes.has(node)) {
          yield node;
          yield* traverse(node.neighbors);
        }
      }
    }
    // 取得集合中的第一个节点
    const firstNode = this.nodes[Symbol.iterator]().next().value;
    // 使用递归生成器迭代每个节点
    for (const node of traverse([firstNode])) {
      visitedNodes.add(node);
    }
    return visitedNodes.size === this.nodes.size;
  }
}
```

### 7.3.3. 生成器作为默认迭代器

因为生成器对象实现了Iterable 接口，而且生成器函数和默认迭代器被调用之后都产生迭代器，所以生成器格外适合作为默认迭代器。下面是一个简单的例子，这个类的默认迭代器可以用一行代码产出类的内容：

```js
class Foo {
  constructor() {
    this.values = [1, 2, 3];
  }
  * [Symbol.iterator]() {
    yield* this.values;
  }
}
const f = new Foo();
for (const x of f) {
  console.log(x);
}
// 1
// 2
// 3
```

这里，for-of 循环调用了默认迭代器（它恰好又是一个生成器函数）并产生了一个生成器对象。这个生成器对象是可迭代的，所以完全可以在迭代中使用。

### 7.3.4. 提前终止迭代器

与迭代器类似，生成器也支持“可关闭”的概念。一个实现Iterator 接口的对象一定有next()方法，还有一个可选的return()方法用于提前终止迭代器。生成器对象除了有这两个方法，还有第三个方法：throw()。

```js
function* generatorFn() {}
const g = generatorFn();
console.log(g); // generatorFn {<suspended>}
console.log(g.next); // f next() { [native code] }
console.log(g.return); // f return() { [native code] }
console.log(g.throw); // f throw() { [native code] }
```

return()和throw()方法都可以用于强制生成器进入关闭状态。

1. **return()**

return()方法会强制生成器进入关闭状态。提供给return()方法的值，就是终止迭代器对象的值：

```js
function* generatorFn() {
  for (const x of [1, 2, 3]) {
    yield x;
  }
}
const g = generatorFn();
console.log(g); // generatorFn {<suspended>}
console.log(g.return(4)); // { done: true, value: 4 }
console.log(g); // generatorFn {<closed>}
```

与迭代器不同，所有生成器对象都有return()方法，只要通过它进入关闭状态，就无法恢复了。后续调用next()会显示done: true 状态，而提供的任何返回值都不会被存储或传播：

```js
function* generatorFn() {
  for (const x of [1, 2, 3]) {
    yield x;
  }
}
const g = generatorFn();
console.log(g.next()); // { done: false, value: 1 }
console.log(g.return(4)); // { done: true, value: 4 }
console.log(g.next()); // { done: true, value: undefined }
console.log(g.next()); // { done: true, value: undefined }
console.log(g.next()); // { done: true, value: undefined }
```

for-of 循环等内置语言结构会忽略状态为done: true 的IteratorObject 内部返回的值。

```js
function* generatorFn() {
  for (const x of [1, 2, 3]) {
    yield x;
  }
}
const g = generatorFn();
for (const x of g) {
  if (x > 1) {
    g.return(4);
  }
  console.log(x);
}
// 1
// 2
```

2. **throw()**

throw()方法会在暂停的时候将一个提供的错误注入到生成器对象中。如果错误未被处理，生成器就会关闭：

```js
function* generatorFn() {
  for (const x of [1, 2, 3]) {
    yield x;
  }
}
const g = generatorFn();
console.log(g); // generatorFn {<suspended>}
try {
  g.throw('foo');
} catch (e) {
  console.log(e); // foo
}
console.log(g); // generatorFn {<closed>}
```

不过，假如生成器函数内部处理了这个错误，那么生成器就不会关闭，而且还可以恢复执行。错误处理会跳过对应的yield，因此在这个例子中会跳过一个值。比如：

```js
function* generatorFn() {
  for (const x of [1, 2, 3]) {
    try {
      yield x;
    } catch(e) {}
  }
}
const g = generatorFn();
console.log(g.next()); // { done: false, value: 1}
g.throw('foo');
console.log(g.next()); // { done: false, value: 3}
```

在这个例子中，生成器在try/catch 块中的yield 关键字处暂停执行。在暂停期间，throw()方法向生成器对象内部注入了一个错误：字符串"foo"。这个错误会被yield 关键字抛出。因为错误是在生成器的try/catch 块中抛出的，所以仍然在生成器内部被捕获。可是，由于yield 抛出了那个错误，生成器就不会再产出值2。此时，生成器函数继续执行，在下一次迭代再次遇到yield 关键字时产出了值3。

注意 如果生成器对象还没有开始执行，那么调用throw()抛出的错误不会在函数内部被捕获，因为这相当于在函数块外部抛出了错误。

# 8. 对象、类与面向对象编程

本章内容
- 理解对象
- 理解对象创建过程
- 理解继承
- 理解类

ECMA-262 将对象定义为一组属性的无序集合。严格来说，这意味着对象就是一组没有特定顺序的值。对象的每个属性或方法都由一个名称来标识，这个名称映射到一个值。正因为如此（以及其他还未讨论的原因），可以把ECMAScript 的对象想象成一张散列表，其中的内容就是一组名/值对，值可以是数据或者函数。

## 8.1. 理解对象

创建自定义对象的通常方式是创建Object 的一个新实例，然后再给它添加属性和方法，如下例所示：

```js
let person = new Object();
person.name = "Nicholas";
person.age = 29;
person.job = "Software Engineer";
person.sayName = function() {
  console.log(this.name);
};
```

这个例子创建了一个名为person 的对象，而且有三个属性（name、age 和job）和一个方法（sayName()）。sayName()方法会显示this.name 的值，这个属性会解析为person.name。早期JavaScript 开发者频繁使用这种方式创建新对象。几年后，对象字面量变成了更流行的方式。前面的例子如果使用对象字面量则可以这样写：

```js
let person = {
  name: "Nicholas",
  age: 29,
  job: "Software Engineer",
  sayName() {
    console.log(this.name);
  }
};
```

这个例子中的person 对象跟前面例子中的person 对象是等价的，它们的属性和方法都一样。这些属性都有自己的特征，而这些特征决定了它们在 JavaScript 中的行为。

### 8.1.1. 属性的类型

ECMA-262 使用一些内部特性来描述属性的特征。这些特性是由为JavaScript 实现引擎的规范定义的。因此，开发者不能在JavaScript 中直接访问这些特性。为了将某个特性标识为内部特性，规范会用两个中括号把特性的名称括起来，比如[[Enumerable]]。

属性分两种：数据属性和访问器属性。

1. **数据属性**

数据属性包含一个保存数据值的位置。值会从这个位置读取，也会写入到这个位置。数据属性有4个特性描述它们的行为。

- [[Configurable]]：表示属性是否可以通过 delete 删除并重新定义，是否可以修改它的特性，以及是否可以把它改为访问器属性。默认情况下，所有直接定义在对象上的属性的这个特性都是true，如前面的例子所示。
- [[Enumerable]]：表示属性是否可以通过 for-in 循环返回。默认情况下，所有直接定义在对象上的属性的这个特性都是true，如前面的例子所示。
- [[Writable]]：表示属性的值是否可以被修改。默认情况下，所有直接定义在对象上的属性的这个特性都是true，如前面的例子所示。
- [[Value]]：包含属性实际的值。这就是前面提到的那个读取和写入属性值的位置。这个特性的默认值为 undefined。

在像前面例子中那样将属性显式添加到对象之后，[[Configurable]]、[[Enumerable]]和[[Writable]]都会被设置为true，而[[Value]]特性会被设置为指定的值。比如：

```js
let person = {
  name: "Nicholas"
};
```

这里，我们创建了一个名为name 的属性，并给它赋予了一个值"Nicholas"。这意味着[[Value]]特性会被设置为"Nicholas"，之后对这个值的任何修改都会保存这个位置。

要修改属性的默认特性，就必须使用Object.defineProperty()方法。这个方法接收3 个参数：要给其添加属性的对象、属性的名称和一个描述符对象。最后一个参数，即描述符对象上的属性可以包含：configurable、enumerable、writable 和value，跟相关特性的名称一一对应。根据要修改的特性，可以设置其中一个或多个值。比如：

```js
let person = {};
Object.defineProperty(person, "name", {
  writable: false,
  value: "Nicholas"
});
console.log(person.name); // "Nicholas"
person.name = "Greg";
console.log(person.name); // "Nicholas"
```

这个例子创建了一个名为name 的属性并给它赋予了一个只读的值"Nicholas"。这个属性的值就不能再修改了，在非严格模式下尝试给这个属性重新赋值会被忽略。在严格模式下，尝试修改只读属性的值会抛出错误。

类似的规则也适用于创建不可配置的属性。比如：

```js
let person = {};
Object.defineProperty(person, "name", {
  configurable: false,
  value: "Nicholas"
});
console.log(person.name); // "Nicholas"
delete person.name;
console.log(person.name); // "Nicholas"
```

这个例子把configurable 设置为false，意味着这个属性不能从对象上删除。非严格模式下对这个属性调用delete 没有效果，严格模式下会抛出错误。此外，一个属性被定义为不可配置之后，就不能再变回可配置的了。再次调用Object.defineProperty()并修改任何非writable 属性会导致错误：

```js
let person = {};
Object.defineProperty(person, "name", {
  configurable: false,
  value: "Nicholas"
});
// 抛出错误
Object.defineProperty(person, "name", {
  configurable: true,
  value: "Nicholas"
});
```

因此，虽然可以对同一个属性多次调用Object.defineProperty()，但在把configurable 设置为false 之后就会受限制了。

在调用Object.defineProperty()时，configurable、enumerable 和writable 的值如果不指定，则都默认为false。多数情况下，可能都不需要Object.defineProperty()提供的这些强大的设置，但要理解JavaScript 对象，就要理解这些概念。

2. **访问器属性**

访问器属性不包含数据值。相反，它们包含一个获取（getter）函数和一个设置（setter）函数，不过这两个函数不是必需的。在读取访问器属性时，会调用获取函数，这个函数的责任就是返回一个有效的值。在写入访问器属性时，会调用设置函数并传入新值，这个函数必须决定对数据做出什么修改。访问器属性有4 个特性描述它们的行为。

- [[Configurable]]：表示属性是否可以通过delete 删除并重新定义，是否可以修改它的特性，以及是否可以把它改为数据属性。默认情况下，所有直接定义在对象上的属性的这个特性都是true。
- [[Enumerable]]：表示属性是否可以通过for-in 循环返回。默认情况下，所有直接定义在对象上的属性的这个特性都是true。
- [[Get]]：获取函数，在读取属性时调用。默认值为undefined。
- [[Set]]：设置函数，在写入属性时调用。默认值为undefined。

访问器属性是不能直接定义的，必须使用Object.defineProperty()。下面是一个例子：

```js
// 定义一个对象，包含伪私有成员year_和公共成员edition
let book = {
  year_: 2017,
  edition: 1
};
Object.defineProperty(book, "year", {
  get() {
    return this.year_;
  },
  set(newValue) {
    if (newValue > 2017) {
      this.year_ = newValue;
      this.edition += newValue - 2017;
    }
  }
});
book.year = 2018;
console.log(book.edition); // 2
```

在这个例子中，对象book 有两个默认属性：year_和edition。year_中的下划线常用来表示该属性并不希望在对象方法的外部被访问。另一个属性year 被定义为一个访问器属性，其中获取函数简单地返回year_的值，而设置函数会做一些计算以决定正确的版本（edition）。因此，把year 属性修改为2018 会导致year_变成2018，edition 变成2。这是访问器属性的典型使用场景，即设置一个属性值会导致一些其他变化发生。

获取函数和设置函数不一定都要定义。只定义获取函数意味着属性是只读的，尝试修改属性会被忽略。在严格模式下，尝试写入只定义了获取函数的属性会抛出错误。类似地，只有一个设置函数的属性是不能读取的，非严格模式下读取会返回undefined，严格模式下会抛出错误。

在不支持Object.defineProperty()的浏览器中没有办法修改[[Configurable]]或[[Enumerable]]。

注意 在ECMAScript 5 以前，开发者会使用两个非标准的访问创建访问器属性：__defineGetter__()和__defineSetter__()。这两个方法最早是Firefox 引入的，后来Safari、Chrome 和Opera 也实现了。

### 8.1.2. 定义多个属性

在一个对象上同时定义多个属性的可能性是非常大的。为此，ECMAScript 提供了Object.defineProperties()方法。这个方法可以通过多个描述符一次性定义多个属性。它接收两个参数：要为之添加或修改属性的对象和另一个描述符对象，其属性与要添加或修改的属性一一对应。比如：

```js
let book = {};
Object.defineProperties(book, {
  year_: {
    value: 2017
  },
  edition: {
    value: 1
  },
  year: {
    get() {
      return this.year_;
    },
    set(newValue) {
      if (newValue > 2017) {
        this.year_ = newValue;
        this.edition += newValue - 2017;
      }
    }
  }
});
```

这段代码在book 对象上定义了两个数据属性year_和edition，还有一个访问器属性year。最终的对象跟上一节示例中的一样。唯一的区别是所有属性都是同时定义的，并且数据属性的configurable、enumerable 和writable 特性值都是false。

### 8.1.3. 读取属性的特性

使用Object.getOwnPropertyDescriptor()方法可以取得指定属性的属性描述符。这个方法接收两个参数：属性所在的对象和要取得其描述符的属性名。返回值是一个对象，对于访问器属性包含configurable、enumerable、get 和set 属性，对于数据属性包含configurable、enumerable、writable 和value 属性。比如：

```js
let book = {};
Object.defineProperties(book, {
  year_: {
    value: 2017
  },
  edition: {
    value: 1
  },
  year: {
  get: function() {
    return this.year_;
  },
  set: function(newValue){
    if (newValue > 2017) {
      this.year_ = newValue;
      this.edition += newValue - 2017;
    }
  }
  }
});
let descriptor = Object.getOwnPropertyDescriptor(book, "year_");
console.log(descriptor.value); // 2017
console.log(descriptor.configurable); // false
console.log(typeof descriptor.get); // "undefined"
let descriptor = Object.getOwnPropertyDescriptor(book, "year");
console.log(descriptor.value); // undefined
console.log(descriptor.enumerable); // false
console.log(typeof descriptor.get); // "function"
```

对于数据属性year_，value 等于原来的值，configurable 是false，get 是undefined。对于访问器属性year，value 是undefined，enumerable 是false，get 是一个指向获取函数的指针。

ECMAScript 2017 新增了Object.getOwnPropertyDescriptors()静态方法。这个方法实际上会在每个自有属性上调用Object.getOwnPropertyDescriptor()并在一个新对象中返回它们。对于前面的例子，使用这个静态方法会返回如下对象：

```js
let book = {};
Object.defineProperties(book, {
  year_: {
    value: 2017
  },
  edition: {
    value: 1
  },
  year: {
    get: function() {
      return this.year_;
    },
    set: function(newValue){
      if (newValue > 2017) {
        this.year_ = newValue;
        this.edition += newValue - 2017;
      }
    }
  }
});
console.log(Object.getOwnPropertyDescriptors(book));
// {
// edition: {
// configurable: false,
// enumerable: false,
// value: 1,
// writable: false
// },
// year: {
// configurable: false,
// enumerable: false,
// get: f(),
// set: f(newValue),
// },
// year_: {
// configurable: false,
// enumerable: false,
// value: 2017,
// writable: false
// }
// }
```

### 8.1.4. 合并对象

JavaScript 开发者经常觉得“合并”（merge）两个对象很有用。更具体地说，就是把源对象所有的本地属性一起复制到目标对象上。有时候这种操作也被称为“混入”（mixin），因为目标对象通过混入源对象的属性得到了增强。

ECMAScript 6 专门为合并对象提供了Object.assign()方法。这个方法接收一个目标对象和一个或多个源对象作为参数，然后将每个源对象中可枚举（Object.propertyIsEnumerable()返回true）和自有（Object.hasOwnProperty()返回true）属性复制到目标对象。以字符串和符号为键的属性会被复制。对每个符合条件的属性，这个方法会使用源对象上的[[Get]]取得属性的值，然后使用目标对象上的[[Set]]设置属性的值。

```js
let dest, src, result;
/**
* 简单复制
*/
dest = {};
src = { id: 'src' };
result = Object.assign(dest, src);
// Object.assign 修改目标对象
// 也会返回修改后的目标对象
console.log(dest === result); // true
console.log(dest !== src); // true
console.log(result); // { id: src }
console.log(dest); // { id: src }
/**
* 多个源对象
*/
dest = {};
result = Object.assign(dest, { a: 'foo' }, { b: 'bar' });
console.log(result); // { a: foo, b: bar }
/**
* 获取函数与设置函数
*/
dest = {
  set a(val) {
    console.log(`Invoked dest setter with param ${val}`);
  }
};
src = {
  get a() {
    console.log('Invoked src getter');
    return 'foo';
  }
};
Object.assign(dest, src);
// 调用src 的获取方法
// 调用dest 的设置方法并传入参数"foo"
// 因为这里的设置函数不执行赋值操作
// 所以实际上并没有把值转移过来
console.log(dest); // { set a(val) {...} }
```

Object.assign()实际上对每个源对象执行的是浅复制。如果多个源对象都有相同的属性，则使用最后一个复制的值。此外，从源对象访问器属性取得的值，比如获取函数，会作为一个静态值赋给目标对象。换句话说，不能在两个对象间转移获取函数和设置函数。

```js
let dest, src, result;
/**
* 覆盖属性
*/
dest = { id: 'dest' };
result = Object.assign(dest, { id: 'src1', a: 'foo' }, { id: 'src2', b: 'bar' });
// Object.assign 会覆盖重复的属性
console.log(result); // { id: src2, a: foo, b: bar }
// 可以通过目标对象上的设置函数观察到覆盖的过程：
dest = {
  set id(x) {
      console.log(x);
  }
};
Object.assign(dest, { id: 'first' }, { id: 'second' }, { id: 'third' });
// first
// second
// third
/**
* 对象引用
*/
dest = {};
src = { a: {} };
Object.assign(dest, src);
// 浅复制意味着只会复制对象的引用
console.log(dest); // { a :{} }
console.log(dest.a === src.a); // true
```

如果赋值期间出错，则操作会中止并退出，同时抛出错误。Object.assign()没有“回滚”之前赋值的概念，因此它是一个尽力而为、可能只会完成部分复制的方法。

```js
let dest, src, result;
/**
* 错误处理
*/
dest = {};
src = {
a: 'foo',
  get b() {
    // Object.assign()在调用这个获取函数时会抛出错误
    throw new Error();
  },
  c: 'bar'
};
try {
  Object.assign(dest, src);
} catch(e) {}
// Object.assign()没办法回滚已经完成的修改
// 因此在抛出错误之前，目标对象上已经完成的修改会继续存在：
console.log(dest); // { a: foo }
```

### 8.1.5. 对象标识及相等判定

在ECMAScript 6 之前，有些特殊情况即使是===操作符也无能为力：

```js
// 这些是===符合预期的情况
console.log(true === 1); // false
console.log({} === {}); // false
console.log("2" === 2); // false
// 这些情况在不同JavaScript 引擎中表现不同，但仍被认为相等
console.log(+0 === -0); // true
console.log(+0 === 0); // true
console.log(-0 === 0); // true
// 要确定NaN 的相等性，必须使用极为讨厌的Number.isNaN()
console.log(NaN === NaN); // false
console.log(Number.isNaN(NaN)); // true
```

为改善这类情况，ECMAScript 6 规范新增了Object.is()，这个方法与===很像，但同时也考虑到了上述边界情形。这个方法必须接收两个参数：

```js
console.log(Object.is(true, 1)); // false
console.log(Object.is({}, {})); // false
console.log(Object.is("2", 2)); // false
// 正确的0、-0、+0 相等/不等判定
console.log(Object.is(+0, -0)); // false
console.log(Object.is(+0, 0)); // true
console.log(Object.is(-0, 0)); // false
// 正确的NaN 相等判定
console.log(Object.is(NaN, NaN)); // true
```

要检查超过两个值，递归地利用相等性传递即可：

```js
function recursivelyCheckEqual(x, ...rest) {
  return Object.is(x, rest[0]) &&
  (rest.length < 2 || recursivelyCheckEqual(...rest));
}
```

### 8.1.6. 增强的对象语法

ECMAScript 6 为定义和操作对象新增了很多极其有用的语法糖特性。这些特性都没有改变现有引擎的行为，但极大地提升了处理对象的方便程度。

本节介绍的所有对象语法同样适用于ECMAScript 6 的类，本章后面会讨论。

注意 相比于以往的替代方案，本节介绍的增强对象语法可以说是一骑绝尘。因此本章及本书会默认使用这些新语法特性。

1. **属性值简写**

在给对象添加变量的时候，开发者经常会发现属性名和变量名是一样的。例如：

```js
let name = 'Matt';
let person = {
  name: name
};
console.log(person); // { name: 'Matt' }
```

为此，简写属性名语法出现了。简写属性名只要使用变量名（不用再写冒号）就会自动被解释为同名的属性键。如果没有找到同名变量，则会抛出ReferenceError。

以下代码和之前的代码是等价的：

```js
let name = 'Matt';
let person = {
  name
};
console.log(person); // { name: 'Matt' }
```

代码压缩程序会在不同作用域间保留属性名，以防止找不到引用。以下面的代码为例：

```js
function makePerson(name) {
  return {
    name
  };
}
let person = makePerson('Matt');
console.log(person.name); // Matt
```

在这里，即使参数标识符只限定于函数作用域，编译器也会保留初始的name 标识符。如果使用Google Closure 编译器压缩，那么函数参数会被缩短，而属性名不变：

```js
function makePerson(a) {
  return {
    name: a
  };
}
var person = makePerson("Matt");
console.log(person.name); // Matt
```

2. **可计算属性**

在引入可计算属性之前，如果想使用变量的值作为属性，那么必须先声明对象，然后使用中括号语法来添加属性。换句话说，不能在对象字面量中直接动态命名属性。比如：

```js
const nameKey = 'name';
const ageKey = 'age';
const jobKey = 'job';
let person = {};
person[nameKey] = 'Matt';
person[ageKey] = 27;
person[jobKey] = 'Software engineer';
console.log(person); // { name: 'Matt', age: 27, job: 'Software engineer' }
```

有了可计算属性，就可以在对象字面量中完成动态属性赋值。中括号包围的对象属性键告诉运行时将其作为JavaScript 表达式而不是字符串来求值：

```js
const nameKey = 'name';
const ageKey = 'age';
const jobKey = 'job';
let person = {
  [nameKey]: 'Matt',
  [ageKey]: 27,
  [jobKey]: 'Software engineer'
};
console.log(person); // { name: 'Matt', age: 27, job: 'Software engineer' }
```

因为被当作JavaScript 表达式求值，所以可计算属性本身可以是复杂的表达式，在实例化时再求值：

```js
const nameKey = 'name';
const ageKey = 'age';
const jobKey = 'job';
let uniqueToken = 0;
function getUniqueKey(key) {
  return `${key}_${uniqueToken++}`;
}
let person = {
[getUniqueKey(nameKey)]: 'Matt',
[getUniqueKey(ageKey)]: 27,
[getUniqueKey(jobKey)]: 'Software engineer'
};
console.log(person); // { name_0: 'Matt', age_1: 27, job_2: 'Software engineer' }
```

注意 可计算属性表达式中抛出任何错误都会中断对象创建。如果计算属性的表达式有副作用，那就要小心了，因为如果表达式抛出错误，那么之前完成的计算是不能回滚的。

3. **简写方法名**

在给对象定义方法时，通常都要写一个方法名、冒号，然后再引用一个匿名函数表达式，如下所示：

```js
let person = {
  sayName: function(name) {
    console.log(`My name is ${name}`);
  }
};
person.sayName('Matt'); // My name is Matt
```

新的简写方法的语法遵循同样的模式，但开发者要放弃给函数表达式命名（不过给作为方法的函数命名通常没什么用）。相应地，这样也可以明显缩短方法声明。

以下代码和之前的代码在行为上是等价的：

```js
let person = {
  sayName(name) {
    console.log(`My name is ${name}`);
  }
};
person.sayName('Matt'); // My name is Matt
```

简写方法名对获取函数和设置函数也是适用的：

```js
let person = {
  name_: '',
  get name() {
    return this.name_;
  },
  set name(name) {
    this.name_ = name;
  },
  sayName() {
    console.log(`My name is ${this.name_}`);
  }
};
person.name = 'Matt';
person.sayName(); // My name is Matt
```

简写方法名与可计算属性键相互兼容：

```js
const methodKey = 'sayName';
let person = {
  [methodKey](name) {
    console.log(`My name is ${name}`);
  }
}
person.sayName('Matt'); // My name is Matt
```

注意 简写方法名对于本章后面介绍的ECMAScript 6 的类更有用。

### 8.1.7. 对象解构

ECMAScript 6 新增了对象解构语法，可以在一条语句中使用嵌套数据实现一个或多个赋值操作。简单地说，对象解构就是使用与对象匹配的结构来实现对象属性赋值。

下面的例子展示了两段等价的代码，首先是不使用对象解构的：

```js
// 不使用对象解构
let person = {
  name: 'Matt',
  age: 27
};
let personName = person.name,
    personAge = person.age;
console.log(personName); // Matt
console.log(personAge); // 27
```

然后，是使用对象解构的：

```js
// 使用对象解构
let person = {
  name: 'Matt',
  age: 27
};
let { name: personName, age: personAge } = person;
console.log(personName); // Matt
console.log(personAge); // 27
```

使用解构，可以在一个类似对象字面量的结构中，声明多个变量，同时执行多个赋值操作。如果想让变量直接使用属性的名称，那么可以使用简写语法，比如：

```js
let person = {
name: 'Matt',
age: 27
};
let { name, age } = person;
console.log(name); // Matt
console.log(age); // 27
```

解构赋值不一定与对象的属性匹配。赋值的时候可以忽略某些属性，而如果引用的属性不存在，则该变量的值就是undefined：

```js
let person = {
  name: 'Matt',
  age: 27
};
let { name, job } = person;
console.log(name); // Matt
console.log(job); // undefined
```

也可以在解构赋值的同时定义默认值，这适用于前面刚提到的引用的属性不存在于源对象中的情况：

```js
let person = {
  name: 'Matt',
  age: 27
};
let { name, job='Software engineer' } = person;
console.log(name); // Matt
console.log(job); // Software engineer
```

解构在内部使用函数ToObject()（不能在运行时环境中直接访问）把源数据结构转换为对象。这意味着在对象解构的上下文中，原始值会被当成对象。这也意味着（根据ToObject()的定义），null和undefined 不能被解构，否则会抛出错误。

```js
let { length } = 'foobar';
console.log(length); // 6
let { constructor: c } = 4;
console.log(c === Number); // true
let { _ } = null; // TypeError
let { _ } = undefined; // TypeError
```

解构并不要求变量必须在解构表达式中声明。不过，如果是给事先声明的变量赋值，则赋值表达式必须包含在一对括号中：

```js
let personName, personAge;
let person = {
  name: 'Matt',
  age: 27
};
({name: personName, age: personAge} = person);
console.log(personName, personAge); // Matt, 27
```

