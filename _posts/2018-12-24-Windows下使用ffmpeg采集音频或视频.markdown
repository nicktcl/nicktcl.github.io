---
title: Windows下使用ffmpeg采集音频或视频
date: 2018-12-24 16:08:25

---
1、一开始在命令行下使用ffmpeg时执行“ffmpeg -list_devices true -f dshow -i dummy
”使用dshow来枚举当前系统上存在的音视频采集设备时，发现中文乱码，后来在老师帮助下，在命令行下执行命令“ chcp 65001”
将windows命令行窗口的编码改为了utf-8编码，就解决了ffmpeg的中文乱码问题，

2、ffmpeg查看设备的命令：  
ffmpeg -list_devices true -f dshow -i dummy

3、录音为文件：  
ffmpeg -f dshow -i audio=“麦克风阵列 (11- USB PnP Audio Device)” out.mp3

4、实时采集音频并播放：  
ffplay -f dshow -i audio=“麦克风阵列 (11- USB PnP Audio Device)”

5、实时采集音频并播放并绘制实时音频的左右声道的波形：  
ffplay -showmode 1 -f dshow -i audio=“麦克风阵列 (11- USB PnP Audio Device)”

6、采集摄像头实时视频并实时显示：  
ffplay -showmode 0 -f dshow -i video=“Integrated Webcam”

参考资料：  
1、 [ 运行bat时隐藏cmd窗口_百度知道 ](https://zhidao.baidu.com/question/269741610.html)  
2、 [ Windows下如何一次运行多个命令 - skykingf的专栏 - CSDN博客
](https://blog.csdn.net/skykingf/article/details/11992351)  
3、 [ Windows 设置CMD命令行编码 - Melon的博客 - CSDN博客
](https://blog.csdn.net/wyl530274554/article/details/74642697)  
4、 [ Windows7环境下命令行一次运行多条命令 - automation13的博客 - CSDN博客
](https://blog.csdn.net/automation13/article/details/76285401)

