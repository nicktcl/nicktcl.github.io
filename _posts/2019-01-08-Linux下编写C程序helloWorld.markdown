---
layout:		post
title: 		Linux下编写C程序helloWorld
date: 		2019-01-08 15:39:28
author:		"唐传林"
header-img: "img/post-bg-2015.jpg"
catalog:	 true
tags:
    - linux
---
###  前言

最近需要在树莓派上写c语言程序，树莓派所安装的系统为raspberry，隶属于debian系统。本文简单记录一下在linux下编写c语言程序的步骤。

###  步骤

1、打开终端窗口，执行以下命令安装gcc编译环境，树莓派系统默认已经安装好gcc环境，可跳过该步骤；

    
```    
    sudo apt-get install gcc
```    

2、执行以下命令安装头文件库，这就是build- essential软件包，树莓派系统默认已经安装好build- essential软件包，可跳过该步骤；

    
```   
    sudo apt-get install build-essential
```    

3、执行以下命令新建一个名为 “helloWorld” 的文件夹；

    
```   
    mkdir helloWorld
```    

4、执行以下命令进入“helloWorld” 文件夹；

    
```    
    cd helloWorld
```   

5、执行以下命令新建一个名为 “hello.c” 的文本文件；

    
```  
    sudo nano hello.c
```    

6、在新建的 “hello.c” 文本文件中写入以下代码；

    
```    
    #include <stdio.h>
    int main()
    {
    	printf("Hello world!\n");
    	return 0;
    }
```   

7、按下 ` ctrl+o ` 保存文本文件；  
8、按下 ` ctrl+x ` 退出nano文本编辑器；  
9、执行以下命令使用gcc编译hello.c;

    
```    
    gcc hello.c -o hello
```    

10、编译通过后，我们执行 ` ls ` 会在当前目录中看到hello文件，这就是编译后生成的可执行文件。  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190108153630969.png)  
11、执行以下命令，可以看到在终端中输出了”Hello world!”，这就说明我们的程序运行成功了。

    
```    
    ./hello
```    

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190108153710102.png)

###  特别说明

GCC中对于文件后缀的规定有点特殊，特别是C++源代码文件的后缀不是cpp，而是cc或cxx。  
.c为后缀的文件，C语言源代码文件；  
.a为后缀的文件，是由目标文件构成的档案库文件；  
.C，.cc或.cxx 为后缀的文件，是C++源代码文件；  
.h为后缀的文件，是程序所包含的头文件；  
.i 为后缀的文件，是已经预处理过的C源代码文件；  
.ii为后缀的文件，是已经预处理过的C++源代码文件；  
.m为后缀的文件，是Objective-C源代码文件；  
.o为后缀的文件，是编译后的目标文件；  
.s为后缀的文件，是汇编语言源代码文件；  
.S为后缀的文件，是经过预编译的汇编语言源代码文件。

###  参考资料

1、 [ Linux下编写C程序( GCC )（hello，world） - 小彭的Android之旅 - CSDN博客
](https://blog.csdn.net/geeker_12/article/details/10911275)

