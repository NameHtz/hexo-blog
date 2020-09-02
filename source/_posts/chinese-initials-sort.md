---
title: 按照中文拼音首字母顺序排序
date: 2020-08-25 18:57:06
tags: 笔记、javascript
---

localeCompare() 方法返回一个数字来指示一个参考字符串是否在排序顺序前面或之后或与给定字符串相同。

<!-- more -->

新的 locales 、 options 参数能让应用程序定制函数的行为即指定用来排序的语言。  
locales 和 options 参数是依赖于具体实现的，在旧的实现中这两个参数是完全被忽略的。

```javascript
let arr = ["按", "照", "中", "文", "拼", "音", "首", "字", "母", "顺", "序", "排", "序"];
arr.sort((a, b) => a.localeCompare(b, "zh-Hans-CN", {sensitivity:"accent"}))
// ["按", "母", "排", "拼", "首", "顺", "文", "序", "序", "音", "照", "中", "字"]
```

[String.prototype.localeCompare()](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/localeCompare)
