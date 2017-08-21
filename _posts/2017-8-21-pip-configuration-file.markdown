---
layout: post
title: "技术 - pip 配置文件详解"
date: 2017-08-21 11:00
categories: 技术
comments: false
---

![](https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1503295044039&di=8b18bbd2d59633dc5fb88c00a343b727&imgtype=jpg&src=http%3A%2F%2Fd.hiphotos.baidu.com%2Fimage%2Fpic%2Fitem%2Fbd3eb13533fa828b755a7b8ef71f4134970a5a66.jpg)

`pip` 是 `python` 的包管理工具，利用 `pip` 我们可以非常轻松的管理第三方库。这里简单罗列一下 `pip` 的配置文件的常用配置。`pip` 配置文件名为 `pip.conf`，存在于当前用户目录下——`~/.pip/pip.conf`只对当前用户起作用，存在于`/etc/pip.conf`目录下对所有用户起作用。

* **网络代理**

```
[global]
proxy = http://<proxy host>:<proxy port>
```

* **设置新的源，这里使用阿里的源，速度比较快**

```
[global]
trusted-host = mirrors.aliyun.com
index-url = http://mirrors.aliyun.com/pypi/simple
```
