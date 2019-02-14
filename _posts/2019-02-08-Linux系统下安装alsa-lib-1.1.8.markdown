---
layout:		post
title: 		Linux系统下安装alsa-lib-1.1.8
date: 		2019-02-08 17:45:48
author:		"唐传林"
header-img: "img/post-bg-2015.jpg"
catalog:	 true

---
###  前言

本文介绍如何在Linux系统下安装最新版本的alsa音频驱动。

###  alsa-lib 下载地址

2019年2月8日，当前alsa-lib最新版本为1.1.8.  
alsa-lib-1.1.8 下载地址： [ ftp://ftp.alsa-project.org/pub/lib/alsa-
lib-1.1.8.tar.bz2 ](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.1.8.tar.bz2)  
或是到官网找到最新版本的下载下来： [ http://www.alsa-project.org/main/index.php/Main_Page
](http://www.alsa-project.org/main/index.php/Main_Page)

###  安装步骤

1、下载alsa-lib-1.1.8

    
```   
    wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.1.8.tar.bz2
```    

2、解压

    
```    
    tar jxvf alsa-lib-1.1.8.tar.bz2
```    

3、检测你的安装平台的目标特征

    
```    
    ./configure
```    

4、编译

    
```    
    make
```    

5、安装

    
```    
    make install
```    

###  参考资料

1、 [ 在Linux中安装ALSA声卡驱动 - 程序园 ](http://www.voidcn.com/article/p-chcmvatc-
xy.html)  
2、 [ Linux 命令详解（三）./configure、make、make install 命令 - Tinywan - 博客园
](https://www.cnblogs.com/tinywan/p/7230039.html)

