在 JavaScript 中，this 的值取决于多种因素。本篇文章详细地解释了 this 的各种行为。

## 1. 全局上下文

this 在全局上下文中，即在任何函数体的外部时，都指向全局对象，在浏览器宿主环境中就是 window。

来看下面的例子：

```js
let o1 = {
  this: this,
  o2: {
    this: [this],
  },
};

console.log(o1.this === window); // true
console.log(o1.o2.this[0] === window); // true
```

在这个例子中，对象 o1 的 this 属性引用 this 值，而这个 this 值在全局上下文中指向 window。同样的，o2 的 this 值引用一个数组对象，这个数组的第一个元素为 this，但无论如何 this 值都在全局上下文中，所以都指向 window。

## 2. 标准函数上下文

this 出现在标准函数上下文中，此时的 this 取决于函数调用的方式。

1. 在非严格模式下直接调用标准函数，则其内部的 this 指向全局对象。

来看下面几个例子：

```js
function getThis() {
  return this;
}
console.log(getThis() === window); // true
```

在这个例子中，getThis 是一个函数声明，它返回内部的 this 值。之后在全局上下文中直接调用了 getThis，它返回了全局对象。

非严格模式下直接调用标准函数，其内部的 this 值指向全局对象，而不论调用的上下文：

```js
function foo() {
  function getThis() {
    console.log(this === window); // true
  }
  getThis();
}
foo();
```

在这个例子中，getThis 在函数 foo 的上下文中直接调用，但不论是在全局上下文还是函数上下文中，非严格模式下直接调用标准函数，其内部的 this 都指向全局对象。

2. 严格模式下直接调用标准函数，则其内部的 this 为 undefined。

来看下面几个例子：

```js
function getThisInStrict() {
  "use strict";
  return this;
}
console.log(getThisInStrict() === window); // false
console.log(getThisInStrict() === undefined); // true
```

在这个例子中，函数 getThisInStrict 的作用域内使用了严格模式。之后，在全局上下文中调用了 getThisInStrict，它内部的 this 为 undefined 而不是全局对象。

同样的，严格模式下直接调用标准函数，其内部的 this 为 undefined，而不论调用的上下文。

3. 标准函数作为方法调用时，this 指向直接调用者，而非间接调用者。

来看下面几个例子：

```js
function getThis() {
  return this;
}

let o = {
  name: "o",
};

o.getThis = getThis;
console.log(o.getThis().name); // o
```

在这个例子中，getThis 作为 o 的方法在全局上下文中调用。getThis 内部的 this 指向 o。

这个规则不受严格模式和调用方法时的上下文影响：

```js
"use strict";

function getThis() {
  return this;
}

function foo() {
  const o = {
    name: "o",
  };
  o.getThis = getThis;
  console.log(o.getThis().name); // o
}
foo();
```

在这个例子中，全局使用了严格模式。之后在函数 foo 上下文中，getThis 作为 o 的方法被调用。其内部的 this 指向 o。

复杂的情况是通过间接方式调用函数：

```js
function getThis() {
  return this;
}

console.log(getThis.prototype.constructor === getThis); // true
console.log(getThis.prototype.constructor() === getThis.prototype); // true

let constructor = getThis.prototype.constructor;
console.log(constructor() === window); // true
```

在这个例子中，getThis.prototype.constructor 返回 getThis 函数对象本身。在执行 getThis.prototype.constructor()时，getThis 的直接调用者为 getThis.prototype，因此 this 指向 getThis.prototype。之后，将 getThis.prototype.constructor 赋给 constructor，并直接调用，因此 this 指向全局对象。

4. 标准函数作为构造函数调用，this 指向正在构建的对象：

```js
function Person() {
  this.name = "Nicholas";
  console.log(this instanceof Person); // true
}
new Person();
```

在这个例子中，Person 作为构造方法调用，this 指向被构建的对象，因此 `this instanceOf Person` 为 true。

## 3. 箭头函数

箭头函数的 this 行为和标准函数的截然不同。

1. 箭头函数在全局上下文中，则其 this 绑定全局对象，且严格模式和方法调用对该 this 没有影响。

来看下面几个例子：

```js
const getThisInArrowFunc = () => {
  "use strict";
  return this;
};

console.log(getThisInArrowFunc() === window); // true
```

在这个例子中，getThisInArrowFunc 位于全局上下文，其内部使用了严格模式，但这不影响 this 的值。this 依旧绑定全局对象。

```js
var name = "window";
const o1 = {
  name: "o1",
  o2: {
    name: "o2",
    getThis: () => this,
  },
};
console.log(o1.o2.getThis().name); // window
```

在这个例子中，getThis 作为 o2 的方法被 o1 间接在全局上下文中调用，但不论是否作为方法被调用，getThis 都在全局上下文中，因此其内部的 this 还是绑定全局对象。

2. 箭头函数在函数上下文中，则其 this 绑定紧邻的外层函数的 this。

```js
var name = "window";
function foo() {
  const o1 = {
    name: "o1",
    o2: {
      name: "o2",
      getThis: () => this,
    },
  };
  console.log(o1.o2.getThis().name); // window
}
foo();
```

在这个例子中，箭头函数 getThis 在 foo 函数的上下文中。这里 foo 在非严格模式下直接调用，所以函数 foo 的 this 指向全局对象，箭头函数绑定了该值。

当然，如过外层的函数 foo 以方法调用，则该箭头函数内部的 this 就绑定 foo 的直接调用者。

有读者知道，在事件回调或定时回调中调用某个函数时，this 值指向的并非想要的对象。此时将回调函数写成箭头函数就可以解决问题：

```js
function King() {
  this.royaltyName = "Henry";
  // this 引用King 的实例
  setTimeout(() => console.log(this.royaltyName), 1000);
}
function Queen() {
  this.royaltyName = "Elizabeth";
  // this 引用window 对象
  setTimeout(function () {
    console.log(this.royaltyName);
  }, 1000);
}
new King(); // Henry
new Queen(); // undefined
```
