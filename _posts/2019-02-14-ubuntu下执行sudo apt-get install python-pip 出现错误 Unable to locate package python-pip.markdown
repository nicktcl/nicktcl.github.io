---
layout:		post
title: 		ubuntu下执行sudo apt-get install python-pip 出现错误 Unable to locate package python-pip
date: 		2019-02-14 15:07:06
author:		"唐传林"
header-img: "img/post-bg-2015.jpg"
catalog:	 true
categories:
- python
tags:
- python
- pip
- 错误

---
ubuntu13.04下执行sudo apt-get install python-pip 出现以下错误：  
E: Unable to locate package python-pip

解决办法：  
摘自 [ https://askubuntu.com/questions/672808/sudo-apt-get-install-python-pip-
is-failing ](https://askubuntu.com/questions/672808/sudo-apt-get-install-
python-pip-is-failing)

python-pip is in the universe repositories, therefore use the steps below:

    
    
    sudo apt-get install software-properties-common
    sudo apt-add-repository universe
    sudo apt-get update
    sudo apt-get install python-pip
    

