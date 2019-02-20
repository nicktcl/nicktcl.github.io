---
layout:  post
title:   Altium Designer——PCB中更改线宽的技巧总结
date:   2018-03-31 16:08:10
author:  "唐传林"
header-img: "img/post-bg-2015.jpg"
catalog:   true
categories:
- Altium Designer
tags:
- Altium Designer

---
#  Altium Designer——PCB中更改线宽的技巧总结

###  1.设置altium designer的默认pcb线宽

在布线前直接在设计规则中设置：Design-Rules-Routing-Width,修改这个里面的Preferred
Width即可，还可以进一步设置不同层的Min、Max、Preferred Width。

###  2.布线过程中修改pcb线宽

选择Place-Line（快捷键P-L）中按TAB键，显示下图所示的对话框，可以修改Line Width和Current Layer。

###  3.布线完成后批量修改线宽

（1）在空白处右键，点击Find Same Objects，是十字线选择要修改的线（或者直接在线上右键）。  
（2）如更改相同线宽和同网络的，就将Net和Width的最右侧改为Same，点击OK，这就选择好了想要的线。  
（3）在PCB Inspector中输入想要的Width再点回车即可。

###  4.简单修改一个网络的线宽

可以点击选择要修改的线，按住Shift同时选择多条线，按住Shift，双击选择的线，在弹出的对话框中更改线宽。或者快捷键S-P，选择一个网络，不过要在按住Shift的同时，去掉对焊盘的选择。然后同上更改线宽。

###  5.布线完成后修改所有的线宽

在界面的右下角PCB-PCB Filter中打开边侧栏PCB Filter，输入Iswire后回车，即全选所有线，点击空白处一下，然后按F11
在Width中改成你想要的线宽。

