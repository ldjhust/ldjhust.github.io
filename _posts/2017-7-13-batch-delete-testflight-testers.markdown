---
layout: post
title: "iOS发布 - 批量删除TestFlight Extern Tester"
date: 2017-7-13 11:10
categories: iOS发布
comments: false
---

![](../imgs/batch_delete_testflight_testers/title.jpg)

`TestFlight`是苹果为开发者提供的正式发布前灰度测试功能，使用简单，只需要用户邮箱即可邀请用户参与测试，每次可最多邀请`2000`名用户参与测试。苹果今年四月对`TestFlight`进行一次改版，其中删除了测试人员编辑页面全选的功能。

![](../imgs/batch_delete_testflight_testers/1.png)

如果你也跟我一样每次做`TestFlight`发布时都需要替换所有的邮箱，那么你就会跟我一样对苹果的这一变更感受到深深的伤害，尤其是听说苹果在今年的`WWDC`上说将会增加`TestFlight`的`2000`测试人员上限至`10000`时。

多次向苹果反馈无果后只能自助，好在天无绝人之路，多番`Google`之后找到了这样一个工具——[tampermonkey](https://tampermonkey.net/)。官方介绍它是一款免费的浏览器插件，支持在浏览器上运行用户自定义脚本，再结合`jQuery`框架我们就可以开发出辅助全选的功能。以下是我完成的代码，希望能对与我一样有此需求的人有所帮助：

```
// ==UserScript==
// @name         selectAllTesters
// @namespace    zhegebuhuichongde
// @version      0.1
// @description  select all Testers with ctrl key
// @author       leo
// @match        https://itunesconnect.apple.com/*
// @require      http://cdn.bootcss.com/jquery/3.2.1/jquery.min.js
// @grant        none
// ==/UserScript==

(function() {
    'use strict';

    // 观察所在的编辑页面源码可以看出每个tester都是一个checkbox，所以使用":checkbox"作为选择器
    var tester = ":checkbox";

    // 当页面上检测到鼠标点击且被点击的元素与tester相符（即被点击的元素是checkbox）时，触发事件
    $(document).on("click", tester, function (e) {
        // 如果同时按住了Windows键盘上的ctrl键/Mac键盘上的command键，这里我们以ctrl/command键作为全选暗号
        if (e.ctrlKey || e.metaKey) {
            // 那么就利用jQuery选择器选择页面上所有的checkbox元素并执行click操作
            $(tester).click();
            // 另外必须加上这一句，否则鼠标点击的这个checkbox反而不会被选中
            this.click();
        }
    });
})();
```

下面再给大家介绍一下`tampermonkey`的安装以及自定义脚本的安装和使用方法。

## `tampermonkey`安装

因为个人惯用`Chrome`，因此这里介绍在`Chrome`上安装`tampermonkey`的方法，其他浏览器`Google`一下应该都可以解决。

1、 打开拓展程序管理界面

![](../imgs/batch_delete_testflight_testers/2.png)

2、 选择获取更多拓展程序

![](../imgs/batch_delete_testflight_testers/3.png)

3、 搜索`tampermonkey`并安装

## 自定义脚本安装及使用

### 安装自定义脚本
1、 添加新脚本

![](../imgs/batch_delete_testflight_testers/4.png)

2、 用前面分享给大家的代码替换界面编辑器里面的所有代码

![](../imgs/batch_delete_testflight_testers/5.png)

3、 保存

![](../imgs/batch_delete_testflight_testers/6.png)

经过上面几步之后，准备及安装工作都已经OK了，下面解释一下实际的用法。

### 自定义脚本用法
**用法：**在编辑页面按住`ctrl`（`Mac`上是`command`）键，然后鼠标点击任一个测试人员前面的小框框就可以一次性选中页面上显示出来的所有测试人员

>PS: 这个脚本只能够选择到页面上已经有的测试人员，而苹果的所有测试人员界面只会显示`2000`个测试人员中的前面一部分，个人觉得应该是为了提高页面加载速度，所以我们需要先将页面一直往下滚动手动将`2000`个测试人员都加载出来，然后再用脚本提供的这个功能。当然，**<font color="red">你也可以一部分一部分的选择删除（这也是我经过实践后最推荐的方案，虽然需要多来几次）</font>**，因为如果机器性能不好，那么当你在一直滚动加载所有测试人员的时候很有可能中途页面卡死而导致重新来过，<font color="red">另外一次性要求脚本选则太多会花费一些时间才能反应过来（这里的时间应该是线性的）</font>。
>
>PPS: <font color="red">大家可以根据需要自行修改</font>

## 主要参考
* [tampermonkey官网](http://tampermonkey.net)
* [如何使用tampermonkey ?](https://jingyan.baidu.com/article/fb48e8be5b9d1d6e622e14f2.html)
* [jQuery事件绑定.on()简要概述及应用](http://www.jb51.net/article/33880.htm)
* [jQuery 参考手册 - 选择器](http://www.w3school.com.cn/jquery/jquery_ref_selectors.asp)
* [jQuery 参考手册 - 事件](http://www.w3school.com.cn/jquery/jquery_ref_events.asp)
* [Jquery event.keyCode](http://963630220-qq-com.iteye.com/blog/1960022)