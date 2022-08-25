### Shading 3 (Texture Mapping Cont.)

#### interpolation Across Triangles

Why do we want to interpolate?

* Specify values at vertices
* Obtain smoothly varying values across triangles

What do we want to interpolate?

* Texture coordinates, colors, normal vectors , ...

How do we interpolate?

* Barycentric coordinates 

barycentric Coordinates
A coordinate system for triangles ( α,β, γ)  均非负

![](../../../assets/img/2022-08-25/fast_23-04-02.png)

What's the barycentric coordinate of A?

![](../../../assets/img/2022-08-25/fast_23-06-53.png)

#### barycentric Coordinates

Geometric viewpoint — proportional areas

![](../../../assets/img/2022-08-25/fast_23-07-53.png)

What's the barycentric coordinate of the centroid?

![](../../../assets/img/2022-08-25/fast_23-10-17.png)

![](../../../assets/img/2022-08-25/fast_23-10-57.png)

#### Linearly interpolate values at vertices

![](../../../assets/img/2022-08-25/fast_23-12-58.png)

投影后位置会变化，取三维位置信息计算。



#### Simpie Texture Mapping: Diffuse Color

![](../../../assets/img/2022-08-25/fast_23-16-01.png)



### Texture Magnification

### (What if the texture is too small?)

#### Texture Magnification - Easy Case

Generally don't want this — insufficient texture resolution
A pixel on a texture — a texel(纹理元素、纹素)

![](../../../assets/img/2022-08-25/fast_23-18-54.png)

#### Bilinear interpolation 

![](../../../assets/img/2022-08-25/fast_23-20-45.png)

<img src="../../../assets/img/2022-08-25/fast_23-22-17.png" style="zoom:50%;" />

Bilinear interpolation usually gives pretty good results
at reasonable costs

bicubic 临近16个点

### Texture Magnification (hard case)

### (What if the texture is too large?)

Point barnpling Textures — Problem

![](../../../assets/img/2022-08-25/fast_23-25-55.png)



#### Screen Pixel " Footprint" in Texture

![](../../../assets/img/2022-08-25/fast_23-27-23.png)

#### Antiaiiaslng — Supersampling?

Will supersampling work?

* Yes, high quality, but costly
* When highly minified, many texels in pixel footprint
* Signal frequency too large in a pixel
* Need even higher sampling frequency

Let's understand this problem in another way

* What if we don't sample?

* Just need to get the average value within a range!

#### Point Query vs. (Avg.) Range Query

#### Mipmap

#### Allowing (fast, approx., square) range queries

![](../../../assets/img/2022-08-25/fast_23-48-17.png)

<img src="../../../assets/img/2022-08-25/fast_23-49-06.png" style="zoom:50%;" />

图像金字塔同理 ， 额外存储量，多了1/3



what is the storage overhead of a mipmap?

#### Compuling Mipmap Level D

![](../../../assets/img/2022-08-25/fast_23-53-10.png)

![](../../../assets/img/2022-08-25/fast_23-54-56.png)

在第几层查uv texture值

![](../../../assets/img/2022-08-25/fast_23-57-37.png)



#### Trilinear interpolation

![](../../../assets/img/2022-08-25/fast_23-59-04.png)

![](../../../assets/img/2022-08-26/fast_00-00-46.png)

#### Mipmap Limitations

<img src="../../../assets/img/2022-08-26/fast_00-02-47.png" style="zoom:50%;" />

Overblur Why?          Mipmap trilinear sampling

#### Anisotropic Filtering（各向异性过滤）

<img src="../../../assets/img/2022-08-26/fast_00-04-47.png" style="zoom:50%;" />

##### Better than Mipmap!

Ripmaps and summed area tables

* Can look up axis-aligned

* rectangular zones
*  Diagonal footprints still a problem

<img src="../../../assets/img/2022-08-26/fast_00-05-48.png"  />

#### Irreguiac Pixel Footprint in Texture

<img src="../../../assets/img/2022-08-26/fast_00-07-08.png"  />

EWA filtering

* Use multiple lookups
*  Weighted average
* Mipmap hierarchy still helps
* Can handle irregular footprints

<img src="../../../assets/img/2022-08-26/fast_00-09-00.png"  />