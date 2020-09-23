---
title: JS Array 里找出，最大值、最小值
tags: javaScript
date: 2020-09-23 10:35:30
---

#### Math
+ max
```javascript
function max(arr) {
  return Math.max.apply(null, arr);
}
let list = [5,4,3,0,2,9];
max(list) // 9
```
<!-- more -->
+ min 
```javascript
function min(arr) {
  return Math.min.apply(null, arr);
}
let list = [5,4,3,0,2,9,100,1024,32,16,8,21,30];
min(list) // 0
```
<b class="bgc-e4e6e8">Math.min</b>  <b class="bgc-e4e6e8">Math.max</b> 都比较消耗堆栈  


#### reduce
+ max
```javascript
function max(arr) {
  return arr.reduce((a,b) => (a > b ? a : b))
}
let list = [5,4,3,0,2,9,100,1024,32,16,8,21,30];
max(list) // 1024
```
+ min
```javascript
function min(arr) {
  return arr.reduce((a,b) => (a < b ? a : b))
}
let list = [5,4,3,0,2,9,100,1024,32,16,8,21,30];
min(list) // 0
```
