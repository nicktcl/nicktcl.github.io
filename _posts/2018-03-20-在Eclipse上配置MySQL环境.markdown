---
title: 在Eclipse上配置MySQL环境
date: 2018-03-20 18:04:38

---
#  在Eclipse上配置MySQL环境

###  电脑环境：

Windows10教育版 64位 （OS内部版本：16299.125）  
Eclipse版本： [ eclipse-jee-oxygen-2-win32-x86_64
](https://www.eclipse.org/downloads/download.php?file=/oomph/epp/oxygen/R2
/eclipse-inst-win64.exe)  
MySQL的JDBC驱动程序版本： [ mysql-connector-java-5.1.46.zip
](https://cdn.mysql.com//Downloads/Connector-J/mysql-connector-
java-5.1.46.zip)

###  在Eclipse上配置MySQL环境步骤：

1、首先，请按照博客“ [ Windows10下安装MySQL5.0详细教程
](http://blog.csdn.net/tang_chuanlin/article/details/79603063)
”在电脑上安装好MySQL5.0;  
2、到 [ MySQL官网下载MySQL的JDBC驱动程序 ](https://cdn.mysql.com//Downloads/Connector-J
/mysql-connector-java-5.1.46.zip) ,解压后得到以下文件。其中最关键的是“mysql-connector-
java-5.1.46-bin.jar”文件。  
![这里写图片描述](//img-
blog.csdn.net/20180320160618933?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
3、打开Eclipse，依次打开Window——>preferences——>java——>Build Path——>User Libraries.  
![这里写图片描述](//img-
blog.csdn.net/20180320161208968?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
![这里写图片描述](//img-
blog.csdn.net/20180320161402942?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
4、点击右侧的new按钮， 并输入JDBC，选中对勾，点击右下角“Apply and close”。  
![这里写图片描述](//img-
blog.csdn.net/20180320161601780?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
5、回到上一级界面，点击Add External JARs，打开到你的jdbc存放的目录，点击右下角“Apply and close”。  
![这里写图片描述](//img-
blog.csdn.net/20180320161735418?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
![这里写图片描述](//img-
blog.csdn.net/20180320161742551?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
![这里写图片描述](//img-
blog.csdn.net/20180320161852710?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
6、接下来是项目导入jar包，项目右键——>Build Path——>Configure Build Path。  
![这里写图片描述](//img-
blog.csdn.net/20180320162054246?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
7、点击右侧Libraries菜单下的Add Library——>User Library-Next。打上对勾点击finish。  
![这里写图片描述](//img-
blog.csdn.net/20180320164227745?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
![这里写图片描述](//img-
blog.csdn.net/20180320164449204?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
![这里写图片描述](//img-
blog.csdn.net/20180320164456239?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
8、回到上一级界面就可以看到你添加的JDBC，点击右下角“Apply and close”。  
![这里写图片描述](//img-
blog.csdn.net/20180320164624365?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
9、这样在你的项目下就可以看到你导入的JDBC了。  
![这里写图片描述](//img-
blog.csdn.net/20180320170055670?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
10、我们写一段java代码测试连接MySQL。项目右键——>New——>Class。  
![这里写图片描述](//img-
blog.csdn.net/20180320170352745?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
11、输入类名，点击finish。  
![这里写图片描述](//img-
blog.csdn.net/20180320170556101?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
12、键入如下测试代码。

    
    
    import java.sql.*;
    
    public class TestJDBC {
        public static void main(String args[]) {
            Connection conn=null;
            try {
              Class.forName("com.mysql.jdbc.Driver");     
              System.out.println("Success loading Mysql Driver!");
            }
            catch (Exception e) {
              System.out.print("Error loading Mysql Driver!");
              e.printStackTrace();
            }
    
            try {
              conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/test", "root", "12345678");
              System.out.println("Success connect Mysql server!");
              conn.close();
    
            }
            catch (Exception e) {
              System.out.print("get data error!");
              e.printStackTrace();
            }  
        }
    }

13、运行后在Eclipse控制如得到如下提示则说明Eclisep的MySQL环境配置成功。  
![这里写图片描述](//img-
blog.csdn.net/20180320180339115?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

