---
layout: post
title: "Linux - 使用ssh秘钥免密码登录Linux"
date: 2017-12-25 12:25
categories: Linux
comments: false
---

![](http://b.hiphotos.baidu.com/image/pic/item/a71ea8d3fd1f4134264ac90b2f1f95cad1c85e42.jpg)

`Linux` 远程登录一般都用`ssh`协议，具体有两种方式：

1. 用户名密码登录
2. 用户名秘钥登录

使用用户名密码登录时有受到“中间人攻击”的风险，所以推荐使用用户名秘钥登录，下面介绍如何配置`ssh`秘钥免密码登录远程`Linux`服务器。

1. 配置远程Linux服务器上的sshd配置文件（etc/ssh/sshd_config）：

```
# 禁止密码登录
PasswordAuthentication no

# 开启秘钥登录公钥验证登录
RSAAuthentication yes
PubkeyAuthentication yes

# 指定授权公钥所在的文件地址
# 如下配置是去当前用户家目录下的.ssh目录寻找authorized_keys文件，这也是一般配置
AuthorizedKeysFile      .ssh/authorized_keys

# 如下配置可以解决ssh登录慢的问题
GSSAPIAuthentication no
UseDNS no
```

2. 以上配置都修改好之后保存退出，然后重启`sshd`服务

```
sudo systemctl restart sshd
```

3. 在本地主机上配置`ssh`公秘钥对（详细步骤参考最后的参考文章，windows可以用putty，*nix直接命令行ssh-keygen 即可）

4. 注意`ssh`秘钥登录时，远程`Linux`主机随机反过来一串字符串，本地在**当前用户**的家目录下寻找秘钥进行加密传送到远程`Linux`，然后远程`Linux`按照上面配置
在**要登录的用户**的家目录下的`.ssh`目录中的`authorized_keys`文件中寻找匹配公钥进行解密，得到的字符串与最初发送出去的字符串进行比对，匹配上则登录成功，反之则
失败，所以这里一定要注意：**本地当前用户**、**要登录远程Linux中的用户**

5. 很有可能上面步骤都正确结果还是无法登录，这是就要看一下权限问题，`ssh`秘钥登录对`$HOME`目录、`$HOME/.ssh`目录以及`$HOME/.ssh/authorized_keys`文件
的权限都有严格要求，过大的权限会导致额外的风险，因此`ssh`不认，正确的权限配置如下：

```
chmod 700 $HOME
chmod 700 $HOME/.ssh
chmod 600 $HOME/.ssh/authorized_keys
```

参考：
1. [SSH 原理和基本使用：ssh 安全配置 以及ssh key 认证登录](http://blog.51cto.com/skypegnu1/1641064)
