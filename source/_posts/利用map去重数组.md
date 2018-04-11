---
title: 利用map去重数组
date: 2018-04-11 10:51:27
tags: 'js'
---

```
  function unique(arr) {
    var map = new Map()
    arr.forEach(v => map.set(v, 1))
    return [...map.keys()]
  }
  unique([1,1,2,2,3]) // [1,2,3]
```