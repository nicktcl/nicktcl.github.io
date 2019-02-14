---
layout:		post
title: 		Altium Designer——批量隐藏元件注释（Comment）
date: 		2018-07-23 16:45:41
author:		"唐传林"
header-img: "img/post-bg-2015.jpg"
catalog:	 true
categories:
- Altium Designer

---
#  Altium designer——批量隐藏元件注释（Comment）

###  电脑环境：

1、Windows10教育版 64位 1803版本（操作系统版本：17134.165）  
2、Altium Ddesigner 17.1.5（Build 472） [ 点这里下载，密码：rwsx ](https://pan.baidu.com/s
/19GIaF-YiytO_bwTFtSURvA)

##  步骤

1、在原理图中用鼠标右键点击一下元件的元件值，在菜单中选中“查找相似元件”，英文版为“Find Similar Objects”。  
![这里写图片描述](http://img-blog.csdn.net/20180723162438480?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

2、调出全局修改的界面,在弹出来的菜单中，在Part comment
后面的下拉框中选择Same,即设定筛选条件为筛选所有相同comment的元件，然后点击OK。  
注意：此时下面Select Matching前的方框要打上勾，系统已将所有的相同comment的元件进行了选中。  
![这里写图片描述](http://img-blog.csdn.net/20180723162741897?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
3、在下面弹出来方框中，只要点击Part
Comment，将弹出窗口，只需要在Hide后的方框内打上勾就可以了，我们可以看到，此时相同COMMENT的值就已全部隐藏。  
如果要隐藏所有的元件comment只需在Part comment 后面的下拉框中选择Any，即设定筛选条件为筛选图中的元任何件，在下面Select
Matching前的方框要打上勾，接下来操作与前面一样。  
![这里写图片描述](http://img-blog.csdn.net/20180723163041632?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
4、点击“清除当前过滤器区域”，或者使用“Shift+C”清除。  
![这里写图片描述](http://img-blog.csdn.net/20180723164154642?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

###完整操作如下gif图：  
![这里写图片描述](http://img-blog.csdn.net/20180723163818181?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

若要重新显示所有元件注释（Comment），则先显示出一个元件的注释（Comment），然后再用上述方法，在上述第三步中去除Hide后的方框中的勾。如下图：  
![这里写图片描述](http://img-blog.csdn.net/2018072316435249?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

