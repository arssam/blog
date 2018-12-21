---
title: 总结出现 undefined 值的情形
date: 2018-12-19 15:07:41
tags: 'js'
---

## 总结出现 undefined 值的情形
  1. 什么是 undefined
  undefined是js的基本数据类似Undefined的值，也是它的唯一值

  2. 为什么要特别注意编码过程工出现undefined的情况，先来看看以下熟悉的报错
  · TypeError: 'undefined' is not a function
  · TypeError: Cannot read property '' of undefined
  以上情况的出现会导致js直接抛出错误，终止程序的运行。

  3. 出现 undefined 值的情形
  · 未初始化的变量
```
let myVariable;  
myVariable; // => undefined 
```
  tips：
  1. 优先使用 const，其次是 let，对 var 说再见

  · 访问对象不存在的属性
```
let favoriteMovie = {  
  title: 'Blade Runner'
};
favoriteMovie.actors; // => undefined  
```
  tips: 
  1. 检查属性的存在
  - obj.prop !== undefined: 和 undefined 直接比较
  - typeof obj.prop !== 'undefined': 验证属性值类型
  - obj.hasOwnProperty('prop'): 验证对象是否有自己的属性
  - 'prop' in obj: 验证对象是否有自己的或继承的属性
  推荐使用in操作符， 语法简洁
  2. 使用解构来访问对象属性
```
const object = {  };  
const { prop = 'default' } = object;  
prop; // => 'default' 
```
  3. 使用默认属性来填充对象
```
const unsafeOptions = {  
  fontSize: 18
};
const defaults = {  
  fontSize: 16,
  color: 'black'
};
const options = {  
  ...defaults,
  ...unsafeOptions
};
options.fontSize; // => 18  
options.color;    // => 'black'  
```


  · 数组越界访问
```
const colors = ['blue', 'white', 'red'];  
colors[5];  // => undefined  
colors[-1]; // => undefined 
```
  · 缺省的函数参数
  函数的参数隐式默认为 undefined
  tips: 
  1. 使用es6的函数的默认参数
  ```
  function multiply(a, b = 2) {  
    a; // => 5
    b; // => 2
    return a * b;
  }
  multiply(5);            // => 10  
  multiply(5, undefined); // => 10  
```

  · 调用没有任何返回值的函数
  ```
  function square(x) {  
    const res = x * x;
  }
  square(2); // => undefined  
  ```
  · void 操作符
  void 表达式会对表达式进行求值，但无论求值结果是什么，它均是返回 undefined：
  ```
void 1;                    // => undefined  
void (false);              // => undefined  
void {name: 'John Smith'}; // => undefined  
```