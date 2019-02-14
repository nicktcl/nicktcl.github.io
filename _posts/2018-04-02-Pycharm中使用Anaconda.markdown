---
layout:		post
title: 		Pycharm中使用Anaconda
date: 		2018-04-02 19:49:30
author:		"唐传林"
header-img: "img/post-bg-2015.jpg"
catalog:	 true
tags:
- python
- PyCharm
- Anaconda
---
#  Pycharm中使用Anaconda

##  问题：

安装完Pycharm和Anaconda后，想让Pycharm能调用Anaconda中包含的各种包。这样就不用重复安装各种包了。

###  Anaconda下载安装

Anaconda指的是一个开源的Python发行版本，其包含了conda、Python等180多个科学包及其依赖项。
因为包含了大量的科学包，Anaconda 的下载文件比较大（约 515 MB）。安装Anaconda后就不用手动安装好多python的包了。

Anaconda的优点总结起来就四个字：省时省心。  
（1）在我们安装好anaconda的时候，这个工具中会自带很多python的包，我们可以在pycharm中可视化进行查看。  
（2）在我们需要使用的包系统中不存在的时候，我们可以很省心的进行包的在线下载，绝对的让你很满意。

[ Anaconda 官方下载地址 ](https://www.anaconda.com/download/)  
[ Anaconda 国内镜像地址 ](https://mirror.tuna.tsinghua.edu.cn/help/anaconda/)

###  Pycharm下载安装

PyCharm是一款Python
IDE，带有一整套可以帮助用户在使用Python语言开发时提高其效率的工具，比如调试、语法高亮、Project管理、代码跳转、智能提示、自动完成、单元测试、版本控制。此外，该IDE提供了一些高级功能，以用于支持Django框架下的专业Web开发。

[ Pycharm 专业版及社区版下载地址
](https://www.jetbrains.com/pycharm/download/#section=windows)

###  Pycharm导入Anaconda

在Pycharm的Files——>settings——>Project Interpreter——>Add local里面添加Anaconda
python.exe. 应用之后就可以调用各种Anaconda的库啦.  
![这里写图片描述](http://img-blog.csdn.net/2018040219435893?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
![这里写图片描述](http://img-blog.csdn.net/20180402194751363?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
![这里写图片描述](http://img-blog.csdn.net/20180402194800139?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
![这里写图片描述](http://img-blog.csdn.net/20180402194823913?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
![这里写图片描述](http://img-blog.csdn.net/20180402194831194?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

###  参考资料：

1、 [ 在pycharm中配置Anaconda以及pip源配置
](https://blog.csdn.net/u012513525/article/details/54947398)  
2、 [ pycharm中使用anaconda部署python环境
](https://blog.csdn.net/qq_29883591/article/details/78077244)  
3、 [ 在pycharm中使用anaconda
](https://blog.csdn.net/xiu_star/article/details/52277623)  
4、 [ Windows 下，使用 Pycharm + Anaconda（NumPy，SciPy 等集成包）的环境配置
](https://blog.csdn.net/Adam_fei/article/details/77844770)

