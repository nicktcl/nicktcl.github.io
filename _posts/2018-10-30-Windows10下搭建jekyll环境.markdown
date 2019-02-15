---
layout:  post
title:   Windows10下搭建jekyll环境
date:   2018-10-30 15:23:04
author:  "唐传林"
header-img: "img/post-bg-2015.jpg"
catalog:   false

---
#  Win10下安装jekyll搭建个人博客

##  前言

几年前看到网上大神自己搭建的个人博客网站，就想过搭建一个属于自己的个人博客网站，为此还专门去研究了建站所需技能，但是购买了域名和云虚拟主机后由于其它事情又一直放着不了了之了。前不久看到了可以利用
[ Github Pages ](http://pages.github.com/) 搭建自己的博客网站，就更想把一直放着的这件事做了。

[ Github Pages ](http://pages.github.com/)
是面向用户、组织和项目开放的公共静态页面搭建托管服务，站点可以被免费托管在 Github 上，我们可以选择使用 Github Pages 默认提供的域名 [
github.io ](http://jekyllcn.com/docs/github-pages/) 或者自定义域名来发布站点。Github Pages
支持自动利用 Jekyll 生成站点，也同样支持纯 HTML 文档，将你的 Jekyll 站 点托管在 Github Pages 上是一个不错的选择。

所以首先得在自己电脑上安装jekyll环境，这样就能在本地编辑预览自己的博客网站，弄好后直接上传到Github就可以发布自己的博客网站了。

网上查阅了很多关于jekyll
的安装教程、但是因为ruby的更新，ruby网站的域名改变、jekyll的更新，按照网络上的教程做的时候遇到了很多问题，解决后写下该博客记录下来以防时间长了忘记。

##  Jekyll 究竟是什么？

Jekyll
是使用Ruby语言开发的一个简单的博客形态静态站点生成工具，类似WordPress。但是和WordPress又有很大的不同，原因是jekyll只是一个生成静态网页的工具，不需要数据库支持。它有一个模版目录，其中包含原始文本格式的文档，通过一个转换器（如
[ Markdown ](http://daringfireball.net/projects/markdown/) ）和我们的 [ Liquid
](http://github.com/Shopify/liquid/wiki)
渲染器转化成一个完整的可发布的静态网站，你可以发布在任何服务器上。截至2017年，Jekyll是最受欢迎的静态网站生成器，主要是由于它被 [ GitHub
](http://en.wikipedia.org/wiki/GitHub)
采用。Jekyll的流行也因为它非常简单，只需要基础的web开发基础，我们可以使用它轻易的把文本转换为自定义的网站/博客。最关键的是jekyll可以免费部署在Github上，而且可以绑定自己的域名。

其它类似的静态(博客)网站生成工具还有 [ **Hugo** ](http://gohugo.io/) （基于go语言）、 [ **Hexo**
](http://gohugo.io/) （基于Node.js）、 [ **Octopress** ](http://octopress.org/)
（基于jekyll）、 [ **Pelican** ](http://getpelican.com/) （基于python）、 [
**Middleman** ](http://middlemanapp.com/) （基于Ruby）等很多很多。更多其它请见 [ **这里**
](http://en.wikipedia.org/wiki/Category:Blog_software) 。

##  为什么要使用 Markdown 和 Jekyll？

发布技术文章和感悟，文章的核心是内容，不是形式，我们不愿意花大量的时间在布局和排版上。而Markdown **「易读易写」** 的哲学和我的期望最相符。

Jekyll是一个静态站点生成器，可以根据Markdown文件自动生成静态的html文件。且Github Pages 支持托管jekyll。

因此我只要在本地编写符合Jekyll规范的Markdown文件，上传到Github上，Github Pages就会自动生成并托管整个网站。

这样做带来的好处是：

  * 专注。只需要关注Markdown内容的编写。无需考虑标签和样式，也不会干扰git的log。 
  * 历史版本。通过git历史可以看到自己思维的变迁。 
  * 免费，不限流量。 
  * 简单。你只要用自己喜欢的编辑器写文章就可以了，其他事情一概不用操心，都由Github 处理。 

##  电脑环境

Windows10教育版 64位 1803版本（操作系统版本：17134.285）

##  所需下载的软件

1、 [ rubyinstaller-2.3.3-x64.exe
](%E9%93%BE%E6%8E%A5%EF%BC%9Ahttp://pan.baidu.com/s/1z1VEB4nC4sp4TUvKYfe7pA)
（without DevKit）、密码：6a0x 、或是 [ 从官网下载 ](http://rubyinstaller.org/downloads/) 。

2、 [ DevKit-mingw64-64-4.7.2-20130224-1432-sfx.exe
](%E9%93%BE%E6%8E%A5%EF%BC%9Ahttp://pan.baidu.com/s/1oOHfs0VSNKjxJtxczsCk4Q)
、密码：t6el、或是 [ 从官网下载 ](http://rubyinstaller.org/downloads/) 。

今天是2018年10月25日，jekyll现为3.8.4版本，它所要求的ruby环境为2.3及以上，我们这里我们用rubyinstaller-2.3.3-x64.exe。

##  安装步骤

在安装jekyll过程中可能遇到的问题单独写了一篇博客整理了一下，请见博客“ [ Win10安装jekyll可能遇到的问题及解决办法
](http://blog.csdn.net/Tang_Chuanlin/article/details/83546278)
”。以下步骤在win7虚拟机下未出现什么错误，而在win10下出现了一些错误。

1、打开下载好的 “rubyinstaller-2.3.3-x64.exe ”
进行安装，安装到默认目录下，不要乱改路径，避免一些不必要的问题，比如我的路径是：“C:\Ruby23-x64”。 **
安装的时候注意勾选把ruby添加到路径PATH  ** ，如果不勾选也可以手动添加。  
![在这里插入图片描述](http://img-blog.csdnimg.cn/2018102920480136.jpg)  
2、在cmd命令行窗口下输入输入 ` “ruby -v” ` ，回车，可看到ruby的版本则说明ruby安装成功。  
![在这里插入图片描述](http://img-blog.csdnimg.cn/2018103015010998.png)  
3、打开下载好的 “DevKit-mingw64-64-4.7.2-20130224-1432-sfx.exe”
解压到自己指定的目录，比如我的路径是：“D:\DevKit”。  
![在这里插入图片描述](http://img-blog.csdnimg.cn/20181030101748231.jpg)  
4、在cmd命令行窗口下输入 ` D: ` ，回车，再输入 ` cd DevKit ` ，回车。  
![在这里插入图片描述](http://img-blog.csdnimg.cn/20181030104450618.jpg)  
5、在cmd命令行窗口下输入 ` ruby dk.rb init ` ，回车。  
![在这里插入图片描述](http://img-blog.csdnimg.cn/20181030104740123.jpg)  
6、记事本打开 “D:\DevKit” 目录下的config.yml 文件，最后一行改为Ruby的安装目录，比如我的是“C:\Ruby23-x64”。  
![在这里插入图片描述](http://img-blog.csdnimg.cn/20181030104908749.jpg)  
7、在cmd命令行窗口下输入 ` ruby dk.rb install ` ，回车。  
![在这里插入图片描述](http://img-blog.csdnimg.cn/20181030104809228.jpg)  
8、在cmd命令行窗口下输入 ` gem -v ` ，回车，查看gem是否正常安装。  
![在这里插入图片描述](http://img-blog.csdnimg.cn/20181030143824357.jpg)  
9、在cmd命令行窗口下输入 ` gem install jekyll ` ，回车，  
![在这里插入图片描述](http://img-blog.csdnimg.cn/20181030141451765.gif)  
10、在cmd命令行窗口下输入 ` gem install bundle ` ，回车。  
![在这里插入图片描述](http://img-blog.csdnimg.cn/20181030142308774.gif)  
11、在cmd命令行窗口下输入 ` jekyll --version ` ，回车，可看到jekyll的版本则说明jekyll安装成功。  
![在这里插入图片描述](http://img-blog.csdnimg.cn/20181030143904356.jpg)  
12、在cmd命令行窗口下输入 ` cd .. ` ，回车，回到D盘根目录。  
![在这里插入图片描述](http://img-blog.csdnimg.cn/20181030144437195.jpg)  
13、在cmd命令行窗口下输入 ` jekyll new myblog ` ，回车，如果没有任何报错，会在当前目录下回生产一个 myblog
文件夹，即新建一个简单的博客静态站点目录。该步骤需要连接网络下载一些文件，所以执行时会有点慢，需要耐心等待。  
![在这里插入图片描述](http://img-blog.csdnimg.cn/20181030145028961.gif)  
14、在cmd命令行窗口下输入 ` cd myblog ` ，回车，进入刚刚新建好的博客静态站点目录。  
![在这里插入图片描述](http://img-blog.csdnimg.cn/20181030145325549.jpg)  
15、在cmd命令行窗口下输入 ` jekyll serve ` ，回车，运行服务器。  
![在这里插入图片描述](http://img-blog.csdnimg.cn/20181030145622281.gif)  
16、在浏览器中输入 [ http://127.0.0.1:4000/ ](http://127.0.0.1:4000/) 访问测试。  
![在这里插入图片描述](http://img-blog.csdnimg.cn/20181030145645852.jpg)

##  参考资料

1、 [ Jekyll on Windows | Jekyll • Simple, blog-aware, static sites
](http://jekyllrb.com/docs/installation/windows/)  
2、 [ Windows下Jekyll安装 - 简书 ](http://www.jianshu.com/p/310d796cf5f3)  
3、 [ Win10环境下Jekyll搭建个人博客
](http://muxinsepith.github.io/2017/03/Win10%E7%8E%AF%E5%A2%83%E4%B8%8BJekyll%E6%90%AD%E5%BB%BA%E4%B8%AA%E4%BA%BA%E5%8D%9A%E5%AE%A2/)  
4、 [ Windows 运行Jekyll - Jekyll • 简单静态博客网站生成器
](http://jekyllcn.com/docs/windows/)  
5、 [ 基于Docker搭建本地Jykell环境 ](http://archerwq.github.io/2017/09/21/setup-jekyll-locally-with-docker/)  
6、 [ 在windows下安装jekyll（一个很好地博客系统） - 简书
](http://www.jianshu.com/p/88e3474cef72)  
7、 [ RubyGems 镜像 - Ruby China ](http://gems.ruby-china.com/)  
8、 [ 安装jekyll出错 Failed to build gem native extension. - CSDN博客
](http://blog.csdn.net/kafeidev/article/details/24490711)  
9、 [ 48 个你需要知道的 Jekyll 使用技巧 - 前端 - 掘金
](http://juejin.im/entry/58eb2b9f2f301e00624d8027)  
10、 [ gem install bundle 安装失败 - qianggezhishen的专栏 - CSDN博客
](http://blog.csdn.net/qianggezhishen/article/details/50250253)  
11、 [ [ruby]rubyGem出现ERROR: Could not find a valid gem时的处理方法 - 李明夕 - 博客园
](http://blog.csdn.net/qianggezhishen/article/details/50250253)  
12、 [ ERROR: Could not find a valid gem ‘jekyll’ (>= 0), here is why: · Issue
#34 · juthilo/run-jekyll-on-windows ](http://github.com/juthilo/run-jekyll-on-windows/issues/34)  
13、 [ Could not find a valid gem ‘jekyll’ 安装jekyll问题解决 - 阳光e站------zSunsoft
Team - ITeye博客 ](http://sunxboy.iteye.com/blog/2217811)  
14、 [ 升级Jekyll 3.0 - itmyhome的专栏 - CSDN博客
](http://blog.csdn.net/itmyhome1990/article/details/50443826)  
15、 [ (ruby)jekyll serve启动报错,error:permission denied -bind2_其他语言_编程问答
](http://www.codes51.com/itwd/4509912.html)  
16、 [ Using Jekyll as a static site generator with GitHub Pages - User
Documentation ](http://help.github.com/articles/using-jekyll-as-a-static-site-generator-with-github-pages/)  
17、 [ [ruby]rubyGem出现ERROR: Could not find a valid gem时的处理方法 - 李明夕 - 博客园
](http://www.cnblogs.com/limingxi/p/4292463.html)  
18、 [ ERROR: Could not find a valid gem ‘jekyll’ (>= 0), here is why: · Issue
#34 · juthilo/run-jekyll-on-windows ](http://github.com/juthilo/run-jekyll-on-windows/issues/34)  
19、 [ Could not find a valid gem ‘jekyll’ 安装jekyll问题解决 - 阳光e站------zSunsoft
Team - ITeye博客 ](http://sunxboy.iteye.com/blog/2217811)  
20、 [ Ruby Gem命令详解 - 简书 ](http://www.jianshu.com/p/728184da1699)  
21、 [ Setting up your GitHub Pages site locally with Jekyll - User
Documentation ](http://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll/)  
22、 [ Bundle、Gem、Gemfile关系 - 简书 ](http://www.jianshu.com/p/32fcdeb5bbec)  
23、 [ Windows安装Jekll - 不折腾会死 - SegmentFault 思否
](http://segmentfault.com/a/1190000010195733)  
24、 [ MSYS2 homepage ](http://www.msys2.org/)  
25、 [ Jekyll搭建写作环境问题集锦 - 简书 ](http://www.jianshu.com/p/12e7e1f8007e)  
26、 [ jekyll-paginate使用失败 - Monkey_D_Luffy的博客 - CSDN博客
](http://blog.csdn.net/qq_26508409/article/details/77927593)  
27、 [ jekyll安装过程中可能会遇到的一些错误及解决办法 - 浪潮之巅的专栏 - CSDN博客
](http://blog.csdn.net/wyc12306/article/details/51504885?utm_source=blogxgwz1)

