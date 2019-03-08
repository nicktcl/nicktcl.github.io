---
layout:  post
title:   Linux使用ffplay实时采集音频并实时播放
date:   2019-02-08 17:18:12
author:  "唐传林"
header-img: "img/post-bg-2015.jpg"
catalog:   true

---

    ffplay -f alsa -ac 2 -i hw:1,0 -ar 44100
    

-f 设定输出格式   
-i 设定输入流（hw:1,0为外接的usb音频采集卡设备，hw:1,0的1指的是第一个外部设备，即usb音频采集卡）；   
-ar 设定采样率（采样率一般选择44100，22050，11025这三种）； 

