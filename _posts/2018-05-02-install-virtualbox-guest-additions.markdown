---
layout: post
title: "Linux - CentOS/Fedora 安装VirtualBox Guest Additions"
date: 2018-05-02 17:28
categories: Linux
comments: false
---


![](http://c.hiphotos.baidu.com/image/pic/item/e1fe9925bc315c609e11bbb781b1cb13485477e6.jpg)


1. 切换到`root`账户
```
su - root
```

2. 更新`kernel`
```
## Fedora 28/27/26/25/24/23/22 ##
dnf update kernel*

## Fedora 21/20/19/18/17, CentOS/RHEL 7/6 ##
yum update kernel*

# 更新之后需要重启
reboot
```

3. 挂载`VirtualBox Guest Additions`
```
mkdir /media/VirtualBoxGuestAdditions
mount -r /dev/cdrom /media/VirtualBoxGuestAdditions
```

4. 安装`epel-release`
```
## CentOS 7 and Red Hat (RHEL) 7 ##
rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm

## CentOS 6 and Red Hat (RHEL) 6 ##
rpm -Uvh https://dl.fedoraproject.org/pub/epel/epel-release-latest-6.noarch.rpm
```

5. 安装依赖包
```
## Fedora 28/27/26/25/24/23/22 ##
dnf install gcc kernel-devel kernel-headers dkms make bzip2 perl

## Fedora 21/20/19/18/17, CentOS/RHEL 7/6 ##
yum install gcc kernel-devel kernel-headers dkms make bzip2 perl
```

6. 设置环境变量
```
## Current running kernel on Fedora 28/27/26/25/24/23/22, CentOS 7/6 and Red Hat (RHEL) 7/6 ##
KERN_DIR=/usr/src/kernels/`uname -r`/build

## Export KERN_DIR ##
export KERN_DIR
```

7. 安装
```
cd /media/VirtualBoxGuestAdditions
./VBoxLinuxAdditions.run
```

8. 重启
```
reboot
```
