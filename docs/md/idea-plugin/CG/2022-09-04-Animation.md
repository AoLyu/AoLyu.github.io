### Animation

"Bring things to life"

* Communication tool
* Aesthetic issues often dominate technical issues

An extension of modeling

* Represent scene models as a function of time

Output: sequence of images that when viewed sequentially provide a sense of motion

* Film: 24 frames per second
* Video (in general): 30 fps
* Virtual reality: 90 fps



#### Keyframe Animation

![](../../../assets/img/2022-09-05/fast_19-51-54.png)



Animator (e.g. lead animator) creates keyframes
Assistant (person or computer) creates in-between frames



#### Keyframe Interpolation

Think of each frame as a vector of parameter values

![](../../../assets/img/2022-09-05/fast_19-54-18.png)

#### Keyframe Interpolation of Each Parameter

Linear interpolation usually not good enough

![](../../../assets/img/2022-09-05/fast_19-54-48.png)

Recall splines for smooth / controllable interpolation

![](../../../assets/img/2022-09-05/fast_19-55-28.png)

#### Physical Simulation

Newton's Law

$F =ma$

#### Pnysiealiy Based Animation

Generate motion of objects using numerical simulation

![](../../../assets/img/2022-09-05/fast_19-57-05.png)

Example: Cloth Simulation

![](../../../assets/img/2022-09-05/fast_19-57-37.png)

Example: Fluids

![](../../../assets/img/2022-09-05/fast_19-58-08.png)



#### Mass Spring System:（质点弹簧系统）

Example of Modeling a Dynamic System

![](../../../assets/img/2022-09-05/fast_19-59-08.png)

Example: Mass Spring Mesh

![](../../../assets/img/2022-09-05/fast_19-59-57.png)

#### A Simple Spring

Idealized spring

![](../../../assets/img/2022-09-05/fast_20-00-56.png)

Force pulls points together
Strength proportional to displacement (Hooke's Law)
$k_s$ is a spring coefficient: stiffness



problem: this spring wants to have zero length



#### Non-Zero Length Spring

Spring with non-zero rest length

![](../../../assets/img/2022-09-05/fast_20-03-07.png)

![](../../../assets/img/2022-09-05/fast_20-03-32.png)

Problem: oscillates forever



#### Dot Notation for Derivatives

If $x$ is a vector for the position of a point of interest, we will use dot notation for velocity and acceleration:

![](../../../assets/img/2022-09-05/fast_20-04-57.png)

#### Introducing Energy Loss

Simple motion damping

<img src="../../../assets/img/2022-09-05/fast_20-05-37.png" style="zoom:50%;" />

* Behaves like viscous drag on motion
* Slows down motion in the direction of velocity
* $k_d$ is a damping coefficient



#### Problem: slows down all motion

• Want a rusty spring's oscillations to slow down, but should it also fall to the ground more slowly?



#### Internal Damping for Spring

Damp only the internal, spring-driven motion

![](../../../assets/img/2022-09-05/fast_20-07-51.png)

* Viscous drag only on change in spring length
  * Won't slow group motion for the spring system (e.g.
    global translation or rotation of the group)
* Note: This is only one specific type of damping



#### Structures from Springs

<img src="../../../assets/img/2022-09-05/fast_20-11-05.png" style="zoom:50%;" />

#### Structures from Springs

Behavior is determined by structure linkages

<img src="../../../assets/img/2022-09-05/fast_20-26-39.png" style="zoom:50%;" />

This structure will not resist shearing
This structure will not resist out-of-plane bending...



<img src="../../../assets/img/2022-09-05/fast_20-28-25.png" style="zoom:60%;" />

This structure will resist shearing but has anisotropic bias
This structure will not resist out-of-plane bending either...

<img src="../../../assets/img/2022-09-05/fast_20-29-52.png" style="zoom:60%;" />

This structure will resist shearing.
Less directional bias.
This structure will not resist out-of-plane bending either...

![](../../../assets/img/2022-09-05/fast_20-30-58.png)

This structure will resist shearing.
Less directional bias.

This structure will resist out-of-plane bending Red springs should be much weaker



#### Example: Mass Spring Dress + Character

<img src="../../../assets/img/2022-09-05/fast_20-32-29.png" style="zoom:60%;" />



#### Aside: FEM (Finite Element Method) Instead of Springs (有限元)

![](../../../assets/img/2022-09-05/fast_20-34-00.png)

受力分析



#### Particle Systems

Model dynamical systems as collections of large numbers of particles
Each particle's motion is defined by a set of physical (or non-physical) forces
Popular technique in graphics and games

* Easy to understand, implement
* Scalable: fewer particles for speed, more for higher complexity

Challenges

* May need many particles (e.g. fluids)
* May need acceleration structures (e.g. to Ind nearest particles for interactions)

<img src="../../../assets/img/2022-09-05/fast_20-37-56.png" style="zoom:60%;" />

#### Particle System Animations

For each frame in animation

* [If needed) Create new particles
* Calculate forces on each particle
* Update each particle's position and velocity
* [If needed) Remove dead particles
* Render particles



#### Particle System Forces

Attraction and repulsion forces

* Gravity, electromagnetism
* Springs, propulsion

Damping forces

* Friction, air drag, viscosity

Collisions

* Walls, containers, fixed objects
* Dynamic objects, character body parts

Gravida tional Attraction
Newton's universal law of gravitation

* Gravitational pull between particles

![](../../../assets/img/2022-09-05/fast_20-42-23.png)

#### Example: Galaxy Simulation

![](../../../assets/img/2022-09-05/fast_20-42-54.png)

先模拟，再渲染

#### Simulated Flocking as an ODE

Model each bird as a particle

Subject to very simple forces:

* attraction to center of neighbors

* attraction to center of neighbors
* repulsion from individual neighbors
* alignment toward average trajectory •of neighbors
* Simulate evolution of large particle system•numerically
  Emergent complex behavior (also seen in fish, bees，..)

![](../../../assets/img/2022-09-05/fast_20-44-51.png)

#### Example: Molecular Dynamics

![](../../../assets/img/2022-09-05/fast_20-45-58.png)



#### Example: Crowds + "Rock" Dynamics

![](../../../assets/img/2022-09-05/fast_20-46-29.png)

#### Forward Kinematics （正逆运动学）

(Slides by Prof. James O'Brien)

Articulated skeleton

* Topology (what's connected to what)
* Geometric relations from joints
* Tree structure (in absence of loops)

Joint types

* Pin (ID rotation)
* ![](../../../assets/img/2022-09-05/fast_20-48-33.png)
* Ball (2D rotation) 

![](../../../assets/img/2022-09-05/fast_20-48-54.png)

* Prismatic joint (translation)

![](../../../assets/img/2022-09-05/fast_20-48-04.png)

#### Forward Kinematics

Example: simple two segment arm in 2D

<img src="../../../assets/img/2022-09-05/fast_20-49-48.png" style="zoom:50%;" /> <img src="../../../assets/img/2022-09-05/fast_20-50-43.png" style="zoom:50%;" />

![](../../../assets/img/2022-09-05/fast_20-50-15.png)



尖端运动学



#### Kinematics Pros and Cons

Strengths

* Direct control is convenient
* Implementation is straightforward

Weaknesses

* Animation may be inconsistent with physics
* Time consuming for artists



#### inverse Kinematics

![](../../../assets/img/2022-09-05/fast_20-52-14.png)

Direct inverse kinematics: for two-segment arm, can solve for parameters analytically

![](../../../assets/img/2022-09-05/fast_20-52-51.png)



#### Why is the problem hard?

Multiple solutions in configuration space

![](../../../assets/img/2022-09-05/fast_20-53-25.png)

![](../../../assets/img/2022-09-05/fast_20-53-49.png)

Why is the problem hard?

* Solutions may not always exist

![](../../../assets/img/2022-09-05/fast_20-54-39.png)

Numerical solution to general N-link 1K problem

* Choose an initial configuration
* Define an error metric (e.g. square of distance between goal and current position)
* Compute gradient of error as function of configuration
* Apply gradient descent (or Newton's method, or other optimization procedure)



#### Rigging (提线木偶模型)

Rigging is a set of higher level controls on a character that allow more rapid & intuitive modification of pose,  deformations, expression, etc.

Important

* Like strings on a puppet
* Captures all meaningful character changes
* Varies from character to character

Expensive to create

* Manual effort
* Requires both artistic and technical training

![](../../../assets/img/2022-09-05/fast_20-58-05.png)

软选取，磨皮

控制点控制模型



#### Blend Shapes

Instead of skeleton, interpolate directly between surfaces 

E.g., model a collection of facial 

expressions:
Simplest scheme: take linear combination of vertex positions
Spline used to control choice of weights over time

<img src="../../../assets/img/2022-09-05/fast_20-59-57.png" style="zoom:50%;" />

#### Motion Capture

Data-driven approach to creating animation
sequences

* Record real-world performances (e.g. person executing an
  activity)
* Extract pose as a function of time from the data collected

![](../../../assets/img/2022-09-05/fast_21-01-47.png)

#### Motion Capture Pros and Cons

Strengths

* Can capture large amounts of real data quickly
* Realism can be high

Weaknesses

* Complex and costly set-ups
* Captured animation may not meet artistic needs, requiring alterations



#### Motion Capture Equipment

![](../../../assets/img/2022-09-05/fast_21-03-16.png)

#### Optical Motion Capture

![](../../../assets/img/2022-09-05/fast_21-03-44.png)

* Markers on subject
* Positions by triangulation from multiple cameras
* cameras, 240 Hz, occlusions are difficult

#### Optical Motion Capture

![](../../../assets/img/2022-09-05/fast_21-04-32.png)

Ronda Roussey in Electronic Arts' motion capture studio



#### Motion Data

![](../../../assets/img/2022-09-05/fast_21-05-08.png)

#### Challenges of Facial Animation

Uncanny valley (恐怖谷效应)   生成的过于真实，被用来做坏事情怎么办？
• In robotics and graphics
• As artificial character  appearance approaches human realism, our emotional response goes negative, until it achieves a sufficiently convincing level of realism in expression

![](../../../assets/img/2022-09-05/fast_21-06-44.png)

#### Facia; Motion Capture

![](../../../assets/img/2022-09-05/fast_21-07-39.png)

#### The Production Pipeline

![](../../../assets/img/2022-09-05/fast_21-08-12.png)



 















