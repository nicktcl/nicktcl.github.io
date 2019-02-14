---
layout:		post
title: 		一键安装JDK和JRE并自动配置Java环境变量
date: 		2018-05-08 16:27:37
author:		"唐传林"
header-img: "img/post-bg-2015.jpg"
catalog:	 true
tags:
- java
---
#  一键安装JDK和JRE并自动配置Java环境变量

#  问题描述：

那天装完ctex（CTeX_2.9.2.164），之后在命令行下运行和编译Java文件提示没有Java环境，查看环境变量后发现系统变量 path
被覆盖，上网查询后发现这是ctex的一个bug，之前好多人也遇到过这种情况。

看来，CTeX的编程人员在写环境变量这步，写的不是”+=”，而是”=”，这样的bug实在是不应该。现在最新版的CTeX听说已经修复了该问题。

然后又急着要在命令行下编译和运行java程序，若是重新手动安装动安装JDK和JRE和配置Java环境变量又要花费好多时间，所以就有了一键安装JDK和JRE并自动配置Java环境变量的想法，上网一搜，之前还真有人这么干过，参考了他们写的博客，照着做了一遍自动安装好了JDK和JRE，并自动配置好了Java环境变量。

#  步骤记录：

1、请[点击这里手动到Oracle官网下载JDK安装包和JRE安装包]。( [
http://www.oracle.com/technetwork/java/javase/downloads/index.html
](http://www.oracle.com/technetwork/java/javase/downloads/index.html) )  
![这里写图片描述](http://img-blog.csdn.net/20180508155220371?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
![这里写图片描述](http://img-blog.csdn.net/20180508155510509?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
![这里写图片描述](http://img-blog.csdn.net/2018050816582347?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
2、将下载好的jdk安装包和jre安装包拷贝到c盘根目录下。  
![这里写图片描述](http://img-blog.csdn.net/20180508155647646?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
3、在c盘根目录下新建一个txt文件，文件名为JDKinstall，文件后缀修改成.bat后缀。  
![这里写图片描述](http://img-blog.csdn.net/20180508155959927?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
4、右键点击刚刚新建好的JDKinstall.bat，点击“编辑”用记事本打开，复制以下内容到里面，并保存退出。

    
```cmd    
    @echo off
    
    %1 mshta vbscript:CreateObject("Shell.Application").ShellExecute("cmd.exe","/c %~s0 ::","","runas",1)(window.close)&&exit
    
    set myjdkpath=C:\Java\jdk1.8
    
    echo **********************************************
    echo.
    echo             欢迎使用一键安装jdk
    echo.
    echo       安装请按任意键，退出直接关闭窗口
    echo.
    echo **********************************************
    
    pause
    
    echo.
    echo 正在安装jdk，请不要执行其他操作
    echo.
    echo 请稍等，这大约需要三、四分钟
    echo.
    start /WAIT C:\jdk-8u171-windows-x64.exe /qn INSTALLDIR=`C:\Java\jdk1.8`
    echo jdk安装完毕
    
    set JAVA_HOME=C:\Java\jdk1.8
    set PATH=%PATH%;%%JAVA_HOME%%\bin;%%JAVA_HOME%%\jre\bin
    set CLASSPATH=.;%%JAVA_HOME%%\lib\dt.jar;%%JAVA_HOME%%\lib\tools.jar
    
    set RegV=HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Environment
    
    reg add "%RegV%" /v "JAVA_HOME" /d "%JAVA_HOME%" /f
    reg add "%RegV%" /v "Path" /t REG_EXPAND_SZ /d "%PATH%" /f
    reg add "%RegV%" /v "CLASSPATH" /d "%CLASSPATH%" /f
    mshta vbscript:msgbox("Java环境已成功注册！",64,"成功")(window.close)
    
    #-Dfile.encoding=utf-8
    
    exit
```


5、在c盘根目录下再新建一个txt文件，文件名为JREinstall，文件后缀修改成.bat后缀。  
![这里写图片描述](http://img-blog.csdn.net/20180508160723643?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
6、右键点击刚刚新建好的JREinstall.bat，点击“编辑”用记事本打开，复制以下内容到里面，并保存退出。

    
```cmd    
    @echo off
    
    %1 mshta vbscript:CreateObject("Shell.Application").ShellExecute("cmd.exe","/c %~s0 ::","","runas",1)(window.close)&&exit
    
    set myjrepath=C:\Java\jre
    
    echo **********************************************
    echo.
    echo           将要安装软件运行环境jre
    echo.
    echo       安装请按任意键，退出直接关闭窗口
    echo.
    echo **********************************************
    
    pause
    
    echo.
    echo 正在安装jre，请不要执行其他操作
    echo.
    echo 请稍等，这个时间大约需要四、五分钟
    echo.
    start /WAIT C:\jre-8u171-windows-x64.exe /s INSTALLDIR=C:\Java\jre
    echo jre安装完毕
    
    set JAVA_HOME=C:\Java
    set PATH=%PATH%;%%JAVA_HOME%%\jre\bin
    set CLASSPATH=.;%%JAVA_HOME%%\jre\lib
    
    set RegV=HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Environment
    
    reg add "%RegV%" /v "JAVA_HOME" /d "%JAVA_HOME%" /f
    reg add "%RegV%" /v "Path" /t REG_EXPAND_SZ /d "%PATH%" /f
    reg add "%RegV%" /v "CLASSPATH" /d "%CLASSPATH%" /f
    mshta vbscript:msgbox("Java环境已成功注册！",64,"成功")(window.close)
    
    exit
```


7、依此  以管理员身份运行  刚刚做好的两个.bat批处理文件，运行时按任意键后就可开始安装。  
注意：自动安装时电脑不要执行其他操作，执行其他操作可能导致一键安装失败。  
![这里写图片描述](http://img-blog.csdn.net/20180508161609891?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
![这里写图片描述](http://img-blog.csdn.net/20180508161617392?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
![这里写图片描述](http://img-blog.csdn.net/20180508162250192?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
![这里写图片描述](http://img-blog.csdn.net/2018050816225842?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

##  下面步骤是检验java环境是否安装成功。

8、回到桌面按住“ ` windows+r ` ”打开“运行”对话框，输入 ` cmd ` ，点击“确定”打开命令行。  
![这里写图片描述](http://img-blog.csdn.net/20180316202549631?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
![这里写图片描述](http://img-blog.csdn.net/20180316202557227?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
9、在命令行输入“ ` java ` ”，可看到下图结果：  
![这里写图片描述](http://img-blog.csdn.net/20180316203308807?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
10、在命令行下输入“ ` javac ` ”，可看到下图结果：  
![这里写图片描述](http://img-blog.csdn.net/20180316203347903?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
11、若出现下图结果，则说明一键安装失败，需要重新进行一键安装或直接手动。  
![这里写图片描述](http://img-blog.csdn.net/20180316203440962?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

#####  若用上述方法一键安装不成功，请参看博客 [ Windows10下java环境配置
](https://blog.csdn.net/tang_chuanlin/article/details/79586667)
手动安装JDK和JRE和配置Java环境变量。

#  参考资料：

1、 [ 批处理命令：一键安装JDK/一键安装JRE和自动配置Java环境变量
](https://www.cnblogs.com/Gekkii/p/gekkii.html)  
2、 [  
一键安装JDK和自动配置Java环境变量
](https://blog.csdn.net/caijunfen/article/details/70154143?locationNum=4&fps=1)  
3、 [ 安装CTeX后环境变量（Path）被覆盖的解决方法 ](http://www.pythoner.com/202.html)  
4、 [ CTEX安装必须注意 系统变量 path 被覆盖
](https://blog.csdn.net/thesby/article/details/50850510)

