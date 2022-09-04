### Cameras-Lenses-and-Light-Fileds

#### Imaging = Synthesis + Capture

<img src="../../../assets/img/2022-09-03/fast_17-11-03.png" style="zoom:50%;" /> <img src="../../../assets/img/2022-09-03/fast_17-11-30.png" style="zoom:50%;" />

合成图像

1. 光栅
2. 光线追踪

捕捉方法成像

1. 照相（现实物品）



#### Whats Happening Inside the Camera?

<img src="../../../assets/img/2022-09-03/fast_17-32-33.png" style="zoom:50%;" />

#### Pinholes & Lenses Form Image on Sensor

<img src="../../../assets/img/2022-09-03/fast_17-33-23.png" style="zoom:50%;" />



#### Shutter Exposes Sensor For Precise Duration

<img src="../../../assets/img/2022-09-03/fast_17-34-53.png" style="zoom:50%;" />

#### Sensor Accumulates Irradiance During Exposure

<img src="../../../assets/img/2022-09-03/fast_17-35-35.png" style="zoom:50%;" />

#### Why Sensors Without Lenses?

Each sensor point would integrate light from all points on the
object, so all pixel values would be similar i.e. the sensor records irradiance

<img src="../../../assets/img/2022-09-03/fast_17-36-32.png" style="zoom:50%;" />

#### Pinhole Image Formation

<img src="../../../assets/img/2022-09-03/fast_17-37-41.png" style="zoom:50%;" />



#### Largest Pinhole Photograph

<img src="../../../assets/img/2022-09-03/fast_17-38-14.png" style="zoom:50%;" />

照片任何地方都是清晰的，不存在虚化



#### Effect of Focal Length on FOV

<img src="../../../assets/img/2022-09-03/fast_17-40-02.png" style="zoom:50%;" />

For a fixed sensor size, decreasing the focal length increases
the field of view.

<img src="../../../assets/img/2022-09-03/fast_17-40-42.png" style="zoom:50%;" />

#### Focal Length v. Field of View

<img src="../../../assets/img/2022-09-03/fast_17-43-19.png" style="zoom:50%;" />

* For historical reasons, it is common to refer to angular field of view by focal length of a lens used on a 35mm-format film (36 x 24mm)
* Examples of focal lengths on 35mm format:
  • 17mm is wide angle 1040
  • 50mm is a "normal" lens 470
  • 200mm is telephoto lens 120
* Careful! When we say current cell phones have approximately 28mm "equivalent" focal length, this uses the above convention.

<img src="../../../assets/img/2022-09-03/fast_17-45-07.png" style="zoom:50%;" />



#### Effect of Sensor Size on FOV

<img src="../../../assets/img/2022-09-03/fast_17-47-04.png" style="zoom:50%;" />

#### Sensor Sizes

<img src="../../../assets/img/2022-09-03/fast_17-48-40.png" style="zoom:50%;" />

#### Maintain FOV on Smaller Sensor?

<img src="../../../assets/img/2022-09-03/fast_17-50-04.png" style="zoom:50%;" />



To maintain FOV, decrease focal length of lens in proportion to width/height of sensor



#### Exposure

* H = T x E

* Exposure = time x irradiance
* Exposure time (T)
  - Controlled by shutter

- Irradiance (E)
  - Power of light falling on a unit area of sensor
  - Controlled by lens aperture and focal length

辐射度量学



#### Exposure Controls in Photography

Aperture size

* Change the f-stop by opening / closing the aperture (if
  camera has iris control)

Shutter speed

* Change the duration the sensor pixels integrate light

ISO gain

* Change the amplification (analog and/or digital) between
  sensor values and digital image values



####  Exposure. Aperture, Shutter, Gain (ISO)

<img src="../../../assets/img/2022-09-03/fast_20-34-17.png" style="zoom:50%;" />



ISO (Gain)
Third variable for exposure
Film: trade sensitivity for grain
Digital: trade sensitivity for noise

* Multiply signal before analog-to-digital conversion
* Linear effect (ISO 200 needs half the light as ISO 100)



#### ISO Gain vs Noise in Canon T2i

<img src="../../../assets/img/2022-09-03/fast_20-37-20.png" style="zoom:50%;" />



#### F-Number (F-Stop): Exposure Levels

Written as FN or F/N. N is the f-number.
Informal understanding: the inverse-diameter of a round aperture

<img src="../../../assets/img/2022-09-03/fast_20-38-21.png" style="zoom:50%;" />



#### Physical Shutter (1/25 Sec Exposure)

<img src="../../../assets/img/2022-09-03/fast_20-39-46.png" style="zoom:50%;" />



#### Side Effect of Shutter Speed

Motion blur: handshake, subject movement
Doubling shutter time doubles motion blur

<img src="../../../assets/img/2022-09-03/fast_20-41-13.png" style="zoom:50%;" />

 

#### Side Effect of Shutter Speed

Note: motion blur is not always bad!
Tip: think about anti-aliasing

<img src="../../../assets/img/2022-09-03/fast_20-43-22.png" style="zoom:50%;" />

Rolling shutter: different parts of photo taken at different times

<img src="../../../assets/img/2022-09-03/fast_20-47-26.png" style="zoom:50%;" />

扭曲，不同时间进来的光

#### Constant Exposure: F-stop vs Shutter Speed

Example: these pairs of aperture and shutter speed
give equivalent exposure

<img src="../../../assets/img/2022-09-03/fast_20-48-35.png" style="zoom:50%;" />

If the exposure is too bright/dark, may need to adjust f-stop and/or shutter up/down.

* Photographers must trade off depth of field (?) and motion blur for moving subjects



#### High-Speed Photography

Normal exposure = extremely fast shutter speed x (large aperture and/or high ISO)

<img src="../../../assets/img/2022-09-03/fast_20-50-28.png" style="zoom:50%;" />



#### High-Speed Photography

<img src="../../../assets/img/2022-09-03/fast_20-51-08.png" style="zoom:50%;" />

#### Long-exposure Photography

<img src="../../../assets/img/2022-09-03/fast_20-51-50.png" style="zoom:50%;" />

<img src="../../../assets/img/2022-09-03/fast_20-52-49.png" style="zoom:50%;" />

#### Thin Lens Approximation

Real Lens Designs Are Highly Complex

<img src="../../../assets/img/2022-09-03/fast_20-53-52.png" style="zoom:50%;" />

#### Real Lens Elements Are Not Ideal — Aberrations

<img src="../../../assets/img/2022-09-03/fast_20-55-07.png" style="zoom:50%;" />

Real plano-convex lens (spherical surface shape). Lens does not converge rays to a point anywhere.

 

#### Ideal Thin Lens — Focal Point

<img src="../../../assets/img/2022-09-03/fast_21-45-02.png" style="zoom:50%;" />

(1) All parallel rays entering a lens pass through its focal point.

(2) All rays through a focal point will be in parallel after passing the lens.

(3) Focal length can be arbitrarily changed (in reality, yes!).

棱镜组可以改变焦距

#### The Thin Lens Equation

<img src="../../../assets/img/2022-09-03/fast_21-47-04.png" style="zoom:50%;" />

#### Gauss' Ray Tracing Construction

<img src="../../../assets/img/2022-09-03/fast_21-49-25.png" style="zoom:50%;" />

$\frac{h_o}{z_o-f} = \frac{h_i}{f}$           $\frac{h_o}{f} = \frac{h_i}{z_i-f}$



#### Gauss/ Ray Tracing Construction

<img src="../../../assets/img/2022-09-03/fast_21-52-38.png" style="zoom:50%;" />

Gaussian Thin Lens Equation



#### Computing Circle of Confusion (CoC) Size

<img src="../../../assets/img/2022-09-03/fast_21-54-20.png" style="zoom:50%;" />

Circle of confusion is proportional to the size of the aperture

<img src="../../../assets/img/2022-09-03/fast_21-55-05.png" style="zoom:50%;" />

#### CoC vs. Aperture Size

<img src="../../../assets/img/2022-09-03/fast_21-57-55.png" style="zoom:50%;" />



#### Revisiting F-Number (a.k.a. F-stop)

* Formal definition: The f-number of a lens is defined as
  the focal length divided by the diameter of the aperture
* Common f-stops on real lenses:
  1.4, 2, 2.8, 4.0, 5.6, 8, 11, 16, 22, 32
*  An f-stop of 2 is sometimes written f/2, reflecting the fact that the absolute aperture diameter (A) can be computed by dividing focal length (f) by the relative aperture (N).



#### Example F-stop Calculations

<img src="../../../assets/img/2022-09-03/fast_22-00-49.png" style="zoom:50%;" />



#### Size of CoC is Inversely Proportional to F-stop

<img src="../../../assets/img/2022-09-03/fast_22-01-37.png" style="zoom:50%;" />

<img src="../../../assets/img/2022-09-03/fast_22-02-12.png" style="zoom:50%;" />

#### Ray Tracing Ideal Thin Lenses



#### Examples of Renderings with Lens Focus

<img src="../../../assets/img/2022-09-03/fast_22-03-22.png" style="zoom:50%;" />



#### Ray Tiacing for Defocus Blur (Thin Lens)

<img src="../../../assets/img/2022-09-03/fast_22-03-58.png" style="zoom:50%;" />



(One possible) Setup:

* Choose sensor size, lens focal length and aperture size
* Choose depth of subject of interest $z_o$
  * Calculate corresponding depth of sensor $z_i$ from thin lens equation (focusing)

Rendering:

* For each pixel x' on the sensor (actually, film (胶片))

* Sample random points x" on lens plane

* You know the ray passing through the lens will hit x"' (using the thin lens formula)

  estimate radiance on ray x" -> x"'

  

#### Depth of Field

<img src="../../../assets/img/2022-09-03/fast_22-08-03.png" style="zoom:50%;" />

Set circle of confusion as the maximum permissible blur spot on the image plane that will appear sharp under final viewing conditions



#### Circle of Confusion for Depth of Field

i.e. depth range in a scene where the corresponding CoC is considered small enough

<img src="../../../assets/img/2022-09-03/fast_22-09-59.png" style="zoom:50%;" />

#### Depth of Field (FYI)

<img src="../../../assets/img/2022-09-03/fast_22-11-28.png" style="zoom:50%;" /> <img src="../../../assets/img/2022-09-03/fast_22-12-26.png" style="zoom:50%;" /> 

$DOF = D_F - D_N$

<img src="../../../assets/img/2022-09-03/fast_22-13-58.png" style="zoom:50%;" />



