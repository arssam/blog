---
title: exports 和 module.exports 的区别
date: 2018-01-03 17:32:18
tags: 'node'
---

1. module.exports 初始值为一个空对象 {}
2. exports 是指向的 module.exports 的引用
3. require() 返回的是 module.exports 而不是 exports

类似于：
```
var module.exports = {}
exports = module.exports
```