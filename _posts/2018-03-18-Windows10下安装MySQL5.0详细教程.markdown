---
layout:		post
title: 		Windows10下安装MySQL5.0详细教程
date: 		2018-03-18 20:02:25
author:		"唐传林"
header-img: "img/post-bg-2015.jpg"
catalog:	 true

---
#  Windows10下安装MySQL5.0详细教程

想记录一下这些步骤，以防时间久了忘记。

###  电脑环境：

windows10教育版 64位 （OS内部版本：16299.125）

##  安装步骤：

1、到 [ MySQL官网下载MySQL5.0安装程序
](https://cdn.mysql.com/archives/mysql-5.0/mysql-5.0.96-winx64.zip) 。  
注意：MySQL官网有好多个版本，本教程以MySQL5.0为例子进行介绍。  
[ 需要MySQL其他版本点击这里 ](https://downloads.mysql.com/archives/community/)  
![这里写图片描述](//img-blog.csdn.net/20180318185706592?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
2、解压后双击打开“Setup.exe”，点击“Next”。  
![这里写图片描述](//img-blog.csdn.net/20180318185934282?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
3、下图步骤中请选择“Custom”。  
![这里写图片描述](//img-blog.csdn.net/20180318191603732?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
4、点击右下角“Change”可以改变安装路径。  
![这里写图片描述](//img-blog.csdn.net/20180318191708877?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
5、点击“Install”。  
6、点击“Next”出现如下界面。  
![这里写图片描述](//img-blog.csdn.net/20180318191804327?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
7、勾选上“Configure the MySQL Sever now”，然后点击“Finish”。  
![这里写图片描述](//img-blog.csdn.net/20180318191856252?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
8、点击“Next”出现如下界面。  
![这里写图片描述](//img-blog.csdn.net/20180318192019303?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
9、选择配置方式。  
“Detailed Configuration（手动精确配置）”，  
“Standard Configuration（标准配置）”，  
我们选择“Detailed Configuration”，方便熟悉配置过程。  
![这里写图片描述](//img-blog.csdn.net/20180318192218790?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
10、选择服务器类型。  
“Developer Machine（开发测试类，mysql 占用很少资源）”，  
“Server Machine（服务器类型，mysql占用较多资源）”，  
“Dedicated MySQL Server Machine（专门的数据库服务器，mysql占用所有可用资源）”，  
大家根据自己的类型选择了，我们做开发一般选“Developer Machine”。  
![这里写图片描述](https://img-blog.csdn.net/20180430173637927?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
11、选择mysql数据库的大致用途。  
“Multifunctional Database（通用多功能型，好）”，  
“Transactional Database Only（服务器类型，专注于事务处理，一般）”，  
“Non-Transactional Database Only（非事务处理型，较简单，主要做一些监控、记数用，对MyISAM数据类型的支持仅限于non-
transactional），  
随自己的用途而选择了，我这里选择“Multifunctional Database”，按“Next”继续。  
![这里写图片描述](//img-blog.csdn.net/20180318193314872?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
12、对InnoDB Tablespace进行配置，就是为InnoDB
数据库文件选择一个存储空间，如果修改了，要记住位置，重装的时候要选择一样的地方，否则可能会造成数据库损坏。我这里没有修改，使用默认位置，直接按“Next”继续。  
![这里写图片描述](//img-blog.csdn.net/2018031819350834?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
13、选择一般mysql 访问量，同时连接的数目。  
“Decision Support(DSS)/OLAP（20个左右）”，。  
“Online Transaction Processing(OLTP)（500个左右）”，  
“Manual Setting（手动设置，自己输一个数）”，  
我这里选“Manual Setting”，输入“20”，做简单的开发应该够用了，按“Next”继续。  
![这里写图片描述](//img-blog.csdn.net/20180318193748935?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
14、是否启用TCP/IP连接，设定端口，如果不启用，就只能在自己的机器上访问mysql 数据库了，我这里启用，把前面的勾打上，Port
Number：3306，在这个页面上，您还可以选择“启用标准模式”Enable Strict
Mode），这样MySQL就不会允许细小的语法错误。还有一个关于防火墙的设置“Add firewall exception
……”需要选中，将MYSQL服务的监听端口加为windows防火墙例外，避免防火墙阻断。按“Next”继续。  
![这里写图片描述](//img-blog.csdn.net/20180318194028304?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
15、对mysql默认数据库语言编码进行设置，这个比较重要。  
![这里写图片描述](//img-blog.csdn.net/20180318194841338?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
第一个：“Standard Character Set”是西文编码，  
第二个：“Best Support For Multilingualism”是多字节的通用utf8编码，  
第三个：“Manual Selected Default Character Set / Collation”是自己选择编码格式。

这里我们选择“Manual Selected Default Character Set / Collation”，然后在Character Set
那里选择或填入“gbk”。  
按“Next”继续。

当然也可以用“gb2312”，区别就是gbk的字库容量大，包括了gb2312的所有汉字，并且加上了繁体字、和其它乱七八糟的字——使用mysql
的时候，在执行数据操作命令之前运行一次“SET NAMES
GBK;”（运行一次就行了，GBK可以替换为其它值，视这里的设置而定），就可以正常的使用汉字（或其它文字）了，否则不能正常显示汉字。

注意：如果要用原来数据库的数据，最好能确定原来数据库用的是什么编码，如果这里设置的编码和原来数据库数据的编码不一致，在使用的时候可能会出现乱码。  ;

16、选择是否将mysql 安装为windows服务，还可以指定Service Name（服务标识名称），是否将mysql的bin目录加入到Windows
PATH（加入后，就可以直接使用bin下的文件，而不用指出目录名，比如连接，“mysql.exe -uusername
-ppassword;”就可以了，不用指出mysql.exe的完整地址，很方便），我这里全部打上了勾，Service Name不变。按“Next”继续。  
![这里写图片描述](//img-blog.csdn.net/20180318195206528?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
17、这一步询问是否要修改默认root 用户（超级管理）的密码（默认为空），“New root
password”如果要修改，就在此填入新密码（如果是重装，并且之前已经设置了密码，在这里更改密码可能会出错，请留空，并将“Modify Security
Settings”前面的勾去掉，安装配置完成后另行修改密码），“Confirm（再输一遍）”内再填一次，防止输错。“Enable root access
from remote machines（是否允许root 用户在其它的机器上登陆，如果要安全，就不要勾上，如果要方便，就勾上它）”。最后“Create
An Anonymous
Account（新建一个匿名用户，匿名用户可以连接数据库，不能操作数据，包括查询）”，一般就不用勾了，设置完毕，按“Next”继续。  
![这里写图片描述](//img-blog.csdn.net/20180318200013933?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
18、确认设置无误，如果有误，按“Back”返回检查。按“Execute”使设置生效。  若在这一步点击 execute 导致窗口未响应，请参见博客 [
“MySQL安装 最后一步 execute 未响应解决方法”
](https://blog.csdn.net/tang_chuanlin/article/details/79615152) 。  
![这里写图片描述](//img-blog.csdn.net/20180318200021627?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
19、出现如下图说明安装成功。设置完毕，按“Finish”结束mysql的安装与配置。  
![这里写图片描述](//img-blog.csdn.net/20180319164202547?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

