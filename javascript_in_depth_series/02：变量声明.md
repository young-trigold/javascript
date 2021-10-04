**目录：**
- [1. var](#1-var)
- [2. let](#2-let)
- [3. const](#3-const)
- [4. 声明风格与最佳实践](#4-声明风格与最佳实践)

ECMAScript 变量是松散类型的，意思是变量可以用于保存任何类型的数据。每个变量只不过是一个用于保存任意值的命名占位符。有 3 个关键字可以声明变量：var、const 和 let。其中，var 在 ECMAScript 的所有版本中都可以使用，而 const 和 let 只能在 ECMAScript 6 及更晚的版本中使用。

## 1. var

要定义变量，可以使用 var 操作符（注意 var 是一个关键字），后跟变量名（即标识符，如前所述）：

```javascript
var message;
```

这行代码定义了一个名为 message 的变量，可以用它保存任何类型的值。（不初始化的情况下，变量会保存一个特殊值 undefined，下一节讨论数据类型时会谈到。）ECMAScript 实现变量初始化，因此可以同时定义变量并设置它的值：

```javascript
var message = 'hi';
```

这里，message 被定义为一个保存字符串值 hi 的变量。像这样初始化变量不会将它标识为字符串类型，只是一个简单的赋值而已。随后，不仅可以改变保存的值，也可以改变值的类型：

```javascript
var message = 'hi';

// 合法，但不推荐
message = 100;
```

在这个例子中，变量 message 首先被定义为一个保存字符串值 hi 的变量，然后又被重写为保存了数值 100。虽然不推荐改变变量保存值的类型，但这在 ECMAScript 中是完全有效的。

1. **函数作用域**

关键的问题在于，使用 var 操作符定义的变量会成为包含它的函数的局部变量。比如，使用 var 在一个函数内部定义一个变量，就意味着该变量将在函数退出时被销毁：

```javascript
const foo = function () {
  // 局部变量
  var message = 'hi';
};

foo();

// ReferenceError: message is not defined
console.log(message);
```

这里，message 变量是在函数内部使用 var 定义的。函数叫 test()，调用它会创建这个变量并给它赋值。调用之后变量随即被销毁，因此示例中的最后一行会导致错误。不过，在函数内定义变量时省略 var 操作符，可以创建一个全局变量：

```javascript
const foo = function () {
  // 全局变量
  message = 'hi';
};

foo();

// 'hi'
console.log(message);
```

去掉之前的 var 操作符之后，message 就变成了全局变量。只要调用一次函数 test()，就会定义这个变量，并且可以在函数外部访问到。

虽然可以通过省略 var 操作符定义全局变量，但不推荐这么做。在局部作用域中定义的全局变量很难维护，也会造成困惑。这是因为不能一下子断定省略 var 是不是有意而为之。在严格模式下，如果像这样给未声明的变量赋值，则会导致抛出 ReferenceError。

如果需要定义多个变量，可以在一条语句中用逗号分隔每个变量（及可选的初始化）：

```javascript
var message = 'hi',
  found = false,
  age = 29;
```

这里定义并初始化了 3 个变量。因为 ECMAScript 是松散类型的，所以使用不同数据类型初始化的变量可以用一条语句来声明。插入换行和空格缩进并不是必需的，但这样有利于阅读理解。

在严格模式下，不能定义名为 eval 和 arguments 的变量，否则会导致语法错误。

2. **声明提升**

使用 var 时，下面的代码不会报错。这是因为使用这个关键字声明的变量会自动提升到函数作用域顶部：

```javascript
const foo = function () {
  console.log(age);
  var age = 26;
};

// undefined
foo();
```

之所以不会报错，是因为 ECMAScript 运行时把它看成等价于如下代码：

```javascript
const foo = function () {
  var age;
  console.log(age);
  age = 26;
};

// undefined
foo();
```

这就是所谓的“提升”（hoist），也就是把所有变量声明都拉到函数作用域的顶部。

3. **重复声明**

此外，反复多次使用 var 声明同一个变量也不会报错：

```javascript
const foo = function () {
  var age = 16;
  var age = 26;
  var age = 36;
  console.log(age);
};

// 36
foo();
```

这是因为，由于 var 声明提升，所有的 age 变量会被提升至函数作用域顶部，之后合并相同的变量声明，以上代码实际上等价于：

```javascript
const foo = function () {
  var age;
  age = 16;
  age = 26;
  age = 36;
  console.log(age);
};

// 36
foo();
```

再来看一个例子：

```javascript
const foo = function () {
  var age = 16;
  var age;
  var age = 26;
  var age;
  var age = 36;
  console.log(age);
};

// 36
foo();
```

以上代码实际和上一个例子是等同的。

## 2. let

let 跟 var 的作用差不多，但有着非常重要的区别。最明显的区别是，let 声明的范围是块级作用域，而 var 声明的范围是函数作用域。

```javascript
{
  var name = 'Matt';

  // 'Matt'
  console.log(name);
}

// 'Matt'
console.log(name);

{
  let age = 26;

  // 26
  console.log(age);
}

// ReferenceError: age is not defined
console.log(age);
```

在这里，age 变量之所以不能在 if 块外部被引用，是因为它的作用域仅限于该块内部。块作用域是函数作用域的子集，因此适用于 var 的作用域限制同样也适用于 let。

let 也不允许同一个块作用域中出现冗余声明。这样会导致报错：

```javascript
var age;
var age;
let age;

// SyntaxError: Identifier 'age' has already been declared
let age;
```

当然，JavaScript 引擎会记录用于变量声明的标识符及其所在的块作用域，因此嵌套使用相同的标识符不会报错，而这是因为同一个块中没有重复声明：

```javascript
var name = 'Nicholas';

// 'Nicholas'
console.log(name);

if (true) {
  var name = 'Matt';

  // 'Matt'
  console.log(name);
}

let age = 30;

// 30
console.log(age);

if (true) {
  let age = 26;

  // 26
  console.log(age);
}
```

对声明冗余报错不会因混用 let 和 var 而受影响。这两个关键字声明的并不是不同类型的变量，它们只是指出变量的作用域。

```javascript
if (true) {
  var name;
}

// SyntaxError: Identifier 'name' has already been declared
let name;
```

let 与 var 的另一个重要的区别，就是 let 声明的变量不会在作用域中被提升。

```javascript
// name 会被提升
// undefined
console.log(name);
var name = 'Matt';

// age 不会被提升
// ReferenceError: Cannot access 'age' before initialization
console.log(age);
let age = 26;
```

1. **暂时性死区**

ES6 规定，只要在一个块级作用域中存在 let 声明之前就访问该变量，就会报错，而不论这个变量是否在外层作用域中已经声明。let 变量声明和声明前使用该变量的语句之间形成的区域称为 **暂时性死区(temporal dead zone, TDZ)**。

来看下面的例子：

```javascript
let foo = 'foo';

{
  // 'foo'
  console.log(foo);
}
```

在这个例子中，变量 foo 已经在块作用域外声明过，因此在块作用域中可以访问 foo。但是如果在输出语句下面放上一个相同标识符的 let 变量声明，就会报错：

```javascript
let foo = 'foo';

{
  // ReferenceError: Cannot access 'foo' before initialization
  console.log(foo);
  let foo;
}
```

尽管这看起来有些愚蠢，但这样规定的目的就是防止开发者在声明之前就访问变量。

暂时性死区内代码不会得到执行：

```javascript
let foo = 'foo';

{
  // TDZ 开始
  // ReferenceError: Cannot access 'foo' before initialization
  console.log(foo);
  console.log(bar);
  let bar = 'bar';

  // TDZ结束
  let foo;
}
```

“暂时性死区” 也意味着 typeof 不再是一个百分之百安全的操作：

```javascript
// OK
// undefined
console.log(typeof something);

// ReferenceError: Cannot access 'otherthing' before initialization
console.log(typeof otherthing);
let otherthing;
```

在没有 let 之前，typeof 运算符是百分之百安全的，永远不会报错。现在这一点也不成立了。

2. **全局声明**

与 var 关键字不同，使用 let 在全局作用域中声明的变量不会成为 window 对象的属性（var 声明的变量则会）。

```javascript
var name = 'Matt';

// 'Matt'
console.log(window.name);

let age = 26;

// undefined
console.log(window.age);
```

不过，let 声明仍然是在全局作用域中发生的，相应变量会在页面的生命周期内存续。因此，为了避免 SyntaxError，必须确保页面不会重复声明同一个变量。

3. **条件声明**

在使用 var 声明变量时，由于声明会被提升，JavaScript 引擎会自动将多余的声明在作用域顶部合并为一个声明。因为 let 的作用域是块，所以不可能检查前面是否已经使用 let 声明过同名变量，同时也就不可能在没有声明的情况下声明它。

```html
<script>
  var name = 'Nicholas';
  let age = 26;
</script>

<script>
  // 假设脚本不确定页面中是否已经声明了同名变量
  // 那它可以假设还没有声明过
  var name = 'Matt';

  // 这里没问题，因为可以被作为一个提升声明来处理
  // 不需要检查之前是否声明过同名变量
  // 如果age 之前声明过，这里会报错
  let age = 36;
</script>
```

使用 try/catch 语句或 typeof 操作符也不能解决，因为条件块中 let 声明的作用域仅限于该块。

```html
<script>
  let name = 'Nicholas';
  let age = 36;
</script>
<script>
  // 假设脚本不确定页面中是否已经声明了同名变量
  // 那它可以假设还没有声明过
  if (typeof name === 'undefined') {
    let name;
  }

  // name 被限制在if {} 块的作用域内
  // 因此这个赋值形同全局赋值
  name = 'Matt';
  try {
    // 如果age 没有声明过，则会报错
    console.log(age);
  } catch (error) {
    let age;
  }

  // age 被限制在catch {}块的作用域内
  // 因此这个赋值形同全局赋值
  age = 26;
</script>
```

为此，对于 let 这个新的 ES6 声明关键字，不能依赖条件声明模式。

4. **for 循环**

在 let 出现之前，for 循环定义的迭代变量会渗透到循环体外部：

```javascript
for (var i = 0; i < 3; i++) {
  // 循环逻辑
}

// 3
console.log(i);
```

改成使用 let 之后，这个问题就消失了，因为迭代变量的作用域仅限于 for 循环块内部：

```javascript
for (let i = 0; i < 3; i++) {
  // 循环逻辑
}

// ReferenceError: i is not defined
console.log(i);
```

在使用 var 的时候，最常见的问题就是对迭代变量的奇特声明和修改：

```javascript
for (var i = 0; i < 3; i++) {
  // 你可能以为会输出 0, 1, 2
  // 实际上会输出 3, 3, 3
  setTimeout(() => console.log(i), 0);
}
```

以上代码实际等同于：

```javascript
var i = 0;

if (i < 3) {
  setTimeout(() => console.log(i), 0);
  i++;
  setTimeout(() => console.log(i), 0);
  i++;
  setTimeout(() => console.log(i), 0);
  i++;
  ...
}
```

setTimeout 是异步执行的代码，同步代码先执行，后再执行异步代码。同步代码执行完后，i 的值变了为 3，此时再按先来先服务的机制执行异步代码，第一次出现的异步代码执行结果为 3， 第 2 次和第 3 次出现的异步代码执行结果都是 3。

使用立即执行函数可以避免这种现象：

```javascript
for (var i = 0; i < 3; i++) {
  // 0, 1, 2
  ((i) => setTimeout(() => console.log(i), 0))(i);
}
```

在执行顺序上的等同代码：

```javascript
var i = 0;
if (i < 3) {
  // 传入的 i 为 0
  ((i) => setTimeout(() => console.log(i), 0))(i);
  i++;

  // 传入的 i 为 1
  ((i) => setTimeout(() => console.log(i), 0))(i);
  i++;

  // 传入的 i 为 2
  ((i) => setTimeout(() => console.log(i), 0))(i);
  i++;
  ...
}
```

虽然 setTimeout 是异步代码，但利用立即执行函数传入的每个 i 值都发生了变化。也可以写成这样：

```javascript
for (var i = 0; i < 3; ) {
  ((i) => setTimeout(() => console.log(i), 0))(i++);
}
```

而在使用 let 声明迭代变量时，JavaScript 引擎在后台会为每个迭代循环声明一个新的迭代变量。每个 setTimeout 引用的都是不同的变量实例，所以 console.log 输出的是我们期望的值，也就是循环执行过程中每个迭代变量的值。

```javascript
for (let i = 0; i < 3; i++) {
  // 0, 1, 2
  setTimeout(() => console.log(i), 0);
}
```

这种每次迭代声明一个独立变量实例的行为适用于所有风格的 for 循环，包括 for-in 和 for-of 循环。

## 3. const

const 的行为与 let 基本相同，唯一一个重要的区别是用它声明变量时必须同时初始化变量，且尝试修改 const 声明的变量会导致运行时错误。

```javascript
const age = 26;

// TypeError: Assignment to constant variable.
age = 36;

// const 也不允许重复声明
const name = 'Matt';

// SyntaxError: Identifier 'name' has already been declared
const name = 'Nicholas';

// const 声明的作用域也是块
const name = 'Matt';

if (true) {
  const name = 'Nicholas';
}

// 'Matt'
console.log(name);
```

const 声明的限制只适用于它指向的变量的引用。换句话说，如果 const 变量引用的是一个对象，那么修改这个对象内部的属性并不违反 const 的限制。

```javascript
const person = {};

// ok
person.name = 'Matt';
```

JavaScript 引擎会为 for 循环中的 let 声明分别创建独立的变量实例，虽然 const 变量跟 let 变量很相似，但是不能用 const 来声明迭代变量（因为迭代变量会自增）：

```javascript
// TypeError: Assignment to constant variable.
for (const i = 0; i < 10; i++) {}
```

不过，如果你只想用 const 声明一个不会被修改的 for 循环变量，那也是可以的。也就是说，每次迭代只是创建一个新变量。这对 for-of 和 for-in 循环特别有意义：

```javascript
let i = 0;

// 7, 7, 7, 7, 7
for (const j = 7; i < 5; i++) {
  console.log(j);
}

const object = {a: 1, b: 2};

// a, b
for (const key in object) {
  console.log(key);
}

// 1, 2, 3, 4, 5
for (const value of [1, 2, 3, 4, 5]) {
  console.log(value);
}
```

## 4. 声明风格与最佳实践

ECMAScript 6 增加 let 和 const 从客观上为这门语言更精确地声明作用域和语义提供了更好的支持。行为怪异的 var 所造成的各种问题，已经让 JavaScript 社区为之苦恼了很多年。随着这两个新关键字的出现，新的有助于提升代码质量的最佳实践也逐渐显现。

1. 不使用 var

有了 let 和 const，大多数开发者会发现自己不再需要 var 了。限制自己只使用 let 和 const 有助于提升代码质量，因为变量有了明确的作用域、声明位置，以及不变的值。

2. const 优先，let 次之

使用 const 声明可以让浏览器运行时强制保持变量不变，也可以让静态代码分析工具提前发现不合法的赋值操作。因此，很多开发者认为应该优先使用 const 来声明变量，只在提前知道未来会有修改时，再使用 let。这样可以让开发者更有信心地推断某些变量的值永远不会变，同时也能迅速发现因意外赋值导致的非预期行为。
