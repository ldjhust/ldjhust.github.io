---
layout: post
title: "python - 手动安装 pip"
date: 2017-9-30 16:06
categories: python
comments: false
---

![](https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1506768797619&di=864f4b0a9cfe6dcb9d06d66fa3ff2631&imgtype=0&src=http%3A%2F%2Fc.hiphotos.baidu.com%2Fimage%2Fpic%2Fitem%2Fc9fcc3cec3fdfc03e8419f78dd3f8794a4c22630.jpg)

1. 先安装 setuptools

   a. 从 https://pypi.doubanio.com/simple 下载最新的 setuptools 安装包（xxx.tar.gz）
   b. 解压 tar -xvf xxx.tar.gz
   c. cd 到解压出的目录
   d. 执行 python setup.py install

2. 在安装 pip

   a. 从 https://pypi.doubanio.com/simple 下载最新的 pip 安装包 (xxx.tar.gz)
   b. 解压 tar -xvf xxx.tar.gz
   c. cd 到解压出的目录
   d. 执行 python setup.py install
   e. 执行 pip -V 查看版本号以及检验 pip 是否安装成功
