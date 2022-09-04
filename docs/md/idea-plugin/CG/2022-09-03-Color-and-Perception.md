### Color and Perception

#### What do we see?

3D world

![](F:\code_reference\AoLyu.github.io\docs\assets\img\2022-09-03\fast_22-38-09.png)

2D image

![](../../../assets/img/2022-09-03/fast_22-38-59.png)

#### The plenoptic Function (全光函数)

![](../../../assets/img/2022-09-03/fast_22-40-00.png)

Q: What is the set of all things that we can ever see?
A: The Plenoptic Function (Adelson & Bergen)

Let's start with a stationary person and try to rameterize everythinq that he can see...



P(θ，φ，λ，t)

is intensity of light

* Seen from a single view point
*  Over time
*  As a function of wave length

![](../../../assets/img/2022-09-03/fast_22-42-16.png)

![](../../../assets/img/2022-09-03/fast_22-42-36.png)

* Can reconstruct every possible view, at every moment, from every position, at every wavelength
*  Contains every photograph, every movie, everything that anyone has ever seen! it completely captures our visual reality! Not bad for a function...

#### Sampling Plenoptic Function (top view)

![](../../../assets/img/2022-09-03/fast_22-44-08.png)

Just lookup -- Quicktime VR

#### Ray

Let's not worry about time and color:

![](../../../assets/img/2022-09-03/fast_22-44-08.png)

![](../../../assets/img/2022-09-03/fast_22-45-24.png)

#### 5D

* 3D position
* 2D direction

#### Ray Rouse

#### Infinite line

• Assume light is constant (vacuum)

![](../../../assets/img/2022-09-03/fast_22-47-00.png)

#### 4D

* 2D direction
*  2D position
* non-dispersive medium

#### Only need plenoptic surface

![](../../../assets/img/2022-09-03/fast_22-48-42.png)

Figure 1: The surface of a cube holds all the radiance information due to the enclosed object.



#### Synthesizing novel views

![](../../../assets/img/2022-09-03/fast_22-51-06.png)



#### Lumigraph / Lightfield

Outside convex space

![](../../../assets/img/2022-09-03/fast_22-52-44.png)

#### Lumigraph - Organization

2D position
2D direction

![](../../../assets/img/2022-09-03/fast_22-54-18.png)

2 plane parameterization

2D position
2D position

![](../../../assets/img/2022-09-03/fast_22-56-14.png)

光场参数化

![](../../../assets/img/2022-09-03/fast_23-00-29.png)

Hold s,t constant
Let u,v vary
An image

![](../../../assets/img/2022-09-03/fast_23-02-07.png)

#### Lumigraph / Lightfield

![](../../../assets/img/2022-09-03/fast_23-03-14.png)

#### Stanford camera array

<img src="../../../assets/img/2022-09-03/fast_23-05-33.png" style="zoom:50%;" />

#### Interal Imaging ("Fly's Eye" Lenslets)

![](../../../assets/img/2022-09-03/fast_23-07-19.png)

分光（红绿蓝）

Spatially-multiplexed light field capture using lenslets:

* Impose fixed trade-off between spatial and angular resolution

#### The Lytro Light Field Camera

Lytro: founded by Prof. Ren Ng (UC Berkeley)
Microlens design
Most significant function

* Computational Refocusing
  (virtually changing focal length & aperture size, etc. after taking the photo)

![](../../../assets/img/2022-09-03/fast_23-18-06.png)

可以后期聚焦

#### Light Field Camera

Understanding

* Each pixel (irradiance) is now stored as a block of pixels (radiance)
* A close-up view of a picture taken

<img src="../../../assets/img/2022-09-03/fast_23-21-14.png" style="zoom: 50%;" /> <img src="../../../assets/img/2022-09-03/fast_23-20-48.png" style="zoom: 50%;" />

#### Light Field Camera

How to get a "regular" photo from the light field photo?

* A simple case — always choose the pixel at the bottom of each block
* Then the central ones & the top ones
* Essentially "moving the camera around"

Computational / digital refocusing

* Same idea: visually changing focal length, picking the refocused ray directions accordingly

<img src="../../../assets/img/2022-09-03/fast_23-24-41.png" style="zoom:50%;" />

In all, all these functionalities are available because

* The light field contains everything Any problems to light field cameras?
* Insufficient spatial resolution (same film used for both spatial and directional information)

* High cost   (intricate designation of microlenses)

* Computer Graphics is about trade-offs



####  The Fundamental Components of Light

![](../../../assets/img/2022-09-03/fast_23-30-42.png)

* Newton showed sunlight can be subdivided into a rainbow with a prism 
* Resulting light cannot be further subdivided with a second prism

#### The Visible Spectrum of Light

Electromagnetic radiation
• Oscillations of different frequencies (wavelengths)

![](../../../assets/img/2022-09-03/fast_23-32-25.png)

#### Spectra; Power Distribution (SPD) （谱功率密度）

Salient property in measuring light

* The amount of light present at each wavelength
*  Units:
  * radiometric units / nanometer (e.g. watts / nm)
  * Can also be unit-less
* Often use "relative units" scaled to maximum wavelength for comparison across wavelengths when absolute units are not important

#### Daylight Spectral Power Distributions Vary

![](../../../assets/img/2022-09-03/fast_23-34-49.png)

#### Spectra; Power Distribution of Light Sources

Describes distribution of energy by wavelength

![](../../../assets/img/2022-09-03/fast_23-35-47.png)

#### Linearity of Spectral Power Distributions

![](../../../assets/img/2022-09-03/fast_23-36-46.png)

#### What is Color?

* Color is a phenomenon of human perception; it is not a
  universal property of light
* Different wavelengths of light are not "colors"

#### Biological Basis of Color

Anatorny of The Human Eye

![](../../../assets/img/2022-09-03/fast_23-38-32.png)



#### Retinal I hotoreceptor Cells: Rods and Cones

Rods are primary receptors in very
low light ("scotopic" conditions),
e.g. dim moonlight

* —120 million rods in eye
* Perceive only shades of gray, no color

Cones are primary receptors in typical light levels ("photopic")

* —6-7 million cones in eye
* Three types of cones, each with different spectral sensitivity
* Provide sensation of color

![](../../../assets/img/2022-09-03/fast_23-40-22.png)

#### Spectra; Response of Human Cone Cells

Three types of cone cells: S, M, and L (corresponding to peak
response at short, medium, and long wavelengths)

![]()![fast_23-41-15](../../../assets/img/2022-09-03/fast_23-41-15.png)

#### Fraction of Three Cone Cell Types Varies Widely

![](../../../assets/img/2022-09-03/fast_23-42-26.png)

不同人，三种细胞分布不一样

Distribution of cone cells at edge of fovea in 12 different humans with al color vision. Note high variability of percentage of different cone pes. (false color image)

#### Spectra; Response of Human Cone Cells

Now we have three detectors (S, M, L cone cells), each with a different spectral response curve

![](../../../assets/img/2022-09-03/fast_23-44-14.png)

不同人，这三个数不一样

#### The Human Visual System

Human eye does not measure and brain does not receive information about each wavelength of light
• Rather, the eye "sees" only three response values (S, M, L), and this is only info available to brain

![](../../../assets/img/2022-09-03/fast_23-45-46.png)

#### Metamerism （同色异谱）

Metamers
Metamers are two different spectra (00-dim) that project to the
same (S,M,L) (3-dim) response.

* These will appear to have the same color to a human 

The existence of metamers is critical to color reproduction

* Don't have to reproduce the full spectrum of a real world
  scene

* Example: A metamer can reproduce the perceived color of a real-world scene on a display with pixels of only three
  colors

#### Metamerism

The theory behind color matching

![](../../../assets/img/2022-09-03/fast_23-48-33.png)

#### Color Reproduction / Matching

Additive Color

* Given a set of primary lights, each with its own spectral distribution (e.g. R,G,B display pixels):

![](../../../assets/img/2022-09-03/fast_23-49-43.png)

* Adjust the brightness of these lights and add them together:

![](../../../assets/img/2022-09-03/fast_23-50-17.png)

<img src="../../../assets/img/2022-09-03/fast_23-50-50.png" style="zoom:50%;" />

* The color is now described by the
  scalar values:

  R,G,B

#### Additive Color Matching Experiment

![](../../../assets/img/2022-09-03/fast_23-51-59.png)



#### Example Experiment1

![](../../../assets/img/2022-09-03/fast_23-52-38.png)

#### Experiment 2

![](../../../assets/img/2022-09-03/fast_23-53-35.png)

#### CIE RGB Color Matching Experiment

Same setup as additive color matching before, but primaries are monochromatic light (single wavelength)

![](../../../assets/img/2022-09-03/fast_23-54-38.png)

The test light is also a monochromatic light

![](../../../assets/img/2022-09-03/fast_23-55-18.png)

#### CIE RGB Color Matching Functions

Graph plots how much of each CIE RGB primary light must be combined to match a monochromatic light of wavelength given on x-axis

![](../../../assets/img/2022-09-03/fast_23-56-13.png)

#### Coior• Reproduction with Matching Functions

For any spectrum s, the perceived color is matched by the following formulas for scaling the CIE RGB primaries

![](../../../assets/img/2022-09-03/fast_23-56-59.png)

#### Standard Color Spaces

Standardized RGB (sRGB)

* makes a particular monitor RGB standard
* other color devices simulate that monitor by calibration
* widely adopted today
* gamut (?) is limited



#### A Universal Color Space: CIE XYZ

Imaginary set of standard color primaries X, Y, Z

* Primary colors with these matching functions do not exist
* Y is luminance (brightness regardless of color)

Designed such that

* Matching functions are strictly positive
* Span all observable colors

![](../../../assets/img/2022-09-04/fast_00-00-14.png)

####  Separating Luminance, Chromaticity

![](../../../assets/img/2022-09-04/fast_00-04-01.png)

#### CIE Chromaticity Diagram

![](../../../assets/img/2022-09-04/fast_00-05-50.png)

#### Gamut

Gamut is the set of chromaticities generated by a set of color
primaries

Different color spaces represent different ranges of colors

So they have different gamuts, i.e.
they cover different regions on the chromaticity diagram

![](../../../assets/img/2022-09-04/fast_00-06-48.png)

sRGB只表示了其中一个三角形

#### Perceptually Organized Color Spaces

#### HSV Color Space (Hue-Saturation-Value)

Axes correspond to artistic characteristics of color
Widely used in a "color picker"

![](../../../assets/img/2022-09-04/fast_00-08-04.png)

#### Perceptual Dimensions of Color

Hue

* the "kind" of color, regardless of attributes
* colorimetric correlate: dominant wavelength
* artist's correlate: the chosen pigment color

Saturation (t@$DE)

* the "colorfulness"
* colorimetric correlate: purity
* artist's correlate: fraction of paint from the colored tube

Lightness (or value) (ÄE)

* the overall amount of light
* colorimetric correlate: luminance
* artist's correlate: tints are lighter, shades are darker

CIELAB Space (AKA L\*a\*b)
A commonly used color space that strives for perceptual
uniformity

* L* is lightness (brightness)
* • a* and b* are color-opponent pairs
  * a* is red-green
  * b* is blue-yellow

![](../../../assets/img/2022-09-04/fast_00-11-27.png)

#### Opponent Color Theory 互补色

There's a good neurological basis for the color space dimensions in CIE LAB

* the brain seems to encode color early on using three axes:
  * white — black, redF green, yellow — blue
* the white — black axis is lightness; the others determine hue and saturation

#### Opponent Color Theory

* one piece of evidence: you can have a light green, a dark green, a yellow-green, or a blue-green, but you can't have a reddish green (just doesn't make sense)
  * thus red is the opponent to green
* another piece of evidence: afterimages (following slides)

<img src="../../../assets/img/2022-09-04/fast_00-15-23.png" style="zoom: 33%;" /> <img src="../../../assets/img/2022-09-04/fast_00-15-54.png" style="zoom: 33%;" />

盯着第一幅图看久后看第二幅图会变绿

#### Everything is Relative

![](../../../assets/img/2022-09-04/fast_00-17-54.png)

A 和 B 颜色是一样的

![](../../../assets/img/2022-09-04/fast_00-19-12.png)

#### Everything is Relative

![](../../../assets/img/2022-09-04/fast_00-19-37.png)

#### CMYK: Subtractive Color Space

Subtractive color model

* The more you mix,the darker it will be Cyan, Magenta, Yellow, and Key Widely used in printing

![](../../../assets/img/2022-09-04/fast_00-20-58.png)

Question:

* If mixing C, M and Y gives K, why do you need K?

![](../../../assets/img/2022-09-04/fast_00-21-14.png)

打印墨水，为什么要黑色？ 墨水要成本，混合浪费墨水



