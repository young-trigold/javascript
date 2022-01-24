JavaScript 是动态类型的语言，所以经常有判断值类型的需求。本文循规蹈矩地详细介绍了各种判断类型的方法。

## 1. typeof

typeof 操作符是开发者最为熟悉的方法。typeof 主要用于原始值类型的判断，因为 typeof 对于引用值（还有 null）都返回 'object' 字符串。

typeof 的返回值情况如下表所示：

| 操作数类型   | 返回结果    |
| ------------ | ----------- |
| Undefined    | 'undefined' |
| Null         | 'object'    |
| Boolean      | 'boolean'   |
| Number       | 'number'    |
| String       | 'string'    |
| Symbol       | 'symbol'    |
| Function     | 'function'  |
| 其他引用类型 | 'object'    |

代码及输出结果如下所示：

```js
var types = [undefined, null, false, 0, '', Symbol(), () => {}, {}].map(
  function (ele) {
    return typeof ele;
  },
);

console.log.apply(this, types);
// 'undefined' 'object' 'boolean' 'number' 'string' 'symbol' 'function' 'object'
```

值得注意的是，函数可以用 typeof 识别。

到这里，我们可以使用 typeof 操作符编写第 1 版的类型判断函数：

```js
var getType = function (any) {
  if (any === null) {
    return 'null';
  }

  return typeof any;
};
```

typeof 的局限性在于对于引用值，typeof 不能给出具体的类型。

## 2. 利用原型判断

instanceof 操作符用以判断一个值的原型链上具有的原型。instanceof 操作符主要用于判断使用构造函数创建的引用值。

如下所示：

```js
var object = new Object();

console.log(object instanceof Object);
// 'true'
```

由于所有的引用类型的顶层原型都是 Object.prototype，因此所有引用值都是 Object 的实例。如下所示：

```js
var date = new Date();

console.log(date instanceof Object);
// 'true'
```

尽管如此，我们还是可以做一个“过滤网”，将 Object 放在过滤网的底部，这样便可以判断所有使用构造函数创建的值的类型。不过，大可不必这么麻烦，我们也可以使用 Object.getPrototypeOf() 以同样的原理，直接获取该引用值的原型。

第 2 版的类型判断函数如下所示：

```js
var getType = function (any) {
  if (any === null) {
    return 'null';
  } else if (typeof any === 'object') {
    return Object.getPrototypeOf(any).varructor.name;
  } else {
    return typeof any;
  }
};
```

至此，我们已经可以判断出原始值以及使用构造函数创建的引用值的类型。

## 3. Object.prototype.toString

Object.prototype.toString() 方法直接在值上调用时，会返回 '[object type]'，其中 type 是由 JavaScript 引擎识别的。这个方法主要用于识别一些特殊的内置对象。不过也可以识别使用构造函数创建的引用值。

如下所示：

```js
var getType = function (any) {
  return Object.prototype.toString.call(any).slice(8, -1);
};

var windowType = getType(this);
console.log(windowType);
// 'Window'

var mathType = getType(Math);
console.log(mathType);
// 'Math'

var mapType = getType(new Map());
console.log(mapType);
// 'Map'
```

由此，我们可以写出第 3 版的类型判断函数：

```js
var getType = function (any) {
  if (any === null) {
    return 'null';
  } else if (typeof any === 'object') {
    return Object.prototype.toString.call(any).slice(8, -1);
  } else {
    return typeof any;
  }
};
```
