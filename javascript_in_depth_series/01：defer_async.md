**目录：**

- [1. 推迟执行脚本](#1-推迟执行脚本)
- [2. 异步执行脚本](#2-异步执行脚本)

## 1. 推迟执行脚本

HTML 4.01 为`<script>`元素定义了一个叫 defer 的属性。当浏览器解析到带有 defer 属性的脚本时，浏览器会并行地下载该脚本，并行的意思是它不会像正常脚本那样在下载时阻塞后面的 HTML 解析，当整个 HTML 文件解析完毕时，带有 defer 属性的脚本才会按照他们出现的顺序执行。

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

## 2. 异步执行脚本

HTML5 为`<script>`元素定义了 async 属性。当浏览器解析到带有 async 属性的脚本时，浏览器会并行地下载该脚本，并行的意思是它不会像正常脚本那样在下载时阻塞后面的 HTML 解析，当该脚本下载完毕时，该脚本会被立即执行，这和 defer 不同，脚本执行时会阻塞后面的 HTML 解析。

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

当出现另一个 async 脚本时，同样的，浏览器会并行地下载它，但是由于不能准确地知道哪个脚本先下载完毕，所以多个异步脚本可能不会以他们出现的顺序执行。

异步脚本保证会在页面的 load 事件前执行，但可能会在 DOMContentLoaded（参见第 17 章）之前或之后。Firefox 3.6、Safari 5 和 Chrome 7 支持异步脚本。使用 async 也会告诉页面你不会使用 document.write，不过好的 Web 开发实践根本就不推荐使用这个方法。

下图总结了普通脚本，异步脚本和延迟脚本的特点：

![2-3-async-defer](illustrations/2-3-async-defer.svg)
