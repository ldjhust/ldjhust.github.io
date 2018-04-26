---
layout: post
title: "Linux - lsof 常用方式"
date: 2018-04-26 14:33
categories: Linux
comments: false
---


![](http://d.hiphotos.baidu.com/image/pic/item/bd315c6034a85edff62cdd7045540923dc5475c4.jpg)


1. 查看某个进程打开了哪些文件
```
lsof –c 进程名
lsof –p 进程号
```

2. `lsof` 常用方式
```
lsof abc.txt 显示开启文件abc.txt的进程
lsof -i :22 知道22端口现在运行什么程序
lsof -c nsd 显示nsd进程现在打开的文件
lsof -g gid 显示归属gid的进程情况
lsof +d /usr/local/ 显示目录下被进程开启的文件
lsof +D /usr/local/ 同上，但是会搜索目录下的目录，时间较长
lsof -d 4 显示使用fd为4的进程
lsof -i [i] 用以显示符合条件的进程情况
```
