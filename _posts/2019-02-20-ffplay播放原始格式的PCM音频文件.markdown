---
layout:  post
title:   ffplay播放原始格式的PCM音频文件
date:   2019-02-20 16:29:41
author:  "唐传林"
header-img: "img/post-bg-2015.jpg"
catalog:   false

---
播放16kHz 单声道 16bit的xxx.pcm的PCM文件为例：

    
    
    ffplay -ar 16000 -channels 1 -f s16le -i xxx.pcm
    

