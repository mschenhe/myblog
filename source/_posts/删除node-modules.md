---
title: 快速删除node-modules
date: 2020-03-09 10:44:38
tags: node-modules
categories: 问题
---
##### 解决方法：使用npm的一个名为rimraf的模块进行删除
##### ● 安装(推荐全局安装)：
```
npm install -g rimraf
```
##### ● 使用：
```
cd xxx [the folder which includes node_modules folder]
rimraf node_modules
```