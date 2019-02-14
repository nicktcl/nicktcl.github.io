---
layout:		post
title: 		Linux下通过rdesktop连接Windows远程桌面
date: 		2019-01-08 14:11:50
author:		"唐传林"
header-img: "img/post-bg-2015.jpg"
catalog:	 true

---
###  前言

最近用windows自带的进程桌面远程连接树莓派的桌面环境，突发其想想用树莓派反过来远程连接一下windows的桌面环境。这样就可以随身携带树莓派，然后在外面就可以随时使用自己的windows电脑。

###  什么是 rdesktop ？

rdesktop是linux下支持Windows远程桌面连接的客户端程序，在linux系统下可通过它远程访问Windows桌面，支持多种版本。rdesktop是sourceforge下支持GPL协议的一个开源项目，采用RDP（Remote
Desktop Protocol,远程桌面协议），几乎可以连接windows的所有版本，诸如NT 4 Terminal Server, 2000, XP,
2003, 2003 R2, Vista, 2008, 7, and 2008 R2等。目前，rdesktop可运行于所有的基于X
window平台的Unix系统中。

主页： [ http://www.rdesktop.org/ ](http://www.rdesktop.org/)  
Github仓库： [ https://github.com/rdesktop/rdesktop
](https://github.com/rdesktop/rdesktop)

###  安装 rdesktop

命令行安装，操作很简单。

  * Debian（Ubuntu）系统下执行： 

    
    
    $ sudo apt-get install rdesktop
    

  * Centos/RedHat可以通过yum命令在线安装： 

    
    
    yum -y install rdesktop
    

###  windows开启远程桌面

基本操作：计算机—属性—远程设置—远程。  
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190108140043464.png?x-oss-
process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=,size_16,color_FFFFFF,t_70)  
要开启Windows远程桌面，有三个选项，第一个如果是不允许连接到本机，则选择“不允许连接到这台计算机”，这样可以阻止任何人使用远程桌面或
RemoteApp连接到您的计算机。后面两个选项，“允许任意版本远程桌面计算机”和“仅运行使用网络级别身份验证的远程桌面的计算机”，两者差别如下：

“允许运行任意版本远程桌面的计算机连接”——如果不确定将要连接过来的计算机操作系统，可以选择这一项。安全性较第三个选项低。  
“只允许运行带网络级身份验证的远程桌面的计算机连接”——允许使用运行带网络级身份验证的远程桌面或 RemoteApp 版本计算机的人连接到您的计算机。

###  rdesktop连接windows远程桌面

打开命令行，仅需要一条命令：

    
    
    $ rdesktop -f 192.168.1.112  (这里的ip对应自己windows的ip地址)
    

就ok了。

-f 参数默认全屏打开，使用Ctrl + Alt + Enter可以退出全屏模式。 

###  rdesktop使用拓展

linux下执行 ` rdesktop -help ` 可以打开rdesktop的帮助文档。

    
    
    pi@raspberrypi:~ $ rdesktop -help
    rdesktop: A Remote Desktop Protocol client.
    Version 1.8.3. Copyright (C) 1999-2011 Matthew Chapman et al.
    See http://www.rdesktop.org/ for more information.
    
    Usage: rdesktop [options] server[:port]
       -u: user name
       -d: domain
       -s: shell / seamless application to start remotly
       -c: working directory
       -p: password (- to prompt)
       -n: client hostname
       -k: keyboard layout on server (en-us, de, sv, etc.)
       -g: desktop geometry (WxH)
       -i: enables smartcard authentication, password is used as pin
       -f: full-screen mode
       -b: force bitmap updates
       -L: local codepage
       -A: path to SeamlessRDP shell, this enables SeamlessRDP mode
       -B: use BackingStore of X-server (if available)
       -e: disable encryption (French TS)
       -E: disable encryption from client to server
       -m: do not send motion events
       -C: use private colour map
       -D: hide window manager decorations
       -K: keep window manager key bindings
       -S: caption button size (single application mode)
       -T: window title
       -t: disable use of remote ctrl
       -N: enable numlock syncronization
       -X: embed into another window with a given id.
       -a: connection colour depth
       -z: enable rdp compression
       -x: RDP5 experience (m[odem 28.8], b[roadband], l[an] or hex nr.)
       -P: use persistent bitmap caching
       -r: enable specified device redirection (this flag can be repeated)
             '-r comport:COM1=/dev/ttyS0': enable serial redirection of /dev/ttyS0 to COM1
                 or      COM1=/dev/ttyS0,COM2=/dev/ttyS1
             '-r disk:floppy=/mnt/floppy': enable redirection of /mnt/floppy to 'floppy' share
                 or   'floppy=/mnt/floppy,cdrom=/mnt/cdrom'
             '-r clientname=<client name>': Set the client name displayed
                 for redirected disks
             '-r lptport:LPT1=/dev/lp0': enable parallel redirection of /dev/lp0 to LPT1
                 or      LPT1=/dev/lp0,LPT2=/dev/lp1
             '-r printer:mydeskjet': enable printer redirection
                 or      mydeskjet="HP LaserJet IIIP" to enter server driver as well
             '-r sound:[local[:driver[:device]]|off|remote]': enable sound redirection
                         remote would leave sound on server
                         available drivers for 'local':
                         alsa:      ALSA output driver, default device: default
             '-r clipboard:[off|PRIMARYCLIPBOARD|CLIPBOARD]': enable clipboard
                          redirection.
                          'PRIMARYCLIPBOARD' looks at both PRIMARY and CLIPBOARD
                          when sending data to server.
                          'CLIPBOARD' looks at only CLIPBOARD.
             '-r scard[:"Scard Name"="Alias Name[;Vendor Name]"[,...]]
              example: -r scard:"eToken PRO 00 00"="AKS ifdh 0"
                       "eToken PRO 00 00" -> Device in Linux/Unix enviroment
                       "AKS ifdh 0"       -> Device shown in Windows enviroment
              example: -r scard:"eToken PRO 00 00"="AKS ifdh 0;AKS"
                       "eToken PRO 00 00" -> Device in Linux/Unix enviroment
                       "AKS ifdh 0"       -> Device shown in Windows enviroment
                       "AKS"              -> Device vendor name
       -0: attach to console
       -4: use RDP version 4
       -5: use RDP version 5 (default)
       -o: name=value: Adds an additional option to rdesktop.
               sc-csp-name        Specifies the Crypto Service Provider name which
                                  is used to authenticate the user by smartcard
               sc-container-name  Specifies the container name, this is usally the username
               sc-reader-name     Smartcard reader name to use
               sc-card-name       Specifies the card name of the smartcard to use
    

###  命令举例

比如如下命令：

    
    
    $ rdesktop -f -a 16 -u username -p password  IP  -r sound:on/off -g 1024*768
    

说明：  
1、username和password分别是目标电脑的帐号和密码，-a 16表示位色，最高就是16位；  
2、IP为目标电脑的IP地址（可能需要先连接VPN）；  
3、sound：on表示传送目标电脑的声音，off则为关闭；  
4、-g 后接想要显示的分辨率，使用 -g workarea 可自适应铺满当前linux窗口大小  
5、使用 -f 参数进入全屏模式，中途可使用Ctrl+Alt+Enter组合键退出全屏（不知道的就郁闷了）;  
6、-r** disk:share_name=/local-disk** 将本地磁盘映射到远程电脑，其中share_name为显示名称，可自定义
，local-disk表示本地linux的一个目录，比如 /data。  
7、-r clipboard:PRIMARYCLIPBOARD 允许在远程主机和本机之间共享剪切板，就是可以复制粘贴。  
（更多参数详见命令行help结果……）

###  参考资料

1、 [ Linux下通过rdesktop连接Windows远程桌面 - 简书
](https://www.jianshu.com/p/91fb0b1c6815)

