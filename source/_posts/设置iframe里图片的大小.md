---
title: 设置iframe里图片的大小
date: 2019-11-29 15:12:01
tags: iframe
categories: 问题
---
```javascript
let iframe = document.getElementById('myiframe');
let iwindow = iframe.contentWindow;
let idoc = iwindow.document;
let img = idoc.getElementsByTagName('img')[0];
img.width = iframe.clientHeight;
```
PS:第四行代码必须在iframe加载结束之后才能获取到