---
title: react样式污染处理
date: 2019-11-27 15:41:12
tags: react
categories: react
---
在vue中可通过scope来设置样式私有，在react中可通过css modules实现样式私有。
链接：https://juanha.github.io/2017/01/10/react-css-modules/
#### 一、使用xx.module.css来设置样式
在文件中引入css文件：
```
import styles from ‘./table.css’
```
将类名设置成style.xx的形式：
```html
<div className={styles.table}></div>
```
![pic1](pic1.jpg)
组件渲染后类名后会跟着一串字符串：
![pic2](pic2.jpg)
同时还会生成一个以hash映射形式来匹配相应的类名的table.css.js文件
![pic3](pic3.jpg)
同时还提供compose组合方法来处理样式复用：
![pic4](pic4.jpg)
##### 优点：
1、所有样式都是局部化的，解决了命名冲突和全局污染问题
2、Class名的生成规则配置灵活
3、引入组件，只需引用组件的js文件，不需要额外去引入css文件
4、依然是css，学习成本几乎为零
##### 缺点：
1、必须使用驼峰式的命名（若以’-‘命名，则需要通过styles[]这种形式关联）
2、需要频繁的输入style.**
3、引用一个未定义的css模块时解析结果为undefined，但并无警告提示
#### 二、Css modules实现了自动化映射css modules，扩展了render方法，根据styleName的值去在关联的styles对象中查找相应的css-modules，并给每个css类赋予一个带有全局唯一名字的本地标识符的类名。
![pic5](pic5.jpg)
React css modules提供了options作为第三个参数来对css modules的配置：
1、allowMultiple默认为false
2、errorWhenNotFound默认为true
```
CSSModules(Component, styles, options); 
options = { allowMultiple: false, errorWhenNotFound: true }
```
##### 优点：
1、不再关注是否使用驼峰来命名class名
2、不再每次使用css modules都用style.**来关联对象
3、通过
```html
<div className="global-css" styleName="local-css"></div>
```
明显区分全局css和css modules
4、当styleName关联一个undefined css modules时，会得到一个警告信息(errorWhenFound option)
5、强制使用一个css modules，推崇使用css modules的样式组合(allowMultiple option)
 