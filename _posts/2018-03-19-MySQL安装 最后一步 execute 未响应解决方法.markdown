---
layout:		post
title: 		MySQL安装 最后一步 execute 未响应解决方法
date: 		2018-03-19 18:25:53
author:		"唐传林"
header-img: "img/post-bg-2015.jpg"
catalog:	 true

---
#  MySQL安装 最后一步 execute 未响应解决方法

####  电脑环境：

windows10教育版 64位 （OS内部版本：16299.125）  
MySQL版本： [ mysql-5.0.96-winx64
](https://cdn.mysql.com/archives/mysql-5.0/mysql-5.0.96-winx64.zip)

##  问题：

为了写上一篇博客“ [ Windows10下安装MySQL5.0详细教程
](http://blog.csdn.net/tang_chuanlin/article/details/79603063)
”记录一下MySQL安装步骤，把之前安装配置好的MySQL卸载了重新安装，结果重新安装的时候就在最后一步execute”时出现未响应。

##  原因：

安装MySQL到最后一步“execute”时出现未响应，一般显示在安装MySQL程序最后一步的2，3项就不动了。  
这种情况一般是因为以前安装过MySQL数据库而未卸载干净。  ;

##  解决办法：

1、打开任务管理器结束掉未响应的MySQL安装程序;  
2、依次打开 控制面板 ——> 所有控制面板项 ——> 程序和功能，卸载MySQL Server 5.0，若控制面板没有MySQL Server
5.0就不用做这一步了;  
3、打开 我的电脑 ——> c盘 ——> Program Files，删除MySQL文件夹。  
4、打开“ ` C:\ProgramData `
”，删除MySQL文件夹。该programData文件是隐藏的默认，设置显示后即可见，或者直接复制上边的地址到地址栏回车即可进入。  
5、回到桌面按住 “ windows+r ” 打开“运行”对话框，输入 ` regedit ` ，点击“确定”打开注册表。  
6、删除  
HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Services\Eventlog\Application\MySQL文件夹;  
7、删除  
HKEY_LOCAL_MACHINE\SYSTEM\ControlSet002\Services\Eventlog\Application\MySQL  
文件夹。  
HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Eventlog\Application\MySQL  
的文件夹。如果没有可以不用删除了。  
8、为了稳妥，用腾迅电脑管家或者 [ 软媒魔方 ](http://sw.bos.baidu.com/sw-search-
sp/software/84765693d3add/pcmaster_6.2.1.0_full.zip)
中的cleanermaster清理一下电脑中的垃圾和无效的注册表文件;  
9、  重启电脑。一定要重启电脑。  
10、重启电脑后重新安装MySQL就不会再在最后一步“execute”时出现未响应了。

#####  参考资料：

1、 [ 完全卸载mysql数据库图文教程
](https://jingyan.baidu.com/article/f96699bbaa8fc1894f3c1b5a.html)  
2、 [ MySQL安装未响应解决方法
](https://www.cnblogs.com/ywangzi/archive/2012/08/27/2658885.html)  
3、 [ MySQL安装到最后一步未响应的解决方法
](http://blog.csdn.net/u012894785/article/details/44985545)

