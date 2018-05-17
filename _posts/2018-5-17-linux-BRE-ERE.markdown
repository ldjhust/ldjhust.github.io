---
layout: post
title: "Linux - 基本正则表达式(BRE)与拓展正则表达式差异"
date: 2018-05-17 16:33
categories: Linux
comments: false
---


![](http://c.hiphotos.baidu.com/image/pic/item/0df3d7ca7bcb0a46f8c4938f6763f6246a60afa5.jpg)


基本正则表达式(BRE)与拓展正则表达式(ERE)的区别仅仅只在于元字符：
* BRE中只有 `^$.[]*` 是元字符
* ERE中 `^$.[]*+(){}?|` 都是元字符

ERE中新增加的元字符在BRE中只是普通的字符，如+在BRE中只能匹配加号。如果想在BRE中也表达特殊含义，那么就需要转义，例：
* echo “abcdefg” | grep ‘a.+g’ # 不匹配任何字符串
* echo “abcdefg” | grep ‘a.\+g’ # 匹配整个字符串
* echo “abcdefg” | grep –E ‘a.+g’ # 使用ERE，匹配整个字符串
* echo “abcdefg” | egrep ‘a.+g’ # ERE，匹配整个字符串

附Linux中个工具对正则表达式的支持情况：

![](../imgs/reference-article/tools.png)
