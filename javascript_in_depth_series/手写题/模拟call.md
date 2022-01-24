## 1. call 简介

Function.prototype.call(thisArg, ...args) 用于强行指定一个函数调用时的内部 this 值。call 方法的第 1 个参数就是指定的 this 值。其余参数则是函数本来需要的参数。

```javascript
var id = 'window';
const obj = {id: 'obj'};

function showId() {
  console.log(this.id);
}

showId();
// -> 'window'

showId.call(obj);
// -> 'obj'
```

## 2. thisArg

很多人忽略的一点便是 thisArg。thisArg 在严格模式和非严格模式是由区别的。

在非严格模式下，如果传入的 thisArg 为 undefined 或 null，则实际使用的 thisArg 为 global 对象。

```javascript
var id = 'window';

function showThis() {
  console.log(this.id);
}

showThis.call(undefined);
// -> 'window'

showThis.call(null);
// -> 'window'
```

如果传入的 thisArg 为其余原始值，则为对应的包装类型。

```javascript
function showThis() {
  console.log(Object.prototype.toString.call(this).slice(8, -1));
}

showThis.call(true);
// -> 'Boolean'

showThis.call('');
// -> 'String'

showThis.call(0);
// -> 'Number'

showThis.call(Symbol());
// -> 'Symbol'
```

如果传入的 thisArg 为引用值，则不做改变。

在严格模式下，传入的 thisArg 就是最终值。

## 3. 模拟

```javascript
// 只能完整模拟非严格模式
Function.prototype.myCall = function (thisArg, ...args) {
  if (typeof thisArg === 'object' && thisArg !== null) {
    // thisArg 为引用值
    const sym = Symbol();
    thisArg[sym] = this;
    try {
      return thisArg[sym]();
    } finally {
      delete thisArg[sym];
    }
  } else if (thisArg === undefined || thisArg === null) {
    // thisArg 为 undefined 或 null
    return this();
  } else {
    // thisArg 为其他原始值
    const typeOfThisArg = typeof thisArg;
    let wrapper = null;

    switch (typeOfThisArg) {
      case 'boolean':
        wrapper = new Boolean(thisArg);
        break;

      case 'number':
        wrapper = new Number(thisArg);
        break;

      case 'string':
        wrapper = new String(thisArg);
        break;

      default:
        break;
    }

    const sym = Symbol();
    wrapper[sym] = this;
    return wrapper[sym]();
  }
};
```
