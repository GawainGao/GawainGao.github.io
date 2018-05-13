---
layout: post
title: "Automatically rotate picture"
data: 2018-05-13 15:45:50 +0900
categories: ImageProcessing
tag: Matlab
---

* content
{:toc}






自动旋转倾斜的照片
--------------------

有时因为摄影时相机位置不够标准，得到的照片会有一定角度的倾斜。我使用 Matlab 自动实现倾斜照片的自动更正。


过程
-----------------------------
首先在 Matlab 里面输入照片。然后使用 Otsu 方法进行二值化。Otsu 方法中会用到 graythresh 函数，这个函数可以得到分割的阈值。之后使用 im2bw 函数进行分割。使用 imshow 函数进行输出。


```
ori = imread('CMOSdata/20180416/1.jpg');
imshow(ori);
%Show the original picture
level = graythresh(ori);
bw = im2bw(ori,level);
imshow(bw);
%Get the black-white picture of original one
```

为了寻找旋转的角度，我使用 hough 变换去寻找图片内可以参考的水平线或者竖直线。
Matlab中 hough 变换的输入函数是二值图像后再进行 canny 边界提取后的图像，首先使用 hough 函数得到 hough 变换后的累加器中各项的值，之后对这些值进行最大值的查找，从而判断出标准水平线的位置和角度。

我们选取所有线中最长的，作为我们的基准直线，用这个基准直线的角度来对原图像进行旋转。其中 hough 变换得到的角度便可以作为我们的旋转角度。

Matlab 中，已知斜率求角度可以使用 atan(k)*180/pi。

```
ed = edge(bw,'canny');
imshow(ed);


%Get the black-white picture of original one
[H,theta,rho] = hough(ed,'ThetaRes',0.1);
figure, imshow(imadjust(mat2gray(H)),[],'XData',theta,'YData',rho,'InitialMagnification','fit');
xlabel('\theta (degrees)'), ylabel('\rho');
axis on, axis normal, hold on;
colormap(hot)



peaks = houghpeaks(H,8,'threshold',ceil(0.3*max(H(:))));
lines = houghlines(ed,theta,rho,peaks,'FillGap',5,'MinLength',7);

figure; imshow(ori), hold on
max_len = 0;
for k = 1:length(lines)
    xy = [lines(k).point1; lines(k).point2];
    plot(xy(:,1),xy(:,2),'LineWidth',2,'Color','green');
    plot(xy(1,1),xy(1,2),'x','LineWidth',2,'Color','red');
    plot(xy(2,1),xy(2,2),'x','LineWidth',2,'Color','red');
    
    len = norm(lines(k).point1 - lines(k).point2);
    if (len > max_len)
        max_len = len;
        xy_long = xy;
    end
end
plot(xy_long(:,1),xy_long(:,2),'LineWidth',2,'Color','red');

hold off

angle = atan((xy_long(2,2) - xy_long(1,2))/(xy_long(2,1) - xy_long(1,1)))*180/pi;
ori_ang = imrotate(ori,angle);
imshow(ori_ang);


```
之后我们对 hough 变换得到的图像进行特征区域的提取。我们使用 Matlab 的 Image Processing Toolbox工具箱中的Color Thresholder 工具箱进行二值化。可以得到一个createMask 函数，利用这个函数我们得到了 RGB 三个阈值。从而使用代码进行阈值分割。

阈值分割分为单阈值和多阈值方法，这里我们使用的是多阈值方法。在固定阈值和动态阈值中我们选择的是固定阈值方法，因为我们所要分类的对象是特定的。其中固定阈值中还分为全局阈值和局部阈值。


```
clc
clear
close all
ori = imread('CMOSdata/20180416/rotate_cut.png');
% Convert RGB image to chosen color space
I = ori;
% Define thresholds for channel 1 based on histogram settings
channel1Min = 120.000;
channel1Max = 255.000;
% Define thresholds for channel 2 based on histogram settings
channel2Min = 108.000;
channel2Max = 255.000;
% Define thresholds for channel 3 based on histogram settings
channel3Min = 117.000;
channel3Max = 255.000;
% Create mask based on chosen histogram thresholds
sliderBW = (I(:,:,1) >= channel1Min ) & (I(:,:,1) <= channel1Max) & ...
    (I(:,:,2) >= channel2Min ) & (I(:,:,2) <= channel2Max) & ...
    (I(:,:,3) >= channel3Min ) & (I(:,:,3) <= channel3Max);
BW = sliderBW;

% Initialize output masked image based on input image.
maskedRGBImage = ori;

% Set background pixels where BW is false to zero.
maskedRGBImage(repmat(~BW,[1 1 3])) = 0;
imshow(BW);
imshow(maskedRGBImage);

```

