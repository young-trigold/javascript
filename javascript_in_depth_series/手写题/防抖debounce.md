## 1. 简介

本文讲解了 **debounce(防抖)** 函数的逻辑，并实现了一个基本的 debounce 函数。

- debounce 函数属于控制回调在时间线上调用的一种函数。
- debounce 函数对在时间线上连续调用的多个回调，只在延迟一定时间后触发最后一次回调。

因此，debounce 函数多用于 input, resize 类型的事件回调。

要实现这个 debounce 函数，首先得明白它的参数和返回值，以及关键的函数体逻辑。

## 2. debounce 函数的参数

一个防抖函数必要的参数有 2 个: callback, wait。

- callback 就是我们需要防抖的回调函数，比如: onInput。
- wait 就是我们需要延长回调调用的时间，比如: 500(ms)。

## 3. debounce 函数的返回值

一个被防抖的回调函数：debouncedCallback。

## 4. debounce 函数的函数体逻辑

要知道这个逻辑，就需要清楚被防抖的回调函数在时间线上的调用表现。

防抖回调函数的

1. 第 1 次（1th）被调用时，会发生什么？

会等待 wait 时间后，被执行。

```javascript
delayedCallback1th = setTimeOut(() => callback(...arguments), wait);
```

2. 2th 被调用，会发生什么？

这要看 2th 是不是被“连续调用”的。如果和 1th 调用的时间差小于 wait，那么判定为“连续调用”。
此时，根据防抖函数连续调用回调时，只执行最后一次回调的原则，那么 1th 回调在 wait 时间后不能被执行。
本次回调应该在 wait 时间后执行，如果不是连续调用的，则 1th 应该被执行，2th 应在 wait 时间后执行。

```javascript
clearTimeout(delayedCallback1th);
delayedCallback2th = setTimeout(() => callback(...arguments), wait);
```

3. nth

依次类推。

```javascript
clearTimeout(delayedCallbackn-1th)
delayedCallbacknth = setTimeout(() => callback(...arguments), wait)
```

统一逻辑:

```javascript
lastCallback; //用于保存最后一次的延时回调
clearTimeout(lastCallback); //这对于第 1 次回调是无效的
lastCallback = setTimeout(() => callback(...arguments), wait);
```

不需要判断不是连续调用的情况，因为在这种情况下，clearTimeout(delayedCallback1th) 是无效的

## 5. 最终实现

```javascript
/**
 *
 * @param {Function} callback 要防抖的回调函数
 * @param {number} wait 需要延迟调用的时间
 * @returns {Function} 已经被防抖的回调函数
 */
var debounce = function debounce(callback, wait) {
  var lastCallback;

  return function debouncedCallback() {
    clearTimeout(lastCallback);

    lastCallback = setTimeout(function () {
      callback.apply(null, arguments);
    }, wait);
  };
};
```

## 6. 测试

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
    <meta
      name="viewport"
      content="width=device-width, minimum-scale=1.0, maximum-scale=1.0, user-scalable=no"
    />
    <title>防抖函数测试</title>
  </head>
  <body>
    <p>
      <input type="text" id="input1" />
      <span id="span1"></span>
    </p>
    <p>
      <input type="text" id="input2" />
      <span id="span2"></span>
    </p>

    <script defer>
      var $ = document.querySelector.bind(document);
      var log = console.log;

      var input1 = $('#input1');
      var input2 = $('input#input2');
      var span1 = $('#span1');
      var span2 = $('#span2');

      var onInput1 = (event) => {
        span1.innerHTML = event.target.value;
      };

      input1.addEventListener('input', onInput1);

      var onInput2 = (event) => {
        span2.innerHTML = event.target.value;
      };

      var debounce = function debounce(callback, wait) {
        var lastCallback;

        return function debouncedCallback() {
          clearTimeout(lastCallback);

          lastCallback = setTimeout(function () {
            callback.apply(null, arguments);
          }, wait);
        };
      };

      input2.addEventListener('input', debounce(onInput2, 250));
    </script>
  </body>
</html>
```
