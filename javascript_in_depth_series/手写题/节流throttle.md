## 1. 简介

本文讲解了 **throttle(节流)** 函数的时间线回调调用的控制逻辑，并实现了一个基本的 throttle 函数。

- throttle 函数属于控制时间线上回调调用的一种函数。
- throttle 函数对在时间线上的多个回调，如果本次回调距离上次成功执行的回调之间的时间大于延迟则执行，否则不执行。

因此，throttle 函数多用于节省 scroll, mousemove, touchmove 类型的事件回调。

要实现这个 throttle 函数，首先得明白它的参数和返回值，以及关键的函数体逻辑。

## 2. throttle 函数的参数

一个节流函数必要的参数有 2 个: callback，delay。

- callback 就是我们需要节流的回调函数，比如：onScroll。
- delay 就是我们需要延长回调的时间间隔，比如：17(ms)。

## 3. throttle 函数的返回值

一个被节流的回调函数：throttledCallback。

## 4. throttle 函数的函数体逻辑

要知道这个逻辑，就需要清楚被节流的回调函数在时间线上的调用表现。

被节流的回调函数

1. 第 1 次(1th)被调用时，会发生什么？

立即执行

```javascript
callback.apply(null, arguments);
```

2. 2th 被调用，会发生什么？

测量和第 1 次回调之间的时间间隔，如果大于 delay 则执行本次回调，否则不执行。

```javascript
if (Date.now() - callTime1th > delay) callback.apply(null, arguments);
```

3. 3th

测量和上一次成功执行的回调之间的时间间隔，如果大于 delay 则执行本次回调，否则不执行。

```javascript
let lastTrulyCallbackTime;
const curCallbackTime = Date.now();

if (curCallbackTime - lastTrulyCallbackTime > delay) {
  lastTrulyCallbackTime = curCallbackTime;
  callback.apply(null, arguments);
}
```

统一逻辑:

```javascript
var lastTrulyCallbackTime = -Infinity; // 第1次肯定被执行
var curCallbackTime = Date.now();

if (curCallbackTime - lastTrulyCallbackTime > delay) {
  lastTrulyCallbackTime = curCallbackTime;
  callback.apply(null, arguments);
}
```

## 5. 最终实现

```javascript
/**
 *
 * @param {Function} callback 要节流的回调函数
 * @param {number} delay 需要延迟调用的时间
 * @returns {Function} 已经被节流的回调函数
 */
var throttle = function throttle(callback, delay) {
  var lastTrulyCallbackTime = -Infinity;

  return function throttledCallback() {
    var curCallbackTime = Date.now();

    if (curCallbackTime - lastTrulyCallbackTime > delay) {
      lastTrulyCallbackTime = curCallbackTime;
      callback.apply(null, arguments);
    }
  };
};
```

## 6. 测试

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta
      name="viewport"
      content="width=device-width, initial-scale=1.0, user-scalable=no"
    />
    <title>节流函数测试</title>
    <style>
      body {
        margin: 0;
        display: flex;
        height: 100vh;
        align-items: center;
        flex-wrap: wrap;
      }
      *.item {
        width: 250px;
        height: 250px;
        margin: 0 auto;
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: larger;
      }
    </style>
  </head>
  <body>
    <div class="item" style="background-color: red" id="item1">0</div>
    <div class="item" style="background-color: blue" id="item2">0</div>
  </body>
  <script defer>
    var $ = document.querySelector.bind(document);

    var handleMousemove = function (event) {
      event.target.innerHTML = parseInt(event.target.innerHTML) + 1;
    };

    var throttle = function throttle(callback, delay) {
      var lastTrulyCallbackTime = -Infinity;

      return function throttledCallback() {
        var curCallbackTime = Date.now();

        if (curCallbackTime - lastTrulyCallbackTime > delay) {
          lastTrulyCallbackTime = curCallbackTime;
          callback.apply(null, arguments);
        }
      };
    };

    $('#item1').addEventListener('mousemove', handleMousemove);
    $('#item2').addEventListener('mousemove', throttle(handleMousemove, 17));
  </script>
</html>
```
