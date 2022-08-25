### Rasterization 2 (Antialiasing and Z-buffering)

##### Sampling is Ubiquitous in Computer Graphics



#### Photograph = Sample Image Sensor Plane

![](../../../assets/img/2022-08-24/fast_23-09-38.png)



#### Video = Sample Time

![](../../../assets/img/2022-08-24/fast_23-10-42.png)

#### Sampling Artifacts (Errors / Mistakes / lnaccuracies) in Computer Graphics



#### Moire Patterns in Imaging

![](../../../assets/img/2022-08-24/fast_23-12-57.png)

Skip odd rows and columns



#### Wagon Wheel Illusion (False Motion)

![](../../../assets/img/2022-08-24/fast_23-15-21.png)

有的圈正转，有的反转，人眼采样跟不上



#### Sampllng Artifacts in Computer Graphics

Artifacts due to sampling - "Aliasing

* Jaggies一sampling in space
* Moire一undersampling images
* Wagon wheel effect一sampling intime
* [Many more]...

Behind the Aliasing Artifacts

* Signals are changing too fast (high frequency),
* but sampled too slowly



### Antialiasing Idea: Blurring (Pre-Filtering) Before Sampling

####   Rasterization: Point Sampling in Space

![](../../../assets/img/2022-08-24/fast_23-20-49.png)



Note Jaggies in rasterized triangle where pixel values are pure red or white

 ![](../../../assets/img/2022-08-24/fast_23-22-34.png)

Note antialiased edges in rasterized triangle where pixel values take intermediate values

#### Antialiasing vs Blurred Aliasing

![](../../../assets/img/2022-08-24/fast_23-25-47.png)



### Frequency Domain 频域

 Frequencies Cos2πfx

![](../../../assets/img/2022-08-24/fast_23-32-40.png)



#### Fourier Transform

Represent a function as a weighted sum Of sines and
cosmes

![](../../../assets/img/2022-08-24/fast_23-34-45.png)

![](../../../assets/img/2022-08-24/fast_23-35-15.png)

![](../../../assets/img/2022-08-24/fast_23-36-55.png)

![](../../../assets/img/2022-08-24/fast_23-37-28.png)

![](../../../assets/img/2022-08-24/fast_23-38-04.png)

![](../../../assets/img/2022-08-24/fast_23-38-31.png)

![](../../../assets/img/2022-08-24/fast_23-39-30.png)

![](../../../assets/img/2022-08-24/fast_23-40-02.png)

。。。



#### Fourier Transfor Decomp A Signal Into Frequencies

![](../../../assets/img/2022-08-24/fast_23-43-01.png)

Recall $e^{ix} = cos\ x + i\ sin\ x$

#### Higher Frequencies Need Faster Sampling

 ![](../../../assets/img/2022-08-24/fast_23-45-25.png)

 

#### UnderSampling Creates Frequency Aliases

  ![](../../../assets/img/2022-08-24/fast_23-47-14.png)

High-frequency signal is insufficiently sampled : samples erroneously appear to be from a low-frequency signal

Two frequencies that are indistinguishable at a given sampling
T are called "aliases"

两个完全不同的函数，得到的采样结果完全一样

#### Filtering = Getting rid of certain frequency contents



#### Visualizing Image Frequency Content

![](../../../assets/img/2022-08-24/fast_23-51-45.png)

中心低频，周围高频

亮度决定信息量



#### Filter Out Low Frequencies Only (Edges)

![](../../../assets/img/2022-08-24/fast_23-54-50.png)

 High-pass filter

高频看出来是边界

 Filter Out High Frequencies (Blur)![](../../../assets/img/2022-08-24/fast_23-57-29.png)

Low-pass filter



#### Filter Out Low and High Frequencies

![](../../../assets/img/2022-08-24/fast_23-59-03.png)

水波纹

![](../../../assets/img/2022-08-24/fast_23-59-47.png)

数字图像处理

现在多数通过机器学习来做了

 

#### Filtering = Convolution（= Averaging)

![](../../../assets/img/2022-08-25/fast_00-03-36.png)

Point-wise local averaging in a " sliding window"

![](../../../assets/img/2022-08-25/fast_00-05-36.png)



#### Convolution Theorem

Convolution in the spatial domain is equal to multiplication
in thefrequency domain,and Vice versa
Option1，

* Filterbyconvolutioninthespatialdomain

Option2：

* Transform to frequency domain (Fourier transform)
* Multiply by Fourier transform of convolution kernel
* Transform back to spatial domain(inverse Fourier)

![](../../../assets/img/2022-08-25/fast_00-08-34.png)

低通滤波 

时域上乘积 等于 频域上卷积



Box Filter

<img src="../../../assets/img/2022-08-25/fast_00-12-05.png" style="zoom:50%;" />

1/9 不影响图像整体亮度

Wider Filter Kernel = Lower Frequencies

<img src="../../../assets/img/2022-08-25/fast_00-15-49.png" style="zoom:50%;" />



#### Sampling=Repeating Frequency Contents

<img src="../../../assets/img/2022-08-25/fast_00-17-31.png" style="zoom:50%;" />



#### Aliasing = Mixed Frequency Contents

<img src="../../../assets/img/2022-08-25/fast_00-20-25.png" style="zoom:50%;" />

采样间隔变大（稀疏），频谱会变小，走样

 

How Can We Reduce Aliasing Error?

Option1：lncrease sampling rate

* Essentially ncreasing the distance between replicas in the Fourier domain
* Higher resolution displays, sensors, frame buffers
* But:costly & may need very high resolution

Option 2：Antialiasing

* Making Fourier contents “narrower" before repeating
* i.e.Filtering out high frequencies before sampling



模糊低通滤波

Antialiasing= Limiting, then repeating

<img src="../../../assets/img/2022-08-25/fast_00-26-15.png" style="zoom:50%;" />

A Practical Pre-Filter

A 1 pixel-width box filter ( low pass , blurring)

<img src="../../../assets/img/2022-08-25/fast_00-27-50.png" style="zoom:50%;" /> 



#### Antialiasing By Averagin Values in Pixel Area

Solution:

* Convolvef(x,y)bya1-pixelbox-blur
  * Recall:convolving=filtering=averaging
* Then sample at every pixel's center

#### Antialiasing By  Computing Average Pixel Value

ln rasterizing one triangle, the average value inside a pixel
area of f(x，y) = inside(triangle, x, y) is equal to theareaof the
pixel covered by the triangle

<img src="../../../assets/img/2022-08-25/fast_00-31-27.png" style="zoom:50%;" />



### Antialiasing By Supersampling (MSAA)

####  Supersampling

Approximate the effect of the 1-pixel box filter by sampling multiple locations within a pixel and averaging their values.



#### Point Sampling : One Sample Per Pixel

<img src="../../../assets/img/2022-08-25/fast_00-35-06.png" style="zoom:50%;" />



#### Supersampling:Step 1

Take NxN Samples in each pixel.

<img src="../../../assets/img/2022-08-25/fast_00-36-13.png" style="zoom:50%;" />

#### Supersampling:Step 2

Average the NXN samples "inside" each pixel.

<img src="../../../assets/img/2022-08-25/fast_00-41-00.png" style="zoom:50%;" />

SupersampIing:Step 2

This is the corresponding signal emitted by the display

<img src="../../../assets/img/2022-08-25/fast_00-47-49.png" style="zoom:50%;" />



No free lunch!

* What's the cost of MSAA?

Milestones (personal idea)

* FXAA (Fast Approximate AA) 换边界
* TAA (Temporal AA)   复用上一帧

 Super resolution / super sampling

* From low resolution to high resolution
* Essentially still "not enough samples" problem
* DLSS (Deep Learning Super Sampling) （猜测）







![]()