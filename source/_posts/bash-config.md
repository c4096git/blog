---
title: '通过 PS1 美化你的 bash'
date: 2022-04-23
categories: 技术
tags: 
- Linux
- Shell
- 配置
---
众所周知，bash 的默认配置虽谈不上丑，但绝对不算好看。实际上，在 bash 的配置文件中，有一个叫 `PS1` 的变量。通过对其赋值，可以自定义 bash 外观，还算是比较强大的。
<!-- more -->
### 显示信息    
```bash
nano ~/.bashrc
```
在这个文件中，你大概会看到这么一行（PS1 后的东西可能不一样，大同小异）：
```bash
PS1='${debian_chroot:+($debian_chroot)}\h:\w\$ '
```
看起来比较迷惑。取消注释后，执行 `source ~/.bashrc` 可以看到 bash 的外观变了。    
下面是 PS1 变量中可以使用的一些参数：

|参数|用途|例子|
|:---:|:---:|:---:|
|\v|显示 bash 版本信息|-|    
|\H|显示完整的主机名称|localhost.localdomain|    
|\h|仅显示主机的第一个名称|localhost|
|\u|显示当前用户名|root|
|\d|显示日期|Jan Apr 1|
|\t|显示 24 小时格式的完整时间|19:19:10|  
|\A|显示 24 小时格式的简略时间|19:10|
|\T|显示 12 小时格式的完整时间|11:45:14|  
|\@|显示 12 小时格式的简略时间|08:10 am|  
|\w|完整显示当前目录|/yajuu/senpai|    
|\W|显示当前目录的最后一个目录|senpai|
|\#|显示执行的第几条命令|19|
|\$|显示当前用户的提示符|#|

### 颜色
```bash
\e[F;Bm
```
其中 F 是文本颜色，B 是背景色（背景色可以不填）。下面是所有可用的颜色，`30~37` 为文本颜色，`40~47` 为背景颜色。   

|文本|背景|颜色|
|:---:|:---:|:---:|
|31|41|红色|
|32|42|绿色|
|33|43|黄色|
|34|44|蓝色|
|35|45|紫色|
|36|46|深绿|
|37|47|白色|

在 PS1 末尾，可以添加 `\e[0m` 以关闭颜色。