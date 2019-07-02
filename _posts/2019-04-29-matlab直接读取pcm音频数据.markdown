---
layout:  post
title:   matlab直接读取pcm音频数据
date:   2019-04-29 14:37:53
author:  "唐传林"
header-img: "img/post-bg-2015.jpg"
catalog:   true

---

    Fs=8000;
    fid = fopen('D:\test_8000Hz.pcm','r');
    x = fread(fid,inf,'int16');
    sound(x,Fs);
    

1、fopen():打开一个指定的文件  
例如：fid = fopen(‘D:\test_8000Hz.pcm’,‘r’);  
其中，"test_8000Hz.pcm"是要打开的pcm文件

2、fread()：读取指定的文件的内容  
例如：x= fread(fid, inf, ‘int16’);  
其中，fid是要读取的文件的标识符，inf表示要读取整个文件，

3、sound()：用来播放语音和音频  
例如：sound(x，8000)；  
其中，x是要播放的声音矢量， 8000是采样率。

