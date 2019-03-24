# 数字图像处理第五次作业
## 自动化66史玉康
## 2161800034
### 1、频域低通滤波器：设计低通滤波器包括 butterworth and Gaussian (选择合适的半径，计算功率谱比),平滑测试图像test1和2;分析各自优缺点；

**问题分析**

频域滤波是在频率域对图像做处理的一种方法：

<img src="https://github.com/YukiShiyk/hw5/blob/master/image/%E6%8F%92%E5%85%A5.jpg"  div align=center />.

其包括以下几个步骤：
①给定一幅大小为m*n的输入图像f(x,y)，确定填充参数，典型的选取M=2*m,N=2*n;

②对f(x,y)添加必要数量的0，形成大小为P*Q的填充后的图像fp(x,y);

③用(-1)^(x+y)乘以fp(x,y)移到变换中心；

④计算来自步骤三的图像的DFT，得到F(u,v);

⑤生成一个实的、对称的滤波函数H(u,v),其大小为P*Q，中心在(P/2,Q/2)的位置处，用阵列相乘得到乘积G(u,v)=H(u,v)*F(u,v)

⑥得到处理后的图像：

其中滤波器大小与频谱大小相同，相乘即可得到新的频谱。

Butterworth低通滤波器的函数表达式如下所示：

<img src="http://chart.googleapis.com/chart?cht=tx&chl= H\left ( u,v \right )= \frac{1}{1+\left [ \frac{D\left ( u,v \right )}{D_{0}} \right ]^{2n}}" style="border:none;">

其中

<img src="http://chart.googleapis.com/chart?cht=tx&chl= D\left ( u,v \right )= \left [ \left ( u-\frac{P}{2} \right ) ^{2}+\left ( v-\frac{Q}{2} \right ) ^{2}\right ]" style="border:none;">

阶数越高，滤波器的过度越剧烈，振铃现象越明显；

BLPF传递函数并没有在通过频率和滤除频率之间给出明显截止的尖锐的不连续性。对于具有平滑传递函数的滤波器，可在这样一点截止频率，即使得H（u,v）下降到最大值的某个百分数。对于上式，截止频率点是当D（U,v）=D0时的点

高斯低通滤波器的函数表达式如下所示：

<img src="http://chart.googleapis.com/chart?cht=tx&chl= H\left ( u,v\right )=e^{\frac{-D^{2}\left ( u,v \right )}{2D_{0}^{2}}}" style="border:none;">

其中D（u,v）是距离频率域举行中心的距离。D0是截止频率。当D（u，v）=D0时，GLPF下降到其最大值的0.607之处。
高斯滤波器的过渡特性非常平坦。因此不会产生振铃现象。

功率谱

建立一组标准截止频率轨迹的一种方法试计算包含规定的总图像功率值Pt的圆。该值是通过求每个点（u，v）处填充后图像的功率谱分量
的和得到的。

**处理结果**

<img src="https://github.com/YukiShiyk/hw5/blob/master/image/test1butter25.jpg"  width="400" height="400" div align=center />.<img src="https://github.com/YukiShiyk/hw5/blob/master/image/test1butter.jpg"  width="400" height="400" div align=center />.<img src="https://github.com/YukiShiyk/hw5/blob/master/image/test1butter75.jpg"  width="400" height="400" div align=center />.
<img src="https://github.com/YukiShiyk/hw5/blob/master/image/test1butter100.jpg"  width="400" height="400" div align=center />.

<img src="https://github.com/YukiShiyk/hw5/blob/master/image/test1gauss25.jpg"  width="400" height="400" div align=center />.<img src="https://github.com/YukiShiyk/hw5/blob/master/image/test1gauss.jpg"  width="400" height="400" div align=center />.
<img src="https://github.com/YukiShiyk/hw5/blob/master/image/test1gauss75.jpg"  width="400" height="400" div align=center />.
<img src="https://github.com/YukiShiyk/hw5/blob/master/image/test1gauss100.jpg"  width="400" height="400" div align=center />.


<img src="https://github.com/YukiShiyk/hw5/blob/master/image/test2butter25.jpg"  width="400" height="400" div align=center />.<img src="https://github.com/YukiShiyk/hw5/blob/master/image/test2butter.jpg"  width="400" height="400" div align=center />.<img src="https://github.com/YukiShiyk/hw5/blob/master/image/test2butter75.jpg"  width="400" height="400" div align=center />.
<img src="https://github.com/YukiShiyk/hw5/blob/master/image/test2butter100.jpg"  width="400" height="400" div align=center />.

<img src="https://github.com/YukiShiyk/hw5/blob/master/image/test2gauss25.jpg"  width="400" height="400" div align=center />.<img src="https://github.com/YukiShiyk/hw5/blob/master/image/test2gauss.jpg"  width="400" height="400" div align=center />.
<img src="https://github.com/YukiShiyk/hw5/blob/master/image/test2gauss75.jpg"  width="400" height="400" div align=center />.
<img src="https://github.com/YukiShiyk/hw5/blob/master/image/test2gauss100.jpg"  width="400" height="400" div align=center />.

功率谱比的计算结果：

test 1 :(D0=25) butterworth：gaussian=0.9435:0.9228

test 1 :(D0=50) butterworth：gaussian=0.9760:0.9622

test 1 :(D0=75) butterworth：gaussian=0.9868:0.9766

test 1 :(D0=100) butterworth：gaussian=0.9919:0.9839

test 2 :(D0=25) butterworth：gaussian=0.9596:0.9481

test 2 :(D0=50) butterworth：gaussian=0.9785:0.9707

test 2 :(D0=75) butterworth：gaussian=0.9850:0.9793

test 2 :(D0=100) butterworth：gaussian=0.9884:0.9839

**结果分析**

①对比每组图像处理结果中的原始图像和低通滤波后的图像，可以清晰地看到低通滤波器的平滑效果（模糊效果）

②对于每组图像分别选取截止半径为25,50,75,100的巴特沃斯低通滤波器和高斯低通滤波器进行低通滤波。对比不同的截止半径得到的滤波后图像来看，随着
截止半径的减小，滤波后的图像越来越模糊，功率谱比越来越小，即滤波后包含的低频分量越来越少。

③对比巴特沃斯低通滤波器和高斯低通滤波器的效果可知，两种滤波器达到的基本效果是一致的，即平滑图像，滤除高通分量，保留低通分量。但两者在相同的截止频率时，得到的功率谱比却不同，
主要原因是两个滤波器在过渡带处的差异。

④巴特沃斯低通滤波器的优缺点：它在通频带内外都有平稳的幅频特性，但有较长的过渡带，在过渡带上很容易造成失真。

⑤高斯低通滤波器的优缺点：在频域具有平滑性能

**代码整理**
```swift 

close all;clear all;clc;
[filename, pathname] = uigetfile({'*.jpg'; '*.bmp'; '*.gif';'*.pgm';'*.tif'}, '选择图片');
I=imread([pathname, filename]);
I=im2double(I);
M=2*size(I,1);  %滤波器行数
N=2*size(I,2);  %滤波器列数
u=-M/2:(M/2-1);
v=-N/2:(N/2-1);
[U,V]=meshgrid(u,v);
D=sqrt(U.^2+V.^2);
D0=50;
n=4;
H1=1./(1+(D./D0).^(2*n));  %构造巴特沃斯滤波器
H2=exp(-D.^2/2./D0^2);     %构造高斯滤波器
J1=fftshift(fft2(I,size(H1,1),size(H1,2)));  %转换到频域
J2=fftshift(fft2(I,size(H2,1),size(H2,2)));  %转换到频域
K1=J1.*H1;
K2=J2.*H2;
L1=ifft2(ifftshift(K1));  %傅立叶反变换
L1=L1(1:size(I,1),1:size(I,2));  %改变图像大小
L2=ifft2(ifftshift(K2));  %傅立叶反变换
L2=L2(1:size(I,1),1:size(I,2));  %改变图像大小
s=0;
s1=0;
for x1=1:size(J1,1)
for y1=1:size(J1,2)
    m1=(abs(K1(x1,y1)))^2;
    s1=s1+m1;   
    m2=(abs(J1(x1,y1)))^2;
    s=s+m2;
end
end
a1=s1/s;
disp(a1);
s3=0;
s4=0;
for x2=1:size(J2,1)
for y2=1:size(J2,2)
    m3=(abs(K2(x2,y2)))^2;
    s4=s4+m3;   
    m4=(abs(J2(x2,y2)))^2;
    s3=s3+m4;
end
end
a2=s4/s3;
 %计算功率谱比
disp(a2);
figure(1);
subplot(221),imshow(I),title('原始图像');  %显示原始图像
subplot(222);imshow(L1),title(['经过butterworth低通滤波器后的图像,D0=' num2str(D0)]);  %显示滤波后的图像
subplot(223);imshow(abs(255.*J1./max(max(J1)))),title('原始图像的频谱图');
subplot(224);imshow(abs(255.*K1./max(max(K1)))),title(['经过butterworth低通滤波器后的频谱图,D0=' num2str(D0)]);
figure(2);
subplot(221),imshow(I),title('原始图像');  %显示原始图像
subplot(222);imshow(L2),title(['经过Gaussian低通滤波器后的频谱图,D0=' num2str(D0)]);  %显示滤波后的图像
subplot(223);imshow(abs(255.*J2./max(max(J2)))),title('原始图像的频谱图');
subplot(224);imshow(abs(255.*K2./max(max(K2)))),title(['经过Gaussian低通滤波器后的频谱图,D0=' num2str(D0)]);

```

###  2、频域高通滤波器：设计高通滤波器包括butterworth and Gaussian，在频域增强边缘。选择半径和计算功率谱比，测试图像test3,4：分析各自优缺点；

**问题分析**

其包括以下几个步骤：
①给定一幅大小为m*n的输入图像f(x,y)，确定填充参数，典型的选取M=2*m,N=2*n;

②对f(x,y)添加必要数量的0，形成大小为P*Q的填充后的图像fp(x,y);

③用(-1)^(x+y)乘以fp(x,y)移到变换中心；

④计算来自步骤三的图像的DFT，得到F(u,v);

⑤生成一个实的、对称的滤波函数H(u,v),其大小为P*Q，中心在(P/2,Q/2)的位置处，用阵列相乘得到乘积G(u,v)=H(u,v)*F(u,v)

⑥得到处理后的图像：

其中滤波器大小与频谱大小相同，相乘即可得到新的频谱。

Butterworth高通滤波器的函数表达式如下所示：

<img src="http://chart.googleapis.com/chart?cht=tx&chl= H\left ( u,v \right )= \frac{1}{1+ left [ \frac{D_{0}} {D\left ( u,v \right )}\right ]^{2n}}" style="border:none;">

其中

<img src="http://chart.googleapis.com/chart?cht=tx&chl= D\left ( u,v \right )= \left [ \left ( u-\frac{P}{2} \right ) ^{2}+\left ( v-\frac{Q}{2} \right ) ^{2}\right ]" style="border:none;">

阶数越高，滤波器的过度越剧烈，振铃现象越明显；

BLPF传递函数并没有在通过频率和滤除频率之间给出明显截止的尖锐的不连续性。对于具有平滑传递函数的滤波器，可在这样一点截止频率，即使得H（u,v）下降到最大值的某个百分数。对于上式，截止频率点是当D（U,v）=D0时的点

高斯低通滤波器的函数表达式如下所示：

<img src="http://chart.googleapis.com/chart?cht=tx&chl= H\left ( u,v\right )=1-e^{\frac{-D^{2}\left ( u,v \right )}{2D_{0}^{2}}}" style="border:none;">

其中D（u,v）是距离频率域举行中心的距离。D0是截止频率。当D（u，v）=D0时，GLPF下降到其最大值的0.607之处。
高斯滤波器的过渡特性非常平坦。因此不会产生振铃现象。

**处理结果**

<img src="https://github.com/YukiShiyk/hw5/blob/master/image/3.1.25.jpg"  width="400" height="400" div align=center />.
<img src="https://github.com/YukiShiyk/hw5/blob/master/image/3.1.50.jpg"  width="400" height="400" div align=center />.
<img src="https://github.com/YukiShiyk/hw5/blob/master/image/3.1.75.jpg"  width="400" height="400" div align=center />.

<img src="https://github.com/YukiShiyk/hw5/blob/master/image/3.2.25.jpg"  width="400" height="400" div align=center />.
<img src="https://github.com/YukiShiyk/hw5/blob/master/image/3.2.50.jpg"  width="400" height="400" div align=center />.
<img src="https://github.com/YukiShiyk/hw5/blob/master/image/3.2.75.jpg"  width="400" height="400" div align=center />.

<img src="https://github.com/YukiShiyk/hw5/blob/master/image/4.1.25.jpg"  width="400" height="400" div align=center />.
<img src="https://github.com/YukiShiyk/hw5/blob/master/image/4.1.50.jpg"  width="400" height="400" div align=center />.
<img src="https://github.com/YukiShiyk/hw5/blob/master/image/4.1.75.jpg"  width="400" height="400" div align=center />.

<img src="https://github.com/YukiShiyk/hw5/blob/master/image/4.2.25.jpg"  width="400" height="400" div align=center />.
<img src="https://github.com/YukiShiyk/hw5/blob/master/image/4.2.50.jpg"  width="400" height="400" div align=center />.
<img src="https://github.com/YukiShiyk/hw5/blob/master/image/4.2.75.jpg"  width="400" height="400" div align=center />.


功率谱比的计算结果：

test 3 :(D0=25) butterworth：gaussian=0.0188:0.0136

test 3 :(D0=50) butterworth：gaussian=0.0034:0.0028

test 3 :(D0=75) butterworth：gaussian=0.0010:9.5356e-04

test 4 :(D0=25) butterworth：gaussian=0.0369:0.0285

test 4 :(D0=50) butterworth：gaussian=0.0153:0.0119

test 4 :(D0=75) butterworth：gaussian=0.0087:0.0067

**结果分析**

①对比每组图像处理结果中的原始图像和高通滤波后的图像，可以清晰地看到高通滤波器边缘增强效果；通过傅里叶谱可以清晰地看到滤波器的截断效果。

②对于每幅图像分别选取截止半径为25,50,75的巴特沃斯高通滤波器和高斯高通滤波器。对比不同的截止半径可知，随着截止频率D0的增加，滤波后的图像边缘应该
越来越清晰，功率谱比越来越小，即滤波后包含的高频分量越来越少。但当D0增大到一定程度时，边缘将消失，主要是因为流出的能量过多，图像全部变成了黑色。

③对比巴特沃斯高通滤波器和高斯高通滤波器的效果可知，两种滤波器达到的基本效果是一致的，即增强图像边缘，滤除低通分量，保留高频分量。但两者截止频率相同时
得到的功率谱比却不同，主要原因是两个滤波器在过渡带处的差异。

**代码整理**

```swift

close all;clear all;clc;
[filename, pathname] = uigetfile({'*.jpg'; '*.bmp'; '*.gif';'*.pgm';'*.tif'}, '选择图片');
I=imread([pathname, filename]);
I=im2double(I);
M=2*size(I,1);  %滤波器行数
N=2*size(I,2);  %滤波器列数
u=-M/2:(M/2-1);
v=-N/2:(N/2-1);
[U,V]=meshgrid(u,v);
D=sqrt(U.^2+V.^2);
D0=100;
n=4;
H1=1./(1+(D0./D).^(2*n));  %构造巴特沃斯高通滤波器
H2=1-exp(-D.^2/2./D0^2);     %构造高斯高通滤波器
J1=fftshift(fft2(I,size(H1,1),size(H1,2)));  %转换到频域
J2=fftshift(fft2(I,size(H2,1),size(H2,2)));  %转换到频域
K1=J1.*H1;
K2=J2.*H2;
L1=ifft2(ifftshift(K1));  %傅立叶反变换
L1=L1(1:size(I,1),1:size(I,2));  %改变图像大小
L2=ifft2(ifftshift(K2));  %傅立叶反变换
L2=L2(1:size(I,1),1:size(I,2));  %改变图像大小
s=0;
s1=0;
for x1=1:size(J1,1)
for y1=1:size(J1,2)
    m1=(abs(K1(x1,y1)))^2;
    s1=s1+m1;   
    m2=(abs(J1(x1,y1)))^2;
    s=s+m2;
end
end
a1=s1/s;
disp(a1);
s3=0;
s4=0;
for x2=1:size(J2,1)
for y2=1:size(J2,2)
    m3=(abs(K2(x2,y2)))^2;
    s4=s4+m3;   
    m4=(abs(J2(x2,y2)))^2;
    s3=s3+m4;
end
end
a2=s4/s3;
 %计算功率谱比
disp(a2);
figure(1);
subplot(221),imshow(I),title('原始图像');  %显示原始图像
subplot(222);imshow(L1),title(['经过butterworth高通滤波器后的图像,D0=' num2str(D0)]);  %显示滤波后的图像
subplot(223);imshow(abs(255.*J1./max(max(J1)))),title('原始图像的频谱图');
subplot(224);imshow(abs(255.*K1./max(max(K1)))),title(['经过butterworth高通滤波器后的频谱图,D0=' num2str(D0)]);
figure(2);
subplot(221),imshow(I),title('原始图像');  %显示原始图像
subplot(222);imshow(L2),title(['经过Gaussian高通滤波器后的频谱图,D0=' num2str(D0)]);  %显示滤波后的图像
subplot(223);imshow(abs(255.*J2./max(max(J2)))),title('原始图像的频谱图');
subplot(224);imshow(abs(255.*K2./max(max(K2)))),title(['经过Gaussian低通滤波器后的频谱图,D0=' num2str(D0)]);

```
###  3、其他高通滤波器：拉普拉斯和Unmask，对测试图像test3,4滤波；分析各自优缺点；

**处理结果**

<img src="https://github.com/YukiShiyk/hw5/blob/master/image/test3la.jpg"  width="400" height="400" div align=center />.
<img src="https://github.com/YukiShiyk/hw5/blob/master/image/test3un.jpg"  width="400" height="400" div align=center />.
<img src="https://github.com/YukiShiyk/hw5/blob/master/image/test4la.jpg"  width="400" height="400" div align=center />.
<img src="https://github.com/YukiShiyk/hw5/blob/master/image/test4un.jpg"  width="400" height="400" div align=center />.

**结果分析**

①对比每组图像处理结果中的原始图像和滤波后的图像，可以看到滤波器边缘增强的效果；

②对于拉普拉斯算子和unmask滤波，两者达到的滤波效果基本上是一致的。


**代码整理**

```swift

close all;clear all;clc;
[filename, pathname] = uigetfile({'*.jpg'; '*.bmp'; '*.gif';'*.pgm';'*.tif'}, '选择图片');
I=imread([pathname, filename]);
I=im2double(I);
M=2*size(I,1);  %滤波器行数
N=2*size(I,2);  %滤波器列数
u=-M/2:(M/2-1);
v=-N/2:(N/2-1);
[U,V]=meshgrid(u,v);
D=sqrt(U.^2+V.^2);
c=1;
D0=100;
k1=1;k2=1;
H1=1+c*4*pi^2.*D.^2;  %构造拉普拉斯高通滤波器
H2=1-exp(-D.^2/2./D0^2);     %构造Unmask高通滤波器
J1=fftshift(fft2(I,size(H1,1),size(H1,2)));  %转换到频域
J2=fftshift(fft2(I,size(H2,1),size(H2,2)));  %转换到频域
K1=J1.*H1;
K2=k1+k2.*J2.*H2;
L1=ifft2(ifftshift(K1));  %傅立叶反变换
L1=L1(1:size(I,1),1:size(I,2));  %改变图像大小
L2=ifft2(ifftshift(K2));  %傅立叶反变换
L2=L2(1:size(I,1),1:size(I,2));  %改变图像大小
s=0;
s1=0;
for x1=1:size(J1,1)
for y1=1:size(J1,2)
    m1=(abs(K1(x1,y1)))^2;
    s1=s1+m1;   
    m2=(abs(J1(x1,y1)))^2;
    s=s+m2;
end
end
a1=s1/s;
disp(a1);
s3=0;
s4=0;
for x2=1:size(J2,1)
for y2=1:size(J2,2)
    m3=(abs(K2(x2,y2)))^2;
    s4=s4+m3;   
    m4=(abs(J2(x2,y2)))^2;
    s3=s3+m4;
end
end
a2=s4/s3;
 %计算功率谱比
disp(a2);
figure(1);
subplot(221),imshow(I),title('原始图像');  %显示原始图像
subplot(222);imshow(L1),title('经过拉普拉斯高通滤波器后的图像');  %显示滤波后的图像
subplot(223);imshow(abs(255.*J1./max(max(J1)))),title('原始图像的频谱图');
subplot(224);imshow(abs(255.*K1./max(max(K1)))),title('经过拉普拉斯高通滤波器后的频谱图');
figure(2);
subplot(221),imshow(I),title('原始图像');  %显示原始图像
subplot(222);imshow(L2),title(['经过unmask高通滤波器后的频谱图,D0=' num2str(D0)]);  %显示滤波后的图像
subplot(223);imshow(abs(255.*J2./max(max(J2)))),title('原始图像的频谱图');
subplot(224);imshow(abs(255.*K2./max(max(K2)))),title(['经unmask7低通滤波器后的频谱图,D0=' num2str(D0)]);

```

### 4、比较并讨论空域低通高通滤波（Project3）与频域低通和高通的关系；

* 空域滤波和频域滤波间的纽带是卷积定理，空域滤波和频域滤波的滤波器互为傅里叶变换。

* 使用空间域滤波和频率域滤波对存在图像噪声有一定的减弱作用和对边缘的检测效果。

* 从空域和频域低通滤波器对图片的滤波效果看，空域滤波中，平滑滤波器算法简单，处理速度快，但在降低噪声的同时使图像模糊，特别是在边缘和细节处。而中值滤波对椒盐噪声的抑制效果比较好，但对点、线等细节较多的图像却不太合适。空域低通滤波对椒盐噪声过滤效果差，图像较为模糊。而在频域滤波中，去噪声的同时将会导致边缘信息损失而使图像模糊，并且产生振铃效应，而且计算量大，计算时间长。

* 从空域和频域高通滤波器对图片的滤波效果看，空域滤波中，算法比较简单，处理速度较快。在锐化方面效果明显，线条突出；频域滤波中，算法复杂，计算速度慢，有微量振铃效果，图像结果显示比较平缓。







