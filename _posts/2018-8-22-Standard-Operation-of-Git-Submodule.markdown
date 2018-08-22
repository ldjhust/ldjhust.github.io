---
layout: post
title: "Git - 使用git submodule的规范操作"
date: 2018-08-22 10:54
categories: Git
comments: false
---

![](http://h.hiphotos.baidu.com/image/pic/item/37d3d539b6003af3057ef951382ac65c1038b63e.jpg)

1. 初始化添加sbumodule并提交到remote repository
	git submodule add [-b branch-name] <git repository url> [path] // 不加path 会默认在当前目录下添加同名子模块
	git commit -am "Add submodule xxx"
	git push
2. clone带submodule的repository
	方法一：
	git clone <git repository url> // 这样clone下来submodule只是空的目录，必须进一步操作
	git submodule init
	git submodule update
	方法二：
	git clone --recursive <git repository url>
3. 将本地的submodule更新为remote repository的状态（因为可能有其他人更新了submodule的commit id）
	git pull
	git submodule update
4. 更新submodule的commit id并准备推送到remote repository（有多个submodule时千万注意不要覆盖了别人的变更）
	# 第一步要先将本地更新为remote repository的状态
	git pull
	git submodule update
	# 第二步更改希望修改的submodule的commit id
	cd <submodule xxx>
	git checkout <branch name> // 切换到分支上，这样才能执行git pull将submoudle库的上更新拿下来
	git pull
	git checkout <commit id> // 切换到指定的commit id
	# 第三步将变更提交到remote repository
	cd .. // 回到主库
	git pull //再看一下是不是没有其他人在remote repository有更新了，如果有，那么上面的步骤需要再来一遍
	git add . // 没有其他人有更新了，那我们就将我们的更新添加到暂存区准备提交了
	git commit -m "Update submodule xxx to xxx commit id"
	git push // 推送到远端
5. 移除不需要submodule
	git submodule deinit <submodule name>
	git rm <submodule name>
	git commit -m "Remove submodule xxx"
	git push
6. 修改已有submodule的remote repository url并且将此变更推送到主库的remote repository
		a. 修改.gitmodules文件中该submodule的url属性
		b. 使用git submodule sync命令，将新的URL更新到文件.git/config中：
		git submodule sync
		git commit -am "modify submodule xxx's remote repository url"
		git push
7. 其他人修改了已有submodule的remote repository url，我们怎么同步到本地
		a. 先执行git pull将.gitmodules文件的的变更同步到本地，但是此时.git/config中还没有同步到
    b. 执行git submodule sync [submodule name]将变更同步到.git/config中
