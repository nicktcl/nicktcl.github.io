---
layout:  post
title:   notepad++配置tcc构建c语言开发环境
date:   2019-06-29 20:45:50
author:  "唐传林"
header-img: "img/post-bg-2015.jpg"
catalog:   true
categories:
- c语言                                                                    
tags:
- notepad
- tcc配置
- c语言

---
#  前言

原来大学刚学c语言时用的都是VC6.0编译器，现在的老师之前推荐了tcc编译器，并且推荐将tcc配置到notepad++，就可以很方便地很c语言了。  
然后去查了下tcc编译器的介绍和它的作者。  
tcc（Tiny C Compiler）编译器是世界上最小的C语言编译器，而且是开源的， 小到只有约100K.
(VC，GCC，动不动几十M几百M几个G的，特别是安装一次头疼一次)。别看它小, 功能还是很强。可以编译所有C99标准的ANSI
C程序。支持CPU包括：X86 32或64位, ARM，支持Windows, Linux, OSX.（跨平台跨系统的能力，比VC强）。  
TCC是由大牛Fabrice Bellard开发的，这位大牛还开发过 Qemu,
FFmepg(FFmepg被称作音视频处理的瑞士军刀，没有FFmepg，就没有抄它的暴风影音，格式工厂，腾讯视频，以及其它好多好多音视频播放器)。

#  tcc特点

  * 小！您可以在任何地方编译和执行C代码，例如在救援磁盘上（x86 TCC可执行文件大约100KB，包括C预处理器，C编译器，汇编器和链接器）。 
  * 快速！tcc生成x86代码。没有字节码开销。编译，组装和链接比GCC 快几倍。 
  * 无限！任何C动态库都可以直接使用。TCC正在全面遵守ISOC99标准。TCC当然可以编译自己。 
  * 安全！tcc包括一个可选的内存和绑定检查器。绑定的检查代码可以与标准代码自由混合。 
  * 直接编译和执行C源代码。无需链接或组装。包括完整的C预处理器和类似GNU的汇编程序。 
  * 支持C脚本：只需在C源代码的第一行添加“＃！/ usr / local / bin / tcc -run”，然后直接从命令行执行。 
  * 使用libtcc，您可以使用TCC作为动态代码生成的后端。 

#  配置步骤

1、下载tcc软件  
作者主页： [ http://bellard.org ](http://bellard.org)  
tcc主页： [ http://bellard.org/tcc/ ](http://bellard.org/tcc/)  
下载页： [ http://download.savannah.gnu.org/releases/tinycc/](http://download.savannah.gnu.org/releases/tinycc/)

TCC最新版本是0.9.27（截止2019年6月29日）。  
根据自己电脑系统（32位还是64位）下载执行程序：  
[ tcc-0.9.27-win64-bin.zip](http://download.savannah.gnu.org/releases/tinycc/tcc-0.9.27-win64-bin.zip)  
[ tcc-0.9.27-win32-bin.zip](http://download.savannah.gnu.org/releases/tinycc/tcc-0.9.27-win32-bin.zip)

无需安装的，只需要解压即可。  
解压缩到 c:\tcc , 可见目录下有 tcc.exe, 这个是编译器命令行程序，没有IDE界面的。  
将 c:\tcc 加入到 系统路径中 (PATH)后，则可以在任何命令行窗口中使用了。

2、安装Notepadd++  
主页： [ http://notepad-plus-plus.org/ ](http://notepad-plus-plus.org/)  
Notepadd++最新版本是7.7.1（截止2019年6月29日）。  
下载地址： [ npp.7.7.1.Installer.exe ](http://notepad-plus-plus.org/repository/7.x/7.7.1/npp.7.7.1.Installer.exe)

3、打开Notepad++，一次打开菜单“NotePad++ --> 插件 -->Plugin Manager -->show Pluyin Manger
-->安装NppExec插件”。

#####  方法一：在NotePad++中配置TCC编译信息，此种方法可以生成.exe文件。

4、按F6出现Execute对话框，填写如下信息：

    
    
    NPP_SAVE
    tcc "$(CURRENT_DIRECTORY)\$(FILE_NAME)" -o "$(CURRENT_DIRECTORY)\$(NAME_PART).exe"
    echo
    echo =================编译成功后开始运行====================
     "$(CURRENT_DIRECTORY)\$(NAME_part).exe"
    

5、点击Save输入名字，这里我命名为“tcc”然后点OK  
![在这里插入图片描述](http://img-blog.csdnimg.cn/20190629201943637.png)

#####  方法二：在NotePad++中配置TCC编译信息，此种方法跳过编译链接的步骤，直接运行程序。

6、按F6出现Execute对话框，参数如下：

    
    
    NPP_SAVE
    tcc -run "$(CURRENT_DIRECTORY)\$(FILE_NAME)"
    

7、点击Save输入名字，这里我命名为“tcc_run”然后点OK；  
![在这里插入图片描述](http://img-blog.csdnimg.cn/2019062920222991.png)

#####  为tcc设置快捷键

8、NotePad++中依次点击：插件 ->NppExec ->Advanced Options，然后如图操作；  
![在这里插入图片描述](http://img-blog.csdnimg.cn/20190629203237614.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9uaWNrdGNsLmJsb2cuY3Nkbi5uZXQ=,size_16,color_FFFFFF,t_70)  
![在这里插入图片描述](http://img-blog.csdnimg.cn/20190629203051338.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9uaWNrdGNsLmJsb2cuY3Nkbi5uZXQ=,size_16,color_FFFFFF,t_70)  
![在这里插入图片描述](http://img-blog.csdnimg.cn/20190629203250620.gif)  
![在这里插入图片描述](http://img-blog.csdnimg.cn/20190629203419133.gif)  
9、关闭notepadd++，重新打开notepadd++，依次点击：宏 ->管理快捷键；  
![在这里插入图片描述](http://img-blog.csdnimg.cn/20190629203756796.png)  
10、在弹出的对话框中找到“插件命令”，然后找到“tcc”（若刚刚设置为其它名字，则这里为你设置的那个名字），双击打开；  
![在这里插入图片描述](http://img-blog.csdnimg.cn/20190629204014383.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9uaWNrdGNsLmJsb2cuY3Nkbi5uZXQ=,size_16,color_FFFFFF,t_70)  
11、在弹发的对话框中设置快捷键，我这里我配置快捷键为alt+F9；  
![在这里插入图片描述](http://img-blog.csdnimg.cn/20190629204233834.png)  
12、"tcc_run"设置步骤也同上9、10、11步骤；  
13、测试能否运行。  
(注：用方法一编译的c语言的.exe程序默认名为 文件名.exe ，使用这种方法尽量为自己的程序新建一个文件夹)

#  参考资料

1、 [ notepadd++和TCC/MinGW构建c/c++环境 - 咸鱼的博客 - CSDN博客](http://blog.csdn.net/qq_38875084/article/details/78386486)  
2、 [ TCC研究(1): Tiny C Compiler最小的C语言编译器，自己编译自己 - JoStudio - CSDN博客](http://blog.csdn.net/c80486/article/details/44528829)

