---
title: JSON序列化深度拷贝对象的毛病
date: 2019-02-18 19:35:12
tags: 'js'
---

## 如下： 
- 1.他无法实现对函数 、RegExp等特殊对象的克隆

- 2.会抛弃对象的constructor,所有的构造函数会指向Object

- 3.对象有循环引用,会报错

- 4.稀疏数组复制错误

```
// 构造函数
function person(pname) {
  this.name = pname;
}

const Messi = new person('Messi');

// 函数
function say() {
  console.log('hi');
};

const oldObj = {
  a: say,
  b: new Array(1),
  c: new RegExp('ab+c', 'i'),
  d: Messi
};

const newObj = JSON.parse(JSON.stringify(oldObj));

// 无法复制函数
console.log(newObj.a, oldObj.a); // undefined [Function: say]
// 稀疏数组复制错误
console.log(newObj.b[0], oldObj.b[0]); // null undefined
// 无法复制正则对象
console.log(newObj.c, oldObj.c); // {} /ab+c/i
// 构造函数指向错误
console.log(newObj.d.constructor, oldObj.d.constructor); // [Function: Object] [Function: person]

```

对象有循环引用,会报错的例子
```
const oldObj = {};

oldObj.a = oldObj;

const newObj = JSON.parse(JSON.stringify(oldObj));
console.log(newObj.a, oldObj.a); // TypeError: Converting circular structure to JSON
```