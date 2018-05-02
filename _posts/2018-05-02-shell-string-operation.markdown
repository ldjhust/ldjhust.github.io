---
layout: post
title: "Linux - Shell 字符串操作"
date: 2018-05-02 15:25
categories: Linux
comments: false
---


![]()

1. 计算字符串长度
```
echo ${#string}
```

2. 截取从某一位置开始的字符串
```
echo ${string:position}
```

3. 截取从某一位置开始长度为x的字符串
```
echo ${string:position:length}
```

4. 从头开始删除最短匹配到的字符串
```
echo ${string#substring}
```

5. 从头开始删除最长匹配到的字符串
```
echo ${string##substring}
```

6. 从结尾开始删除最短匹配到的字符串
```
echo ${string%substring}
```

7. 从结尾开始删除最长匹配到的字符串
```
echo ${string%%substring}
```

8. 替换第一个匹配到的字符串
```
echo ${string/substring/replacement}
```

9. 替换所有匹配到的字符串
```
echo ${string//substring/replacement}
```

10. 如果字符串开头是xxx，则用指定字符串替换
```
echo ${string/#substring/replacement}
```

11. 如果字符串结尾是xxx，则用指定字符串替换
```
echo ${string/%substring/replacement}
```

应用举例：
1 获取文件名：echo ${filename%.*}
2 获取文件拓展名：echo ${filename##*.}
