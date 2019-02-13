---
title: Gussian Process for Regression（2）--杨小白初恋博客第二春
date: 2018-03-21 22:18:04

---
#  Gussian Process for Regression（2）

在第一篇文章中展示了高斯回归预测，大致流程以及核心代码，在总结中也说道了预测模型归根到底还是模型参数的求解，这一篇就简单说说高斯回归模型中的参数是如何求解出来的。  
《目录》

#  极大似然函数由来

![这里写图片描述](//img-
blog.csdn.net/20180321212254333?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1lhbmdNaW5nbGlhbmc2NjY=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
拉普拉斯近似(the Laplace approximation)  
因为后验概率不再是高斯分布，因此要引入一些基于分析计算和数值抽样的近似方法其目的是为了找到一个高斯分布来近似一系列连续值的概率密度。  
拉普拉斯近似的推导  
单一连续变量：

###  1.寻找众数

假定分布  p  (  x  )  =  （  1  /  z  ）  ∗  f  (  z  )  p  (  x  )  =  （  1  /  z
）  ∗  f  (  z  )  
其中Z=∫f(z)dz是归一化系数。Z的值是未知的。在拉普拉斯方法中，我们就是要寻找高斯近似q(z)，他的中心位于p(z)众数的位置，所以就去寻找众数,即寻找一个点使p′(z)=0

###  2.泰勒展开 并取指数

高斯分布的对数是变量的二次函数。所以考虑lnf(z)以众数 为中心的泰勒展开:  
![这里写图片描述](//img-
blog.csdn.net/20180321213749217?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1lhbmdNaW5nbGlhbmc2NjY=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
注意：这里一阶导数为0,z0 为其局部最大值点故不存在一阶项。  
两边同时取指数  
![这里写图片描述](//img-
blog.csdn.net/20180321213851734?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1lhbmdNaW5nbGlhbmc2NjY=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

###  3.归一化

使用归一化的高斯分布的标准形式，得到归一化的概率分布q(z):  
![这里写图片描述](//img-
blog.csdn.net/20180321213936804?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1lhbmdNaW5nbGlhbmc2NjY=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
高斯近似只在精度A>0时有良好的定义，也就是驻点 一定是个局部最大值，使得f(z)在驻点 处的二阶导数为负  
推广到M维空间z上  
M维空间z上的概率分布p(z)=f(z)Z,在驻点 处，梯度∇f(z)将会消失，在驻点 处展开,我们有：  
![这里写图片描述](//img-
blog.csdn.net/20180321214359850?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1lhbmdNaW5nbGlhbmc2NjY=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
这里Hessian矩阵A是M维度方阵,A=∇∇lnf(z)∣z= 取指数得到：  
![这里写图片描述](//img-
blog.csdn.net/20180321214514695?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1lhbmdNaW5nbGlhbmc2NjY=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)
A为f(z)的Hessian矩阵  
注意：Hessian矩阵格式，对数似然函数的Hessian矩阵的逆矩阵即为协方差矩阵K ![这里写图片描述](//img-
blog.csdn.net/20180321214645878?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1lhbmdNaW5nbGlhbmc2NjY=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
归一化，其中归一化因子 ![这里写图片描述](//img-
blog.csdn.net/20180321214916446?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1lhbmdNaW5nbGlhbmc2NjY=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)
，q(z)正比于f(z)  
![这里写图片描述](//img-
blog.csdn.net/20180321214937644?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1lhbmdNaW5nbGlhbmc2NjY=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
前提是精度矩阵A是正定的,表明驻点 一定是一个局部最大值  
方差等于对数似然函数的二阶导数  
对数似然函数的Hessian矩阵的逆矩阵即为协方差矩阵K，即k=A^-1  
论文中维度用n表示,即用n代替M.因为此处为高斯，故其假定均值为0，即在Z0为0.  
综上所述可得最大似然后验概率的拉普拉斯近似表达式  
![这里写图片描述](//img-
blog.csdn.net/20180321214955664?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1lhbmdNaW5nbGlhbmc2NjY=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)  
两边同时取对数即有极大对数似然函数 ![这里写图片描述](//img-
blog.csdn.net/20180321220614229?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1lhbmdNaW5nbGlhbmc2NjY=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

###  4.核心源代码

    
    
    %目标函数
    Z=(1/2)*y'*(covar^-1)*y+(1/2)*log(det(covar))+(n/2)*log(2*pi);%调用求极小值函数
    求解参数的指令
    y = [-1.65 -1.1 -.33 .22 .55 0.88]'; %y值范围，即迭代范围
    c=[1 1];%参量数，这里有a(1) a(2)即sigmaf l 两个参量
    
    %所调用的目标函数
    Z=(1/2)*y'*(covar^-1)*y+(1/2)*log(det(covar))+(n/2)*log(2*pi);
    options=optimset('fminsearch');%求极小值函数执行语句
    options.TolX=0.001;
    options.Display='off';
    [a,sfval,sexit,soutput]=fminsearch(@fun,c,options,y,Z)%调用求极小值函数
    注：a为所求参数sigmaf sigman l，sfval即最小似然函数的极值(因fminsearch只能求极小值，故此处是将极大似然函数取负数后求极小值得出的三个参量)，sexit为退出迭代条件，soutput为结构输出output，包含最优化函数的信息，fun为最小化函数，c为参量个数，option为执行指令，y为输入量，z为目标函数极大似然函数的负数。

##  模型求解结果

![这里写图片描述](//img-
blog.csdn.net/20180321221329942?watermark/2/text/Ly9ibG9nLmNzZG4ubmV0L1lhbmdNaW5nbGlhbmc2NjY=/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

##  总结

上面求解出来的结果和高斯回归论文里面的结果还是有一点误差，但这基本够用了，编程再优化一下就可以了，都是换汤不换药的。

