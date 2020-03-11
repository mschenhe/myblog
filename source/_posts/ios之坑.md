---
title: ios之坑
date: 2019-12-20 15:03:15
tags: ios
categories: 问题
---
#### 一、ios移动端软键盘收起后input输入框焦点错位或无法输入
##### 问题：点击时间插件选择时间之后无法在input中输入文本
##### 解决方法：
```javascript
$('input').on('blur',function(){
  window.scroll(0,0)
})
```
##### 链接：https://blog.csdn.net/mf_9_5_2_7/article/details/100940795
#### 二、input边框有阴影
##### 解决：
```css
input{
  outline: none;
  -webkit-appearance: none; /*去除系统默认的样式*/
  -webkit-tap-highlight-color: rgba(0, 0, 0, 0); /* 点击高亮的颜色*/
}
```
