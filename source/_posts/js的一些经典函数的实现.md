---
title: js的一些经典函数的实现
date: 2019-01-21 11:02:33
tags: 'js'
---

1. bind函数
```
Function.prototype.Bind = Function.prototype.Bind || function(obj) {
  return function() {
    return this.apply(obj, arguments)
  }
}
```

2. new的实现
```
function create() {
	// 创建一个空的对象
    var obj = new Object(),
	// 获得构造函数，arguments中去除第一个参数
    Con = [].shift.call(arguments);
	// 链接到原型，obj 可以访问到构造函数原型中的属性
    obj.__proto__ = Con.prototype;
	// 绑定 this 实现继承，obj 可以访问到构造函数中的属性
    var ret = Con.apply(obj, arguments);
	// 优先返回构造函数返回的对象
	return ret instanceof Object ? ret : obj;
}
```
