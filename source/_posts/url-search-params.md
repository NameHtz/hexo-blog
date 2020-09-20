---
title: URLSearchParams
date: 2020-08-31 08:18:09
tags: javaScript
---

URLSearchParams

```javascript
let params = new URLSearchParams(window.location.search);
params.has('name') // true
params.get('name') // js

params.set('age', '24');
params.toString(); // name=js&age=24

params.delete('age');
params.toString(); // name=js
 
```