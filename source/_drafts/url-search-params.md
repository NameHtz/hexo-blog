---
title: URLSearchParams
tags:
---

```javascript
let params = new URLSearchParams(window.location.search);
params.has('name') // true
params.get('name') // js

params.set('age', '24');
params.toString(); // name=js&age=24

params.delete('age');
params.toString(); // name=js
 
```