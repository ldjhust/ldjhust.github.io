---
layout: post
title: "Linux - 删除 /swapfile1 报not permitted"
date: 2018-04-18 14:46
categories: Linux
comments: false
---


![](http://c.hiphotos.baidu.com/image/pic/item/7acb0a46f21fbe09810db97167600c338744ad00.jpg)

告警系统突然告警 `/` 分区磁盘容量不足，实际查看是发现是因为交换分区生成 `/swapfile1` 占了空间，需要删除 `/swapfile1`：
```
sudo rm /swapfile1
```

执行如上命令时系统报错：
```
rm: cannot remove `/swapfile1': Operation not permitted
```

经过查询是因为 `swap` 还没有关闭，`/swapfile1` 还在使用中所以无法删除，应该先关闭，再删除：
```
sudo swapoff /swapfile1
sudo rm /swapfile1
```
