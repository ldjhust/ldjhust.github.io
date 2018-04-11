---
layout: post
title: "Flask - 修改css文件不生效问题原因及解决方法"
date: 2018-04-11 14:56
categories: Flask
comments: false
---

![](https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1523441086386&di=f854651c3d3c0c1c9aa674573f3580e1&imgtype=0&src=http%3A%2F%2Fwww.wallcoo.com%2Fnature%2FHD_Best%2520of%2520nature%25201920x1200%2Fimages%2FWin7_24.jpg)

最近在用`Flask`写一个`web`项目时碰到一个奇怪的现象（前端新手），修改`css`文件时再浏览器前端刷新看不到修改的结果，显示的依然是修改前的效果，
久久不能理解，`Google`一番之后才明白这是因为浏览器缓存了`css`文件的结果。一些方案说通过`Ctrl + F5`强制浏览器刷新可以解决，试了一下的确可以
看到修改之后的效果，说明有效，但是这并不是一个根本的解决方案，继续搜索发现通过给`css`文件的连接之后加一个动态的参数同样可以解决问题，如当前
系统的时间戳，或者`css`文件的哈希值：
```
.../xxx.css?t=<时间戳>
.../xxx.css?h=<哈希值>
```

通过每次修改`css`文件后产生一个变化的`url`来让浏览器重新从`server`端读取`css`文件来解决缓存问题，我觉得这是更根本的解决方案，下面介绍一下如何来做。

1. 计算`css`文件的哈希值
```
import hashlib

def get_sha1(filename):
    """
    :param filename: css文件的路径
    :return css文件的哈希值
    """
    # 以二进制的方式打开文件进行读取，其它方式可能会在计算哈希值的时候出错
    with open(filename, "rb") as f:
        sha1obj = hashlib.sha1()
        sha1obj.update(f.read())
        
        return sha1obj.hexdigest()
```

2 `Jinja2`模板里面使用`url_for`来获取`css`文件的路径，再添加一个多余的参数它会自动作为`css`文件`url`的参数
```
# h=hashcode这个多余的参数会自动作为css文件的参数，最后个url格式为：xxx/static/css/style.css?h=xxx
<link href={{ url_for("static", filename="css/style.css", h=hashcode) }} rel="stylesheet" type="text/css" />
```

3 `render_template`时将hashcode传递给`Jinja2`模板，这里以访问根`url`为例
```
@app.route("/")
def index():
    return render_template("index.html", hashcode=get_sha1("static/css/style.css")[, ...])
```

OK，经过以上三步的改造，我们每次修改`css`文件都会在浏览器端实时更新。
