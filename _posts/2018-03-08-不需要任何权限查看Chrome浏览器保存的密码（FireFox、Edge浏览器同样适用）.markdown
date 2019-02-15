---
layout:		post
title: 		不需要任何权限查看Chrome浏览器保存的密码（FireFox、Edge浏览器同样适用）
date: 		2018-03-08 12:41:47
author:		"唐传林"
header-img: "img/post-bg-2015.jpg"
catalog:	 true

---
#  不需要任何权限查看Chrome浏览器保存的密码（FireFox、Edge浏览器同样适用）

* * *

##  前言

如今我们为了方便，在浏览器中都保存了很多账号的密码，这样每次登录保存过的账号就不用输入密码了，但是方便的同时也存在着很多的问题。

通常，我们在Chrome中，在地址栏输入chrome://settings/passwords,就可以跳出浏览器自带的密码管理列表了。

![这里写图片描述](https://img-blog.csdn.net/20180308091101146?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvVGFuZ19DaHVhbmxpbg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

当我们要查看Chrome浏览器上保存的某一个密码时，点击“眼睛”图标，会弹出一个对话框来要求输入Windows密码来验证你的权限。所以用这种方法查看密码时必须知道Windows开机密码。  
![这里写图片描述](https://img-blog.csdn.net/20180308091528937?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvVGFuZ19DaHVhbmxpbg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

##  现在我们用另一种方法就可不用任何权限查看Chrome浏览器保存的密码。

1、用浏览器打开要查看保存密码的页面。这里我们用163邮箱登录来做实验。  
![这里写图片描述](https://img-blog.csdn.net/20180308093006659?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvVGFuZ19DaHVhbmxpbg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
2、按F12打开网页源码  
![这里写图片描述](https://img-blog.csdn.net/20180308093055718?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvVGFuZ19DaHVhbmxpbg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
3、按Ctrl+F在网页源码中搜索“password”，会查找到好几个“password”，我们需要定位到与密码输入框有关的那一个“password”。  
![这里写图片描述](https://img-blog.csdn.net/2018030809332482?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvVGFuZ19DaHVhbmxpbg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

![这里写图片描述](https://img-blog.csdn.net/20180308094156734?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvVGFuZ19DaHVhbmxpbg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

4、找到input type=”password”一行

![这里写图片描述](https://img-blog.csdn.net/20180308094240948?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvVGFuZ19DaHVhbmxpbg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

5、将 type=”password”改为type=”text”  
![这里写图片描述](https://img-blog.csdn.net/20180308094337502?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvVGFuZ19DaHVhbmxpbg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

现在就可看到保存的密码了。  
![这里写图片描述](https://img-blog.csdn.net/20180308094535535?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQvVGFuZ19DaHVhbmxpbg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

##  最后，建议大家，一些重要的站点不要让浏览器记住密码，人不在电脑旁记得按下“ ` win+L ` ”锁屏。

