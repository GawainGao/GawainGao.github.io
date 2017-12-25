---
layout: post
title: "Fuzzy in Image Processing"
data: 2017-12-25 19:45:50 +0900
categories: Image Processing
tag: Matlab
---

* content
{:toc}









Fuzzy in Image processing
==================

Fuzzy set theory
--------------------

During the computer processing, the set is always clear. But sometimes we need a fuzzy way to judge if a element is inside a set or not.

When a person is over 20 years old, someone think he is old but some others do not think so. So we can give a fuzzy defination, this man is generally getting older.

We define the Z as the class. Originally, one element has two statues, in{1} or out{0}. But in fuzzy defination, the element will be judged by the degree of membership. The fuzzy set A is consisted by value and this degree of membership. When DOM is {1}, it definately a member of A, when DOM is {0}, definately not. But when the DOM is between 0 and 1, it is an uncomplite member of A.

What's more, some priciple:

To A's NOT, `DOM = 1 - DOM`
To A or B, `DOM = max[DOM1,DOM2]`
To A and B, `DOM = min[DOM1,DOM2]`

To here, we can use this principle to deal with some problmes.


Fuzzy transform in Gray-Level-Trans
-----------------------------

Use the rule as follow:

```
R1: If a pixel is dark, let it darker.
R2: If a pixel is gray, let it there.
R3: If a pixel is light, let it brighter.
```

This rule is our method. Now we need a DOM function to judge a pixel is belonging to which one. With these rules, the picture can be more clear.

Attachment is the Matlab code:

```
%%

function [drak,gray,brig] = Fuzzy_Knowledge(Intensity) %Save as .m file.

  if(Intensity <= 0.27) drak = double(1);  %Divide the darkness into three part
  elseif(Intensity >= 0.5) drak = double(0);
  else drak = (0.5 - double(Intensity))/(0.22);
  end    
  if(Intensity >= 0.72) brig = double(1);  %Divide the birghtnees into three part
  elseif(Intensity <= 0.5) brig = double(0);   
  else brig = double((double(Intensity) - 0.5)/0.22);
  end
  if(Intensity >= 0.72) gray = double(0);  %Divide the gray level into three part
  elseif(Intensity <= 0.27) gray = double(0);
  elseif(Intensity <= 0.5) gray = double((double(Intensity) - 0.27)/0.22);
  else gray = double((0.72 - double(Intensity))/0.22);
  end
end

```

```
close all;
clear all;
clc;

%% ---------Using Fuzzy for intensity transfromations---------------
f = imread('');
f = mat2gray(f,[0 255]);    %Change to gray level picture

[M,N]=size(f);
g = zeros (M,N);

 for x = 1:1:M    %Change each pixel intensity by the gravity of drakness, gray and brightness
     for y = 1:1:N
         [drak,gray,brig] = Fuzzy_Knowledge(f(x,y));
         g(x,y) = ((drak * 0) + (gray * 0.5) + (brig * 1))/(drak + gray + brig); 
     end
 end
figure();
subplot(1,2,1);
imshow(f,[0 1]);
xlabel('a).Original Image');

subplot(1,2,2);
imshow(g,[0 1]);
xlabel('b).Result of fuzzy');

figure();
subplot(1,2,1);
h = imhist(f)/(M*N);
bar(0:1/255:1,h);
axis([0 1 0 .2]),grid;
xlabel('c).The Histogram of a');

subplot(1,2,2);
h = imhist(g)/(M*N);
bar(0:1/255:1,h);
axis([0 1 0 .2]),grid;
xlabel('d).The Histogram of b');

```

Fuzzy for detecting the edge
---------

We can make a new rule by fuzzy. If we want to do fuzzy detecting for edge, since when the gradient of the picture smooth, if means this part is not edge, we can set this pixel to be bright. Otherwise, if a pixel the gradient is sharp, means this is the edge, we can set if to be dark, which means edge.

So we first get the gradient of each 9 pixels and use the rule as follow:

```
If top is zero AND right is zero, THEN this pixel is NOT edge.
If top is zero AND left is zero, THEN this pixel is NOT edge.
If below is zero AND right is zero, THEN this pixel is NOT edge.
If below is zero AND left is zero, THEN this pixel is NOT edge.
			ELSE is edge.
```

Pay attention, these zero, white and black are all fuzzy. What's more, if two pixels gray level is near, we want to use the Guass function to remove the noise and make the input clear. Then we want if the fuzzy of edge part is high, it will easily to be judged as the edge.

```
%%

function [W1,W2,W3,W4,B] = Fuzzy_Knowledge_Filters(Intensity)

for x = 1:1:3
   for y = 1:1:3
       if((Intensity(x,y) <= 0.2) &&(Intensity(x,y) >= -0.2))
           Intensity(x,y) = exp(-20*Intensity(x,y).*Intensity(x,y));   %Use the Guass method to make it clear
       else Intensity(x,y) = 0;
       end
   end
end

W1 = min(Intensity(1,2),Intensity(2,3));   %If a AND b use the minimum
W2 = min(Intensity(2,3),Intensity(3,2));
W3 = min(Intensity(3,2),Intensity(2,1));
W4 = min(Intensity(2,1),Intensity(1,2));
B = min(min(1-W1,1-W2),min(1-W3,1-W4));
end
```

```
%% ---------Using Fuzzy for Spatial Filters---------------
close all;
clear all;
clc;

f = imread('');
f = mat2gray(f,[0 255]);

[M,N]=size(f);
f_Ex = zeros(M+2,N+2);

for x = 1:1:M
    for y = 1:1:N
        f_Ex(x+1,y+1) = f(x,y);
    end
end

z = zeros (3,3);
g = zeros (M+2,N+2);
for x = 2:1:M+1
    for y = 2:1:N+1
        z(1,1) = f_Ex(x-1,y-1) - f_Ex(x,y);
        z(1,2) = f_Ex(x-1,y) - f_Ex(x,y);
        z(1,3) = f_Ex(x-1,y+1) - f_Ex(x,y);
        z(2,1) = f_Ex(x,y-1) - f_Ex(x,y);
        z(2,2) = f_Ex(x,y) - f_Ex(x,y);
        z(2,3) = f_Ex(x,y+1) - f_Ex(x,y);
        z(3,1) = f_Ex(x+1,y-1) - f_Ex(x,y);
        z(3,2) = f_Ex(x+1,y) - f_Ex(x,y);
        z(3,3) = f_Ex(x+1,y+1) - f_Ex(x,y);
        [W1,W2,W3,W4,B] = Fuzzy_Knowledge_Filters(z);
        V1 = 0.8 * W1 + 0.2;
        V2 = 0.8 * W2 + 0.2;
        V3 = 0.8 * W3 + 0.2;
        V4 = 0.8 * W4 + 0.2;
        V5 = 0.8 - (0.8 * B);
        g(x,y) = ((W1*V1) + (W2*V2) + (W3*V3) + (W4*V4) + (B*V5))/(W1+W2+W3+W4+B); 
    end
end

figure();
subplot(1,2,1);
imshow(f,[0 1]);
xlabel('a).Original Image');

subplot(1,2,2);
imshow(g,[0 1]);
xlabel('b).Result of fuzzy');
```