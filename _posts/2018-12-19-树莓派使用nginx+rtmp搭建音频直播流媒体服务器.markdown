---
title: 树莓派使用nginx+rtmp搭建音频直播流媒体服务器
date: 2018-12-19 15:55:07

---
##  前言

想使用树莓派连接usb音频采集卡实时采集收音机接收到的音频，树莓派上运行着由nginx+RTMP
搭建的直播流媒体服务器，这样就可以在客户端上通过支持rtmp串流协议的播放器就可以正常接收到音频直播流了。

###  采用方案

  * 树莓派作为流媒体服务器 
  * 直播协议：RTMP 
  * 实时音频源：usb音频采集卡实时采集的收音机电台音频 

####  什么是nginx？

Nginx是一款轻量级的Web 服务器/反向代理服务器及电子邮件（IMAP/POP3）代理服务器，并在一个BSD-like
协议下发行。其特点是占有内存少，并发能力强，事实上nginx的并发能力确实在同类型的网页服务器中表现较好，中国大陆使用nginx网站用户有：百度、京东、新浪、网易、腾讯、淘宝等。

###  什么是RTMP？

RTMP是Real Time Messaging
Protocol（实时消息传输协议）的首字母缩写。该协议基于TCP，是一个协议族，包括RTMP基本协议及RTMPT/RTMPS/RTMPE等多种变种。RTMP是一种设计用来进行实时数据通信的网络协议，主要用来在Flash/AIR平台和支持RTMP协议的流媒体/交互服务器之间进行音视频和数据通信。支持该协议的软件包括Adobe
Media Server/Ultrant Media Server/red5等。

###  NGINX-RTMP 流媒体服务器

基于NGINX模块，使用C语言编写的流媒体服务器，也是目前市场上使用最多的流媒体服务器。伴随着2012年CDN业务的扩展，直播业务需求暴涨，由于NGINX-
RTMP中直播点播共用一套服务器，且用户熟悉信任NGINX；NGINX-RTMP逐渐处于行业垄断地位。

##  场景介绍

建议使用最新的树莓派镜像文件，我用之前做过一些东西在上面的树莓派系统在安装nginx服务器时出现了找不到很多需要的依赖，后来又换成了树莓派最新的raspbian系统。

本文所用树莓派系统镜像： ` 2018-11-13-raspbian-stretch-full.img `  
本文所用树莓派系统版本： ` Linux raspberrypi 4.14.79+ #1159 Sun Nov 4 17:28:08 GMT 2018
armv6l GNU/Linux `

##  树莓派搭建nginx+rtmp流媒体服务器步骤

先执行 ` sudo apt-get update ` 更新一下当前系统的软件列表，再进行以下操作。

1、安装所需要的依赖；

    
    
    sudo apt-get install build-essential libpcre3 libpcre3-dev libssl-dev
    

2、安装nginx和rtmp，依此执行以下每一行命令；

    
    
    wget http://nginx.org/download/nginx-1.11.8.tar.gz
    
    wget https://github.com/arut/nginx-rtmp-module/archive/master.zip
    
    tar -zxvf nginx-1.11.8.tar.gz
    
    unzip master.zip
    
    cd nginx-1.11.8
    
    ./configure --with-http_ssl_module --add-module=../nginx-rtmp-module-master
    
    make
    
    sudo make install
    

3、执行 ` sudo nano /usr/local/nginx/conf/nginx.conf ` 修改nginx配置文件，添加以下内容。

    
    
    # /usr/local/nginx/conf/nginx.conf
    # 添加
    rtmp {
        server {
            listen 1935;
            chunk_size 4096;
            application live {
                live on;
                record off;
               }
            }
        }
    

4、启动nginx+rtmp流媒体服务器

    
    
    sudo /usr/local/nginx/sbin/nginx
    

5、安装ffmpeg，默认树莓派最新的raspbian系统中已经带有ffmpeg；

    
    
    sudo apt install ffmpeg
    

6、将usb音频采集卡插到树莓派的usb口，启动ffmpeg从usb音频采集卡实时采集实时的外部收音机电台音频，并推流到树莓派上搭建好的nginx+rtmp流媒体服务器。

    
    
    ffmpeg -f alsa -ac 2 -i hw:1,0 -ar 44100 -f flv rtmp://192.168.10.109/live/audio
    

参数说明：主要参数：  
-f 设定输出格式   
-i 设定输入流（hw:1,0为外接的usb音频采集卡设备，hw:1,0的1指的是第一个外部设备，因为树莓派内部没有声卡，所以只能使用外部的usb音频采集卡）；   
-ar 设定采样率（因为输出为flv格式，所以采样率只能选择44100，22050，11025这三种）； 

另外，192.168.10.109为树莓派的IP地址。

7、在windows客户端中使用PotPlayer打开链接“rtmp://192.168.10.109/live/audio”，即可收听到实时的收音机电台音频，延时大概为2秒。

##  参考资料

1、 [ 树莓派使用nginx+rtmp搭建直播服务器 - zizi7的专栏 - CSDN博客
](https://blog.csdn.net/zizi7/article/details/54347223)  
2、 [ 树莓派nginx+rtmp搭建直播流媒体服务 - 夜魂 - 开源中国
](https://my.oschina.net/yehun/blog/1633459)  
3、 [ 树莓派使用nginx+rtmp搭建直播服务器 - 程序园 ](http://www.voidcn.com/article/p-ebijbfwd-
bad.html)  
4、 [ 树莓派使用nginx+rtmp搭建直播服务器 | Cyckerr
](https://cyckerr.github.io/blog/2017/09/29/SmartQQ/)  
5、 [ 使用树莓派实现24小时不间断直播 - EdmondFrank’s 时光足迹
](https://edmondfrank.github.io/blog/2018/02/12/shi-yong-shu-mei-pai-shi-xian-
24xiao-shi-bu-jian-duan-zhi-bo/)  
6、 [ 用树莓派做 RTMP 流直播服务器，可推送至斗鱼直播 | 树莓派实验室
](http://shumeipai.nxez.com/2017/11/01/build-rtmp-stream-live-server-with-
raspberry-pi.html)  
7、 [ FFmpeg 录制桌面、麦克风、摄像头 - 勤能补拙 - CSDN博客
](https://blog.csdn.net/candcplusplus/article/details/53955012)  
8、 [ ffmpeg 音视频集大成者之学习-iibull-ChinaUnix博客
](http://blog.chinaunix.net/uid-27875-id-5783016.html)  
9、 [ ALSA 音频工具 amixer、aplay、arecord - 卢小喵的学习笔记 - CSDN博客
](https://blog.csdn.net/lu_embedded/article/details/52447678)  
10、 [ Linux使用ffmpeg直播推流 ](https://blog.mangege.com/tech/2015/02/15/1.html)
(很重要的一个参考资料)  
11、 [ ffmpeg 音视频集大成者之学习-iibull-ChinaUnix博客
](http://blog.chinaunix.net/uid-27875-id-5783016.html)  
12、 [ FFmpeg 录制桌面、麦克风、摄像头 - 勤能补拙 - CSDN博客
](https://blog.csdn.net/candcplusplus/article/details/53955012)

