---
layout: post
title: "Linux - Linux知识点总结"
date: 2018-01-22 15:09
categories: Linux
comments: false
---

![](http://f.hiphotos.baidu.com/image/pic/item/503d269759ee3d6db032f61b48166d224e4ade6e.jpg)

1 sudo echo x > /path/to/file 时 Permission denied
```
分析：
echo 是一个 shell 命令，> or >> 也是一个 shell 命令，前面的 sudo 只能保证 echo 有 root 权限，但是 > or >> 却还是普通用户的权限

解决：
1. 用 sh -c 或 bash -c 将后面的命令全部抱起来，这里包起来的命令就都有 root 权限了
   sudo sh -c "echo x > /path/to/file" or sudo bash -c "echo x > /path/to/file"
   
2. 利用 tee 命令
   echo x | sudo tee /path/to/file
   echo x | sudo tee -a /path/to/file，-a 相当于 >>
```
