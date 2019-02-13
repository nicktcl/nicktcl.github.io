---
title: Tomcat新特性：支持Servlet3.0注解定义，无需配置web.xml
date: 2018-03-21 21:19:58

---
#  Tomcat新特性：支持Servlet3.0注解定义，无需配置web.xml

###  前言

tomcat从7.0版本开始就支持Servlet3.0，在Eclipse中不再需要web.xml配置servlet，而通过注解的方式找寻servlet。

###  电脑环境：

Windows10教育版 64位 （OS内部版本：16299.125）  
jdk版本：jdk1.8_111  
Eclipse版本： [ eclipse-jee-oxygen-2-win32-x86_64
](https://www.eclipse.org/downloads/download.php?file=/oomph/epp/oxygen/R2
/eclipse-inst-win64.exe)  
tomcat版本： [ tomcat8.0
](https://archive.apache.org/dist/tomcat/tomcat-8/v8.0.50/bin/apache-
tomcat-8.0.50-windows-x64.zip)  
MySQL的JDBC驱动程序版本： [ mysql-connector-java-5.1.46.zip
](https://cdn.mysql.com//Downloads/Connector-J/mysql-connector-
java-5.1.46.zip)

###  步骤

1、首先打开Eclipse软件，打开后在工具栏依次点击【File】——>【New】——>【Dynamic Web
Project】，这个就代表新建的项目是WEB项目。  
2、填写项目的基本信息，包括项目名、项目运行时服务器版本。可以选择tomcat或者其他都可以，看项目需要。在这里我们输入一个【TestTomcat8】来测试项目的建立，输入完毕后我们点击【Next】按钮。  
![这里写图片描述](//img-
blog.csdn.net/20180321132231864?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
3、这个窗口显示的WEB项目中需要编译的JAVA文件的目录，默认是SRC目录，这个我们不需要改，直接点击【Next】。  
![这里写图片描述](//img-
blog.csdn.net/20180321132335569?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
4、接着弹出窗口，显示的是我们的WEB项目，WEB文件相关的目录，就是html或者jsp还有js那些web相关的文件存放的目录，默认是【WebContent】，你也可以修改成你想要的文件名，不用勾选创建web.xml复选框。然后点击finish。  
![这里写图片描述](//img-
blog.csdn.net/20180321201743109?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
5、右键点击项目，然后New——>Servlet。  
![这里写图片描述](//img-
blog.csdn.net/20180321205354826?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
6、在对话框中输入包名 ` cn.nicktcl.test.hello ` 和类名 ` HelloWorld2 ` ，点击finish。  
![这里写图片描述](//img-
blog.csdn.net/20180321210356671?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
7、将以下代码粘贴到文件HelloWorld2.java如下位置。  
![这里写图片描述](//img-
blog.csdn.net/20180321211913447?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

    
    
                PrintWriter out = response.getWriter();  
                out.write("<html>\r\n");  
                out.write("<head>\r\n");  
                // 设定解码方式  
                out.write("<meta http-equiv=\"Content-Type\" content=\"text/html; charset=UTF-8\">\r\n");  
                out.write("</head>\r\n");  
                out.write("\r\n");  
                out.write("<body>\r\n");  
                out.write("<H1>\r\n");  
                out.write("helloworld2");  
                out.write("\r\n");  
                out.write("</H1>\r\n");  
                out.write("</body>\r\n");  
                out.write("</html>");  
        }

8、点击运行按扭旁边的小箭头——>Run As——>Run on Sever。  
![这里写图片描述](//img-
blog.csdn.net/20180321211001968?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
9、点击finish。  
![这里写图片描述](//img-
blog.csdn.net/20180321211102117?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
10、控制如出现如下界面则说明tomcat已经在后台运行。  
![这里写图片描述](//img-
blog.csdn.net/20180321211144897?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
11、我们打开自己的浏览器，在地址栏输入以下路径验证是否可以访问到刚写的页面： [
http://localhost:8080/TestTomcat8/HelloWorld2
](http://localhost:8080/TestTomcat8/HelloWorld2)
，其中Hello是项目的名称，HelloWorld是类名称。可看到正常输出HelloWorld2。  
![这里写图片描述](//img-
blog.csdn.net/20180321211659748?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

###  参考资料

1、 [ Tomcat7.0新特性：支持Servlet3.0注解定义，无需配置web.xml
](http://blog.csdn.net/u010087830/article/details/42392695)  
2、 [ Servlet2.5和 3.0区别（Servlet 3.0 新特性详解）
](http://blog.csdn.net/fuxiaohui/article/details/72762213)

