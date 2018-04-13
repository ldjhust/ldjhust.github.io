---
layout: post
title: "Git - 本地目录转为Git仓库并提交"
date: 2018-04-13 09:51
categories: Git
comments: false
---

![](http://a.hiphotos.baidu.com/image/pic/item/902397dda144ad34e98003fedca20cf431ad8588.jpg)

1. 在远程创建`Git`仓库并复制地址
```
# 例如在GitHub上创建仓库并有如下地址
https://github.com/xxx/test.git
```

2. 进入本地工作目录并初始化为`Git`目录
```
cd xxx/work/
git init
```

3. 为本地`Git`目录添加远程仓库的`URL`
```
# 将第一步的地址添加到这里
git remote add origin https://github.com/ldjhust/test.git
```

4. 提交本地目录到远程仓库
```
# 第一次提交必须说明提交到哪一个远程仓库以及分支，否则会出现: No refs in common and none specified; doing nothing.
git add .
git commit -m "Initial commit"
git push origin master
```
