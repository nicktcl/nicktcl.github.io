---
layout:  post
title:   解决You are using pip version 9.0.1, however version 9.0.3 is available. You should consider upgrading
date:   2018-04-01 15:10:38
author:  "唐传林"
header-img: "img/post-bg-2015.jpg"
catalog:   false

---
#  解决You are using pip version 9.0.1, however version 9.0.3 is available. You
should consider upgrading

###  电脑环境：

Windows10教育版 64位 （OS内部版本：16299.125）

##  问题：

在用pip命令安装python第三方包时出现“You are using pip version 9.0.1, however version 9.0.3
is available. You should consider upgrading”，直接运行命令：python -m pip install
–upgrade pip也无法解决。下载最新pip的.whl文件直接安装还是不行。

###  解决办法：

1、 [ 到python pip官网下载最新的pip ](http://pypi.python.org/pypi/pip) 。（
注意下载的是.tar.gz 文件，而不是.whl文件。  ）  
![这里写图片描述](http://img-blog.csdn.net/20180401145956866?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
2、解压后放到D盘根目录下。  
3、使用管理员模式打开命令行。  
4、输入 ` D: ` 进入D盘根目录。  
![这里写图片描述](http://img-blog.csdn.net/20180401150607283?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
5、输入 ` cd .\pip-10.0.0b1\ ` 进入刚刚解压得到的pip文件夹。  
![这里写图片描述](http://img-blog.csdn.net/20180401150808697?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
6、输入 ` python setup.py install ` 后按回车进行安装。  
![这里写图片描述](http://img-blog.csdn.net/20180401151022115?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

