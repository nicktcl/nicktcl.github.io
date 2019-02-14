---
layout:		post
title: 		在 Eclipse 上新建web项目（配置tomcat8.0后）
date: 		2018-03-21 15:32:57
author:		"唐传林"
header-img: "img/post-bg-2015.jpg"
catalog:	 true

---
#  在 Eclipse 上新建web项目（配置tomcat8.0后）

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

###  在 Eclipse 上新建web项目步骤

1、首先打开Eclipse软件，打开后在工具栏依次点击【File】——>【New】——>【Dynamic Web
Project】，这个就代表新建的项目是WEB项目。  
2、填写项目的基本信息，包括项目名、项目运行时服务器版本。可以选择tomcat或者其他都可以，看项目需要。在这里我们输入一个【TestTomcat8】来测试项目的建立，输入完毕后我们点击【Next】按钮。  
![这里写图片描述](http://img-blog.csdn.net/20180321132231864?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
3、这个窗口显示的WEB项目中需要编译的JAVA文件的目录，默认是SRC目录，这个我们不需要改，直接点击【Next】。  
![这里写图片描述](http://img-blog.csdn.net/20180321132335569?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
4、接着弹出窗口，显示的是我们的WEB项目，WEB文件相关的目录，就是html或者jsp还有js那些web相关的文件存放的目录，默认是【WebContent】，你也可以修改成你想要的文件名，注意，下面有个复选框，表示的是是否要自动生成web.xml文件。

web.xml：这个文件是WEB项目的核心文件，也是WEB项目的入口，老版本的Eclipse都会有这个文件，但是新版本的Eclipse因为可以使用在JAVA代码中注解的方式，所以提供让用户选择是否要生成。  
我们这里在自动生成web.xml文件那里打上勾，然后点击【Finish】。  
![这里写图片描述](http://img-blog.csdn.net/20180321132746622?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

5、下面就是我们新建的WEB项目的目录结果  
JAVA存放目录：SRC  
WEB文件目录：WebContent  
WEB配置文件：web.xml  
![这里写图片描述](http://img-blog.csdn.net/2018032113293151?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

6、右键点击项目，然后New——>Class 。  
![这里写图片描述](http://img-blog.csdn.net/20180321133331600?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
7、输入类名Hello，输入类名HelloWorld，点击finish。  
![这里写图片描述](http://img-blog.csdn.net/20180321151113332?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
8、写人以下测试代码并且保存。

    
    
    package Hello;
    import java.io.IOException;  
    import java.io.PrintWriter;  
    import javax.servlet.ServletException;  
    import javax.servlet.http.HttpServlet;  
    import javax.servlet.http.HttpServletRequest;  
    import javax.servlet.http.HttpServletResponse;  
    
    public class HelloWorld extends HttpServlet {  
    
        public void doGet(HttpServletRequest request, HttpServletResponse response)  
                throws IOException, ServletException {  
            PrintWriter out = response.getWriter();  
            out.write("<html>\r\n");  
            out.write("<head>\r\n");  
            // 设定解码方式  
            out.write("<meta http-equiv=\"Content-Type\" content=\"text/html; charset=UTF-8\">\r\n");  
            out.write("</head>\r\n");  
            out.write("\r\n");  
            out.write("<body>\r\n");  
            out.write("<H1>\r\n");  
            out.write("helloworld");  
            out.write("\r\n");  
            out.write("</H1>\r\n");  
            out.write("</body>\r\n");  
            out.write("</html>");  
        }  
    }  

![这里写图片描述](http://img-blog.csdn.net/2018032115122210?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
10、然后打开项目文件夹下WebContent——>WEB-INF——>web.xml，使用Text editor打开web.xml。  
![这里写图片描述](http://img-blog.csdn.net/2018032115172144?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
11、在web.xml中输入如下内容并且保存。

    
    
    <?xml version="1.0" encoding="UTF-8"?>
    <web-app xmlns="http://java.sun.com/xml/ns/javaee"
      xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
      xsi:schemaLocation="http://java.sun.com/xml/ns/javaee
                          http://java.sun.com/xml/ns/javaee/web-app_3_0.xsd"
      version="3.0"
      >
      <display-name>hello</display-name>
      <description>
    hello
      </description>
      <!--定义控制器 -->
    <servlet>
    <servlet-name>Servlet</servlet-name>
    <servlet-class>Hello.HelloWorld</servlet-class>
    </servlet>
    <!-- 拦截/helloworld的请求 -->
    <servlet-mapping>
    <servlet-name>Servlet</servlet-name>
    <url-pattern>/HelloWorld</url-pattern>
    </servlet-mapping>
    </web-app>

注意：servlet-class标签里的类的名称和路径是前面new包和类时填写的，需要和之前填写的一致，我这里是包名是Hello，类名是HelloWorld
，所以servlet-class标签里的内容是：Hello.HelloWorld

12、在eclipse下切换到HelloWorld编辑框，点击运行按扭旁边的小箭头——>Run As——>Run on Sever。  
![这里写图片描述](http://img-blog.csdn.net/20180321152653450?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
13、点击finish。  
![这里写图片描述](http://img-blog.csdn.net/20180321212049967?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
1、控制如出现如下界面则说明tomcat已经在后台运行。  
![这里写图片描述](http://img-blog.csdn.net/2018032115273852?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
15、我们打开自己的浏览器，在地址栏输入以下路径验证是否可以访问到刚写的页面： [
http://localhost:8080/TestTomcat8/HelloWorld
](http://localhost:8080/TestTomcat8/HelloWorld)
，其中Hello是项目的名称，HelloWorld是类名称。可看到正常输出HelloWorld。  
![这里写图片描述](http://img-blog.csdn.net/20180321153221608?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

###  参考资料

1、 [ 使用eclipse建立第一个web项目(java)
](http://blog.csdn.net/zhouzezhou/article/details/52496511)  
2、 [ eclipse怎么样新建web项目，eclipse新建web项目
](https://jingyan.baidu.com/article/ce436649f3334e3773afd3e0.html)

