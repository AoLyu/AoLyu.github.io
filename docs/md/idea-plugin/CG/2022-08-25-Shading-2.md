### Shading 2 (Shading, Pipeline and Texture Mapping) 

#### Specular Term (Blinn-Phong)

* Bright near mirror reflection direction

![](../../../assets/img/2022-08-25/fast_21-07-15.png)

V close to mirror direction $\rightleftharpoons$ half vector near normal

* Measure "near" by dot product of unit vectors

![](../../../assets/img/2022-08-25/fast_21-10-43.png)

能不能看到高光，看 n 和 h是不是接近

点乘结果

高光白色

为什么指数p

#### Cosine Power Plots

Increasing p narrows the reflection lobe

![](../../../assets/img/2022-08-25/fast_21-14-37.png)

p  取值100~200

![](../../../assets/img/2022-08-25/fast_21-16-12.png)



#### Ambient Term

Shading that does not depend on anything

* Add constant color to account for disregarded
  illumination and fill in black shadows
* This is approximate / fake!

![](../../../assets/img/2022-08-25/fast_21-17-26.png)



#### Blinn-Phong Reflection Model

![](../../../assets/img/2022-08-25/fast_21-19-11.png)

![](../../../assets/img/2022-08-25/fast_21-19-41.png)



#### Shading Frequencies

What caused the shading difference?

![](../../../assets/img/2022-08-25/fast_21-37-08.png)

####  Shade each triangle (flat shading)

Flat shading

* Triangle face is
  flat — one normal
  vector
* Not good for
  smooth surfaces

![](../../../assets/img/2022-08-25/fast_22-06-32.png)

#### Shade each vertex (Gouraud shading)

* Gouraud shading
  Interpolate colors
  from vertices across
  triangle
* Each vertex has a
  normal vector (how?)

![](../../../assets/img/2022-08-25/fast_22-08-34.png)

#### Shade each pixel (Phong shading)

Phong shading

* Interpolate normal
  vectors across each
  triangle
*  Compute full shading
  model at each pixel
*  Not the Blinn-Phong
  Reflectance Model （频率）

 ![](../../../assets/img/2022-08-25/fast_22-10-25.png)



#### Shading Frequency: Face, Vertex or Pixel

![](../../../assets/img/2022-08-25/fast_22-12-08.png)



####  Defining Per-Vertex Normal Vectors

Best to get vertex normals from the underlying geometry

* e.g. consider a sphere

![](../../../assets/img/2022-08-25/fast_22-14-19.png)

Otherwise have to infer vertex normals from triangle faces

* Simple scheme: average surrounding face normals

![](../../../assets/img/2022-08-25/fast_22-15-39.png)

<img src="../../../assets/img/2022-08-25/fast_22-16-05.png" style="zoom:50%;" />

#### Defining Per-Pixel Normal Vectors

Barycentric interpolation (introducing soon) of vertex normals

![](../../../assets/img/2022-08-25/fast_22-17-34.png)



### Graphics (Real-time Rendering) Pipeline

实时渲染管线

#### Graphics Pipeline

![](../../../assets/img/2022-08-25/fast_22-20-06.png)

![](../../../assets/img/2022-08-25/fast_22-23-25.png)

![](../../../assets/img/2022-08-25/fast_22-24-01.png)

![](../../../assets/img/2022-08-25/fast_22-24-41.png)

![](../../../assets/img/2022-08-25/fast_22-25-52.png)

![](../../../assets/img/2022-08-25/fast_22-27-16.png)



#### Shader Programs

* Program vertex and fragment processing stages
* Describe operation on a single vertex (or fragment)

Example GLSL fragment shader program

```c++
// uniform 全局变量
uniform sampler2D myTexture; // program parameter
// 光照方向
uniform vec3 lightDir;   // program parameter

varying vec2 uv;   // per fragment value (interp. by rasterizer)
// 顶点法线
varying vec3 norm;  // per fragment value (interp. by rasterizer)

void diffuseShader()
{
  vec3 kd;
kd = texture2d(myTexture, uv);  // material color from texture
kd clamp(dot(—lightDir, norm), 0.0, 1.0);  // Lambertian shading model
gl_FragColor = vec4(kd, 1.0);   // output fragment color
}

```

* Shader function executes once per fragment.
*  Outputs color of surface at the current fragment's screen sample position.
*  This shader performs a texture lookup to obtain the surface's material color at this point, then performs a diffuse lighting calculation.

opengl 图形API，每个顶点执行这个 通用shader ，不需要写for 循环，只需要管一个顶点，一个fragment，

写的顶点就叫vertex shader 顶点着色器

写的像素 就叫Fragment color 或者 pixel color



#### Snail Shader Program

![](../../../assets/img/2022-08-25/fast_22-38-33.png)

 

#### Goal: Highly Complex 3D Scenes in Realtime

* 100's of thousands to millions of triangles in scéne
* Complex vertex and fragment shader  computations
* High resolution (2-4 megapixel + Supersampling)
* 30-60 frames per second (even higher for VR)

  

#### Graphics Pipeline Implementation: GPUs

Specialized processors for executing graphics pipeline computations

![](../../../assets/img/2022-08-25/fast_22-42-58.png)

着色器，可编程

#### GPU: Heterogeneous, Multi-Core Procesor

![](../../../assets/img/2022-08-25/fast_22-44-42.png)



### Texture Mapping

#### Diffelenc Colors at Different Places?

![](../../../assets/img/2022-08-25/fast_22-46-36.png)

#### Surfaces are 2D

Surface lives in 3D world space
Every 3D surface point also has a place
where it goes in the 2D image (texture)

![](../../../assets/img/2022-08-25/fast_22-47-48.png)



#### Texture Applied to Surface

![](../../../assets/img/2022-08-25/fast_22-49-55.png)

####   Visuaiizdtion of Texture Coordinates

Each triangle vertex is assigned a texture coordinate (u,v)

![](../../../assets/img/2022-08-25/fast_22-52-32.png) 

u，v 范围 都是 0 到 1

![](../../../assets/img/2022-08-25/fast_22-54-16.png)

 ![](../../../assets/img/2022-08-25/fast_22-55-23.png)

纹理可以重复多次，无缝衔接

![](../../../assets/img/2022-08-25/fast_22-56-14.png)



