---
title: 上传本地项目到github
date: 2020-03-09 11:09:01
tags: github
categories: 问题
---
##### ● 把这个目录变成Git可以管理的仓库
```
$ git init
```
##### ● 文件添加到仓库，不但可以跟单一文件，还可以跟通配符，更可以跟目录。一个点就把当前目录下所有未追踪的文件全部add了(git add .)。
```
git add <要添加的文件名/通配符/目录>
```
##### ● 把文件提交到仓库
```
git commit -m "<提交说明>"
[master (root-commit) 716f6f0] test commit
1 file changed, 0 insertions(+), 0 deletions(-)
create mode 100644 README.md
```
##### ● 关联远程仓库
```
git remote add origin <远程仓库地址>
```
##### ● 把本地库的所有内容推送到远程库上
``` 
git push -u origin master
```