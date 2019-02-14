---
layout:		post
title: 		Matlab读取Excel各个子表的数据进行拟合
date: 		2018-08-18 16:26:48
author:		"唐传林"
header-img: "img/post-bg-2015.jpg"
catalog:	 true

---
#  Matlab读取Excel各个子表的数据进行拟合

#  前言

现有一个Excel文件，里面存有很多个子表，每个子表格式一样，但是数据不一样，现要对每个子表中的好多行数据进行多项式拟合，并将拟合好的结果保存回Excel中各个子表的指定位置。这本来是可以通过人工将所要拟合的数据放到matlab下一次一次拟合再将结果人工保存到Excel中，但是这样太耗时，所以现在想通过Matlab自动读取Excel数据，拟合完成再将结果自动写入Excel中。

#  电脑环境：

1、Windows10教育版 64位 1803版本（操作系统版本：17134.165）  
2、Matlab R2014a（8.3.0.532）64位

#  Matlab 代码实现

    
```matlab    
    clc;clear;
    ReadRange = '';
    y=[-65 -64 -63 -62 -61 -60 -59 -58 -57 -56 -55 -54 -53 -52 -51 -50 -49 -48 -47 -46 -45 -44 -43 -42 -41 -40 -39 -38 -37 -36 -35 -34 -33 -32 -31 -30];
    filename = 'SignalStrengData_7to13.xlsx';%表格文件名
    [status,sheets,xlFormat] = xlsfinfo(filename);%读取excel文件的信息，其中sheets为元胞类型，为excel中每张子表的名字
    for sheet = 1:7%excel中的子表序号循环变量
        folder = sheets{sheet};%当前子表的文件夹的名字,这里必须用{}来提取cell中的数据，不能用[]来提取
    %     fprintf(folder)%testcode
        mkdir (folder) %新建当前子表的文件夹，用于保存图片
        for i=16:27%表格中的行循环次数
            ReadRange = ['D',num2str(i), ':AM',num2str(i)];
            fprintf('正在拟合子表(%s)中%s单元格的数据...', folder, ReadRange)%testcode
            x = xlsread(filename, sheet, ReadRange);%读取指定的单元格数据
            if isempty(x)%判断是否从Excel表格中读取到数据，若读取到的数据为空，则跳出该次循环
                break;
            end
            xishu=polyfit(x,y,3);%三次多项式插值拟合得到系数
            xishu2 = roundn(xishu, -2);%将系数只保留2位小数
            result_xishu = sprintf('%.2f,%.2f,%.2f,%.2f', xishu2);%将系数格式化输出
            fprintf ('\t\t所得系数为：')%打印系数查看一下
            fprintf(result_xishu)
            z=polyval(xishu2,x);%z为用拟合函数根据自变量算出来的值
            h = figure(i);
            plot(x,y,'r*',x,z,'b-');%绘图：拟合曲线和原始数据
            set(h,'visible','off');
            pictureName = sprintf('%s中D%d_AM%d的数据拟合结果', folder, i, i);%构建保存图片的文件名,注意：文件名中不能有冒号，所以此外将冒号改为了下划线
    %         fprintf('\n')%testcode
    %         fprintf(pictureName);%testcode
            fprintf('\t正在保存图片到文件夹...')
            filepath=pwd;           %保存当前工作目录                 
            cd (folder) %把当前工作目录切换到指定文件夹
            saveas(h, pictureName,'jpg');%保存绘图到指定文件夹
            cd (filepath)
            fprintf('\t已保存图片到(%s)文件夹中.',folder)
            fprintf('\t正在写入数据到指定单元格...')
            WriteRange = ['C',num2str(i)];%要写入的单元格
            xlswrite(filename, {result_xishu}, sheet, WriteRange);%将数据写入单元格
            fprintf('\t\t\t已将所得系数写入子表(%s)中%s单元格。\n', folder, WriteRange)
        end
        fprintf('\n子表(%s)  处理完成。\n\n',folder)
    end
```

#  运行结果

![这里写图片描述](http://img-blog.csdn.net/20180818155807812?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

#  生成拟合好的曲线的图片

![这里写图片描述](http://img-blog.csdn.net/20180818160140771?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
![这里写图片描述](http://img-blog.csdn.net/20180818160148775?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
![这里写图片描述](http://img-blog.csdn.net/20180818160156890?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L1RhbmdfQ2h1YW5saW4=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

#  总结

在其中遇到一些小问题，通过查资料都慢慢解决了，比如之前都没接触过matlab中的cell数据类型。需要注意的地方我都在代码中的注释中写好了。  
因为考虑到可以在录数据到Excel中时，可能存在输入错误的情况，然后导致数据错误，以至于最后拟合出来的结果有问题，表现出来就是本该是平滑的曲线，结果有一个点两个点与其他点相差很大。为了解决这个问题，所以就将拟合得到的结果绘制成曲线图并进行保存，然后通过人为的方法来看各个曲线图是否有错误数据。

#  参考资料

1、 [ 曲线拟合 - 维基百科，自由的百科全书
](https://zh.wikipedia.org/wiki/%E6%9B%B2%E7%B7%9A%E6%93%AC%E5%90%88)  
2、 [ 插值 - 维基百科，自由的百科全书 ](https://zh.wikipedia.org/zh/%E6%8F%92%E5%80%BC)  
3、 [ matlab里面如何保留小数特定位数 - CSDN博客
](https://blog.csdn.net/xiakexiaohu/article/details/53760946)  
4、 [ MATLAB如何将数字数组转换成字符串？_百度知道 ](https://zhidao.baidu.com/question/149524049)  
5、 [ Matlab实现数字转换为字符串 - CSDN博客
](https://blog.csdn.net/FX677588/article/details/53257607)  
6、 [ matlab将字符/cell写入excel_FChChou_新浪博客
](http://blog.sina.com.cn/s/blog_994de1530101c57s.html)  
7、 [ 如何用matlab将一组字符串写入excel的一个格? – MATLAB中文论坛
](http://www.ilovematlab.cn/thread-299989-1-1.html)  
8、 [ Matlab连接字符串的方法 _无物_ 新浪博客
](http://blog.sina.com.cn/s/blog_7cc248520100svxr.html)  
9、 [ 用excel画拟合函数，导出公式_百度知道 ](https://zhidao.baidu.com/question/125487254)  
10、 [ excel相邻两列的数据自动求差值_百度知道
](https://zhidao.baidu.com/question/490050581813645812.html)  
11、 [ Excel 两个工作薄切换的快捷键是什么？-Excel基础应用-ExcelHome技术论坛 -
](http://club.excelhome.net/thread-816190-1-1.html)  
12、 [ Excel2013如何将某数据范围的单元格以某种颜色突出显示_excel2013_office之家
](http://www.icanzc.com/excel/4322.html)  
13、 [ Matlab实现保存图片到指定文件夹 - CSDN博客
](https://blog.csdn.net/songyunli1111/article/details/79622374)  
14、 [ matlab 保存figure中的图像 - CSDN博客
](https://blog.csdn.net/zhaoluruoyan89/article/details/78491115)  
15、 [ matlab批量保存图像至指定文件夹（revised） mkdir cd 等 - CSDN博客
](https://blog.csdn.net/flyingworm_eley/article/details/6644975)  
16、 [ matlab绘完图后可以不弹出figure而直接保存吗？ – MATLAB中文论坛
](http://www.ilovematlab.cn/thread-202089-1-1.html)  
17、 [ MATLAB中cell函数用法 _宝言_ 新浪博客
](http://blog.sina.com.cn/s/blog_797ba6c90100s80v.html)  
18、 [ matlab的cell数组 _玉琪星兆_ 新浪博客
](http://blog.sina.com.cn/s/blog_5ecfd9d90100i6ld.html)  
19、 [ matlab 用循环画图并保存 如何不重叠 – MATLAB中文论坛
](http://www.ilovematlab.cn/thread-273579-1-1.html)

