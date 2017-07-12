---
layout: post
title: "网络 - 常用代理设置"
date: 2017-07-12 09:34
categories: 网络
comments: false
---

![](https://picabstract-preview-ftn.weiyun.com:8443/ftn_pic_abs_v2/8238a957d5b6f26e3fe1ab81eae6b45755a71fbbda4c67e8b60c6017e6dc1e3ef13a1e30509289ce5cf3ce4c8aadaac8?pictype=scale&from=30113&version=2.0.0.2&uin=471391503&fname=greylag-goose-2139296_1280.jpg&size=1024)

当网络处在代理之后时，各种需要联网的软件并不能直接正常工作，也需相应的配置代理，本文记录常用软件的代理设置方式，以作备忘。

1 `gem`

```
# 添加源时需要提供代理
gem source --add https://gems.ruby-china.org --http-proxy http://<proxy host>:<port>

# 安装库时也需要提供代理
gem install <package> --http-proxy http://<proxy host>:<port>
```

2 `pip`

```
# 安装库时提供代理
sudo pip install <package> --proxy http://<proxy host>:<port>
```

**持续更新中...**
