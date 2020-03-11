---
title: swiper相关问题
date: 2019-11-27 15:35:05
tags: swiper
categories: 问题
---
#### 一、swiper留白问题
在切换tab页面或下拉刷新过程中可能会因为内容的高度不同导致两个tab内容的高度相同，高度没有初始化，会造成留白等问题。解决方法：增加css即可。
```css
.swiper-slide{height:10px;}
.swiper-alide-active{height:auto;}
```
给swiper-slide加高度，每次切换就可以重置height。
#### 二、swiper动态从后台获取数据，滑动失败
##### 原因：因为swiper提前初始化了，那时数据还没出来
##### 解决方法：
1、使用$nextTick()方法
当Vue构造器里的data值被修改完成后会调用这个方法，也相当于一个钩子函数吧，和构造器里的updated生命周期很像
2、Swiper初始化时，加上这两句话：
![quest2](quest2.jpg)

 