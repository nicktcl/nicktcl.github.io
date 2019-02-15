---
layout:		post
title: 		Altium Designer——捕捉栅格、电气栅格、可见栅格的意义及设置
date: 		2018-07-23 10:31:54
author:		"唐传林"
header-img: "img/post-bg-2015.jpg"
catalog:	 true
categories:
- Altium Designer
tags:
- Altium Designer
---
#  Altium Designer——捕捉栅格、电气栅格、可视栅格的意义及设置

使用Altium Designer画原理图或PCB时，常常需要设置各种栅格，Altium
Designer中有三种栅格（Grids）：捕捉栅格、电气栅格、可视栅格。下面对这三种栅格进行介绍。

##  电脑环境：

1、Windows10教育版 64位 1803版本（操作系统版本：17134.165）  
2、Altium Designer 17.1.5（Build 472） [ 点这里下载，密码：rwsx ](https://pan.baidu.com/s
/19GIaF-YiytO_bwTFtSURvA)

#  可视栅格

可视栅格（Visible Grid）：就是在工作区上看到的网格，这是一种几何点或线构成的网格，其作用类似于坐标线，可帮助用户掌握图件间的距离。  
原理图下切换可视栅格快捷键：Shift+Ctrl+G

#  捕捉栅格

捕捉栅格（Snap）：其作用是控制光标每次移动的距离。  
原理图下切换捕捉栅格快捷键：G  
例如：如果设定值是10mil，鼠标的光标拖动零件引脚，距离可视栅格在10mil范围之内时，零件引脚自动的准确跳到附近可视栅格上，捕获栅格也叫跳转栅格，捕获栅格是看不到的。

#  电气栅格

电气栅格（Elactronical
Grid）：电气栅格的作用是在移动或放置元件时，当元件与周围电气实体的距离在电气栅格的设置范围内时，元件与电气实体会互相吸住。  
原理图下切换电气栅格快捷键：Shift+E

例如：如果设定值是30mil，按下鼠标左键，如果鼠标的光标离电气对象、焊盘、过孔、零件引脚、铜箔导线的距离在30mil范围之内时，光标就自动的跳到电气对象的中心上，以方便对电气对象进行操作。

选择电气对象、放置零件、放置电气对象、放置走线、移动电气对象等等，电气栅格设置的尺寸大，光标捕捉电气对象的范围就大，如果设置过大，就会错误的捕捉到比较远的电气对象上。电气栅格工作时捕获栅格不工作。

#  设置：

1、原理图的可视栅格 、捕获栅格、
电器栅格的设置，可以在菜单“视图（view）”——>“栅格（grids）”中进行设置。或者在原理图中右键单击，然后选择“选项(options)”——>“栅格（grids）”。一般来说，可视栅格最大，捕获栅格和电气栅格比可视栅格小。  
![这里写图片描述](http://img-blog.csdn.net/20180723102737318?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
![这里写图片描述](http://img-blog.csdn.net/20180723101513325?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
![这里写图片描述](http://img-blog.csdn.net/20180723101520850?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
2、PCB图的可视栅格 、捕获栅格、
电器栅格的设置，也可以在菜单“视图（view）”-----“栅格”（grids）中进行设置。一般来说，可视栅格最大，捕获栅格和电气栅格比可视栅格小。  
![这里写图片描述](http://img-blog.csdn.net/20180723103050731?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

###  参考资料：

1、 [ 可见栅格，捕捉栅格和电气栅格各有什么不同？_百度知道 ](https://zhidao.baidu.com/question/142323247)  
2、 [ AD软件中可视栅格 捕捉栅格 电气栅格的功能和设置详解 - Altium Designer 单片机论坛
](http://www.51hei.com/bbs/dpj-95189-1.html)

