---
layout:     post
title:      "MySQL数据库迁移： 将.frm、.myd和.myi文件导入mysql数据库中"
subtitle:   ""
date:       2018年03月22日 19:49:34
author:     "唐传林"
header-img: "img/post-bg-universe"
catalog: true
tags:
    - 电脑技巧
---



-------------------





#### 电脑环境：
Windows10教育版 64位 （OS内部版本：16299.125） 
MySQL版本：[MySQL Server 5.0](https://cdn.mysql.com/archives/mysql-5.0/mysql-5.0.96-winx64.zip)


#### MySQL数据库迁移步骤
1、找到存放数据库文件夹。
安装目录下搜索找到 my.ini 文件，然后在文件中找到 datadir 一行。

`datadir="C:/Program Files/MySQL/MySQL Server 5.0/Data/"`

这个就是存放数据库的文件夹了。
![这里写图片描述](https://img-blog.csdn.net/20180322180350724?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)
![这里写图片描述](https://img-blog.csdn.net/20180322180359785?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

2、在存放数据库文件夹中找到先前建立的数据库名命名的文件夹,然后然后把.frm,.MYD MYI等文件导进去。
说明:
.frm文件 是对应的数据库中的一个表,表示数据表的表结构。
.MYD文件 是INNODB引擎外的数据文件。
.MYI文件 是MyISAM表的索引的扩展名。
![这里写图片描述](https://img-blog.csdn.net/20180322194826637?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)
