---
layout:		post
title: 		Windows下使用ffmpeg采集音频
date: 		2019-01-15 20:44:52
author:		"唐传林"
header-img: "img/post-bg-2015.jpg"
catalog:	 true
categories:
- ffmpeg
tags:
- ffmpeg
- windows
- 音频采集

---
##  前言

本文介绍一下ffmpeg在windows下采集音频的相关命令。

一开始在命令行下使用ffmpeg时执行“ffmpeg -list_devices true -f dshow -i dummy
”使用dshow来枚举当前系统上存在的音视频采集设备时，发现中文乱码，后来在老师帮助下，在命令行下执行命令“ chcp 65001”
将windows命令行窗口的编码改为了utf-8编码，就解决了ffmpeg的中文乱码问题。

####  1、 ffmpeg在windows下查看设备的命令：

    
    
    ffmpeg -list_devices true -f dshow -i dummy 
    

####  2、ffmpeg在windows下录音为文件，输入为usb采集采集卡或麦克风

    
    
    ffmpeg -f dshow -i audio="麦克风阵列 (11- USB PnP Audio Device)" out.mp3
    

其中：“麦克风阵列 (11- USB PnP Audio Device)” 为usb音频采集卡或麦克风在windows设备管理器中的设备名称。

####  3、ffmpeg在windows下实时采集音频并播放，输入为usb采集采集卡或麦克风

    
    
    ffplay -f dshow -i audio="麦克风阵列 (11- USB PnP Audio Device)"
    

####  4、实时采集音频并播放并绘制实时音频的左右声道的波形：

    
    
    ffplay -showmode 1  -f dshow -i audio="麦克风阵列 (11- USB PnP Audio Device)"
    

####  5、采集摄像头实时视频并实时显示：

    
    
    ffplay  -showmode 0 -f dshow -i video="Integrated Webcam"
    

  

###  10张usb音频采集卡同时采集的界面图如下：

![在这里插入图片描述](https://img-blog.csdnimg.cn/20190214214731928.jpg)

