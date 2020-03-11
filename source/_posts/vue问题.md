---
title: vue问题
date: 2019-12-09 14:49:58
tags: vue
categories: vue
---
##### 一、使用 ES7的async/await时报错。Uncaught ReferenceError: regeneratorRuntime is not defined
1、原因：这个regeneratorRuntime在浏览器上是不认识的，通过百度，需要安装一个babel-plugin-transform-runtime插件
2、解决方法：
```
npm i --save-dev babel-plugin-transform-runtime
```
在.babelrc文件中添加:
```
"plugins":[
  [
    "transform-runtime",
    {
      "helpers":false,
      "polyfill":false,
      "regenerator":true,
      "moduleName":"banel-runtime"
    }
  ]
]
```