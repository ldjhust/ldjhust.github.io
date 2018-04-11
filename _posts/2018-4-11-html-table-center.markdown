---
layout: post
title: "HTML - 将table水平上下居中于页面"
date: 2018-04-11 11:30
categories: HTML
comments: false
---

![](http://a.hiphotos.baidu.com/image/pic/item/902397dda144ad34e98003fedca20cf431ad8588.jpg)

单纯的依靠`css`水平上下居中`table`找了很多方法都不怎么有效果，其实我们可以通过取巧的方式达到，因为`table`中的`td`中的内容可以轻松做到水平上下居中，
所以如果我们讲`table`放在一个不显示的`table`的`td`中，那么也可以很容易做到`table`水平上下居中。

代码：
```
<!--
<!DOCTYPE html> 这里需要注释掉，下面的效果才能显示出来，暂时不清楚原因
-->
<html>
  <head>
    <title>测试</title>
  </head>
  <body>
    <table border=0 style="width:100% ;height:100%">
      <tr><td align="center" valign="middle">
        <!--这里才是我们想要展示的表格-->
        <table border="1">
          <tr><td>测试</td></tr>
        </table>
      </td></tr>
    </table>
  </body>
</html>
```
