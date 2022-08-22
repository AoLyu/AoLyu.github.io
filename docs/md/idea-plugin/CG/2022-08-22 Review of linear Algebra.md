### Review of Linear Algebra

#### Graphics' Dependencies

* ##### Basicmathematics

  * lnearalgebra, calculus, statistics

* ##### Basic physics

  * Optics, Mechanics

* ##### MiSC

  * Signal processing
  * Numerical analysis

* ##### And a bit of aesthetics



#### An Example of Rotation

![](../../../assets/img/2022-08-22/fast_22-11-06.png)

#### Vectors

![](../../../assets/img/2022-08-22/fast_22-12-30.png)

* Usually written as $$\vec{a}$$ or in bold **a**
* Or using start and end pants $$\overrightarrow{AB} = B-A$$
* Direction and length
* No absolute starting position
* Magnitude (length) of a vector written as $$\begin{Vmatrix}\vec{a}\end{Vmatrix}$$
* Unit vector
  - A vector with magnitude of 1
  - Finding the unit vector of a vector (normalization):$$\widehat{a} = \vec{a}/\begin{Vmatrix}\vec{a}\end{Vmatrix}$$
  - Used to represent directions

#### Vector Addition

![](../../../assets/img/2022-08-22/fast_22-23-09.png)

* GeometricalIy: Parallelogram law & Triangle law
* Algebraically: Simply add coordinates



#### Cartesian Coordinates

![](../../../assets/img/2022-08-22/fast_22-24-53.png)

* $$X$$ and $Y$ can be any (usually orthogonal unit) vectors

  $$A = \begin{pmatrix} x \\y \end{pmatrix}$$    $$A^T = \begin{pmatrix} x,y \end{pmatrix}$$   $$\begin{Vmatrix}A\end{Vmatrix} = \sqrt{x^2+y^2}$$

  

### Vector MuItipIication

* Dot product
* Cross product
* Orthonormal bases and coordinate frames



#### Dot  (scalar) Product

<img src="../../../assets/img/2022-08-22/fast_22-38-20.png" style="zoom:50%;" />

$$\overrightarrow{a} \cdot \overrightarrow{b} = \begin{Vmatrix}\overrightarrow{a}\end{Vmatrix}\begin{Vmatrix}\overrightarrow{b}\end{Vmatrix}\cos\theta$$

<img src="../../../assets/img/2022-08-22/fast_22-44-36.png" style="zoom: 50%;" />

* For unit vectors

  <img src="../../../assets/img/2022-08-22/fast_22-45-22.png" style="zoom: 50%;" />

* Properties

  <img src="../../../assets/img/2022-08-22/fast_22-47-26.png" style="zoom:50%;" />

#### Dot Product in Cartesian Coordinates

* Component-wise multiplication, then adding up

  * in 2D

    <img src="../../../assets/img/2022-08-22/fast_22-49-11.png" style="zoom:50%;" />

  * In 3D

    <img src="../../../assets/img/2022-08-22/fast_22-50-02.png" style="zoom:50%;" />

#### Dot Product in Graphics

* Find angle between two vectors
  (e.g. cosine of angle between light source and surface)
* Finding projection of one vector on another

#### Dot Product for Projection

<img src="../../../assets/img/2022-08-22/fast_22-52-45.png" />



#### Dot Product in Graphics

* Measure how close two directions are
* Decompose a vector
* Determine forward/ backward

<img src="../../../assets/img/2022-08-22/fast_22-54-51.png" style="zoom:50%;" />

<img src="../../../assets/img/2022-08-22/fast_22-55-32.png" style="zoom:50%;" />

方向是否一致

#### Cross (vector) Product

<img src="../../../assets/img/2022-08-22/fast_22-58-41.png" style="zoom:50%;" />

* Cross product is orthogonal to two initial vectors
* Direction determined by right-hand rule
* UsefuI in constructing coordinate systems (later)



#### Cross product: Properties

<img src="../../../assets/img/2022-08-22/fast_22-59-39.png"  />

opengl 是左手坐标系

#### Cross Product: Cartesian FormuIa?

<img src="../../../assets/img/2022-08-22/fast_23-01-23.png" style="zoom:50%;" />

* Later in this lecture

<img src="../../../assets/img/2022-08-22/fast_23-02-33.png" style="zoom:50%;" />

#### Cross Product in Graphics

* Determine left / right
* Determine inside / outside

<img src="../../../assets/img/2022-08-22/fast_23-03-59.png" style="zoom:50%;" />

<img src="../../../assets/img/2022-08-22/fast_23-04-42.png" style="zoom:50%;" />

#### Orthonormal Bases / Coordinate Frames

* lmportant for representing points, positions, locations
* often, many sets of coordinate systems
  - GIobaI, local，world, model, parts of model (head,
    hands,...）
* CriticaI issue is transforming between these systems/
  bases
  - Atopic for next week

#### Orthonormal Coordinate Frames

* Anyset of 3 vectors (In 3D) that

<img src="../../../assets/img/2022-08-22/fast_23-11-17.png" style="zoom:50%;" />



### Matrices

* Magical 2D arrays that haunt in every CS course
* ln Graphics, pervasively used to represent transformations 
  * Translation，rotation，shear, scale
    (more details in the next lecture)



#### What is a matrix

* Array Of numbers (m×n=m rows，n columns)

  <img src="../../../assets/img/2022-08-22/fast_23-15-02.png" style="zoom:50%;" />

* Addition and multiplication by a scalar are trivial:
  element by element

#### Matrix-Matrix MuItipIication

* \# (number of)columns in A must =\# rows in B
  (MxN)(NxP)=(MxP)

<img src="../../../assets/img/2022-08-22/fast_23-17-51.png" style="zoom:50%;" />

* EIement(i，j) in the product is
  the dot product of row **i** from A and column **j** from B

* Properties
  - **Non-commutative**
    (**AB** and **BA** are different in general)
  - Associative and distributive （结合律和分配率）
    * (AB)C=A(BC)
    * A(B+C)=AB+AC
    * (A+B)C=AC+BC

* Treat vector as a column matrix (m x 1)
* Key for transforming points (next lecture)

* OfficiaI spoiler:2D reflection about y-axis

<img src="../../../assets/img/2022-08-22/fast_23-22-51.png" style="zoom:50%;" />

#### Transpose Of a Matrix

* Switch rows and columns (ij > ji)

<img src="../../../assets/img/2022-08-22/fast_23-22-51.png" style="zoom:50%;" />

* Property

  <img src="../../../assets/img/2022-08-22/fast_23-56-08.png" style="zoom:50%;" />

#### ldentity Matrix and lnverses

<img src="../../../assets/img/2022-08-22/fast_23-58-55.png" style="zoom:50%;" />



#### Vector multiplication in Matrix form

* Dot product?

  <img src="../../../assets/img/2022-08-23/fast_00-02-03.png" style="zoom:50%;" />

* Cross product?

  ![](../../../assets/img/2022-08-23/fast_00-03-16.png)

  

















