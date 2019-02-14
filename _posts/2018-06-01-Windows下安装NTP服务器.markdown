---
layout:		post
title: 		Windows下安装NTP服务器
date: 		2018-06-01 15:00:25
author:		"唐传林"
header-img: "img/post-bg-2015.jpg"
catalog:	 true
tags:
- windows
- ntp
---
#  NTP服务器介绍

NTP服务器【Network Time
Protocol（NTP）】是用来使计算机时间同步化的一种协议，它可以使计算机对其服务器或时钟源（如石英钟，GPS等等)做同步化，它可以提供高精准度的时间校正（LAN上与标准间差小于1毫秒，WAN上几十毫秒）。

#  问题描述

在一个与外界网络隔离的局域网内需要搭建一个NTP服务器给该局域网内的其他设备使用。尝试了一些Windows下的NTP服务器小软件之后，最后查到了Windows默认带有NTP服务器，只是默认没有开启，我们可以通过修改注册表的方式打开Windows默认的NTP服务器。

#  Windows时间服务介绍

从Windows 2000起的所有Microsoft
Windows版本都包括Windows时间服务（W32Time），其具有将计算机时钟同步到NTP服务器的能力。  
W32Time服务最初是为实现Kerberos第五版的身份验证协议，它需要误差5分钟内正确时间值以防止重放攻击。Windows 2000和Windows
XP中只实现了简单的NTP，并在几个方面违反了NTP第3版的标准。从Windows Server 2003和Windows
Vista开始，已包括匹配完整NTP的实现。微软称W32Time服务不能可靠地将同步时间保持在1至2秒的范围内。如果需要更高的精度，微软建议使用其他NTP实现。  
Windows Server 2016现在在某些操作条件下支持1ms的时间精度。

（Windows时间服务介绍 摘抄自 “ [ 网络时间协议 - 维基百科，自由的百科全书
](https://zh.wikipedia.org/wiki/%E7%B6%B2%E8%B7%AF%E6%99%82%E9%96%93%E5%8D%94%E5%AE%9A#Windows%E6%97%B6%E9%97%B4%E6%9C%8D%E5%8A%A1)
“)

#  Windows 下安装NTP服务器方法步骤描述

###  电脑环境：

1、 [ VMware Workstation_full_12.1.0.exe
](https://pan.baidu.com/s/1et6hqiXW5uCg3ZYJoB3EoA) ，密码：jtkr  
2、虚拟机作为NTP服务器：Windows 7 （64位）(VMware 12 pro下的Windows 7 虚拟机 )  
3、物理机：Windows10教育版 64位 1803版本（操作系统版本：17134.48）

###  详细步骤：

1、在Windows 服务器下，按住“ ` windows+r ` ”打开“ ` 运行 ` ”对话框，输入 ` regedit `
，点击“确定”打开注册表。  
![这里写图片描述](http://img-blog.csdn.net/20180601104732388?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
2、在注册表中依次展开：HKEY_LOCAL_MACHINE、SYSTEM、CurrentControlSet、Services、W32Time、TimeProviders、NtpServer，  
在NtpServer项的右侧键值ENablied，将默认的0改为1，1为启用NTP服务器。  
![这里写图片描述](http://img-blog.csdn.net/20180601105045238?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
![这里写图片描述](http://img-blog.csdn.net/2018060110531145?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
![这里写图片描述](http://img-blog.csdn.net/20180601105328288?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
3、再在注册表中依次展开：HKEY_LOCAL_MACHINE、SYSTEM、CurrentControlSet、Services、W32Time、Config  
找到Config项右侧的AnnounceFlags。  
把默认的10改为5，5的意思就是自身为可靠的时间源。  
![这里写图片描述](http://img-blog.csdn.net/20180601105805783?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
![这里写图片描述](http://img-blog.csdn.net/20180601105812626?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
![这里写图片描述](http://img-blog.csdn.net/20180601105820134?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
4、修改完以上之后关闭注册表编辑器，win7下  以管理员身份打开命令行  如下图。Windows10则用Windows+X+A以管理员身份打开命令行。  
![这里写图片描述](http://img-blog.csdn.net/20180601111833480?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
5、在命令提示符中输入： ` net stop w32Time ` ，回车  
等待NTP服务停止。  
然后再输入： ` net start w32Time ` ，回车  
启动NTP服务。  
![这里写图片描述](http://img-blog.csdn.net/20180601112253482?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
6、测试，局域网内windows电脑同步成功！  
![这里写图片描述](http://img-blog.csdn.net/201806011449215?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
7、测试，在ubuntu虚拟机中，在终端输入命令“ ` sudo ntpdate 192.168.10.241 ` ，”出现如下界面则同步成功！  
![这里写图片描述](http://img-blog.csdn.net/20180601144955348?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

#  参考资料

1、 [ NTP服务器_百度百科
](https://baike.baidu.com/item/NTP%E6%9C%8D%E5%8A%A1%E5%99%A8/8633994?fr=aladdin)  
2、 [ 内网测试环境 NTP 服务器搭建
](http://files.cppblog.com/runsisi/%E5%86%85%E7%BD%91%E7%8E%AF%E5%A2%83ntp%E6%9C%8D%E5%8A%A1%E5%99%A8%E6%90%AD%E5%BB%BA.pdf)  
3、 [ 内网NTP服务器搭建 ](http://blog.51cto.com/172595/779816)  
4、 [ meinberg官网 ](https://www.meinberg.de/download/ntp/windows/)  
5、 [ NetTime 开源的Windows系统ntp软件
](http://baijiahao.baidu.com/s?id=1577333340289884776&wfr=spider&for=pc)  
6、 [ 各种NTP SERVER平台软件测试与测试结果_百度文库
](https://wenku.baidu.com/view/1ac330ad4a7302768e9939d1.html)  
7、 [ Windows 如何安装NTP服务器_百度经验
](https://jingyan.baidu.com/article/e4511cf358ebf52b845eaff9.html)  
8、 [ 网络时间协议 - 维基百科，自由的百科全书
](https://zh.wikipedia.org/wiki/%E7%B6%B2%E8%B7%AF%E6%99%82%E9%96%93%E5%8D%94%E5%AE%9A#Windows%E6%97%B6%E9%97%B4%E6%9C%8D%E5%8A%A1)  
9、 [ Network Time Protocol - Wikipedia
](https://en.wikipedia.org/wiki/Network_Time_Protocol)  
10、 [ 运行net start 命令时，提示发生系统错误5，拒绝访问。 - Microsoft Community
](https://answers.microsoft.com/zh-
hans/windows/forum/windows8_1-performance/%E8%BF%90%E8%A1%8Cnet-
start/bec244e5-6385-4950-adc8-0d004905e41a?auth=1)  
11、 [ cmd net start 服务 提示系统错误5 拒绝访问怎么办？-CSDN论坛
](https://bbs.csdn.net/topics/320235799)  
12、 [ 怎么获得win7最高管理员权限
](https://jingyan.baidu.com/article/c275f6ba38fb6ae33d75670b.html)  
13、 [ Win7命令提示符怎么以管理员方式打开
](https://jingyan.baidu.com/article/ca41422fff77021eae99ed86.html)  
14、 [ Win10系统同步Internet 时间出错的解决方法_百度经验
](https://jingyan.baidu.com/article/3c48dd34a6b22ae10be35819.html)  
15、 [ Ubuntu 14.04下时间同步的设置
](https://blog.csdn.net/luozhb529/article/details/39158549)

