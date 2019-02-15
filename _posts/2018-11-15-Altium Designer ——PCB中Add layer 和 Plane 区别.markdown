---
layout:		post
title: 		Altium Designer ——PCB中Add layer 和 Plane 区别
date: 		2018-11-15 21:02:52
author:		"唐传林"
header-img: "img/post-bg-2015.jpg"
catalog:	 true
categories:
- Altium Designer

---
#  Altium Designer ——PCB中Add layer 和 Add Internal Plane区别

![在这里插入图片描述](https://img-blog.csdnimg.cn/20181115210123970.jpg?x-oss-
process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=,size_16,color_FFFFFF,t_70)

1、Add layer：添加中间层。中间层可以作为走线来用，和普通的信号层没有什么区别，只是走线在内部了。是正片腐蚀。

2、Add Internal
Plane：添加内电层。内电层是整个完整的平面，是整个的覆铜的，是负片腐蚀，即有走线的地方是腐蚀掉的。可以做电源层，也可以做地层。

#  参考资料：

1、 [ PCB中Add layer 和 Plane 区别
](https://blog.csdn.net/alihouzi/article/details/44003867)

2、 [ 如何使用Altium designer设计PCB多层板_百度经验
](https://jingyan.baidu.com/article/5bbb5a1b35d81c13eba17999.html)

3、 [ pcb内层（internal plane）有什么作用？_百度知道
](https://zhidao.baidu.com/question/439542181.html)

4、 [ DXP内电层与内电层分割操作汇总 - Altium Designer 单片机论坛
](http://www.51hei.com/bbs/dpj-30172-1.html)

