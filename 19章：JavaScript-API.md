**目录：**

- [19. JavaScript API](#19-javascript-api)
  - [19.1. Atomics 与 SharedArrayBuffer](#191-atomics-与-sharedarraybuffer)
    - [19.1.1. SharedArrayBuffer](#1911-sharedarraybuffer)
    - [19.1.2. 原子操作基础](#1912-原子操作基础)
  - [19.2. 跨上下文通信](#192-跨上下文通信)
  - [19.3. Encoding API](#193-encoding-api)
    - [19.3.1. 文本编码](#1931-文本编码)
    - [19.3.2. 文本解码](#1932-文本解码)
  - [19.4. File API 与 Blob API](#194-file-api-与-blob-api)
    - [19.4.1. File 类型](#1941-file-类型)
    - [19.4.2. FileReader 类型](#1942-filereader-类型)
    - [19.4.3. FileReaderSync 类型](#1943-filereadersync-类型)
    - [19.4.4. Blob 与部分读取](#1944-blob-与部分读取)
    - [19.4.5. 对象 URL 与 Blob](#1945-对象-url-与-blob)
    - [19.4.6. 读取拖放文件](#1946-读取拖放文件)
  - [19.5. 媒体元素](#195-媒体元素)
    - [19.5.1. 属性](#1951-属性)
    - [19.5.2. 事件](#1952-事件)
    - [19.5.3. 自定义媒体播放器](#1953-自定义媒体播放器)
    - [19.5.4. 检测编解码器](#1954-检测编解码器)
    - [19.5.5. 音频类型](#1955-音频类型)
  - [19.6. 原生拖放](#196-原生拖放)

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

## 19.2. 跨上下文通信

跨文档通信，有时候也简称为 **XDM(cross-document messaging)**，是一种在不同执行上下文（如不同工作线程或不同源的页面）间传递信息的能力。例如，www.wrox.com 上的页面想要与包含在内嵌窗格中的 p2p.wrox.com 上面的页面通信。在 XDM 之前，要以安全方式实现这种通信需要很多工作。XDM 以安全易用的方式规范化了这个功能。

注意 跨上下文通信用于窗口之间通信或工作线程之间通信。本节主要介绍使用 postMessage()与其他窗口通信 。关于工作线程之间通信、MessageChannel 和 BroadcastChannel，可以参考第 27 章。

XDM 的核心是 postMessage()方法。除了 XDM，这个方法名还在 HTML5 中很多地方用到过，但目的都一样，都是把数据传送到另一个位置。

postMessage()方法接收 3 个参数：消息、表示目标接收源的字符串和可选的可传输对象的数组（只与工作线程相关）。第二个参数对于安全非常重要，其可以限制浏览器交付数据的目标。下面来看一个例子：

```javascript
const iframeWindow = $('#myframe').contentWindow;
iframeWindow.postMessage('A secret', 'http://www.wrox.com');
```

最后一行代码尝试向内嵌窗格中发送一条消息，而且指定了源必须是"http://www.wrox.com"。如果源匹配，那么消息将会交付到内嵌窗格；否则，postMessage()什么也不做。这个限制可以保护信息不会因地址改变而泄露。如果不想限制接收目标，则可以给postMessage()的第二个参数传"*"，但不推荐这么做。

接收到 XDM 消息后，window 对象上会触发 message 事件。这个事件是异步触发的，因此从消息发出到接收到消息（接收窗口触发 message 事件）可能有延迟。传给 onmessage 事件处理程序的 event 对象包含以下 3 方面重要信息。

- data：作为第一个参数传递给 postMessage()的字符串数据。
- origin：发送消息的文档源，例如"http://www.wrox.com"。
- source：发送消息的文档中 window 对象的代理。这个代理对象主要用于在发送上一条消息的窗口中执行 postMessage()方法。如果发送窗口有相同的源，那么这个对象应该就是 window 对象。

接收消息之后验证发送窗口的源是非常重要的。与 postMessage()的第二个参数可以保证数据不会意外传给未知页面一样，在 onmessage 事件处理程序中检查发送窗口的源可以保证数据来自正确的地方。基本的使用方式如下所示：

```javascript
window.addEventListener('message', (event) => {
  // 确保来自预期发送者
  if (event.origin == 'http://www.wrox.com') {
    // 对数据进行一些处理
    processMessage(event.data);

    // 可选：向来源窗口发送一条消息
    event.source.postMessage('Received!', 'http://p2p.wrox.com');
  }
});
```

大多数情况下，event.source 是某个 window 对象的代理，而非实际的 window 对象。因此不能通过它访问所有窗口下的信息。最好只使用 postMessage()，这个方法永远存在而且可以调用。

XDM 有一些怪异之处。首先，postMessage()的第一个参数的最初实现始终是一个字符串。后来，第一个参数改为允许任何结构的数据传入，不过并非所有浏览器都实现了这个改变。为此，最好就是只通过 postMessage() 发送字符串。如果需要传递结构化数据， 那么最好先对该数据调用 JSON.stringify()，通过 postMessage()传过去之后，再在 onmessage 事件处理程序中调用 JSON.parse()。

在通过内嵌窗格加载不同域时，使用 XDM 是非常方便的。这种方法在混搭（mashup）和社交应用中非常常用。通过使用 XDM 与内嵌窗格中的网页通信，可以保证包含页面的安全。XDM 也可以用于同源页面之间通信。

## 19.3. Encoding API

Encoding API 主要用于实现字符串与定型数组之间的转换。规范新增了 4 个用于执行转换的全局类：TextEncoder、TextEncoderStream、TextDecoder 和 TextDecoderStream。

注意 相比于 **批量(bulk)** 的编解码，对 **流(stream)** 编解码的支持很有限。

### 19.3.1. 文本编码

Encoding API 提供了两种将字符串转换为定型数组二进制格式的方法：批量编码和流编码。把字符串转换为定型数组时，编码器始终使用 UTF-8。

1. **批量编码**

所谓批量，指的是 JavaScript 引擎会同步编码整个字符串。对于非常长的字符串，可能会花较长时间。批量编码是通过 TextEncoder 的实例完成的：

```javascript
const textEncoder = new TextEncoder();
```

这个实例上有一个 encode()方法，该方法接收一个字符串参数，并以 Uint8Array 格式返回每个字符的 UTF-8 编码：

```javascript
const textEncoder = new TextEncoder();
const decodedText = 'foo';
const encodedText = textEncoder.encode(decodedText);

// f 的UTF-8 编码是0x66（即十进制102）
// o 的UTF-8 编码是0x6F（即十进制111）
console.log(encodedText);
// >> Uint8Array(3) [102, 111, 111]
```

编码器是用于处理字符的，有些字符（如表情符号）在最终返回的数组中可能会占多个索引：

```javascript
const textEncoder = new TextEncoder();
const decodedText = '☺';
const encodedText = textEncoder.encode(decodedText);

// ☺的UTF-8 编码是0xF0 0x9F 0x98 0x8A（即十进制240、159、152、138）
console.log(encodedText);
// >> Uint8Array(4) [240, 159, 152, 138]
```

编码器实例还有一个 encodeInto()方法，该方法接收一个字符串和目标 Unit8Array，返回一个字典，该字典包含 read 和 written 属性，分别表示成功从源字符串读取了多少字符和向目标数组写入了多少字符。如果定型数组的空间不够，编码就会提前终止，返回的字典会体现这个结果：

```javascript
const textEncoder = new TextEncoder();
const fooArr = new Uint8Array(3);
const barArr = new Uint8Array(2);
const fooResult = textEncoder.encodeInto('foo', fooArr);
const barResult = textEncoder.encodeInto('bar', barArr);
console.log(fooArr);
// >> Uint8Array(3) [102, 111, 111]

console.log(fooResult);
// >> { read: 3, written: 3 }

console.log(barArr);
// >> Uint8Array(2) [98, 97]

console.log(barResult);
// >> { read: 2, written: 2 }
```

encode()要求分配一个新的 Unit8Array，encodeInto()则不需要。对于追求性能的应用，这个差别可能会带来显著不同。

注意 文本编码会始终使用 UTF-8 格式，而且必须写入 Unit8Array 实例。使用其他类型数组会导致 encodeInto()抛出错误。

2. **流编码**

TextEncoderStream 其实就是 TransformStream 形式的 TextEncoder。将解码后的文本流通过管道输入流编码器会得到编码后文本块的流：

```javascript
async function* chars() {
  const decodedText = 'foo';
  for (let char of decodedText) {
    yield await new Promise((resolve) => setTimeout(resolve, 1000, char));
  }
}

const decodedTextStream = new ReadableStream({
  async start(controller) {
    for await (let chunk of chars()) {
      controller.enqueue(chunk);
    }

    controller.close();
  },
});

const encodedTextStream = decodedTextStream.pipeThrough(
  new TextEncoderStream(),
);

const readableStreamDefaultReader = encodedTextStream.getReader();
(async function () {
  while (true) {
    const {done, value} = await readableStreamDefaultReader.read();

    if (done) {
      break;
    } else {
      console.log(value);
    }
  }
})();
// >> Uint8Array[102]
// >> Uint8Array[111]
// >> Uint8Array[111]
```

### 19.3.2. 文本解码

Encoding API 提供了两种将定型数组转换为字符串的方式：批量解码和流解码。与编码器类不同，在将定型数组转换为字符串时，解码器支持非常多的字符串编码，可以参考 Encoding Standard 规范的“Names and labels”一节。

默认字符编码格式是 UTF-8。

1. **批量解码**

所谓批量，指的是 JavaScript 引擎会同步解码整个字符串。对于非常长的字符串，可能会花较长时间。批量解码是通过 TextDecoder 的实例完成的：

```javascript
const textDecoder = new TextDecoder();
```

这个实例上有一个 decode()方法，该方法接收一个定型数组参数，返回解码后的字符串：

```javascript
const textDecoder = new TextDecoder();

// f 的UTF-8 编码是0x66（即十进制102）
// o 的UTF-8 编码是0x6F（即二进制111）
const encodedText = Uint8Array.of(102, 111, 111);
const decodedText = textDecoder.decode(encodedText);
console.log(decodedText);
// >> 'foo'
```

解码器不关心传入的是哪种定型数组，它只会专心解码整个二进制表示。在下面这个例子中，只包含 8 位字符的 32 位值被解码为 UTF-8 格式，解码得到的字符串中填充了空格：

```javascript
const textDecoder = new TextDecoder();

// f 的UTF-8 编码是0x66（即十进制102）
// o 的UTF-8 编码是0x6F（即二进制111）
const encodedText = Uint32Array.of(102, 111, 111);
const decodedText = textDecoder.decode(encodedText);
console.log(decodedText);
// >> 'f o o '
```

解码器是用于处理定型数组中分散在多个索引上的字符的，包括表情符号：

```javascript
const textDecoder = new TextDecoder();

// ☺的UTF-8 编码是0xF0 0x9F 0x98 0x8A（即十进制240、159、152、138）
const encodedText = Uint8Array.of(240, 159, 152, 138);
const decodedText = textDecoder.decode(encodedText);
console.log(decodedText);
// >> '☺'
```

与 TextEncoder 不同，TextDecoder 可以兼容很多字符编码。比如下面的例子就使用了 UTF-16 而非默认的 UTF-8：

```javascript
const textDecoder = new TextDecoder('utf-16');

// f 的UTF-8 编码是0x0066（即十进制102）
// o 的UTF-8 编码是0x006F（即二进制111）
const encodedText = Uint16Array.of(102, 111, 111);
const decodedText = textDecoder.decode(encodedText);
console.log(decodedText);
// >> 'foo'
```

2. **流解码**

TextDecoderStream 其实就是 TransformStream 形式的 TextDecoder。将编码后的文本流通过管道输入流解码器会得到解码后文本块的流：

```javascript
async function* chars() {
  // 每个块必须是一个定型数组
  const encodedText = [102, 111, 111].map((x) => Uint8Array.of(x));

  for (let char of encodedText) {
    yield await new Promise((resolve) => setTimeout(resolve, 1000, char));
  }
}

const encodedTextStream = new ReadableStream({
  async start(controller) {
    for await (let chunk of chars()) {
      controller.enqueue(chunk);
    }
    controller.close();
  },
});

const decodedTextStream = encodedTextStream.pipeThrough(
  new TextDecoderStream(),
);
const readableStreamDefaultReader = decodedTextStream.getReader();

(async function () {
  while (true) {
    const {done, value} = await readableStreamDefaultReader.read();
    if (done) {
      break;
    } else {
      console.log(value);
    }
  }
})();
// >> 'f'
// >> 'o'
// >> 'o'
```

文本解码器流能够识别可能分散在不同块上的代理对。解码器流会保持块片段直到取得完整的字符。比如在下面的例子中，流解码器在解码流并输出字符之前会等待传入 4 个块：

```javascript
async function* chars() {
  // ☺的UTF-8 编码是0xF0 0x9F 0x98 0x8A（即十进制240、159、152、138）
  const encodedText = [240, 159, 152, 138].map((x) => Uint8Array.of(x));

  for (let char of encodedText) {
    yield await new Promise((resolve) => setTimeout(resolve, 1000, char));
  }
}

const encodedTextStream = new ReadableStream({
  async start(controller) {
    for await (let chunk of chars()) {
      controller.enqueue(chunk);
    }
    controller.close();
  },
});

const decodedTextStream = encodedTextStream.pipeThrough(
  new TextDecoderStream(),
);
const readableStreamDefaultReader = decodedTextStream.getReader();

(async function () {
  while (true) {
    const {done, value} = await readableStreamDefaultReader.read();
    if (done) {
      break;
    } else {
      console.log(value);
    }
  }
})();
// >> '☺'
```

文本解码器流经常与 fetch()一起使用，因为响应体可以作为 ReadableStream 来处理。比如：

```javascript
const response = await fetch(url);
const stream = response.body.pipeThrough(new TextDecoderStream());
const decodedStream = stream.getReader();

for await (let decodedChunk of decodedStream) {
  console.log(decodedChunk);
}
```

## 19.4. File API 与 Blob API

Web 应用程序的一个主要的痛点是无法操作用户计算机上的文件。2000 年之前，处理文件的唯一方式是把`<input type="file">`放到一个表单里，仅此而已。File API 与 Blob API 是为了让 Web 开发者能以安全的方式访问客户端机器上的文件，从而更好地与这些文件交互而设计的。

### 19.4.1. File 类型

File API 仍然以表单中的文件输入字段为基础，但是增加了直接访问文件信息的能力。HTML5 在 DOM 上为文件输入元素添加了 files 集合。当用户在文件字段中选择一个或多个文件时，这个 files 集合中会包含一组 File 对象，表示被选中的文件。每个 File 对象都有一些只读属性。

- name：本地系统中的文件名。
- size：以字节计的文件大小。
- type：包含文件 MIME 类型的字符串。
- lastModifiedDate：表示文件最后修改时间的字符串。这个属性只有 Chome 实现了。

例如，通过监听 change 事件然后遍历 files 集合可以取得每个选中文件的信息：

```javascript
let filesList = $('#files-list');

filesList.addEventListener('change', (event) => {
  let files = event.target.files,
    i = 0,
    len = files.length;
  while (i < len) {
    const f = files[i];
    console.log(`${f.name} (${f.type}, ${f.size} bytes)`);
    i++;
  }
});
```

这个例子简单地在控制台输出了每个文件的信息。仅就这个能力而言，已经可以说是 Web 应用向前迈进的一大步了。不过，File API 还提供了 FileReader 类型，让我们可以实际从文件中读取数据。

### 19.4.2. FileReader 类型

FileReader 类型表示一种异步文件读取机制。可以把 FileReader 想象成类似于 XMLHttpRequest，只不过是用于从文件系统读取文件，而不是从服务器读取数据。FileReader 类型提供了几个读取文件数据的方法。

- readAsText(file, encoding)：从文件中读取纯文本内容并保存在 result 属性中。第二个参数表示编码，是可选的。
- readAsDataURL(file)：读取文件并将内容的数据 URI 保存在 result 属性中。
- readAsBinaryString(file)：读取文件并将每个字符的二进制数据保存在 result 属性中。
- readAsArrayBuffer(file)：读取文件并将文件内容以 ArrayBuffer 形式保存在 result 属性。

这些读取数据的方法为处理文件数据提供了极大的灵活性。例如，为了向用户显示图片，可以将图片读取为数据 URI，而为了解析文件内容，可以将文件读取为文本。

因为这些读取方法是异步的，所以每个 FileReader 会发布几个事件，其中 3 个最有用的事件是 progress、error 和 load，分别表示还有更多数据、发生了错误和读取完成。

progress 事件每 50 毫秒就会触发一次，其与 XHR 的 progress 事件具有相同的信息：lengthComputable、loaded 和 total。此外，在 progress 事件中可以读取 FileReader 的 result 属性，即使其中尚未包含全部数据。

error 事件会在由于某种原因无法读取文件时触发。触发 error 事件时，FileReader 的 error 属性会包含错误信息。这个属性是一个对象，只包含一个属性：code。这个错误码的值可能是 1（未找到文件）、2（安全错误）、3（读取被中断）、4（文件不可读）或 5（编码错误）。

load 事件会在文件成功加载后触发。如果 error 事件被触发，则不会再触发 load 事件。下面的例子演示了所有这 3 个事件：

```javascript
const filesList = document.getElementById('files-list');
filesList.addEventListener('change', (event) => {
  let info = '',
    output = document.getElementById('output'),
    progress = document.getElementById('progress'),
    files = event.target.files,
    type = 'default',
    reader = new FileReader();
  if (/image/.test(files[0].type)) {
    reader.readAsDataURL(files[0]);
    type = 'image';
  } else {
    reader.readAsText(files[0]);
    type = 'text';
  }
  reader.onerror = function () {
    output.innerHTML =
      'Could not read file, error code is ' + reader.error.code;
  };
  reader.onprogress = function (event) {
    if (event.lengthComputable) {
      progress.innerHTML = `${event.loaded}/${event.total}`;
    }
  };
  reader.onload = function () {
    let html = '';
    switch (type) {
      case 'image':
        html = `<img src="${reader.result}">`;
        break;
      case 'text':
        html = reader.result;
        break;
    }
    output.innerHTML = html;
  };
});
```

以上代码从表单字段中读取一个文件，并将其内容显示在了网页上。如果文件的 MIME 类型表示它是一个图片，那么就将其读取后保存为数据 URI，在 load 事件触发时将数据 URI 作为图片插入页面中。如果文件不是图片，则读取后将其保存为文本并原样输出到网页上。progress 事件用于跟踪和显示读取文件的进度，而 error 事件用于监控错误。

如果想提前结束文件读取，则可以在过程中调用 abort()方法，从而触发 abort 事件。在 load、error 和 abort 事件触发后，还会触发 loadend 事件。loadend 事件表示在上述 3 种情况下，所有读取操作都已经结束。readAsText()和 readAsDataURL()方法已经得到了所有主流浏览器支持。

### 19.4.3. FileReaderSync 类型

顾名思义，FileReaderSync 类型就是 FileReader 的同步版本。这个类型拥有与 FileReader 相同的方法，只有在整个文件都加载到内存之后才会继续执行。FileReaderSync 只在工作线程中可用，因为如果读取整个文件耗时太长则会影响全局。

假设通过 postMessage()向工作线程发送了一个 File 对象。以下代码会让工作线程同步将文件读取到内存中，然后将文件的数据 URL 发回来：

```javascript
// worker.js
self.omessage = (messageEvent) => {
  const syncReader = new FileReaderSync();
  console.log(syncReader);
  // >> FileReaderSync {}

  // 读取文件时阻塞工作线程
  const result = syncReader.readAsDataUrl(messageEvent.data);

  // PDF 文件的示例响应
  console.log(result); // data:application/pdf;base64,JVBERi0xLjQK...

  // 把URL 发回去
  self.postMessage(result);
};
```

### 19.4.4. Blob 与部分读取

某些情况下，可能需要读取部分文件而不是整个文件。为此，File 对象提供了一个名为 slice()的方法。slice()方法接收两个参数：起始字节和要读取的字节数。这个方法返回一个 Blob 的实例，而 Blob 实际上是 File 的超类。

blob 表示 **二进制大对象(binary larget object)**，是 JavaScript 对不可修改二进制数据的封装类型。包含字符串的数组、ArrayBuffers、ArrayBufferViews，甚至其他 Blob 都可以用来创建 blob。Blob 构造函数可以接收一个 options 参数，并在其中指定 MIME 类型：

```javascript
console.log(new Blob(['foo']));
// >> Blob {size: 3, type: ""}

console.log(new Blob(['{"a": "b"}'], {type: 'application/json'}));
// >> {size: 10, type: "application/json"}

console.log(new Blob(['<p>Foo</p>', '<p>Bar</p>'], {type: 'text/html'}));
// >> {size: 20, type: "text/html"}
```

Blob 对象有一个 size 属性和一个 type 属性，还有一个 slice()方法用于进一步切分数据。另外也可以使用 FileReader 从 Blob 中读取数据。下面的例子只会读取文件的前 32 字节：

```javascript
const filesList = document.getElementById('files-list');
filesList.addEventListener('change', (event) => {
  let info = '',
    output = document.getElementById('output'),
    progress = document.getElementById('progress'),
    files = event.target.files,
    reader = new FileReader(),
    blob = blobSlice(files[0], 0, 32);

  if (blob) {
    reader.readAsText(blob);

    reader.onerror = function () {
      output.innerHTML =
        'Could not read file, error code is ' + reader.error.code;
    };

    reader.onload = function () {
      output.innerHTML = reader.result;
    };
  } else {
    console.log("Your browser doesn't support slice().");
  }
});
```

只读取部分文件可以节省时间，特别是在只需要数据特定部分比如文件头的时候。

### 19.4.5. 对象 URL 与 Blob

对象 URL 有时候也称作 Blob URL，是指引用存储在 File 或 Blob 中数据的 URL。对象 URL 的优点是不用把文件内容读取到 JavaScript 也可以使用文件。只要在适当位置提供对象 URL 即可。要创建对象 URL，可以使用 window.URL.createObjectURL()方法并传入 File 或 Blob 对象。这个函数返回的值是一个指向内存中地址的字符串。因为这个字符串是 URL，所以可以在 DOM 中直接使用。例如，以下代码使用对象 URL 在页面中显示了一张图片：

```javascript
const filesList = document.getElementById('files-list');
filesList.addEventListener('change', (event) => {
  let info = '',
    output = document.getElementById('output'),
    progress = document.getElementById('progress'),
    files = event.target.files,
    reader = new FileReader(),
    url = window.URL.createObjectURL(files[0]);

  if (url) {
    if (/image/.test(files[0].type)) {
      output.innerHTML = `<img src="${url}">`;
    } else {
      output.innerHTML = 'Not an image.';
    }
  } else {
    output.innerHTML = "Your browser doesn't support object URLs.";
  }
});
```

如果把对象 URL 直接放到`<img>`标签，就不需要把数据先读到 JavaScript 中了。`<img>`标签可以直接从相应的内存位置把数据读取到页面上。

使用完数据之后，最好能释放与之关联的内存。只要对象 URL 在使用中，就不能释放内存。如果想表明不再使用某个对象 URL，则可以把它传给 window.URL.revokeObjectURL()。页面卸载时，所有对象 URL 占用的内存都会被释放。不过，最好在不使用时就立即释放内存，以便尽可能保持页面占用最少资源。

### 19.4.6. 读取拖放文件

组合使用 HTML5 拖放 API 与 File API 可以创建读取文件信息的有趣功能。在页面上创建放置目标后，可以从桌面上把文件拖动并放到放置目标。这样会像拖放图片或链接一样触发 drop 事件。被放置的文件可以通过事件的 event.dataTransfer.files 属性读到，这个属性保存着一组 File 对象，就像文本输入字段一样。

下面的例子会把拖放到页面放置目标上的文件信息打印出来：

```javascript
const droptarget = document.getElementById('droptarget');

const handleEvent = function handleEvent(event) {
  let info = '',
    output = document.getElementById('output'),
    files,
    i,
    len;
  event.preventDefault();

  if (event.type == 'drop') {
    files = event.dataTransfer.files;
    i = 0;
    len = files.length;

    while (i < len) {
      info += `${files[i].name} (${files[i].type}, ${files[i].size} bytes)<br>`;
      i++;
    }
    output.innerHTML = info;
  }
};
droptarget.addEventListener('dragenter', handleEvent);
droptarget.addEventListener('dragover', handleEvent);
droptarget.addEventListener('drop', handleEvent);
```

与后面要介绍的拖放的例子一样，必须取消 dragenter、dragover 和 drop 的默认行为。在 drop 事件处理程序中，可以通过 event.dataTransfer.files 读到文件，此时可以获取文件的相关信息。

## 19.5. 媒体元素

随着嵌入音频和视频元素在 Web 应用上的流行，大多数内容提供商会强迫使用 Flash 以便达到最佳的跨浏览器兼容性。HTML5 新增了两个与媒体相关的元素，即`<audio>`和`<video>`，从而为浏览器提供了嵌入音频和视频的统一解决方案。

这两个元素既支持 Web 开发者在页面中嵌入媒体文件，也支持 JavaScript 实现对媒体的自定义控制。以下是它们的用法：

```html
<!-- 嵌入视频 -->
<video src="conference.mpg" id="myVideo">Video player not available.</video>

<!-- 嵌入音频 -->
<audio src="song.mp3" id="myAudio">Audio player not available.</audio>
```

每个元素至少要求有一个 src 属性，以表示要加载的媒体文件。我们也可以指定表示视频播放器大小的 width 和 height 属性，以及在视频加载期间显示图片 URI 的 poster 属性。另外，controls 属性如果存在，则表示浏览器应该显示播放界面，让用户可以直接控制媒体。开始和结束标签之间的内容是在媒体播放器不可用时显示的替代内容。

由于浏览器支持的媒体格式不同，因此可以指定多个不同的媒体源。为此，需要从元素中删除 src 属性，使用一个或多个`<source>`元素代替，如下面的例子所示：

```html
<!-- 嵌入视频 -->
<video id="myVideo">
  <source src="conference.webm" type="video/webm; codecs='vp8, vorbis'" />
  <source src="conference.ogv" type="video/ogg; codecs='theora, vorbis'" />
  <source src="conference.mpg" />
  Video player not available.
</video>

<!-- 嵌入音频 -->
<audio id="myAudio">
  <source src="song.ogg" type="audio/ogg" />
  <source src="song.mp3" type="audio/mpeg" />
  Audio player not available.
</audio>
```

讨论不同音频和视频的编解码器超出了本书范畴，但浏览器支持的编解码器确实可能有所不同，因此指定多个源文件通常是必需的。

### 19.5.1. 属性

`<video>`和`<audio>`元素提供了稳健的 JavaScript 接口。这两个元素有很多共有属性，可以用于确定媒体的当前状态，如下表所示。

| 属 性               | 数据类型   | 说 明                                                                                                                     |
| ------------------- | ---------- | ------------------------------------------------------------------------------------------------------------------------- |
| autoplay            | Boolean    | 取得或设置 autoplay 标签                                                                                                  |
| buffered            | TimeRanges | 对象，表示已下载缓冲的时间范围                                                                                            |
| bufferedBytes       | ByteRanges | 对象，表示已下载缓冲的字节范围                                                                                            |
| bufferingRate       | Integer    | 平均每秒下载的位数                                                                                                        |
| bufferingThrottled  | Boolean    | 表示缓冲是否被浏览器截流                                                                                                  |
| controls            | Boolean    | 取得或设置 controls 属性，用于显示或隐藏浏览器内置控件                                                                    |
| currentLoop         | Integer    | 媒体已经播放的循环次数                                                                                                    |
| currentSrc          | String     | 当前播放媒体的 URL                                                                                                        |
| currentTime         | Float      | 已经播放的秒数                                                                                                            |
| defaultPlaybackRate | Float      | 取得或设置默认回放速率。默认为 1.0 秒                                                                                     |
| duration            | Float      | 媒体的总秒数                                                                                                              |
| ended               | Boolean    | 表示媒体是否播放完成                                                                                                      |
| loop                | Boolean    | 取得或设置媒体是否应该在播放完再循环开始                                                                                  |
| muted               | Boolean    | 取得或设置媒体是否静音                                                                                                    |
| networkState        | Integer    | 表示媒体当前网络连接状态。0 表示空，1 表示加载中，2 表示加载元数据，3 表示加载了第一帧，4 表示加载完成                    |
| paused              | Boolean    | 表示播放器是否暂停                                                                                                        |
| playbackRate        | Float      | 取得或设置当前播放速率。用户可能会让媒体播放快一些或慢一些。与 defaultPlaybackRate 不同，该属性会保持不变，除非开发者修改 |
| played              | TimeRanges | 到目前为止已经播放的时间范围                                                                                              |
| readyState          | Integer    | 表示媒体是否已经准备就绪。0 表示媒体不可用，1 表示可以显示当前帧，2 表示媒体可以开始播放，3 表示媒体可以从头播到尾        |
| seekable            | TimeRanges | 可以跳转的时间范围                                                                                                        |
| seeking             | Boolean    | 表示播放器是否正移动到媒体文件的新位置                                                                                    |
| src                 | String     | 媒体文件源。可以在任何时候重写                                                                                            |
| start               | Float      | 取得或设置媒体文件中的位置，以秒为单位，从该处开始播放                                                                    |
| totalBytes          | Integer    | 资源需要的字节总数（如果知道的话）                                                                                        |
| videoHeight         | Integer    | 返回视频（不一定是元素）的高度。只适用于`<video>`                                                                         |
| videoWidth          | Integer    | 返回视频（不一定是元素）的宽度。只适用于`<video>`                                                                         |
| volume              | Float      | 取得或设置当前音量，值为 0.0 到 1.0                                                                                       |

上述很多属性也可以在`<audio>`或`<video>`标签上设置。

### 19.5.2. 事件

除了有很多属性，媒体元素还有很多事件。这些事件会监控由于媒体回放或用户交互导致的不同属性的变化。下表列出了这些事件。

| 事 件               | 何时触发                                                         |
| ------------------- | ---------------------------------------------------------------- |
| abort               | 下载被中断                                                       |
| canplay             | 回放可以开始，readyState 为 2                                    |
| canplaythrough      | 回放可以继续，不应该中断，readState 为 3                         |
| canshowcurrentframe | 已经下载当前帧，readyState 为 1                                  |
| dataunavailable     | 不能回放，因为没有数据，readyState 为 0                          |
| durationchange      | duration 属性的值发生变化                                        |
| emptied             | 网络连接关闭了                                                   |
| empty               | 发生了错误，阻止媒体下载                                         |
| ended               | 媒体已经播放完一遍，且停止了                                     |
| error               | 下载期间发生了网络错误                                           |
| load                | 所有媒体已经下载完毕。这个事件已被废弃，使用 canplaythrough 代替 |
| loadeddata          | 媒体的第一帧已经下载                                             |
| loadedmetadata      | 媒体的元数据已经下载                                             |
| loadstart           | 下载已经开始                                                     |
| pause               | 回放已经暂停                                                     |
| play                | 媒体已经收到开始播放的请求                                       |
| playing             | 媒体已经实际开始播放了                                           |
| progress            | 下载中                                                           |
| ratechange          | 媒体播放速率发生变化                                             |
| seeked              | 跳转已结束                                                       |
| seeking             | 回放已移动到新位置                                               |
| stalled             | 浏览器尝试下载，但尚未收到数据                                   |
| timeupdate          | currentTime 被非常规或意外地更改了                               |
| volumechange        | volume 或 muted 属性值发生了变化                                 |
| waiting             | 回放暂停，以下载更多数据                                         |

这些事件被设计得尽可能具体，以便 Web 开发者能够使用较少的 HTML 和 JavaScript 创建自定义的音频/视频播放器（而不是创建新 Flash 影片）。

### 19.5.3. 自定义媒体播放器

使用`<audio>`和`<video>`的play()和pause()方法，可以手动控制媒体文件的播放。综合使用属性、事件和这些方法，可以方便地创建自定义的媒体播放器，如下面的例子所示：

```html
<div class="mediaplayer">
<div class="video">
<video id="player" src="movie.mov" poster="mymovie.jpg"
width="300" height="200">
Video player not available.
</video>
</div>
<div class="controls">
<input type="button" value="Play" id="video-btn">
<span id="curtime">0</span>/<span id="duration">0</span>
</div>
</div>
```

通过使用JavaScript 创建一个简单的视频播放器，上面这个基本的HTML 就可以被激活了，如下所示：

```javascript
// 取得元素的引用
const player = document.getElementById("player"),
btn = document.getElementById("video-btn"),
curtime = document.getElementById("curtime"),
duration = document.getElementById("duration");
// 更新时长
duration.innerHTML = player.duration;
// 为按钮添加事件处理程序
btn.addEventListener( "click", (event) => {
if (player.paused) {
player.play();
btn.value = "Pause";
} else {
player.pause();
btn.value = "Play";
}
});
// 周期性更新当前时间
setInterval(() => {
curtime.innerHTML = player.currentTime;
}, 250);
```

这里的JavaScript 代码简单地为按钮添加了事件处理程序，可以根据当前状态播放和暂停视频。此外，还给`<video>`元素的load 事件添加了事件处理程序，以便显示视频的时长。最后，重复的计时器用于更新当前时间。通过监听更多事件以及使用更多属性，可以进一步扩展这个自定义的视频播放器。同样的代码也可以用于`<audio>`元素以创建自定义的音频播放器。

### 19.5.4. 检测编解码器

如前所述，并不是所有浏览器都支持`<video>`和`<audio>`的所有编解码器，这通常意味着必须提供多个媒体源。为此，也有JavaScript API 可以用来检测浏览器是否支持给定格式和编解码器。这两个媒体元素都有一个名为canPlayType()的方法，该方法接收一个格式/编解码器字符串，返回一个字符串值："probably"、"maybe"或""（空字符串），其中空字符串就是假值，意味着可以在if 语句中像这样使用canPlayType()：

```javascript
if (audio.canPlayType("audio/mpeg")) {
// 执行某些操作
}
```

"probably"和"maybe"都是真值，在if 语句的上下文中可以转型为true。

在只给canPlayType()提供一个MIME 类型的情况下，最可能返回的值是"maybe"和空字符串。这是因为文件实际上只是一个包装音频和视频数据的容器，而真正决定文件是否可以播放的是编码。在同时提供MIME 类型和编解码器的情况下，返回值的可能性会提高到"probably"。下面是几个例子：

```javascript
const audio = document.getElementById("audio-player");

// 很可能是"maybe"
if (audio.canPlayType("audio/mpeg")) {
// 执行某些操作
}

// 可能是"probably"
if (audio.canPlayType("audio/ogg; codecs=\"vorbis\"")) {
// 执行某些操作
}
```

注意，编解码器必须放到引号中。同样，也可以在视频元素上使用canPlayType()检测视频格式。

### 19.5.5. 音频类型

`<audio>` 元素还有一个名为Audio 的原生JavaScript 构造函数，支持在任何时候播放音频。Audio类型与Image 类似，都是DOM元素的对等体，只是不需插入文档即可工作。要通过Audio 播放音频，只需创建一个新实例并传入音频源文件：

```javascript
const audio = new Audio("sound.mp3");

EventUtil.addHandler(audio, "canplaythrough", function(event) {
audio.play();
});
```

创建Audio 的新实例就会开始下载指定的文件。下载完毕后，可以调用play()来播放音频。

在iOS 中调用play()方法会弹出一个对话框，请求用户授权播放声音。为了连续播放，必须在onfinish 事件处理程序中立即调用play()。


## 19.6. 原生拖放

IE4 最早在网页中为JavaScript 引入了对拖放功能的支持。当时，网页中只有两样东西可以触发拖放：图片和文本。拖动图片就是简单地在图片上按住鼠标不放然后移动鼠标。而对于文本，必须先选中，然后再以同样的方式拖动。在IE4 中，唯一有效的放置目标是文本框。IE5 扩展了拖放能力，添加了新的事件，让网页中几乎一切都可以成为放置目标。IE5.5 又进一步，允许几乎一切都可以拖动（IE6 也支持这个功能）。HTML5 在IE 的拖放实现基础上标准化了拖放功能。所有主流浏览器都根据HTML5 规范实现了原生的拖放。

关于拖放最有意思的可能就是可以跨窗格、跨浏览器容器，有时候甚至可以跨应用程序拖动元素。浏览器对拖放的支持可以让我们实现这些功能。
