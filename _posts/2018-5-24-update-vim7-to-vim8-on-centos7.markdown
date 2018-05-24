---
layout: post
title: "Linux - 在CentOS7上两步升级VIM7到VIM8"
date: 2018-05-24 16:36
categories: Linux
comments: false
---


![](http://e.hiphotos.baidu.com/image/pic/item/d6ca7bcb0a46f21fca6fafecfa246b600c33ae32.jpg)

1. 准备`VIM8`的`YUM`源
```
sudo curl -L https://copr.fedorainfracloud.org/coprs/mcepl/vim8/repo/epel-7/mcepl-vim8-epel-7.repo -o /etc/yum.repos.d/mcepl-vim8-epel-7.repo
```

2. 升级`VIM`
```
sudo yum -y update vim*
```

