---
layout: post
title: "网络 - 常用代理设置"
date: 2017-07-12 09:34
categories: 网络
comments: false
---

![](https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1503377034230&di=344b865c976841586090586aa5b3c3a9&imgtype=0&src=http%3A%2F%2Fimg2.niutuku.com%2Fdesk%2F1208%2F1421%2Fntk-1421-3307.jpg)

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

# 或者在配置文件中
mkdir $HOME/.pip
vim $HOME/.pip/pip.conf 输入如下内容
[global]
proxy=http://host:port
```

3 `apt`
```
# 在配置文件中配置代理 /etc/apt/apt.conf
Acquire::http::Proxy "http://<proxy host>:<port>"
```

4 `ping`  `wget`
```
# 设置环境变量 ~/.bash_profile
export http_proxy=<proxy host>:<port>
export https_proxy=${http_proxy}
```

5 `curl`
```
# 使用 -x 选项指定代理
curl -x http://host:port ...
```

6 `npm`
```
npm config set https-proxy "https://<proxy host>:<port>/"
npm config set proxy "http://<proxy host>:<port>/"
npm config set registry "https://registry.npm.taobao.org"
```

7 `git`
```
git config --global http.proxy https://<proxy host>:<port>
```

8 `yum`
```
# /etc/yum.conf
proxy=http://<proxy host>:[<proxy port>]
```

9 `docker`

参考[为 Docker 设置代理](http://www.jianshu.com/p/26d0ebd86673)
```
# 第一步创建 /etc/systemd/system/docker.service.d 文件夹
# 第二步创建 /etc/systemd/system/docker.service.d/http-proxy.conf 文件 （文件名随意）
# 第三步在新创建文件中写入如下配置，然后保存退出
[Service]
Environment="HTTP_PROXY=http://proxy.example.com:80/"
# 第三步补充，如果有不需要经过代理的站点，可参考如下配置
[Service]
Environment="HTTP_PROXY=http://proxy.example.com:80/" "NO_PROXY=localhost,127.0.0.1,daocloud.io"
# 第四步刷新systemd的配置
sudo systemctl daemon-reload
# 第五步验证配置是否生效
$ systemctl show --property=Environment docker
Environment=HTTP_PROXY=http://proxy.example.com:80/
# 第六步重启docker服务
$ sudo systemctl restart docker
# 第七步随意pull无障碍：）
```

**持续更新中...**
