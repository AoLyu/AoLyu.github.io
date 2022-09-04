### Raytracing-3

#### Irradiance

Definition: The irradiance is the power per (perpendicular/ projected) unit area incident on a surface point.

必须垂直物体表面

<img src="../../../assets/img/2022-08-29/fast_01-24-19.png" style="zoom:67%;" />

#### Why Do We Have Seasons?

<img src="../../../assets/img/2022-08-29/fast_01-26-10.png" style="zoom:67%;" />

Earth's axis of rotation: —23.5° off axis

<img src="../../../assets/img/2022-08-29/fast_01-27-34.png" style="zoom:67%;" />



Radiance
Radiance is the fundamental field quantity that describes the distribution of light in an environment

* Radiance is the quantity associated with a ray
* Rendering is all about computing radiance

<img src="../../../assets/img/2022-08-29/fast_01-28-39.png" style="zoom:67%;" />

Light Traveling Along A Ray





Definition: The radiance (luminance) is the power emitted, reflected, transmitted or received by a surface, per unit solid angle, per projected unit area.

<img src="../../../assets/img/2022-08-29/fast_01-29-44.png" style="zoom:67%;" />



Recall

* Irradiance: power per projected unit area
*  Intensity: power per solid angle

So

* Radiance: Irradiance per solid angle
* Radiance: Intensity per projected unit area



#### incident Radiance

Incident radiance is the irradiance per unit solid angle arriving at the surface.

<img src="../../../assets/img/2022-08-29/fast_01-32-27.png" style="zoom:67%;" />

i.e. it is the light arriving at the surface along a given ray point on surface and incident direction).



#### Exiting Radiance

Exiting surface radiance is the intensity per unit projected
area leaving the surface.

<img src="../../../assets/img/2022-08-29/fast_01-34-16.png" style="zoom:67%;" />

e.g. for an area light it is the light emitted along a given ray point on surface and exit direction).



#### Irradiance vs. Radiance

Irradiance: total power received by area dA
Radiance: power received by area dA from "direction" dω

<img src="../../../assets/img/2022-08-29/fast_01-36-08.png" style="zoom:67%;" />



### Bidirectional Reflectance Distribution Function (BRDF)

Radiance from direction $ω_i$ turns into the power E that dA receives
Then power E will become the radiance to any other direction $ω_o$

<img src="../../../assets/img/2022-08-29/fast_01-38-29.png" style="zoom:67%;" />



#### BRDF

The Bidirectional Reflectance Distribution Function (BRDF)
represents how much light is reflected into each outgoing direction $w_r$ from each incoming direction

<img src="../../../assets/img/2022-08-29/fast_01-41-10.png" style="zoom:67%;" />

<img src="../../../assets/img/2022-08-29/fast_01-41-21.png" style="zoom:67%;" />



#### The Reflection Equation

<img src="../../../assets/img/2022-08-29/fast_01-42-43.png" style="zoom:67%;" />

<img src="../../../assets/img/2022-08-29/fast_01-42-52.png" style="zoom:67%;" />

#### Challenge: Recursive Equation

<img src="../../../assets/img/2022-08-29/fast_01-44-26.png" style="zoom:67%;" />

But incoming radiance depends on reflected radiance (at another point in the scene)



#### The Rendering Equation

Re-write the reflection equation:

<img src="../../../assets/img/2022-08-29/fast_01-45-17.png" style="zoom:67%;" />

by adding an Emission term to make it general!
The Rendering Equation

<img src="../../../assets/img/2022-08-29/fast_01-45-50.png" style="zoom:67%;" />

Note: now, we assume that all directions are pointing outwards!



#### Understanding the rendering equation

#### Reflection Equation

<img src="../../../assets/img/2022-08-29/fast_01-49-44.png" style="zoom:67%;" />

<img src="../../../assets/img/2022-08-29/fast_01-50-50.png" style="zoom:67%;" />

<img src="../../../assets/img/2022-08-29/fast_01-52-33.png" style="zoom:67%;" />

<img src="../../../assets/img/2022-08-29/fast_01-53-27.png" style="zoom:67%;" />



#### Rendering Equation as Integral Equation

<img src="../../../assets/img/2022-08-29/fast_01-54-44.png" style="zoom:67%;" />



#### Linear Operator Equation

<img src="../../../assets/img/2022-08-29/fast_01-55-34.png" style="zoom:67%;" />

Can be discretized to a simple matrix equation [or system of simultaneous linear equations] (L, E are vectors, K is the light transport matrix)

#### Ray Tracing and extensions

• General class numerical Monte Carlo methods
• Approximate set of all paths of light in scene

<img src="../../../assets/img/2022-08-29/fast_01-56-34.png" style="zoom:67%;" />

<img src="../../../assets/img/2022-08-29/fast_01-57-42.png" style="zoom:67%;" />

K是反射操作符

#### Shading in Rasterization

<img src="../../../assets/img/2022-08-29/fast_02-00-12.png" style="zoom:67%;" />

<img src="../../../assets/img/2022-08-29/fast_02-00-36.png" style="zoom:67%;" />

<img src="../../../assets/img/2022-08-29/fast_02-01-05.png" style="zoom:67%;" />

<img src="../../../assets/img/2022-08-29/fast_02-01-58.png" style="zoom:67%;" />



#### Probability Review

##### Randono Variables

$X$  random variable. Represents a distribution of potential values

$X~p(x)$  probability density function (PDF). Describes relative
probability of a random process choosing value $x$



Example: uniform PDF: all values over a domain are equally likely

e.g. A six-sided die
$X$ takes on values 1, 2, 3, 4, 5, 6

$p(1) = p(2) = p(3) = p(4) = p(5) = p(6)$

<img src="../../../assets/img/2022-08-29/fast_02-06-42.png" style="zoom:67%;" />

#### Probabilities

$n$ discrete values $x_i$

Width probability $p_i$

Requirements of a probability distribution:

<img src="../../../assets/img/2022-08-29/fast_02-08-25.png" style="zoom: 50%;" />                            <img src="../../../assets/img/2022-08-29/fast_02-09-05.png" style="zoom:67%;" />

#### Expected Value of a Random Variable

The average value that one obtains if repeatedly drawing samples from the random distribution.

$X$ drawn from distribution withn 

$n$ discrete values $x_i$
with probabilities $p_i$

Expected value of X:     <img src="../../../assets/img/2022-08-29/fast_02-11-22.png" style="zoom: 50%;" />

Die example:  <img src="../../../assets/img/2022-08-29/fast_02-12-14.png" style="zoom: 50%;" />=  (1 +2+3+4+5 + 6)/6 = 3.5

#### Continuous Case: Probability Distribution Function (PDF)

$X$ ~ $p(x)$                      <img src="../../../assets/img/2022-08-29/fast_02-13-41.png" style="zoom: 50%;" />

A random variable X that can take any of a continuous set of values, where the relative probability of a particular value is given by a continuous probability density function p(x).



Conditions on p(x):            <img src="../../../assets/img/2022-08-29/fast_02-17-15.png" style="zoom: 50%;" />
Expected value of X:          <img src="../../../assets/img/2022-08-29/fast_02-17-45.png" style="zoom: 50%;" />



#### Function of a Random Variable

A function Y of a random variable X is also a random variable:

$X$~$p(x)$

$Y = f(X)$

Expected value of a function of a random variable:

<img src="../../../assets/img/2022-08-29/fast_02-21-03.png" style="zoom: 50%;" />

