---
title: websocket
date: 2019-11-27 15:31:35
tags: websocket
categories: 学习
---
1、websocket连接必须由浏览器发起，因为请求协议是一个标准的HTTP协议
2、GET请求的地址不是类似于/path/，而是以ws://开头的地址。例如new Socket(‘ws://xxx’,callbackFun)。callbackFun是回调函数
3、建立连接之后加一个定时器，每隔一分钟二维码失效，需要点击刷新
```javascript
function Socket(url, callback) {
  var socket = new WebSocket(url);
  var t;
  //开启连接websocket
  socket.onopen = function(event) {
    //向后台发送消息，触发后台监听器
    console.log("连接成功！");
    t = setTimeout(
      function() {
        //先清空再修改图片
        $('#qrcode').html(" ");
        var txt = "<img src='images/km/usersystem/login/icon_ewmsx.svg' width='170px' height='170px'>";//二维码失效
        $('#qrcode').append(txt);
        //断开链接
        websocket.onclose();
      }, 60000);
}
 
//监听后台发送的消息
socket.onmessage = function(event) {
          callback(event);
}
 
//连接关闭
socket.onclose = function(event) {
  console.log("连接关闭");
  if (undefined != socket) {
    socket.close();
  }
   if (undefined != t) {
     clearTimeout(t);
     t = undefined;
   }
}
 
//连接出错
socket.onerror = function(event) {
  console.log("连接出错");
  $_websocket = null;
  socket.close();
}
  return socket;
}
```
4、
```javascript
//回调方法，处理接受前台的消息
function callbackFun(event) {
  var jsonStr = event.data;
  var data = JSON.parse(jsonStr);
  var sessionid = data.webSocketID;
  if (undefined != sessionid) {
    var str = "http://10.6.246.227:8099/login/qrlogin1?upesntype=urlWithUserCode&webSocketID="+ sessionid; //确认登录的页面
    console.log(str);
    if (undefined == $().qrcode) {
      $_qrcode($);
    }
    $('#qrcode').html(" ");
    $('#qrcode').qrcode({//使用qrcode生成二维码
      text : str,
      height : 170,
      width : 170
    });//str地址      
  }
  var usercode = data.usercode;
   if (undefined != usercode) {
     //调用登录
     dimensionLogin(usercode)
     //断开连接
     websocket.onclose();
   }
 
}
```
