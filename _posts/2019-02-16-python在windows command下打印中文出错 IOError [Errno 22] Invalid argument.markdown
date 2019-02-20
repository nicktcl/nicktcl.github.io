---
layout:  post
title:   python在windows command下打印中文出错 IOError [Errno 22] Invalid argument
date:   2019-02-16 11:51:53
author:  "唐传林"
header-img: "img/post-bg-2015.jpg"
catalog:   false
categories:
- python
tags:
- python
- print
- windows
- command
- cmd

---
###  问题描述：

python版本：2.7.15  
pycharm的python版本：2.7.15  
python文件编码：utf-8  
windows command编码已经通过执行 ` chcp 65001 ` 改为了utf-8编码。

在pycharm环境下测试好的python程序在windows command下执行 ` python test1.py ` 时出现错误“IOError:
[Errno 22] Invalid argument”，错误所指向的一行代码为“print(“世界你好！”)
”这种打印中文字符串的代码。中文英文在google搜索都暂时未找到相关可解决的办法。  
使用 ` print(u'中文python') ` 或者 ` print (unicode("世界你好！", encoding="utf-8")) `
在windows command下执行又会出现错误“LookupError: unknown encoding: cp65001。”

所以自己又写了以下代码进行测试，找到了解决办法。

###  运行过程：

– pycharm下运行：  
![在这里插入图片描述](http://img-blog.csdnimg.cn/20190216115017885.gif)

  * windows command下运行：   
![在这里插入图片描述](http://img-blog.csdnimg.cn/20190216114703247.gif)

###  代码如下：

    
    
    #!/usr/bin/env python2.7
    # coding=utf-8
    
    import os
    import sys
    reload(sys)
    sys.setdefaultencoding('utf8')
    
    username = 'nick'
    print("Python vision is " + sys.version)
    print("hello world.")
    print(" 世界你好！ ")
    print(" 你好，012, 世界你好, user：" + username)
    print(" 123, 世界你好, user：" + username)
    print("1世界你好！")
    print("\n世界你好！")
    print("hello世界你好！")
    
    #print("世界你好！")		# 在windows下command窗口中运行会出错：IOError: [Errno 22] Invalid argument，在pycharm下运行不会出现该错误
    #print "世界你好！"		# 在windows下command窗口中运行会出错：IOError: [Errno 22] Invalid argument，在pycharm下运行不会出现该错误
    
    # print(u'中文python')	# 在windows下command窗口中运行会出错：LookupError: unknown encoding: cp65001
    # print (unicode("世界你好！", encoding="utf-8"))	# 在windows下command窗口中运行会出错：LookupError: unknown encoding: cp65001
    

  

###  错误 IOError: [Errno 22] Invalid argument 解决办法：

需要在中文字符串开头加上一个英文空格，则在windows command下就可正常打印中文字符串。

  

###  错误 LookupError: unknown encoding: cp65001 解决办法：

在windwos command下执行python时，需要先执行以下两行，cmd窗口的编码改为utf-8

    
    
    > chcp 65001
    > set PYTHONIOENCODING=utf-8
    

