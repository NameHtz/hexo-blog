---
title: javaScript Array.map() Array.filter()
tags: javaScript
date: 2020-09-25 16:28:52
---

 `map()` 方法创建一个新数组，其结果是该数组中的每个元素是调用一次提供的函数后的返回值。
 
##### 语法:
```
var new_array = arr.map(function callback(currentValue[, index[, array]]) {
 // Return element for new_array 
}[, thisArg])
```
<!--more-->
##### 参数:
`callback`: 生成新数组元素的函数，使用三个参数:
   1. `currentValue`: (`callback` 数组中正在处理的当前元素)
   2. `index`: (`callback` 数组中正在处理的当前元素的索引)
   3. `array`: (`map` 方法调用的数组)

`thisArg`: (执行 `callback` 函数时值被用作`this`)

##### 例子:
```javascript
let list = [1,2,3,4]; 
let result = list.map(currentValue => currentValue * 2 );
console.log(result) // [2,4,6,8]
```

##### 实现一个 `map`
```javascript
/**
 * @param {Array}
 * @param{function}
 * @param{thisAgs}
 * @returns{Array}
 */
function map() {
  let [array, callback, thisArg] = [...arguments];
  if (!Array.isArray(array)) {
    throw new TypeError(array + ' is not a Array');
  }
  if (typeof callback !== 'function') {
    throw new TypeError(callback + ' is not a function');
  }
  let length = array.length;
  let result = new Array(length)
  for (let i = 0; i < length; i++) {
    if (i in array) {
      result[i] = callback.call(thisArg, array[i], i, array)
    }
  }
  return result
}
console.log(map([1, 2, 3, 4], (item) => ({num: item})))
```

`filter()` 方法创建一个新数组, 其包含通过所提供函数实现的测试的所有元素。

### 语法:

```
var newArray = arr.filter(callback(element[, index[, array]])[, thisArg])
```

##### 参数:

`callback`:用来测试数组的每个元素的函数。返回 true 表示该元素通过测试，保留该元素，false 则不保留。它接受以下三个参数:
   1. `element`: 数组中当前正在处理的元素
   2. `index`: (可选) 正在处理的元素在数组中的索引
   3. `array`: (可选) 调用了 filter 的数组本身

`thisArg` (可选) 执行 callback 时，用于 this 的值

##### 例子:

```javascript
let list = [1,2,3,4]; 
let result = list.filter(element => element > 2 );
console.log(result) // [3,4]
```

##### 实现一个 `filter`

```javascript
/**
 * @param {Array}
 * @param{function}
 * @param{thisAgs}
 * @returns{Array}
 */ 
function filter() {
  let [array, callback, thisArg] = [...arguments];
  if (!Array.isArray(array)) {
    throw new TypeError(array + ' is not a Array');
  }
  if (typeof callback !== 'function') {
    throw new TypeError(callback + ' is not a function');
  }
  let length = array.length;
  let result = []
  for (let i = 0; i < length; i++) {
    if (i in array && callback.call(thisArg, array[i], i, array)) {
      result.push(array[i])
    }
  }
  return result
}
console.log(filter([1, 2, 3, 4], (item) =>(item > 2)))
```