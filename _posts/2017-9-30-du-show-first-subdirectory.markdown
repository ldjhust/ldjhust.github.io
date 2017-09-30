---
layout: post
title: "技术 - DU 只显示第一层子目录所占空间"
date: 2017-09-30 9:30
categories: 技术
comments: false
---

![](https://timgsa.baidu.com/timg?image&quality=80&size=b9999_10000&sec=1506745270505&di=334b89ac2272cc9690698b3d309587db&imgtype=0&src=http%3A%2F%2Ff.hiphotos.baidu.com%2Fzhidao%2Fpic%2Fitem%2F902397dda144ad3464639dc8d1a20cf430ad85a4.jpg)

很多时候我们只关心当前目录下的第一层子目录所占磁盘空间的大小，查看 `du` 命令的 `help` 文档写出如下命令：

    du -h -d 1 .

结果发现跟输出跟想象的不一样。最后经过一番 `Google` 发现如下的写法：

    du -sh *
    
输出与预期一致，只输出了当前目录的第一层子目录所占磁盘空间的大小。
