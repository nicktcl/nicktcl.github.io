---
layout:		post
title: 		Altium Designer——AD画PCB图步骤总结
date: 		2018-04-03 18:01:30
author:		"唐传林"
header-img: "img/post-bg-2015.jpg"
catalog:	 true
categories:
- Altium Designer

---
#  Altium Designer——AD画PCB图步骤总结

本文总结一下AD画PCB的步骤，以防时间久了忘记一些小步骤。现在所用着的AD版本为AD17。

###  电脑环境：

Altium Designer 17.1.5 ( build172 ) [ 点这里下载，密码：rwsx ](https://pan.baidu.com/s
/19GIaF-YiytO_bwTFtSURvA)

###  AD画PCB图步骤：

1、创建工程，新建“PrjPCB”文件。  
2、画原理图，新建“SchDOC”文件。画原理图时，如果没有的器件自己绘制原理图库，同时绘制封装库，并
在原理图库中指定原件封装，这样以后使用自己画的这一原理图封装就不用再手动添加封装了
。系统自带的封装若不是想要的，还可以在属性里面指定封装。网络标号需要放在导线上，不能放在管脚上，否则可能不能检测到网络。电阻电容阻值大小写在元件的comment中，方便最后导出元件清单比较直观。  
3、画PCB图，新建“PcbDoc”文件。然后切换到原理图下，到“设计”菜单下更新原理图到刚刚新建的“PcbDoc”文件。更新时，把room选项勾选去掉。  
4、在画PCB图时，使用“垂直分割”将原理图和PCB图分别放到AD界面左侧和右侧。然后点击一下左侧的原理图窗口，在“工具”菜单下打开“交叉选择模式”，这样选中左侧原理图中的一部分元器件右侧的PCB窗口也选中了对应的元器件，这样就比较方便一部分一部分地进行PCB布局。  
![这里写图片描述](http://img-blog.csdn.net/20180403152931142?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
5、手动布局PCB元器件时遵循就近原则，布局好元器件后再开始手动布线。  
6、大概布线完成后就可以根据实际的布局更改PCB板为合适的大小了。更改PCB板大小的方法：“视图”——>“板子规划模式”，就可以绘制PCB板的大小了。  
7、更改好PCB板的实际大小后，现在切换到keep-out
layer层绘制PCB板的外边框。绘制外边框不能使用导线，要选择菜单“放置”——>“禁止布线”——>“线径”，然后才可以画PCB板的外边框。  
![这里写图片描述](http://img-blog.csdn.net/20180403155213486?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
8、切换到Mechanical1机械层，再选择菜单“放置”——>“尺寸”——>“线性尺寸”，点击PCB板边框角上的两个点量出PCB板的尺寸并放置。放置尺寸时按住空格键可切换需要测量的尺寸的方向。  
![这里写图片描述](http://img-blog.csdn.net/20180403160043123?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
9、在PCB板的四个角落放置螺丝孔，一般设置3.1mm的孔径，5mm的外径。  
10、布线完成后添加滴泪。菜单“工具”——>“滴泪”——>“添加”——>“确定”。
注意：滴泪不能重复添加，若是要修改某根导线，则应该先移除全部滴泪，然后修改导线后重新添加滴泪。  
11、最后该覆铜了。在覆铜前应将布线规则中的Clearance（导线和焊盘间的距离）改为20mil，然后再覆铜。 ![这里写图片描述](https
:http://img-blog.csdn.net/20180403163100980?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
![这里写图片描述](http://img-blog.csdn.net/2018040316311085?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
12、点击菜单“放置”——>“铺铜”进行覆铜。  
13、点击菜单“报告”——>“板子信息”——>“报告”—— 勾选上“Routing
Information”——>“报告”，弹出的网页上就会剩余的连接点数量，若为0，则说明全部连接点都连到一起了。若是不为0
，则说明还有导线没有连接。需要回去检查PCB板上哪里的导线没有连接。  
![这里写图片描述](http://img-blog.csdn.net/20180403180433684?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
14、若是PCB板上有导线没有连接，则回到PCB板中，按住“ shift + s ”，就可以查看到哪些导线没连接。

####  参考资料：

1、 [ altium designer 绘制pcb步骤
](https://blog.csdn.net/zhjc2012/article/details/49226683?locationNum=13&fps=1)  
2、 [ 关于Altinum Designer使用和PCB绘制的小结
](https://blog.csdn.net/Tele_Anti_Nomy/article/details/51322632)  
3、 [ 画PCB板经验总结 ](https://blog.csdn.net/u012075739/article/details/37656913)

