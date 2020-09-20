---
title: javaScript Array some every
tags: javaScript
date: 2020-09-20 22:47:42
---


Array 里的每一项都满足条件 即返回 true 反之 false；

```javascript

const isBelowThreshold = (currentValue) => currentValue < 40;

const array1 = [1, 30, 39, 29, 10, 13];

console.log(array1.every(isBelowThreshold));  // true


```

Array 里只要有一项满足条件 即返回 true，每一项都不满足条件时返回 false；

```javascript

const array = [1, 2, 3, 4, 5];

const even = (element) => element % 2 === 0;

console.log(array.some(even)); // true

```