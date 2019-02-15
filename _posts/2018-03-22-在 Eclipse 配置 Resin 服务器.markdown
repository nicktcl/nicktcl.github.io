---
layout:  post
title:   在 Eclipse 配置 Resin 服务器
date:   2018-03-22 21:29:19
author:  "唐传林"
header-img: "img/post-bg-2015.jpg"
catalog:   false

---
#  在 Eclipse 部署Resin服务器

####  电脑环境：

Windows10教育版 64位 （OS内部版本：16299.125）  
jdk版本：jdk1.8_111  
Eclipse版本： [ eclipse-jee-oxygen-2-win32-x86_64
](http://www.eclipse.org/downloads/download.php?file=/oomph/epp/oxygen/R2
/eclipse-inst-win64.exe)  
Resin版本：Resin4.0  
MySQL的JDBC驱动程序版本： [ mysql-connector-java-5.1.46.zip
](http://cdn.mysql.com//Downloads/Connector-J/mysql-connector-java-5.1.46.zip)

###  在 Eclipse 配置 Resin 服务器的步骤

1、 [ 到Resin官网下载Resin ](http://caucho.com/download/resin-pro-4.0.55.zip)
，并解压到E盘（或其他盘）的根目录文件夹下。  最好放到一个盘的根目录文件夹下，放到中文文件夹下会导致后面Resin运行闪退。

2、打开Eclipse，依次打开Window——>preferences，  
在preferences中打开Server——>Runtime Evironment，点击右侧的Add。  
![这里写图片描述](http://img-blog.csdn.net/20180320212602243?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
![](http://img-blog.csdn.net/20180320212803395?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

3、在点击Add后打开的窗口中选择Resin文件夹下的Resin4.0，勾选上“ ` Creat a new local server `
”然后点击Next。  
![这里写图片描述](http://img-blog.csdn.net/20180322205118403?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

4、需要注意一点的是，Resin运行的环境是JDK，而不是JRE，所以需要在运行环境时，选择JDK。然后Resin
Home选择刚刚下载解压好的resin文件夹。然后点击Next。  
![这里写图片描述](http://img-blog.csdn.net/20180322212057923?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

5、点击Next。  
![这里写图片描述](http://img-blog.csdn.net/20180322205319943?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

6、更改端口不要与tomcat的冲突，点击finish。  
![这里写图片描述](http://img-blog.csdn.net/20180322212220366?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

7、在eclipse下面部分切换到servers子项，右键点击Resin4.0，再点击start就可以运行Resin4.0了。  
![这里写图片描述](http://img-blog.csdn.net/20180322212421475?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

8、当eclipse的控制台输出如下信息，则说明Resin4.0运行成功。  
![这里写图片描述](http://img-blog.csdn.net/2018032221261760?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

9、我们在浏览器输入 ` http://127.0.0.1:8080/ ` ，就可以看到Resin的默认页面。  
![这里写图片描述](http://img-blog.csdn.net/20180322212737585?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

到这里，eclipse与Resin服务器就配置完成了。

####  参考资料：

1、 [ Eclipse集成Resin服务器
](http://blog.csdn.net/shehun1/article/details/38185037)  
2、 [ Eclipse(Luna)集成Resin4.0+服务器，以及配置参数
](http://blog.csdn.net/aixiaoyang168/article/details/50948149)

