---
title: Windows10下java环境配置
date: 2018-03-16 20:48:08
categories:
- java
tags:
- java
- java环境配置

---
#  Windows10下java环境配置

假期重新装了window10的操作系统，现在重新配置一下java的开发环境。  
想记录一下这些步骤，以防时间久了忘记。

#####  更新：2018年5月8日

推荐使用  [ 一键安装JDK和JRE并自动配置Java环境变量
](https://blog.csdn.net/tang_chuanlin/article/details/80240672) 。

##  电脑环境：

windows10教育版 64位 （OS内部版本：16299.125）

##  步骤：

1、首先到Oracle网站下载对应操作系统的jdk安装包。  
[
http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html
](http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html)  
![这里写图片描述](//img-
blog.csdn.net/20180316200358546?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

2、下载完成后点击打开一路点击“下一步”进行安装，安装过程中会先自动安装jdk。  
![这里写图片描述](//img-
blog.csdn.net/20180316201409452?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
中途会弹出另外一个窗口让选择jre安装位置，点击“下一步”后再自动安装jre。  
![这里写图片描述](//img-
blog.csdn.net/20180316201310515?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
出现以下界面则安装成功。  
![这里写图片描述](//img-
blog.csdn.net/20180316201015692?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
3、安装完成后在桌面上右键点击“此电脑”，左键点击“属性”，在弹出的窗口左侧找到“高级系统设置”并点击。  
![这里写图片描述](//img-
blog.csdn.net/20180316201603343?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
4、在弹出的窗口中右下方找到“环境变量”并点击。  
![这里写图片描述](//img-
blog.csdn.net/20180316201739420?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
5、设置如下变量名：  
变量名：Path  
变量值： ` %java_home%\bin;%java_home%\jre\bin; `  
新建变量名：JAVA_HOME  
变量值： ` C:\Program Files\Java\jdk1.8.0_111; ` （这里是jdk的安装目录）  
新建变量名：ClassPath  
变量值： ` %JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar; ` .;

![这里写图片描述](//img-
blog.csdn.net/20180316202235204?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
![这里写图片描述](//img-
blog.csdn.net/20180316202242668?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
![这里写图片描述](//img-
blog.csdn.net/201803162022509?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
6、依次点击“确定”退出窗口。

##  下面步骤是检验java环境是否安装成功。

7、回到桌面按住“ ` windows+r ` ”打开“运行”对话框，输入 ` cmd ` ，点击“确定”打开命令行。  
![这里写图片描述](//img-
blog.csdn.net/20180316202549631?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
![这里写图片描述](//img-
blog.csdn.net/20180316202557227?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
8、在命令行输入“ ` java ` ”，可看到下图结果：  
![这里写图片描述](//img-
blog.csdn.net/20180316203308807?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
9、在命令行下输入“ ` javac ` ”，可看到下图结果：  
![这里写图片描述](//img-
blog.csdn.net/20180316203347903?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
10、若出现下图结果，则说明没有安装成功，需要重新安装。  
![这里写图片描述](//img-
blog.csdn.net/20180316203440962?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

##  写一个“Hello World！”进行测试。

1、在D盘根目录下新建一个“test”文件夹，在“test”文件夹中新建一个txt文件，将其重命名为“test1.java”。  
2、用记事本或NotePad++打开“test1.java”输入如下代码。

    
    
    public class test1 {
        public static void main(String[] args) {
            System.out.print("Hello World!");
        }
    }

3、回到桌面按住“ctrl+r”打开“运行”对话框，输入cmd，点击“确定”打开命令行。  
4、输入“ ` D: ` ”  
![这里写图片描述](//img-
blog.csdn.net/20180316204100361?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
5、输入“ ` cd test ` ”进入“test”文件夹。  
![这里写图片描述](//img-
blog.csdn.net/20180316204229617?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
6、输入“ ` javac test1.java ` ”将“test1.java”文件编译为class文件。  
![这里写图片描述](//img-
blog.csdn.net/20180316204553364?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
7、输入“ ` java test1 ` ”运行刚刚编译的class文件。  
，可以看到打印出的“Hello World！”。  
![这里写图片描述](//img-
blog.csdn.net/20180316204712682?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

