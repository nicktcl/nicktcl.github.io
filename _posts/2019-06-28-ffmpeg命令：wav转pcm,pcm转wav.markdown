---
layout:  post
title:   ffmpeg命令：wav转pcm,pcm转wav
date:   2019-06-28 16:23:15
author:  "唐传林"
header-img: "img/post-bg-2015.jpg"
catalog:   true
categories:
- 音频                                                                    
tags:
- ffmpeg
- 音频
- wav
- pcm

---
1、ffmpeg命令：wav转pcm:

    
    
    ffmpeg -i input.wav -f s16be -ar 8000 -ac 1 -acodec pcm_s16be output.pcm
    

2、ffmpeg命令：pcm转wav:

    
    
    ffmpeg -i input.pcm -f s16be -ar 8000 -ac 2 -acodec pcm_s16be  output.wav
    

