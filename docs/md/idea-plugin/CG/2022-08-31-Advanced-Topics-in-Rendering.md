### Advanced Topics in Rendering

####  Advanced Light Transport

• Unbiased light transport methods
- Bidirectional path tracing (BDPT)
- Metropolis light transport (MLT)

Biased light transport methods

* Photon mapping
* Vertex connection and merging (VCM)

Instant radiosity (VPL / many light methods)



#### Biased vs. Unbiased Monte Carlo Estimators

* An unbiased Monte Carlo technique does not have any
  systematic error
  * The expected value of an unbiased estimator will always be
    the correct value, no matter how many samples are used
    Otherwise, biased

- One special case, the expected value converges to the
correct value as infinite #samples are used — consistent
- We'll look again at this page after introducing Photon
  Mapping

#### Bidirectional Path Tracing (BDPT)

• Recall: a path connects the camera and the light
• BDPT
- Traces sub-paths from both the camera and the light
- Connects the end points from both sub-paths

![](../../../assets/img/2022-08-31/fast_23-08-58.png)



#### Bidirectional Path Tracing (BDPT)

* Suitable if the light transport is complex on the light's side

* Difficult to implement & quite slow

![](../../../assets/img/2022-08-31/fast_23-10-49.png)



#### Metropolis Light Transport (MLT)

* A Markov Chain Monte Carlo (MCMC) application
  - Jumping from the current sample to the next
    with some PDF
* Very good at locally exploring difficult light paths
* Key idea
  - Locally perturb an existing path to get a new path

![](../../../assets/img/2022-09-03/fast_10-31-22.png)

* #### Pros

*  Works great with difficult light path

* Also unbiased

![](../../../assets/img/2022-09-03/fast_10-32-33.png)

​                                                                          caustics

specular 水面



#### Cons

* Difficult to estimate the convergence rate
* Does not guarantee equal convergence rate per pixel
* So, usually produces "dirty" results
* Therefore, usually not used to render animations

![](../../../assets/img/2022-09-03/fast_10-35-19.png)

#### Photon Mapping

* A biased approach & A two-stage method
* Very good at handling Specular-Diffuse-Specular (SDS)
  paths and generating caustics

![](../../../assets/img/2022-09-03/fast_10-37-05.png)



#### Photon lvlapping — Approach (variations apply)

Stage 1 — photon tracing

- Emitting photons from the light source, bouncing them
around, then recording photons on diffuse surfaces

![](../../../assets/img/2022-09-03/fast_10-38-16.png)

Stage 2 — photon collection (final gathering)
- Shoot sub-paths from the camera, bouncing them around, until they hit diffuse surfaces
- Calculation — local density estimation
  - Idea: areas with more photons should be brighter
  - For each shading point, find the nearest N photons.  Take the surface area they over

![](../../../assets/img/2022-09-03/fast_10-41-08.png)

密度估计



#### Pnoton Mapping

![](../../../assets/img/2022-09-03/fast_10-43-11.png)



Why biased?

* Local Density estimation

  dN /dA !=  ΔN / ΔA

* But in the sense of limit

  * More photons emitted ->
  * the same N photons covers a smaller ΔA ->
  * Δ is closer to dA
  * So, biased but consistent!

* An easier understanding bias in rendering
  - Biased == blurry
  - Consistent == not blurry with infinite #samples

* Why not do a "const range" search for density estimation?

#### Vertex Connection and Merging

*  A combination of BDPT and Photon Mapping
* Key idea
  - Let's not waste the sub-paths in BDPT if their end points cannot be connected but can be merged
  - Use photon mapping to handle the merging of nearby
    "photons"

![](../../../assets/img/2022-09-03/fast_10-53-42.png)

#### instant Radiosity (IR)

* Sometimes also called many-light approaches
* Key idea
  - Lit surfaces can be treated as light sources
* Approach
  - Shoot light sub-paths and assume the end point of each sub-path is a Virtual Point Light (VPL) 
  - Render the scene as usual using these VPLs

![](../../../assets/img/2022-09-03/fast_10-56-12.png)



#### instant Radiosity

* Pros: fast and usually gives good results on diffuse scenes
* Cons
  - Spikes will emerge when VPLs are close to shading points
  - Cannot handle glossy materials

![](../../../assets/img/2022-09-03/fast_10-58-07.png)



####  Advanced Appearance Modeling

* Non-surface models
  - Participating media
  - Hair/ fur/ fiber (BCSDF)
  - Granular material
* Surface models
  - Translucent material (BSSRDF)
  - Cloth
  - Detailed material (non-statistical BRDF)
* Procedural appearance
* 

#### Non-Surface Models

Participating Media: Fog

![](../../../assets/img/2022-09-03/fast_11-02-21.png)

Participating Media: Cloud

![](../../../assets/img/2022-09-03/fast_11-03-11.png)

Participating Media

* At any point as light travels through a participating medium, it can be (partially) absorbed and scattered.

![](../../../assets/img/2022-09-03/fast_11-03-56.png)



Participating Media

* Use Phase Function to describe the angular distribution of light scattering at any point x within participating media.

![](../../../assets/img/2022-09-03/fast_11-05-42.png)

Participating Media: Rendering

* Randomly choose a direction to bounce
* Randomly choose a distance to go straight
* At each 'shading point', connect to the light

![](../../../assets/img/2022-09-03/fast_11-06-51.png)

#### Participating Media: Application

![](../../../assets/img/2022-09-03/fast_11-08-14.png)

#### Hair Appearance

![](../../../assets/img/2022-09-03/fast_11-09-57.png)

Kajiya-Kay Model

<img src="../../../assets/img/2022-09-03/fast_11-11-05.png" style="zoom:50%;" />

Kajiya-Kay Model

<img src="../../../assets/img/2022-09-03/fast_11-12-19.png" style="zoom:50%;" />

Marschner Model

<img src="../../../assets/img/2022-09-03/fast_11-12-56.png" style="zoom:50%;" />

Marschner Model

* Glass-like cylinder
* 3 types of light interactions:  (R: reflection, T: transmission)

<img src="../../../assets/img/2022-09-03/fast_11-16-59.png" style="zoom:50%;" />

Marschner model

<img src="../../../assets/img/2022-09-03/fast_11-17-42.png" style="zoom:50%;" />

#### Fur Appearance— As Human Hair

*  Cannot represent diffusive and saturated appearance

<img src="../../../assets/img/2022-09-03/fast_11-42-04.png" style="zoom:50%;" />

#### Human Hair vs Animal Fur

<img src="../../../assets/img/2022-09-03/fast_11-42-39.png" style="zoom:50%;" />

#### Imponance of Medulla

<img src="../../../assets/img/2022-09-03/fast_11-43-20.png" style="zoom:50%;" />



#### Impoflance of Medulla

<img src="../../../assets/img/2022-09-03/fast_11-44-54.png" style="zoom:50%;" />

#### Doubie Cylinder Model

<img src="../../../assets/img/2022-09-03/fast_11-45-50.png" style="zoom:50%;" />

#### Doubie Cylinder Model — Lobes

<img src="../../../assets/img/2022-09-03/fast_15-55-19.png" style="zoom:50%;" />

<img src="../../../assets/img/2022-09-03/fast_15-55-45.png" style="zoom:50%;" />



#### Granular Material

What is granular material?

<img src="../../../assets/img/2022-09-03/fast_15-57-56.png" style="zoom:50%;" />

* Can we avoid explicit modeling of all granules?
  — Yes with procedural definition.

<img src="../../../assets/img/2022-09-03/fast_15-59-02.png" style="zoom:50%;" />



#### Surface Models

Translucent Material: Jade

<img src="../../../assets/img/2022-09-03/fast_16-00-29.png" style="zoom:50%;" />



Translucent Material: Jellyfish

<img src="../../../assets/img/2022-09-03/fast_16-02-09.png" style="zoom:50%;" />



#### Subsurface Scattering

Visual characteristics of many surfaces caused by light exiting at different 

• Violates a fundamental assumption of the BRDF

<img src="../../../assets/img/2022-09-03/fast_16-03-01.png" style="zoom:50%;" />       <img src="../../../assets/img/2022-09-03/fast_16-03-39.png" style="zoom:50%;" />

#### Scattering Functions

* BSSRDF: generalization of BRDF; exitant radiance at one point due to incident differential irradiance at another point:

  <img src="../../../assets/img/2022-09-03/fast_16-04-56.png" style="zoom:50%;" />

* Generalization of rendering equation: integrating over all points on the surface and all directions (!)

  <img src="../../../assets/img/2022-09-03/fast_16-05-44.png" style="zoom:50%;" />

<img src="../../../assets/img/2022-09-03/fast_16-06-18.png" style="zoom:50%;" />

#### Dipole Approximation

* Approximate light diffusion by introducing two point sources.

<img src="../../../assets/img/2022-09-03/fast_16-07-56.png" style="zoom:50%;" />



#### BRDF

<img src="../../../assets/img/2022-09-03/fast_16-09-34.png" style="zoom:50%;" />



BSSRDF

<img src="../../../assets/img/2022-09-03/fast_16-10-33.png" style="zoom:50%;" />

#### BRDF  vs BSSRDF

<img src="../../../assets/img/2022-09-03/fast_16-11-41.png" style="zoom:50%;" />



#### BSSRDF: Application

<img src="../../../assets/img/2022-09-03/fast_16-12-55.png" style="zoom:50%;" />

#### Cloth

* A collection of twisted fibers!
  Two levels of twist

<img src="../../../assets/img/2022-09-03/fast_16-14-17.png" style="zoom:50%;" />

* Woven or knitted

<img src="../../../assets/img/2022-09-03/fast_16-15-04.png" style="zoom:50%;" />



#### Cloth. Render as Surface

* Given the weaving pattern, calculate the overall behavior
*  Render using a BRDF

<img src="../../../assets/img/2022-09-03/fast_16-16-52.png" style="zoom:50%;" />

<img src="../../../assets/img/2022-09-03/fast_16-17-27.png" style="zoom:50%;" />

#### Render as Surface — Limitation

<img src="../../../assets/img/2022-09-03/fast_16-18-46.png" style="zoom:50%;" />

#### Cloth: Render as Participating Media

* Properties of individual fibers & their distribution ->
   scattering parameters
* Render as a participating medium

<img src="../../../assets/img/2022-09-03/fast_16-20-52.png" style="zoom:50%;" />



#### Cloth: Render as Actual Fibers

• Render every fiber explicitly!

<img src="../../../assets/img/2022-09-03/fast_16-22-31.png" style="zoom:50%;" />



#### Detaiied Appearance: Motivation

• Not looking realistic, why?

<img src="../../../assets/img/2022-09-03/fast_16-23-57.png" style="zoom:50%;" />



#### Reai is more complicated

<img src="../../../assets/img/2022-09-03/fast_16-25-11.png" style="zoom:50%;" />



Why details?           Microfacet model

<img src="../../../assets/img/2022-09-03/fast_16-26-21.png" style="zoom: 33%;" /><img src="../../../assets/img/2022-09-03/fast_16-27-09.png" style="zoom: 33%;" /> <img src="../../../assets/img/2022-09-03/fast_16-28-27.png" style="zoom: 33%;" />



#### Recap. Microfacet BRDF

<img src="../../../assets/img/2022-09-03/fast_16-32-04.png" style="zoom: 33%;" />

​		Surface = Specular microfacets + statistical normals

<img src="../../../assets/img/2022-09-03/fast_16-30-50.png" style="zoom: 33%;" />  

NDF: Normal Distribution Function



#### Statistical NDF vs. Actual NDF

Distribution of Normals (NDF)

<img src="../../../assets/img/2022-09-03/fast_16-33-15.png" style="zoom: 80%;" />



#### Define details

<img src="../../../assets/img/2022-09-03/fast_16-34-23.png" style="zoom: 80%;" />



#### Rendering? Too difficult!

<img src="../../../assets/img/2022-09-03/fast_16-44-35.png" style="zoom: 80%;" />

#### Difficult path sampling problem

<img src="../../../assets/img/2022-09-03/fast_16-46-39.png" style="zoom: 80%;" />



#### p-NDFs have sharp features

<img src="../../../assets/img/2022-09-03/fast_16-47-37.png" style="zoom: 80%;" />

#### p-NDF shapes

<img src="../../../assets/img/2022-09-03/fast_16-49-02.png" style="zoom: 80%;" />



#### Recent irend: Wave Optics

<img src="../../../assets/img/2022-09-03/fast_16-50-42.png" style="zoom: 80%;" />

<img src="../../../assets/img/2022-09-03/fast_16-52-56.png" style="zoom: 80%;" />

<img src="../../../assets/img/2022-09-03/fast_16-53-28.png" style="zoom: 80%;" />



#### Detaiied Material under Wave Optics

<img src="../../../assets/img/2022-09-03/fast_16-54-20.png" style="zoom: 80%;" />



#### Detaiied lvlaterial under Wave Optics

<img src="../../../assets/img/2022-09-03/fast_16-55-19.png" style="zoom: 80%;" />

<img src="../../../assets/img/2022-09-03/fast_16-55-52.png" style="zoom: 80%;" />

#### Wave optics

<img src="../../../assets/img/2022-09-03/fast_16-57-01.png" style="zoom: 80%;" />



#### Procedural Appearance

Can we define details without textures?
— Yes! Compute a noise function on the fly.

— 3D noise ->
	internal structure
	if cut or broken

<img src="../../../assets/img/2022-09-03/fast_16-58-17.png" style="zoom: 80%;" />



什么时候用什么时候查。

<img src="../../../assets/img/2022-09-03/fast_16-59-48.png" style="zoom: 80%;" />

— Thresholding
(noise -> binary noise)

```
Example:
if noise(x, y, z) > threshold:
	reflectance = 1
else:
	reflectance = O
```

<img src="../../../assets/img/2022-09-03/fast_17-01-26.png" style="zoom: 80%;" />

* Complex noise functions can be very powerful.

<img src="../../../assets/img/2022-09-03/fast_17-02-20.png" style="zoom: 50%;" />

* Complex noise functions can be very powerful.

<img src="../../../assets/img/2022-09-03/fast_17-03-22.png" style="zoom: 50%;" />

* Complex noise functions can be very powerful.

<img src="../../../assets/img/2022-09-03/fast_17-04-26.png" style="zoom: 50%;" />