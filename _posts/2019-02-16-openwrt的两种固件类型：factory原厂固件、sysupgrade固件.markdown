---
layout:  post
title:   openwrt的两种固件类型：factory原厂固件、sysupgrade固件
date:   2019-02-16 17:51:22
author:  "唐传林"
header-img: "img/post-bg-2015.jpg"
catalog:   false

---
factory多了一些验证的东西，用于在原厂固件的基础上进行升级。

普通家用路由一般不是openwrt固件，如果要将家用路由升级为openwrt固件，就可以用factory刷到路由上。sysupgrade是在openwrt路由基础上升级固件，无论你是原厂固件或者本身就是openwrt固件，要升级到openwrt，factory都适用，但是sysupgrade只能用在升级，TTL救砖的时候就不能用sysupgrade。sysupgrade不包含数据分区，factory带，factory预留原厂分区，sysupgrade只包含openwrt分区。

有一个公式:sysupgrade.bin+空闲空间+系统的配置空间=factory.bin的大小

在openwrt wiki中有专门描述sysupgrade：

sysupgrade替换linux内核和squash文件系统，擦除整个jffs2部分。能保留配置文件，但不能保留二进制安装文件。

