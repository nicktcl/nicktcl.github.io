---
layout:  post
title:   dB、dBm、dBw、dBμV、dBmV、dBV、dBv等单位介绍
date:   2019-03-01 15:39:56
author:  "唐传林"
header-img: "img/post-bg-2015.jpg"
catalog:   false

---
##  前言

我们常常遇到有关信号电平的单位(dBμV、dBmV、dBV、dBm、dBW)，很多人对这些单位模糊不清。我刚刚接触时也懵圈了半天，也是查了一些资料才搞明白。下面我们就它们之间的关系做一下简单论述。

##  单位dB

我们先来认识dB:dB是国标符号,是英文decibel或decimal Bel的缩写,意思是分贝。

DB 是一个纯计数单位：dB =
10logX。dB的意义其实再简单不过了，就是把一个很大（后面跟一长串0的）或者很小（前面有一长串0的）的数比较简短地表示出来。  
如：  
X = 1000000000000000（多少个0了？15个了）= 10logX = 150 dB  
X = 0.000000000000001（多少个0了？15个了） = 10logX = -150 dB

分贝（dB）是无量纲单位，用于量化两个值之间的比率，例如信噪比。

##  单位dBm

dBm 是 以功率1毫瓦（mw）为参考。 0 dBm = 10log1 mw  
由于它以毫瓦为参考，因此它是一个绝对单位，用于测量绝对功率。  
在射频工作中，dBm通常相对于50欧姆阻抗参考。

##  单位dBw

dBw 是 以功率1瓦（w）为参考。 0 dBw = 10log1 W = 10log1000 mw = 30 dBm。  
由于它以瓦特为参考，因此它是一个绝对单位，用于测量绝对功率。  
使用它是因为它能够在短的数量范围内表达非常大和非常小的功率值; 例如，1毫瓦= -30 dBW，1瓦= 0 dBW，10瓦= 10 dBW，100瓦= 20
dBW，以及1,000,000 W = 60 dBW。

##  单位dBμV

dBμV 是以电压1微伏（μV）为参考。广泛用于电视和天线放大器规格。60dBμV= 0 dBmV。

##  单位dBmV

dBμV 是以电压1毫伏（mV）为参考。广泛用于有线电视网络中，一个单一的电视信号的接收器处的终端的标称强度为约0
dBmV的。有线电视使用75Ω同轴电缆，因此0 dBmV对应-78.75 dBW（-48.75 dBm）或约13 nW。

##  单位dBV

dBV是以电压1伏（V）为参考，而不管阻抗。用于测量麦克风灵敏度，并指定-10 dBV的消费线电平，以降低相对于使用+4
dBu线路电平信号的设备的制造成本。[38]

##  几个在线转换工具

1、 [ dBuV 和 dBm转换在线计算器 - 电子发烧友(www.elecfans.com)](http://www.elecfans.com/tools/dbuv.htm)  
2、 [ Convert from dBuV | Cantwell Engineering](http://www.cantwellengineering.com/calculator/convert/dbuv)  
3、 [ dBm, dBW, dBuV Calculators | www.rfmentor.net](http://www.rfmentor.com/content/dbm-dbw-dbuv-calculators)  
4、 [ Dbuv And Dbm Conversion Calculator - Electronic Products](http://www.electronicproducts.com/dBuV_and_dBm_Conversion_Calculator.aspx)

###  参考资料

1、 [ dBm - Wikipedia ](http://en.wikipedia.org/wiki/DBm)  
2、 [ CATV dBm, dBmV, and dBµV Conversions - Tutorial - Maxim](http://pdfserv.maximintegrated.com/en/an/AN808.pdf)  
3、 [ Decibel - Wikipedia ](http://en.wikipedia.org/wiki/Decibel#Voltage)

