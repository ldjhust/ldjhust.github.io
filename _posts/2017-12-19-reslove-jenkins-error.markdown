---
layout: post
title: "持续集成 - Jenkins 错误及解决方案汇总"
date: 2017-12-19 14:40
categories: 持续集成
comments: false
---

![](http://f.hiphotos.baidu.com/image/pic/item/060828381f30e92465709cfb45086e061c95f720.jpg)

| 问题 | 解决方法 |
| --- | --- |
| java.lang.Error: java.lang.reflect.InvocationTargetException | 删除Jenkins所在目录下plugins目录下的所有插件，然后重启jenkins服务，centos系统上Jenkins所在目录为：/var/lib/jenkins |
