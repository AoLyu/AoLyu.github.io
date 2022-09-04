### Materials and Appearances

![](../../../assets/img/2022-08-31/fast_20-58-51.png)

#### What is Material in Computer Graphics?

![](../../../assets/img/2022-08-31/fast_21-02-16.png)



Material == BRDF



#### Diffuse / Lambertian Material (BRDF)

![](../../../assets/img/2022-08-31/fast_21-04-18.png)



![](../../../assets/img/2022-08-31/fast_21-04-44.png)



#### Diffuse / Lambertian Material

Light is equally reflected in each output direction

Suppose the incident lighting is uniform:

<img src="../../../assets/img/2022-08-31/fast_21-05-44.png" style="zoom:50%;" /> <img src="../../../assets/img/2022-08-31/fast_21-06-21.png" style="zoom:50%;" />

ρ反射率



#### Glossy rnaterial (BRDF)

抛光基础

<img src="../../../assets/img/2022-08-31/fast_21-09-52.png"  />

<img src="../../../assets/img/2022-08-31/fast_21-10-29.png"  />



#### Ideal reflective / refractive  material (BSDF*)

<img src="../../../assets/img/2022-08-31/fast_21-11-43.png"  />

<img src="../../../assets/img/2022-08-31/fast_21-12-15.png"  />



#### Perfect Specular Reflection

<img src="../../../assets/img/2022-08-31/fast_21-13-41.png"  />



#### Perfect Specular Reflection

<img src="../../../assets/img/2022-08-31/fast_21-14-27.png"  />

<img src="../../../assets/img/2022-08-31/fast_21-14-53.png" style="zoom:67%;" />

<img src="../../../assets/img/2022-08-31/fast_21-15-27.png" style="zoom:67%;" />



#### Perfect Specular Reflection BRDF

<img src="../../../assets/img/2022-08-31/fast_21-17-37.png"  />



#### Specular Refraction

In addition to reflecting off surface, light may be transmitted through surface.
Light refracts when it enters a new medium.

<img src="../../../assets/img/2022-08-31/fast_21-18-18.png" style="zoom:50%;" /> <img src="../../../assets/img/2022-08-31/fast_21-18-29.png" style="zoom:50%;" /> 

Costics 海水折射



#### Snell s Law

Transmitted angle depends on
	index of refraction (IOR) for incident ray
	index of refraction (IOR) for exiting ray

<img src="../../../assets/img/2022-08-31/fast_21-20-36.png" style="zoom:50%;" /> <img src="../../../assets/img/2022-08-31/fast_21-22-20.png" style="zoom:50%;" />

$η_i\ sinθ_i = η_t\ sinθ_t$



#### Law of Refraction

<img src="../../../assets/img/2022-08-31/fast_21-27-20.png" style="zoom:50%;" /> <img src="../../../assets/img/2022-08-31/fast_21-28-00.png" style="zoom:50%;" /> 



##### Total internal reflection:

When light is moving from a more optically dense
medium to a less optically dense medium
Light incident on boundary from large enough angle will
not exit medium.

<img src="../../../assets/img/2022-08-31/fast_21-29-40.png" style="zoom:50%;" />



#### Snell s Window / Circle

<img src="../../../assets/img/2022-08-31/fast_21-31-55.png"/>

全反射，折射率大的入射折射率小的



#### Fresnel Reflection / Term

Reflectance depends on incident angle (and polarization of light)

<img src="../../../assets/img/2022-08-31/fast_21-50-33.png"/>

 This example: reflectance increases with grazing angle



#### Fresnel Term (Dielectric, η=1.5)

<img src="../../../assets/img/2022-08-31/fast_21-52-09.png"/>

极化现象



垂直看窗户，没反射

斜着看，有反射



#### Fresnel Term (Conductor)

<img src="../../../assets/img/2022-08-31/fast_21-54-01.png"/>



#### Fresnel Term— Formulae

Accurate: need to consider polarization

<img src="../../../assets/img/2022-08-31/fast_21-54-59.png" style="zoom: 67%;" /> <img src="../../../assets/img/2022-08-31/fast_21-55-22.png" style="zoom:50%;" />

**Approximate: Schlick's approximation**

<img src="../../../assets/img/2022-08-31/fast_21-56-42.png" style="zoom: 67%;" />



#### Microfacet Material

Microfacet Material: Motivation

<img src="../../../assets/img/2022-08-31/fast_21-58-28.png" style="zoom: 67%;" />



#### Microfacet Theory

Rough surface

* Macroscale: flat & rough
* Microscale: bumpy & specular

Individual elements of surface act like mirrors

* Known as Microfacets
* Each microfacet has its own normal

<img src="../../../assets/img/2022-08-31/fast_22-00-43.png" style="zoom: 67%;" />



#### Microfacet BRDF

Key: the distribution of microfacets' normals

<img src="../../../assets/img/2022-08-31/fast_22-01-44.png" style="zoom: 67%;" />

<img src="../../../assets/img/2022-08-31/fast_22-02-45.png" style="zoom: 67%;" />



#### Microfacet BRDF

* What kind of microfacets reflect wi to wo?
  (hint: microfacets are mirrors)

<img src="../../../assets/img/2022-08-31/fast_22-03-50.png" style="zoom: 67%;" />



#### Microfacet BRDF: Examples

<img src="../../../assets/img/2022-08-31/fast_22-07-04.png" style="zoom: 67%;" />



#### lsotropic / Anisotropic Materials (BRDFs)

<img src="../../../assets/img/2022-08-31/fast_22-09-06.png" style="zoom: 67%;" />

各向同性/ 各向异性

* Key: directionality of underlying surface

<img src="../../../assets/img/2022-08-31/fast_22-10-33.png" style="zoom: 67%;" />



#### Anisotropic BRDFs

<img src="../../../assets/img/2022-08-31/fast_22-11-25.png" style="zoom: 67%;" />



#### Anisotropic BRDF: Brushed Metal

* How is the pan brushed?

<img src="../../../assets/img/2022-08-31/fast_22-12-49.png" style="zoom: 67%;" />

<img src="../../../assets/img/2022-08-31/fast_22-13-55.png" style="zoom: 67%;" />

<img src="../../../assets/img/2022-08-31/fast_22-14-08.png" style="zoom: 67%;" />



#### Properties of BRDFs

* Non-negativity

  $f_r(ω_i\rightarrow ω_r)≥0$

* Linearity

<img src="../../../assets/img/2022-08-31/fast_22-16-40.png" style="zoom: 67%;" />



#### Properties of BRDFs

* Reciprocity principle

  $f_r(w_r\rightarrow_i) = f_r(w_i\rightarrow_r)$

  <img src="../../../assets/img/2022-08-31/fast_22-19-00.png" style="zoom: 67%;" />

* Energy conservation

<img src="../../../assets/img/2022-08-31/fast_22-19-37.png" style="zoom: 67%;" />

* Isotropic vs. anisotropic

  * If isotropic,  <img src="../../../assets/img/2022-08-31/fast_22-21-31.png" style="zoom: 50%;" />
  * Then, from reciprocity,

  <img src="../../../assets/img/2022-08-31/fast_22-22-27.png" style="zoom: 67%;" />

  <img src="../../../assets/img/2022-08-31/fast_22-22-56.png" style="zoom: 67%;" />



#### Measuring BRDFs: Motivation


Avoid need to develop / derive models
• Automatically includes all of the scattering effects present
Can accurately render with real-world materials
• Useful for product design, special effects ,...
Theory vs. practice:
<img src="../../../assets/img/2022-08-31/fast_22-25-18.png" style="zoom: 67%;" />

#### Image-based BRDF Measurement

<img src="../../../assets/img/2022-08-31/fast_22-26-10.png" style="zoom: 67%;" />



#### Measuring BRDFs: gonioreflectometer

<img src="../../../assets/img/2022-08-31/fast_22-27-18.png" style="zoom: 67%;" />



#### General approach:

```
foreach outgoing direction wo
	move light to illuminate surface with a thin beam from wo
	for each incoming direction wi
		move sensor to be at direction wi from surface
		measure incident radiance
```



#### Improving efficiency:

* Isotropic surfaces reduce dimensionality from 4D to 3D

* Reciprocity reduces # of measurements by half

* Clever optical systems...



#### Challenges in Measuring BRDFs

* Accurate measurements at grazing angles
  * Important due to Fresnel effects
* Measuring with dense enough sampling to capture high frequency specularities
* Retro-reflection
* Spatially-varying reflectance, ...



#### Representing Measured BRDFs

Desirable qualities

* Compact representation
*  Accurate representation of measured data
* Efficient evaluation for arbitrary pairs of directions
* Good distributions available for importance sampling



#### Tabular Representation

<img src="../../../assets/img/2022-08-31/fast_22-33-12.png" style="zoom: 67%;" />



