---
layout: post
title: "Linux - CentOS7 安装python3"
date: 2018-04-09 16:44
categories: Linux
comments: false
---

`CentOS` 默认提供的`Python`是`2.x`，通过如下步骤安装`Python3`：

1. sudo yum install epel-release
2. sudo yum list python3* # 查看有哪些python3的版本
3. sudo yum install -y python36 # 这里以安装python3.6的版本为例
