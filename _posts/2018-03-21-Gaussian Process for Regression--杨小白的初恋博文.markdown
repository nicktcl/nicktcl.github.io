---
title: Gaussian Process for Regression--杨小白的初恋博文
date: 2018-03-21 20:50:06

---
#  Gaussian Process for Regression

对于服从高斯分布的数据，如何根据前面输入输出训练得到一个预测型从而送入一个输入量得到的那个值尽可能的逼近期望值，入下图所示根据前面六点输入输出求解x=0.2时候的对应值：  
![这里写图片描述](//img-
blog.csdn.net/20180321202346699?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1lhbmdNaW5nbGlhbmc2NjY=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

  * **1、符号介绍**
  * **2、公式推导**
  * **3、核心代码**
  * **4、模型结果**
  * **5、总结**

* * *

##  1、符号介绍

x已知范围内的样本值  
x’与x不同的样本值，或预测值  
回归函数f(x)  
l 为计算协方差函数k(x,x’) 的参数  
s  i  g  m  a  f  2  s  i  g  m  a  f  2  或sigmaf为回归函数方差或样本最大协方差,  s  i  g  m
a  n  2  s  i  g  m  a  n  2  或sigman为噪声方差  
K样本协方差阵，K*预测值和样本的协方差阵,K**预测值方差  
P  (  y  ∗  /  y  )  P  (  y  ∗  /  y  )  条件概率

##  2、公式推导

![这里写图片描述](//img-
blog.csdn.net/20180321202122727?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1lhbmdNaW5nbGlhbmc2NjY=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
![这里写图片描述](//img-
blog.csdn.net/20180321202143474?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1lhbmdNaW5nbGlhbmc2NjY=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

###  3、核心代码

MATLAB仿真代码：

    
    
     %一：计算样本的协方差阵
    for i=1:6;
        x1=x(i);
        for j=1:6;
            x2=x(j);
            covar(i,j)= sigmaf^2 * exp(-(x1-x2)^2/(2*l^2));
    if x1==x2;
        covar(i,j) = covar(i,j)+sigman^2;    
    end
        end
    end
    
    %二：预测值的方差KK
    KK=sigmaf^2 * exp(-(X-X)^2/(2*l^2))+sigman^2;   %预测点的方差
    fprintf('KK=\n')
    disp(KK()); 
    %三：样本点与预测点的协方差矩阵k
    k=zeros(1,6);  %初始化
     for i=1:6;
         x1=x(i);
         k(1,i)= sigmaf^2 * exp(-(x1-X)^2/(2*l^2));
     end
     fprintf('k=\n')
     disp(k); 
     %四：求解均值u，并画出图像
    ylabel('竖坐标y') 
     u=k*(covar^-1)*y;  %均值u的计算公式，作为预测值
     fprintf('u=\n')
     disp(u);
     %五：求解var(y)
     var=KK-k*(covar^-1)*k';  %方差var的计算公式

###  4、模型仿真结果

程序运行结果：  
![这里写图片描述](//img-
blog.csdn.net/20180321203820738?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1lhbmdNaW5nbGlhbmc2NjY=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
预测模型求值结果：  
![这里写图片描述](//img-
blog.csdn.net/20180321203833459?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1lhbmdNaW5nbGlhbmc2NjY=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
高斯拟合曲线结果：  
![这里写图片描述](//img-
blog.csdn.net/20180321203847159?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1lhbmdNaW5nbGlhbmc2NjY=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

###  总结

对于预测类型问题主要是求解预测模型模型中的参量，得到回归性函数。模型中的参量求解越精准，其模型就越适应于研究的问题，所以说模型都是万能的也都不是万能的。

