---
layout:		post
title: 		jekyll中markdown要注意的问题
date: 		2019-02-14 16:20:56
author:		"唐传林"
header-img: 	"img/post-bg-2015.jpg"
catalog:	 true
tags:
- jekyll
- markdown
---




#### 1、jekyll中post的markdown文件名格式如下：
2019-02-13-Beautiful Soup 4.2.0 官方中文文档.markdown

#### 2、jekyll中post的markdown文件头格式如下：

```markdown

---
layout:		post
title: 		错误 Unable to locate package python-pip
date: 		2019-02-14 15:10:56
author:		"唐传林"
header-img: 	"img/post-bg-2015.jpg"
catalog:	 true
tags:
- python
---

```
##### 注意：
tags等关键字后面的冒号必须为英文冒号，为中文冒号jekyll编译生成的页面中该篇文章会没有文章标题、作者显示不对、日期不对等问题。
tags下的标签不要添加空格或table。
title下的字段不能带有英文或者中文冒号，title字段中带有中文冒号jekyll编译生成的页面中该篇文章会没有文章标题、作者显示不对、日期不对等问题。
title中可带有单引号。

#### 3、jekyll中post的markdown文件需要使用utf-8无BOM的编码，不能使用utf-8 BOM的编码。
csdn编辑器导出的markdown文件默认为utf-8 BOM的编码，需要用notepad++进行转换一下。爬虫保存的markdown文件默认为utf-8无BOM的编码，不用进行转换。

#### 4、爬虫保存的markdown文件中的图片链接有些会换行，需要人工检查。

#### 5、图片链接需要改为http协议。
爬虫保存的markdown文件中的图片链接有些为https协议的，jekyl生成的页面中这种图片显示会不正常，所以图片链接需要改为http协议，使用notepad++批量替换https为http即可。






