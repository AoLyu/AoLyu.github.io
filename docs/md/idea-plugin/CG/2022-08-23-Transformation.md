#### Transformation 

####  Why Transformation?

 ![](../../../assets/img/2022-08-23/fast_00-25-41.png)

Viewing: (3D to 2D) projection

#### Scale Matrix

![](../../../assets/img/2022-08-23/fast_00-29-28.png)

 <img src="../../../assets/img/2022-08-23/fast_00-30-27.png" style="zoom:50%;" />

<img src="../../../assets/img/2022-08-23/fast_00-32-19.png" style="zoom:50%;" />

![](../../../assets/img/2022-08-23/fast_00-40-25.png)

#### Scale (Non-Uniform)

![](../../../assets/img/2022-08-23/fast_00-40-25.png)

#### Reflection Matrix

![](F:\code_reference\AoLyu.github.io\docs\assets\img\2022-08-23\fast_00-45-12.png)

####  Shear Matrix

![](F:\code_reference\AoLyu.github.io\docs\assets\img\2022-08-23\fast_00-54-04.png)

 ![](F:\code_reference\AoLyu.github.io\docs\assets\img\2022-08-23\fast_00-56-00.png)

![](F:\code_reference\AoLyu.github.io\docs\assets\img\2022-08-23\fast_01-05-46.png)

#### Linear Transforms = Matrics

<img src="F:\code_reference\AoLyu.github.io\docs\assets\img\2022-08-23\fast_01-08-22.png" style="zoom:50%;" />

#### Transiation

<img src="F:\code_reference\AoLyu.github.io\docs\assets\img\2022-08-23\fast_01-11-39.png" style="zoom:50%;" />

#### Why Homogeneous Coordinates

* Translation cannot be represented in matrix form

<img src="F:\code_reference\AoLyu.github.io\docs\assets\img\2022-08-23\fast_01-14-10.png" style="zoom:50%;" />

(So,translation is Not linear transform!)

* But we don‘t want translation to be a special case
* ls there a unified Way to represent all transformations?
  (and what's the cost?)

#### Solution:Homogenous Coordinates

Add a third coordinate ( w-coordinate )

<img src="F:\code_reference\AoLyu.github.io\docs\assets\img\2022-08-23\fast_01-21-08.png" style="zoom:50%;" />

#### Matrix representation Of translations

<img src="F:\code_reference\AoLyu.github.io\docs\assets\img\2022-08-23\fast_01-21-56.png" style="zoom:50%;" />

#### Valid operation if w-coordinate Of result is 1 or 0

* vector+vector=vector
* point - point=vector
* point + vector = point
* point + point = ??

#### ln homogeneous coordinate:

<img src="F:\code_reference\AoLyu.github.io\docs\assets\img\2022-08-23\fast_01-26-46.png" style="zoom:50%;" />

#### Affine Transformations

##### Affine map = linear map + translation

<img src="F:\code_reference\AoLyu.github.io\docs\assets\img\2022-08-23\fast_01-30-18.png" style="zoom:50%;" />

##### Using homogenous coordinates:

<img src="F:\code_reference\AoLyu.github.io\docs\assets\img\2022-08-23\fast_01-30-37.png" style="zoom:50%;" />

#### 2D Transformation

<img src="F:\code_reference\AoLyu.github.io\docs\assets\img\2022-08-23\fast_01-31-47.png" style="zoom:50%;" />

#### Inverse Transform

$$M^{-1}$$

$$M^{-1}$$is the inverse Of transform M in both a matrix and geometric sense

<img src="F:\code_reference\AoLyu.github.io\docs\assets\img\2022-08-23\fast_01-35-43.png" style="zoom:50%;" />



#### Transiate then Rotate

 <img src="F:\code_reference\AoLyu.github.io\docs\assets\img\2022-08-23\fast_01-39-39.png" style="zoom:50%;" />

#### TransformOrdering Matters!

#### Matrix multiplication is not commutative

 <img src="F:\code_reference\AoLyu.github.io\docs\assets\img\2022-08-23\fast_01-41-14.png" style="zoom:50%;" />

#### Note that matrices are applied right to left.

<img src="F:\code_reference\AoLyu.github.io\docs\assets\img\2022-08-23\fast_01-41-27.png" style="zoom:50%;" />

#### Composing  Transforms

Sequenceofaffinetransforms$A_{1}$,$A_{2}$,$A_{3}$,…

* Composebymatrixmultiplication
  * VeryimportantfOrperformance!

<img src="F:\code_reference\AoLyu.github.io\docs\assets\img\2022-08-23\fast_01-45-47.png" style="zoom:50%;" />

#### Decomposing Complex Transforms

How to  rotate around a given point c?

1. Translate center to origin

2. Rotate

3. Translate back

<img src="F:\code_reference\AoLyu.github.io\docs\assets\img\2022-08-23\fast_01-49-37.png" style="zoom:50%;" />

#### Matrix representation?

<img src="F:\code_reference\AoLyu.github.io\docs\assets\img\2022-08-23\fast_01-50-15.png" style="zoom:50%;" />

#### 3D Transformations

Use homogeneous coordinates again:

<img src="F:\code_reference\AoLyu.github.io\docs\assets\img\2022-08-23\fast_01-53-42.png" style="zoom:50%;" />

<img src="F:\code_reference\AoLyu.github.io\docs\assets\img\2022-08-23\fast_01-54-46.png" style="zoom:50%;" />



#### 3D Transformations

Use 4×4 matrices for affine transformations

<img src="F:\code_reference\AoLyu.github.io\docs\assets\img\2022-08-23\fast_01-56-39.png" style="zoom:50%;" />





