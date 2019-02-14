---
layout:		post
title: 		错误 
date: 		2019-02-14 15:25:56
author:		"唐传林"
header-img: 	"img/post-bg-2015.jpg"
catalog:	 true
---


运行python程序时出现以下错误：
```
UnicodeDecodeError: 'ascii' codec can't decode byte 0xe5 in position 0: ordinal not in range(128)
```


解决办法：
摘自：https://stackoverflow.com/questions/21393758/unicodedecodeerror-ascii-codec-cant-decode-byte-0xe5-in-position-0-ordinal

Figured it out.
I put the following at the start of my python file
```linux
import sys
reload(sys)
sys.setdefaultencoding("utf-8")
```
