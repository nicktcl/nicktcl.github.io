---
layout:  post
title:   Linux系统下ALSA音频编程入门
date:   2019-02-08 15:28:27
author:  "唐传林"
header-img: "img/post-bg-2015.jpg"
catalog:   false
categories:
- Linux
tags:
- alsa音频
- alsa编程
- linux
- alsa驱动

---
###  1、Linux 系统下三大主流声卡驱动程序集

Linux 有三个主流的声卡驱动程序集：OSS/Lite（也称为OSS/Free）、OSS/Full （商业软件）、ALSA（自由软件）。

  * OSS/Lite 是现在linux内核中自带的声卡驱动程序集，最初由 Hannu Savolainen 开发。后来 Hannu 跑去开发 Open Sound System（也就是上面所说的OSS/Full）。 由于 Hannu 的“逃跑”，RH 资助 Alan Cox 增强 Hannu 开发的驱动程序，并使它们 完全模块化。现在 Alan Cox 是内核声卡驱程集的维护人。OSS/Lite 从kernel-2.0开始并入内核，现在大家使用的声卡驱程默认都是OSS/Lite中的。 

  * OSS/Full 是由 4Front Technologies 开发并销售的商业软件。它可以驱动很多 声卡并且可以用在很多 UNIX 系统中。OSS/Full 完全兼容以前基于 OSS／Lite 开发 的应用程序。作为一个商业软件，你虽然可以使用它，但是你得不到它的源代码，并且你必须为此而付钱。 

  * ALSA 是linux内核的下一代标准声卡驱动集。 ALSA表示高级Linux声音体系结构(Advanced Linux Sound Architecture)。它由一系列内核驱动，应用程序编译接口(API)以及支持Linux下声音的实用程序组成。开始时 Jaroslav Kysela 等人为 Gravis UltraSound Card 开发驱动程序，后来该计划改名为 ALSA「先进的linux音频 体系」，因为他们认为 ALSA 比原来内核中的 OSS/Lite 驱动程序集更优秀，完全可以 代替 OSS/Lite。他们是对的，ALSA 支持的声卡比 OSS/Lite 多，完全兼容以前基于OSS 开发的程序，SMP（多处理器） 与线程安全设计，并且从 2.5 分支的内核开始，ALSA 的驱动程序集开始并入内核，大家可以在今年的 2.6 版本的内核中看到使用它们。 

###  2、为什么使用 ALSA 开发音频程序

首先，ALSA 是 linux 以后声卡驱动程序的标准，OSS/Lite 迟早会从内核中去除。 开发基于 ALSA 的音频程序可以保证以后的兼容。

其次，我们简单比较一下开发基于 OSS 与 ALSA 的方法。  
OSS 向应用程序提供了一系列的系统接口。开发基于 OSS 的应用程序需要使用open,close,ioctl,read,write
等低级系统调用来完成音频设备的控制、音频流的输入输出。  
而 ALSA 则为应用程序开发人员提供了一个优秀的音频库。利用该音频库，开发人员可以方便快捷地开发出自己的应用程序，细节则留给音频库内部处理。当然 ALSA
也提供了类似于 OSS 的系统接口，不过 ALSA 的开发者建议应用程序开发者使用音频库而不是驱动程序API。

ALSA由许多声卡的声卡驱动程序组成，同时它也提供一个称为libasound的API库。应用程序开发者应该使用libasound而不是内核中的
ALSA接口。因为libasound提供最高级并且编程方便的编程接口。并且提供一个设备逻辑命名功能，这样开发者甚至不需要知道类似设备文件这样的低层接口。相反，OSS/Free驱动是在内核系统调用级上编程，它要求开发者提供设备文件名并且利用ioctrl来实现相应的功能。

为了向后兼容，ALSA提供内核模块来模拟OSS，这样之前的许多在OSS基础上开发的应用程序不需要任何改动就可以在ALSA上运行。另外，libaoss库也可以模拟OSS，而它不需要内核模块。  
ALSA包含插件功能，使用插件可以扩展新的声卡驱动，包括完全用软件实现的虚拟声卡。ALSA提供一系列基于命令行的工具集，比如混音器(mixer)，音频文件播放器(aplay)，以及控制特定声卡特定属性的工具。

###  3、从何开始呢

第一步当然是安装 ALSA 驱动程序与音频库。

    
    
     sudo apt-get install libasound2-dev
    

当前 ALSA 有两个分支，一个是以前的0.5版本，一个是现在的0.9。ALSA的开发者 已经不支持0.5版本了，所以我们要使用0.9。  
大家可以在 ALSA 的主页 [ www.alsa-project.org ](http://www.alsa-project.org) 上下载安装。  
这个页面上的信息对大家安装很有用： [ http://www.alsa-project.org/main/index.php/Documentation
](http://www.alsa-project.org/main/index.php/Documentation) ，建议先浏览一下。

第二步是参考文档与例子。  
在 ALSA 的文档页面上有两篇为应用程序开发者提供的文章：  
ALSA 0.9.0 HOWTO [ [ http://www.suse.de/~mana/alsa090_howto.html
](http://www.suse.de/~mana/alsa090_howto.html) ]  
当然，还有音频库API的在线参考： [ http://www.alsa-project.org/alsa-doc/alsa-lib ](http://www
.alsa-project.org/alsa-doc/alsa-lib)  
音频库API中各个函数的使用说明： [ http://www.alsa-project.org/alsa-doc/alsa-lib/modules.html
](http://www.alsa-project.org/alsa-doc/alsa-lib/modules.html)

###  4、ALSA体系结构

ALSA API可以分解成以下几个主要的接口：

  * 控制接口：提供管理声卡注册和请求可用设备的通用功能 
  * PCM接口：管理数字音频回放(playback)和录音(capture)的接口。后续重点放在这个接口上，因为它是开发数字音频程序最常用到的接口。 
  * Raw MIDI接口:支持MIDI(Musical Instrument Digital Interface),标准的电子乐器。这些API提供对声卡上MIDI总线的访问。这个原始接口基于MIDI事件工作，由程序员负责管理协议以及时间处理。 
  * 定时器(Timer)接口：为同步音频事件提供对声卡上时间处理硬件的访问。 
  * 时序器(Sequencer)接口 
  * 混音器(Mixer)接口 

###  5、设备命名

API库使用逻辑设备名而不是设备文件。设备名字可以是真实的硬件名字也可以是插件名字。硬件名字使用hw:i,j这样的格式。其中i是卡号，j是这块声卡上的设备号。

第一个声音设备是hw:0,0.这个别名默认引用第一块声音设备并且在本文示例中一真会被用到。

插件使用另外的唯一名字，比如 plughw:,表示一个插件，这个插件不提供对硬件设备的访问，而是提供像采样率转换这样的软件特性，硬件本身并不支持这样的特性。

###  6、声音缓存和数据传输

每个声卡都有一个硬件缓存区来保存记录下来的样本。当缓存区足够满时，声卡将产生一个中断。内核声卡驱动然后使用直接内存(DMA)访问通道将样本传送到内存中的应用程序缓存区。类似地，对于回放，任何应用程序使用DMA将自己的缓存区数据传送到声卡的硬件缓存区中。

这样硬件缓存区是环缓存。也就是说当数据到达缓存区末尾时将重新回到缓存区的起始位置。ALSA维护一个指针来指向硬件缓存以及应用程序缓存区中数据操作的当前位置。从内核外部看，我们只对应用程序的缓存区感兴趣，所以本文只讨论应用程序缓存区。

应用程序缓存区的大小可以通过ALSA库函数调用来控制。缓存区可以很大，一次传输操作可能会导致不可接受的延迟，我们把它称为延时(latency)。为了解决这个问题，ALSA将缓存区拆分成一系列周期(period)(OSS/Free中叫片断fragments).ALSA以period为单元来传送数据。

一个周期(period)存储一些帧(frames)。每一帧包含时间上一个点所抓取的样本。对于立体声设备，一个帧会包含两个信道上的样本。分解过程：一个缓存区分解成周期，然后是帧，然后是样本。左右信道信息被交替地存储在一个帧内。这称为交错
(interleaved)模式。在非交错模式中，一个信道的所有样本数据存储在另外一个信道的数据之后。

###  7、Over and Under Run

当一个声卡活动时，数据总是连续地在硬件缓存区和应用程序缓存区间传输。但是也有例外。在录音例子中，如果应用程序读取数据不够快，循环缓存区将会被新的数据覆盖。这种数据的丢失被称为over
run.在回放例子中如果应用程序写入数据到缓存区中的速度不够快，缓存区将会"饿死"。这样的错误被称为"under
run"。在ALSA文档中，有时将这两种情形统称为"XRUN"。适当地设计应用程序可以最小化XRUN并且可以从中恢复过来。

####  参考资料

1、 [ 【Linux&音频】Alsa音频编程【精华】 - 小田的专栏 - CSDN博客
](https://blog.csdn.net/tianshuai1111/article/details/8191711)

