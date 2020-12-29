---
title: requestIdleCallback
date: 2020-12-10 16:55:52
tags: javaScript
---

<b class="bgc-a5673f">记录</b>

来自 `MDN`

[requestIdleCallback](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/requestIdleCallback)

`window.requestIdleCallback()`方法将在浏览器的空闲时段内调用的函数排队。这使开发者能够在主事件循环上执行后台和低优先级工作，而不会影响延迟关键事件，如动画和输入响应。函数一般会按先进先调用的顺序执行，然而，如果回调函数指定了执行超时时间`timeout`，则有可能为了在超时前执行函数而打乱执行顺序。


你可以在空闲回调函数中调用requestIdleCallback()，以便在下一次通过事件循环之前调度另一个回调。

##### 语法

`javascript
 var handle = window.requestIdleCallback(callback[, options])
`