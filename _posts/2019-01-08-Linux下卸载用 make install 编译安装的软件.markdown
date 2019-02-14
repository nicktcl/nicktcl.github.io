---
layout:		post
title: 		Linux下卸载用 make install 编译安装的软件
date: 		2019-01-08 14:15:40
author:		"唐传林"
header-img: "img/post-bg-2015.jpg"
catalog:	 true

---
###  前言

总结一下，在LINUX如果用源码包安装软件包后怎么删除。

###  步骤

第一，看大家安装软件的时候有没有使用–prefix这个命令，如果有那就把你指定的文件给删除了就行了，  
第二，如果没有用这个信念指定就麻烦一点了，那就进入到软件解压后的目录，执行sudo make uninstall看能否成功，  
第三，如果不行，那就进入用 editor 查看 makefile 文件 看看里面卸载的命令是什么如果该源码包没有提供此类方法删除 就只能手动删除  
第四，手动删除最无奈的办法能不能搞干净也只能看运气了，使用whereis xxx 找到软件安装目录，rm -rf 把这些目录都删除，应该能删除干净，

###  例子如下：

    
```    
          whereis python
          python: /usr/bin/python2.6-config /usr/bin/python2.6 /usr/bin/python /usr/lib/python2.6 /usr/lib64/python2.6 /usr/local/bin/python3.3m-config /usr/local/bin/python3.3m /usr/local/bin/python3.3 /usr/local/bin/python3.3-config /usr/local/lib/python3.3 /usr/include/python2.6 /usr/share/man/man1/python.1.gz
          rm -rf /usr/bin/python2.6-config
          rm -rf /usr/bin/python2.6
          rm -rf /usr/bin/python
          rm -rf /usr/lib/python2.6
          rm -rf /usr/lib64/python2.6
```    

