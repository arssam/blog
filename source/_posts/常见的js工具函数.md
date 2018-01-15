---
title: 常见的js工具函数
date: 2018-01-15 11:48:01
tags:
---

## 1. 获取查询参数
```
function query() {
  var search = window.location.search,
			args = search.substring(1).split('&'),
			obj = {},
			key,
			value
  args.forEach(v => {
    if (v.indexOf('=') === -1) {
			obj[decodeURIComponent(v)] = true
    } else {
    	[key, value] = v.split('=')
    	obj[key] = value
    }
  })
 return obj
}

// use:
	```
	url: xxxx.com?a=1
	var { a } = query()
	```

	```
	url: xxx.com?a=1&b=2
	var obj = query()
	console.log(obj) // {a:1,b:2}
	```


## 2. 时间日期格式化
```
Date.prototype.Format = function (fmt) {
    var o = {
        "M+": this.getMonth() + 1, //月份 
        "d+": this.getDate(), //日 
        "h+": this.getHours(), //小时 
        "m+": this.getMinutes(), //分 
        "s+": this.getSeconds(), //秒 
        "q+": Math.floor((this.getMonth() + 3) / 3), //季度 
        "S": this.getMilliseconds() //毫秒 
    };
    if (/(y+)/.test(fmt)) fmt = fmt.replace(RegExp.$1, this.getFullYear().toString().substr(4 - RegExp.$1.length));
    for (var k in o)
        if (new RegExp("(" + k + ")").test(fmt)) fmt = fmt.replace(RegExp.$1, (RegExp.$1.length == 1) ? (o[k]) : (("00" + o[k]).substr(("" + o[k]).length)));
    return fmt;
}

// use:
new Date().Format('yyyy') // 2018
new Date().Format('yyyyMMdd') // 20180115
new Date().Format('yyyyMMdd hh:mm:ss') // 20180115 12:36:50
```


## 3. 获取变量的数据类型
```
function toType(obj) { 
	return Object.prototype.toString.call(obj).match(/\s([a-zA-Z]+)/)[1].toLowerCase();
}

// use:
var obj = {}
var s = ''
toType(obj) // 'object'
toType(obj) // 'string'
```

## 4. 生成随机数
```
function getUuid() { 
	return Math.random().toString(36).substring(2) + (new Date()).getTime().toString(36);
}

// use:
getUUid() // "ray2e4mihzjcfq5fll"
```