**目录：**

- [19. JavaScript API](#19-javascript-api)
  - [19.1. Atomics 与 SharedArrayBuffer](#191-atomics-与-sharedarraybuffer)
    - [19.1.1. SharedArrayBuffer](#1911-sharedarraybuffer)
    - [19.1.2. 原子操作基础](#1912-原子操作基础)

# 19. JavaScript API

本章内容

- Atomics 与 SharedArrayBuffer
- 跨上下文消息
- Encoding API
- File API 与 Blob API
- 拖放
- Notifications API
- Page Visibility API
- Streams API
- 计时 API
- Web 组件
- Web Cryptography API

随着 Web 浏览器能力的增加，其复杂性也在迅速增加。从很多方面看，现代 Web 浏览器已经成为构建于诸多规范之上、集不同 API 于一身的“瑞士军刀”。浏览器规范的生态在某种程度上是混乱而无序的。一些规范如 HTML5，定义了一批增强已有标准的 API 和浏览器特性。而另一些规范如 Web Cryptography API 和 Notifications API，只为一个特性定义了一个 API。不同浏览器实现这些新 API 的情况也不同，有的会实现其中一部分，有的则干脆尚未实现。

最终，是否使用这些比较新的 API 还要看项目是支持更多浏览器，还是要采用更多现代特性。有些 API 可以通过腻子脚本来模拟，但腻子脚本通常会带来性能问题，此外也会增加网站 JavaScript 代码的体积。

注意 Web API 的数量之多令人难以置信（参见 MDN 文档的 Web APIs 词条）。本章要介绍的 API 仅限于与大多数开发者有关、已经得到多个浏览器支持，且本书其他章节没有涵盖的部分。

## 19.1. Atomics 与 SharedArrayBuffer

多个上下文访问 SharedArrayBuffer 时，如果同时对缓冲区执行操作，就可能出现资源争用问题。Atomics API 通过强制同一时刻只能对缓冲区执行一个操作，可以让多个上下文安全地读写一个 SharedArrayBuffer。Atomics API 是 ES2017 中定义的。

仔细研究会发现 Atomics API 非常像一个简化版的指令集架构（ISA），这并非意外。原子操作的本质会排斥操作系统或计算机硬件通常会自动执行的优化（比如指令重新排序）。原子操作也让并发访问内存变得不可能，如果应用不当就可能导致程序执行变慢。为此，Atomics API 的设计初衷是在最少但很稳定的原子行为基础之上，构建复杂的多线程 JavaScript 程序。

### 19.1.1. SharedArrayBuffer

SharedArrayBuffer 与 ArrayBuffer 具有同样的 API。二者的主要区别是 ArrayBuffer 必须在不同执行上下文间切换，SharedArrayBuffer 则可以被任意多个执行上下文同时使用。

在多个执行上下文间共享内存意味着并发线程操作成为了可能。传统 JavaScript 操作对于并发内存访问导致的资源争用没有提供保护。下面的例子演示了 4 个专用工作线程访问同一个 SharedArrayBuffer 导致的资源争用问题：

```javascript
const workerScript = `
self.onmessage = ({data}) => {
const view = new Uint32Array(data);
// 执行1 000 000 次加操作
for (let i = 0; i < 1E6; ++i) {
// 线程不安全加操作会导致资源争用
view[0] += 1;
}
self.postMessage(null);
};
`;
const workerScriptBlobUrl = URL.createObjectURL(new Blob([workerScript]));
// 创建容量为4 的工作线程池
const workers = [];
for (let i = 0; i < 4; ++i) {
  workers.push(new Worker(workerScriptBlobUrl));
}
// 在最后一个工作线程完成后打印出最终值
let responseCount = 0;
for (const worker of workers) {
  worker.onmessage = () => {
    if (++responseCount == workers.length) {
      console.log(`Final buffer value: ${view[0]}`);
    }
  };
}
// 初始化SharedArrayBuffer
const sharedArrayBuffer = new SharedArrayBuffer(4);
const view = new Uint32Array(sharedArrayBuffer);
view[0] = 1;
// 把SharedArrayBuffer 发送到每个工作线程
for (const worker of workers) {
  worker.postMessage(sharedArrayBuffer);
}
//（期待结果为4000001。实际输出可能类似这样：）
// Final buffer value: 2145106
```

为解决这个问题，Atomics API 应运而生。Atomics API 可以保证 SharedArrayBuffer 上的 JavaScript 操作是线程安全的。

注意 SharedArrayBuffer API 等同于 ArrayBuffer API，后者在第 6 章介绍过。关于如何在多个上下文中使用 SharedArrayBuffer，可以参考第 27 章。

### 19.1.2. 原子操作基础

任何全局上下文中都有 Atomics 对象，这个对象上暴露了用于执行线程安全操作的一套静态方法，其中多数方法以一个 TypedArray 实例（一个 SharedArrayBuffer 的引用）作为第一个参数，以相关操作数作为后续参数。

1. **算术及位操作方法**

Atomics API 提供了一套简单的方法用以执行就地修改操作。在 ECMA 规范中，这些方法被定义为 AtomicReadModifyWrite 操作。在底层，这些方法都会从 SharedArrayBuffer 中某个位置读取值，然后执行算术或位操作，最后再把计算结果写回相同的位置。这些操作的原子本质意味着上述读取、修改、写回操作会按照顺序执行，不会被其他线程中断。

以下代码演示了所有算术方法：

```javascript
// 创建大小为1 的缓冲区
let sharedArrayBuffer = new SharedArrayBuffer(1);
// 基于缓冲创建Uint8Array
let typedArray = new Uint8Array(sharedArrayBuffer);
// 所有ArrayBuffer 全部初始化为0
console.log(typedArray); // Uint8Array[0]
const index = 0;
const increment = 5;
// 对索引0 处的值执行原子加5
Atomics.add(typedArray, index, increment);
console.log(typedArray); // Uint8Array[5]
// 对索引0 处的值执行原子减5
Atomics.sub(typedArray, index, increment);
console.log(typedArray); // Uint8Array[0]
以下代码演示了所有位方法：
// 创建大小为1 的缓冲区
let sharedArrayBuffer = new SharedArrayBuffer(1);
// 基于缓冲创建Uint8Array
let typedArray = new Uint8Array(sharedArrayBuffer);
// 所有ArrayBuffer 全部初始化为0
console.log(typedArray); // Uint8Array[0]

const index = 0;
// 对索引0 处的值执行原子或0b1111
Atomics.or(typedArray, index, 0b1111);
console.log(typedArray); // Uint8Array[15]
// 对索引0 处的值执行原子与0b1111
Atomics.and(typedArray, index, 0b1100);
console.log(typedArray); // Uint8Array[12]
// 对索引0 处的值执行原子异或0b1111
Atomics.xor(typedArray, index, 0b1111);
console.log(typedArray); // Uint8Array[3]
前面线程不安全的例子可以改写为下面这样：
const workerScript = `
self.onmessage = ({data}) => {
const view = new Uint32Array(data);
// 执行1 000 000 次加操作
for (let i = 0; i < 1E6; ++i) {
// 线程安全的加操作
Atomics.add(view, 0, 1);
}
self.postMessage(null);
};
`;
const workerScriptBlobUrl = URL.createObjectURL(new Blob([workerScript]));
// 创建容量为4 的工作线程池
const workers = [];
for (let i = 0; i < 4; ++i) {
workers.push(new Worker(workerScriptBlobUrl));
}
// 在最后一个工作线程完成后打印出最终值
let responseCount = 0;
for (const worker of workers) {
worker.onmessage = () => {
if (++responseCount == workers.length) {
console.log(`Final buffer value: ${view[0]}`);
}
};
}
// 初始化SharedArrayBuffer
const sharedArrayBuffer = new SharedArrayBuffer(4);
const view = new Uint32Array(sharedArrayBuffer);
view[0] = 1;
// 把SharedArrayBuffer 发送到每个工作线程
for (const worker of workers) {
worker.postMessage(sharedArrayBuffer);
}
//（期待结果为4000001）
// Final buffer value: 4000001
```

2. **原子读和写**

浏览器的 JavaScript 编译器和 CPU 架构本身都有权限重排指令以提升程序执行效率。正常情况下，JavaScript 的单线程环境是可以随时进行这种优化的。但多线程下的指令重排可能导致资源争用，而且极难排错。

Atomics API 通过两种主要方式解决了这个问题。

- 所有原子指令相互之间的顺序永远不会重排。
- 使用原子读或原子写保证所有指令（包括原子和非原子指令）都不会相对原子读/写重新排序。

这意味着位于原子读/写之前的所有指令会在原子读/写发生前完成，而位于原子读/写之后的所有指令会在原子读/写完成后才会开始。

除了读写缓冲区的值，Atomics.load()和 Atomics.store()还可以构建“代码围栏”。JavaScript 引擎保证非原子指令可以相对于 load()或 store()本地重排，但这个重排不会侵犯原子读/写的边界。以下代码演示了这种行为：

```javascript
const sharedArrayBuffer = new SharedArrayBuffer(4);
const view = new Uint32Array(sharedArrayBuffer);
// 执行非原子写
view[0] = 1;
// 非原子写可以保证在这个读操作之前完成，因此这里一定会读到1
console.log(Atomics.load(view, 0)); // 1
// 执行原子写
Atomics.store(view, 0, 2);
// 非原子读可以保证在原子写完成后发生，因此这里一定会读到2
console.log(view[0]); // 2
```

3. **原子交换**

为了保证连续、不间断的先读后写， Atomics API 提供了两种方法： exchange() 和 compareExchange()。Atomics.exchange()执行简单的交换，以保证其他线程不会中断值的交换：

```javascript
const sharedArrayBuffer = new SharedArrayBuffer(4);
const view = new Uint32Array(sharedArrayBuffer);
// 在索引0 处写入3
Atomics.store(view, 0, 3);
// 从索引0 处读取值，然后在索引0 处写入4
console.log(Atomics.exchange(view, 0, 4)); // 3
// 从索引0 处读取值
console.log(Atomics.load(view, 0)); // 4
```

在多线程程序中，一个线程可能只希望在上次读取某个值之后没有其他线程修改该值的情况下才对共享缓冲区执行写操作。如果这个值没有被修改，这个线程就可以安全地写入更新后的值；如果这个值被修改了，那么执行写操作将会破坏其他线程计算的值。对于这种任务，Atomics API 提供了 compareExchange()方法。这个方法只在目标索引处的值与预期值匹配时才会执行写操作。来看下面这个例子：

```javascript
const sharedArrayBuffer = new SharedArrayBuffer(4);
const view = new Uint32Array(sharedArrayBuffer);
// 在索引0 处写入5
Atomics.store(view, 0, 5);
// 从缓冲区读取值
let initial = Atomics.load(view, 0);
// 对这个值执行非原子操作
let result = initial ** 2;
// 只在缓冲区未被修改的情况下才会向缓冲区写入新值
Atomics.compareExchange(view, 0, initial, result);
// 检查写入成功
console.log(Atomics.load(view, 0)); // 25
如果值不匹配，compareExchange()调用则什么也不做：
const sharedArrayBuffer = new SharedArrayBuffer(4);
const view = new Uint32Array(sharedArrayBuffer);
// 在索引0 处写入5
Atomics.store(view, 0, 5);
// 从缓冲区读取值
let initial = Atomics.load(view, 0);
// 对这个值执行非原子操作
let result = initial ** 2;
// 只在缓冲区未被修改的情况下才会向缓冲区写入新值
Atomics.compareExchange(view, 0, -1, result);
// 检查写入失败
console.log(Atomics.load(view, 0)); // 5
```

4. **原子 Futex 操作与加锁**

如果没有某种锁机制，多线程程序就无法支持复杂需求。为此，Atomics API 提供了模仿 Linux Futex（**快速用户空间互斥量，fast user-space mutex**）的方法。这些方法本身虽然非常简单，但可以作为更复杂锁机制的基本组件。

注意 所有原子 Futex 操作只能用于 Int32Array 视图。而且，也只能用在工作线程内部。

Atomics.wait()和 Atomics.notify()通过示例很容易理解。下面这个简单的例子创建了 4 个工作线程，用于对长度为 1 的 Int32Array 进行操作。这些工作线程会依次取得锁并执行自己的加操作：

```javascript
const workerScript = `
self.onmessage = ({data}) => {
const view = new Int32Array(data);
console.log('Waiting to obtain lock');
// 遇到初始值则停止，10 000 毫秒超时
Atomics.wait(view, 0, 0, 1E5);
console.log('Obtained lock');
// 在索引0 处加1
Atomics.add(view, 0, 1);
console.log('Releasing lock');
// 只允许1 个工作线程继续执行
Atomics.notify(view, 0, 1);
self.postMessage(null);
};
`;
const workerScriptBlobUrl = URL.createObjectURL(new Blob([workerScript]));
const workers = [];
for (let i = 0; i < 4; ++i) {
  workers.push(new Worker(workerScriptBlobUrl));
}
// 在最后一个工作线程完成后打印出最终值
let responseCount = 0;
for (const worker of workers) {
  worker.onmessage = () => {
    if (++responseCount == workers.length) {
      console.log(`Final buffer value: ${view[0]}`);
    }
  };
}
// 初始化SharedArrayBuffer
const sharedArrayBuffer = new SharedArrayBuffer(8);
const view = new Int32Array(sharedArrayBuffer);
// 把SharedArrayBuffer 发送到每个工作线程
for (const worker of workers) {
  worker.postMessage(sharedArrayBuffer);
}
// 1000 毫秒后释放第一个锁
setTimeout(() => Atomics.notify(view, 0, 1), 1000);
// Waiting to obtain lock
// Waiting to obtain lock
// Waiting to obtain lock
// Waiting to obtain lock
// Obtained lock
// Releasing lock
// Obtained lock
// Releasing lock
// Obtained lock
// Releasing lock
// Obtained lock
// Releasing lock
// Final buffer value: 4
```

因为是使用 0 来初始化 SharedArrayBuffer，所以每个工作线程都会到达 Atomics.wait()并停止执行。在停止状态下，执行线程存在于一个等待队列中，在经过指定时间或在相应索引上调用 Atomics.notify() 之前， 一直保持暂停状态。1000 毫秒之后， 顶部执行上下文会调用 Atomics.notify()释放其中一个等待的线程。这个线程执行完毕后会再次调用 Atomics.notify()释放另一个线程。这个过程会持续到所有线程都执行完毕并通过 postMessage()传出最终的值。Atomics API 还提供了 Atomics.isLockFree()方法。不过我们基本上应该不会用到。这个方法在高性能算法中可以用来确定是否有必要获取锁。规范中的介绍如下：

Atomics.isLockFree()是一个优化原语。基本上，如果一个原子原语（compareExchange、load、store、add、sub、and、or、xor 或 exchange）在 n 字节大小的数据上的原子步骤在不调用代理在组成数据的 n 字节之外获得锁的情况下可以执行，则 Atomics.isLockFree(n)会返回 true。高性能算法会使用 Atomics.isLockFree 确定是否在关键部分使用锁或原子操作。如果原子原语需要加锁，则算法提供自己的锁会更高效。

Atomics.isLockFree(4)始终返回 true，因为在所有已知的相关硬件上都是支持的。能够如此假设通常可以简化程序。
