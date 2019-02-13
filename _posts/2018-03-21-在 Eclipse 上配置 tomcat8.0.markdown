---
title: 在 Eclipse 上配置 tomcat8.0
date: 2018-03-21 13:02:24
categories:
- java
tags:
- tomcat8
- eclipse上配置tomcat8

---
#  在 Eclipse 上配置 tomcat8.0

###  电脑环境：

Windows10教育版 64位 （OS内部版本：16299.125）  
Eclipse版本： [ eclipse-jee-oxygen-2-win32-x86_64
](https://www.eclipse.org/downloads/download.php?file=/oomph/epp/oxygen/R2
/eclipse-inst-win64.exe)  
jdk版本：jdk1.8_111  
MySQL的JDBC驱动程序版本： [ mysql-connector-java-5.1.46.zip
](https://cdn.mysql.com//Downloads/Connector-J/mysql-connector-
java-5.1.46.zip)

###  在 Eclipse 上配置 tomcat8.0步骤

1、 [ 到apache官网下载tomcat8.0
](https://archive.apache.org/dist/tomcat/tomcat-8/v8.0.50/bin/apache-
tomcat-8.0.50-windows-x64.zip) ，并解压。需要 [ 下载其他版本的tomcat请点击这里
](https://archive.apache.org/dist/tomcat/) 。  
2、打开Eclipse，依次打开Window——>preferences，  
在preferences中打开Server——>Runtime Evironment，点击右侧的Add。  
![这里写图片描述](//img-
blog.csdn.net/20180320212602243?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
![这里写图片描述](//img-
blog.csdn.net/20180320212803395?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
3、在点击Add后打开的窗口中选择tomcat8.0，然后点击Next。  
![这里写图片描述](//img-
blog.csdn.net/20180321094933499?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
4、添加解压后的Tomcat8.0，点击’Finish’ 。  
![这里写图片描述](//img-
blog.csdn.net/20180321095654531?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
5、如下图所示添加成功，点击右下角“Apply and close”。  
![这里写图片描述](//img-
blog.csdn.net/20180321095908675?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
6、运行Tomcat：打开bin目录——>双击startup.bat。  
![这里写图片描述](//img-
blog.csdn.net/20180321100304436?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
7、出现如下窗口和内容。  
![这里写图片描述](//img-
blog.csdn.net/20180321125939290?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
8、打开浏览器，输入“ [ http://localhost:8080 ](http://localhost:8080)
”出现下面这个页面，恭喜你，可以开始做web应用了。

参考资料：  
1、 [ 在 Eclipse 上配置tomcat7.0
](http://blog.csdn.net/qq_37359142/article/details/57131075)

