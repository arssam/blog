---
title: 简单的实现js双向绑定
date: 2018-04-11 10:50:29
tags: 'js'
---

```
    var obj = {};
    var qq = {}
    qq.hello1 = '1'
    Object.defineProperty(obj,'hello',{
        set:function(val){
            document.getElementById('bb').innerHTML = val;
            document.getElementById('aa').value = val;
        }
    });
    document.getElementById('aa').onkeyup = function(e){
        obj.hello = e.target.value;
    };
    obj.hello = "";

```