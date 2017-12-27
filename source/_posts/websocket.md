---
title: websocket
date: 2017-12-27 14:38:46
tags: 'websocket'
---

WebSocket是基于HTTP协议的，或者说借用了HTTP的协议来完成一部分握手。 
只需要经过一次HTTP请求，就可以做到源源不断的信息传送了。(在程序设计中，这种设计叫做回调）。WebSocket只需要一次HTTP握手，所以说整个通讯过程是建立在一次连接/状态中，也就避免了HTTP的非状态性，服务端会一直知道你的信息，直到你关闭请求。

```
    //注意这里的协议变成了ws://
    var socket = new WebSocket('ws://www.example.com/server.php');
    socket.send('hello');
```

WebSocket只能发送纯文本信息，所以对于复杂的数据结构，在发送之前必须进行序列化。

```
   var message = {
       name: 'sysuzhyupeng',
       age: 24
   }
   socket.send(JSON.stringify(message));
```

当服务器向客户端发来消息时，WebSocket对象就会触发message事件。这个message事件与其他传递消息的协议类似，也是把返回的数据保存在event.data中

```
   socket.onmessage = function(event){
       var data = event.data;
   }
```

WebSocket的支持程度是IE 10+ Edge Firefox 4+ Chrome 4+ Safari 5+ Opera 11.5+