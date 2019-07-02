---
layout:  post
title:   使用rufus制作windows系统安装u盘
date:   2019-04-12 20:35:31
author:  "唐传林"
header-img: "img/post-bg-2015.jpg"
catalog:   true

---
##  前言

之前都是使用UltraISO 9.6.1软件将系统镜像文件ISO刻录到u盘，但是昨天在刻录windows server
2019时，发现它的镜像中“sources”文件夹下的“install.wim”单个文件大于4G了，而UltraISO软件在刻录这个镜像到u盘时，会自动让u盘采用FAT32的文件系统，所以大于4G的“install.wim”这个文件就无法刻录到u盘。若是手动将u盘格式化为NTFS文件系统，刻录时还是会被UltraISO软件格式化为FAT32文件系统。所以只能放弃UltraISO软件了另想办法了。

##  解决办法

使用rufus制作windows系统安装u盘。

##  rufus官方下载地址

[ 官方下载请点这里 ](http://rufus.ie/)

##  软件界面

点击“选择”然后选择需要刻录的系统镜像ISO文件，软件会自己设置好参数，点击“开始”就可以开始刻录到u盘了。使用方法比UltraISO 要简便很多。
![在这里插入图片描述](http://img-blog.csdnimg.cn/20190412203200101.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9uaWNrdGNsLmJsb2cuY3Nkbi5uZXQ=,size_16,color_FFFFFF,t_70)

