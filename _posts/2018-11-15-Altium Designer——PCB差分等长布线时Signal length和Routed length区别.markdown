---
layout:  post
title:   Altium Designer——PCB差分等长布线时Signal length和Routed length区别
date:   2018-11-15 20:01:31
author:  "唐传林"
header-img: "img/post-bg-2015.jpg"
catalog:   false
categories:
- Altium Designer
tags:
- PCB差分布线
- 等长布线
- Altium
- Designer
- Signal 
- length
- Routed
- length

---
#  Altium Designer——PCB差分等长布线时Signal length和Routed length区别

在差分等长布线后，发现布的线长不一致，在PCB的nets里查看长度时看到了Signal length和Routed length。  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20181115200036931.jpg?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=,size_16,color_FFFFFF,t_70)

  * Routed length：形象一点理解就是一条有弯道的路，Routed length指在路的中间取线，到达弯道出再取中线，两线长度和。 
  * Signal length：信号能通过的长度，形象一点理解就是一条有弯道的路，Signal length指这条弯路的最短距离，信号能通过就行。 

等长布线所谓的等长就是Signal length等长，在一些教程里等长布线检查长度时给出的是Routed length。

