```javascript
/**
 * 检测一个函数是否以 new 方式调用
 * @param {Object} thisArg this 值
 * @param {*} constructor 一个函数
 * @returns {void}
 */
var checkCallAsConstructor = function checkCallAsConstructor(
  thisArg,
  constructor,
) {
  if (!(thisArg instanceof constructor))
    throw new TypeError(
      `${constructor.name}(): must be called as constructor!`,
    );
};

/**
 * 检测一个值是否可调用
 * @param {*} any 要检测的值
 * @returns {void}
 */
var checkCallable = function checkCallable(any) {
  if (!(typeof any === 'function')) {
    throw new TypeError(`${any} is not a function!`);
  }
};

/**
 * 使一个回调进入微任务队列
 * @param {Function} callback 微任务回调
 * @returns {void}
 */
var queueMicrotask = function queueMicrotask(callback) {
  checkCallable(callback);

  if (window.queueMicrotask) {
    return window.queueMicrotask(callback);
  } else {
    var flag = false;
    var textNode = document.createTextNode(String(flag));
    var observer = new MutationObserver(callback);
    observer.observe(textNode, {characterData: true});
    flag = !flag;
    textNode.nodeValue = String(flag);
  }
};

/**
 * 期约类 es5 实现
 * 已实现：状态机，期约内部值/原因，thenable 接口
 * 未实现：连锁调用等等
 */
var ES5Promise = (function () {
  var PENDING = 0;
  var FULFILLED = 1;
  var REJECTED = -1;

  /**
   * 获取内部 fulfill 函数
   * @param {Object} thisArg Promise 构造函数内的 this 对象
   * @returns {Function}
   */
  var _getInternalFulfill = function _getInternalFulfill(thisArg) {
    return function fulfill(value) {
      if (thisArg._status === PENDING) {
        thisArg._status = FULFILLED;
        thisArg._result = value;

        if (thisArg._onfullfilled.length > 0) {
          thisArg._onfullfilled.forEach(function (onFulfilled) {
            queueMicrotask(function () {
              onFulfilled(thisArg._result);
            });
          });
        }
      }
    };
  };

  /**
   * 获取内部 reject 函数
   * @param {Object} thisArg Promise 构造函数内的 this 对象
   * @returns {Function}
   */
  var _getInternalReject = function _getInternalReject(thisArg) {
    return function reject(reason) {
      if (thisArg._status === PENDING) {
        thisArg._status = REJECTED;
        thisArg._result = reason;

        if (thisArg._onrejected.length > 0) {
          thisArg._onrejected.forEach(function (onRejected) {
            queueMicrotask(function () {
              onRejected(thisArg._result);
            });
          });
        }
      }
    };
  };

  /**
   * 期约构造函数
   * @constructor
   * @param {function} executor 期约执行器
   * @returns {ES5Promise}
   */
  function ES5Promise(executor) {
    checkCallAsConstructor(this, ES5Promise);
    checkCallable(executor);

    // 期约状态
    this._status = PENDING;

    // 履行回调
    this._onfullfilled = [];

    // 拒绝回调
    this._onrejected = [];

    try {
      executor(_getInternalFulfill(this), _getInternalReject(this));
    } catch (error) {
      _getInternalReject(this)(error);
      throw new Error(error);
    }
  }

  /**
   * 期约字符串化表示
   * @returns {string}
   */
  ES5Promise.prototype.toString = function toString() {
    return '[object ES5Promise]';
  };

  /**
   * then 接口
   * @param {*} onFulfilled 解决回调
   * @param {*} onRejected 拒绝回调
   */
  ES5Promise.prototype.then = function then(onFulfilled, onRejected) {
    if (typeof onFulfilled !== 'function') {
      onFulfilled = function onFulfilled(value) {
        return value;
      };
    }

    if (typeof onRejected !== 'function') {
      onRejected = function onRejected(reason) {
        return reason;
      };
    }

    var self = this;

    switch (this._status) {
      case PENDING: {
        this._onfullfilled.push(onFulfilled);
        this._onrejected.push(onRejected);

        return undefined;
      }

      case FULFILLED: {
        queueMicrotask(function () {
          onFulfilled(self._result);
        });
      }

      case REJECTED: {
        queueMicrotask(function () {
          onRejected(self._result);
        });
      }

      default:
        break;
    }
  };

  return ES5Promise;
})();
```
