---
title: javaScript Array.reduce()
tags: javaScript
---

`reduce()` 方法对数组中的每个元素执行一个由您提供的**reducer**函数(升序执行)，将其结果汇总为单个返回值。

##### 语法:

```
arr.reduce(callback(accumulator, currentValue[, index[, array]])[, initialValue])
```
<!--more-->
##### 参数:

`callback`: 执行数组中每个值 (如果没有提供 `initialValue则第一个值除外`)的函数，包含四个参数:
   1. `accumulator`: 累计器累计回调的返回值; 它是上一次调用回调时返回的累积值，或`initialValue`（见于下方)
   2. `currentValue`: 数组中正在处理的元素
   3. `index`: (可选) 数组中正在处理的当前元素的索引。 如果提供了`initialValue`，则起始索引号为0，否则从索引1起始
   4. `array`: (可选) 调用`reduce()`的数组
`initialValue`: (可选) 作为第一次调用 `callback`函数时的第一个参数的值。 如果没有提供初始值，则将使用数组中的第一个元素。 在没有初始值的空数组上调用 reduce 将报错

##### 例子：

```javascript
[0, 1, 2, 3, 4].reduce(function(accumulator, currentValue, currentIndex, array){
  return accumulator + currentValue;
});
// 10
```

##### 实现一个 reduce

```javascript
/**
 * @param {Array}
 * @param{function}
 * @param{initialValue}
 * @returns{callback 处理后的结果}
 */ 
function reduce() {
  let [array, callback, initialValue] = [...arguments];
  let accumulator = initialValue || array[0];
  let startIndex = initialValue ? 0 : 1;
  for (let i = startIndex; i < array.length; i++){
    accumulator = callback(total, array[i], i, array)
  }
  return accumulator
}
let num = reduce([1,2,3,4],function(total, value){return total = total + value},0); // 10
```

##### 用 reduce 实现 map

```javascript
/**
 * @param {Array}
 * @param{function}
 * @param{thisAgs}
 * @returns{Array}
 */ 
function mapUsingReduce() {
  let [array, callback, thisArg] = [...arguments];
  if (!Array.isArray(array)) {
    throw new TypeError(array + ' is not a Array');
  }
  if (typeof callback !== 'function') {
    throw new TypeError(callback + ' is not a function');
  }
  return array.reduce(function (accumulator, currentValue, index, array) {
    accumulator[index] = callback.call(thisArg, currentValue, index, array);
    return accumulator
  }, [])
}
mapUsingReduce([1,2,3,4,5], function(value){return value * 2}) // [2, 4, 6, 8, 10]
```

##### 用 reduce 实现 filter


```javascript
/**
 * @param {Array}
 * @param{function}
 * @param{thisAgs}
 * @returns{Array}
 */ 
function filterUsingReduce() {
  let [array, callback, thisArg] = [...arguments];
  if (!Array.isArray(array)) {
    throw new TypeError(array + ' is not a Array');
  }
  if (typeof callback !== 'function') {
    throw new TypeError(callback + ' is not a function');
  }
  return array.reduce(function (accumulator, currentValue, index, array) {
    //accumulator
    if(callback.call(thisArg, currentValue, index, array)) {
      accumulator.push(currentValue)
    };
    return accumulator
  }, [])
}
filterUsingReduce([1,2,3,4,5,6], function(value){return value > 3}) //[4, 5, 6]
```