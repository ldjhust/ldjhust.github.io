---
layout: post
title: "Linux - VIM常用命令说明"
date: 2017-12-26 17:28
categories: Linux
comments: false
---

![](http://d.hiphotos.baidu.com/image/pic/item/728da9773912b31b7b69cde38f18367adbb4e1f7.jpg)

<table>
    <tr>
        <td><b>VIM 常用命令介绍</b></td>
        <td></td>
        <td></td>
        <td></td>
    </tr>
    <tr>
        <td><b>末行模式可用命令</b></td>
        <td></td>
        <td><b>编辑常用命令</b></td>
        <td></td>
    </tr>
    <tr>
        <td>命令</td>
        <td>作用</td>
        <td>命令</td>
        <td>作用</td>
    </tr>
    <tr>
        <td>:w</td>
        <td>保存</td>
        <td>dd</td>
        <td>删除（剪切）光标所在整行</td>
    </tr>
    <tr>
        <td>:q</td>
        <td>退出</td>
        <td>5dd</td>
        <td>删除（剪切）从光标处开始的5行</td>
    </tr>
    <tr>
        <td>:q!</td>
        <td>强制退出（放弃对文档的修改内容）</td>
        <td>yy</td>
        <td>复制光标所在整行</td>
    </tr>
    <tr>
        <td>:wq!</td>
        <td>强制保存退出</td>
        <td>5yy</td>
        <td>复制从光标处开始的5行</td>
    </tr>
    <tr>
        <td>:set nu</td>
        <td>显示行号</td>
        <td>n</td>
        <td>显示搜索命令定位到的下一个字符串</td>
    </tr>
    <tr>
        <td>:set nonu</td>
        <td>不显示行号</td>
        <td>N</td>
        <td>显示搜索命令定位到的上一个字符串</td>
    </tr>
    <tr>
        <td>:命令</td>
        <td>执行该命令</td>
        <td>u</td>
        <td>撤销上一步的操作</td>
    </tr>
    <tr>
        <td>:整数</td>
        <td>跳转到该行</td>
        <td>p</td>
        <td>将之前删除（dd）或复制（yy）过的数据粘贴到光标后面</td>
    </tr>
    <tr>
        <td>:s/one/two</td>
        <td>将当前光标所在行的第一个one替换成two</td>
        <td></td>
        <td></td>
    </tr>
    <tr>
        <td>:s/one/two/g</td>
        <td>将当前光标所在行的所有one替换成two</td>
        <td></td>
        <td></td>
    </tr>
    <tr>
        <td>:%s/one/two/g</td>
        <td>将全文中的所有one替换成two</td>
        <td></td>
        <td></td>
    </tr>
    <tr>
        <td>?字符串</td>
        <td>在文本中从下至上搜索该字符串</td>
        <td></td>
        <td></td>
    </tr>
    <tr>
        <td>/字符串</td>
        <td>在文本中从上至下搜索该字符串</td>
        <td></td>
        <td></td>
    </tr>
    <tr>
        <td></td>
    </tr>
</table>
