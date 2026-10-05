---
title: Lecture 02 — Vectors in Three Dimensions
short_title: 02 · Vectors in Three Dimensions
description: The right-handed xyz-coordinate system, distance and midpoints, spheres and balls, regions defined by inequalities, and vector operations in three dimensions.
date: 2026-08-27
numbering:
  enumerator: "2.%s"
---

:::{div}
:class: lecture-meta
**Class meeting:** Thursday, August 27, 2026  
**Reading:** Briggs §13.2; Lang, Ch. I, §1 (points in $n$-space) and §4 (norm, distance, balls and spheres)  
**Prerequisites:** [Lecture 01](lecture-01.md): vector operations, components, magnitude, unit vectors in $\R^2$.  
**PDF version:** [Lecture 02 notes (PDF)](../downloads/MTSC451_Lecture_02.pdf)
:::

## Learning Objectives

After this lecture you should be able to:

1. locate points in a right-handed $xyz$-coordinate system and describe simple sets in $\R^3$;
2. compute distances and midpoints in $\R^3$;
3. write the equation of a sphere and recover its center and radius by completing the square;
4. describe balls, spherical shells, and other regions defined by inequalities;
5. carry out vector operations in $\R^3$ and use the basis $\vvi,\vvj,\vvk$.

## Motivation

Physical space is three-dimensional: an aircraft has a horizontal position and an altitude, and a force on a structure can point in any direction in space. Everything in [Lecture 01](lecture-01.md) was stated for pairs of numbers, but the definitions—componentwise addition, scalar multiplication, length from the Pythagorean theorem—never used the fact that there were only two components. Lang makes this point directly: a point in $n$-space is an $n$-tuple $(x_1,\dots,x_n)$, and the algebra is identical for every $n$. What is new in $\R^3$ is the geometry we must learn to visualize.

## The Coordinate System in $\R^3$

We use three mutually perpendicular axes, oriented by the **right-hand rule**: when the fingers of the right hand curl from the positive $x$-axis toward the positive $y$-axis, the thumb points along the positive $z$-axis. A point is an ordered triple $(x,y,z)$; the set of all such triples is $\R^3$.

```{figure} ../assets/figures/lecture-02-fig-1.svg
:label: l02-fig-point
:alt: A right-handed coordinate system with the x-axis pointing toward the viewer and to the lower left, the y-axis to the right, and the z-axis up. The point P with coordinates x0, y0, z0 is marked, and dashed lines outline the rectangular box whose edges run from the coordinate planes to P, with x0, y0, and z0 marked on the axes.
:width: 420px

Locating the point $P(x_0,y_0,z_0)$ in a right-handed coordinate system.
```

:::{admonition} Key Idea
:class: tip
The **coordinate planes** are the $xy$-plane ($z=0$), the $xz$-plane ($y=0$), and the $yz$-plane ($x=0$). They divide space into eight **octants**; the first octant is $\{x>0,\ y>0,\ z>0\}$. Each coordinate axis is the intersection of two coordinate planes; for example, the $z$-axis is $\{x=0\}\cap\{y=0\}$.
:::

A single equation in $x,y,z$ typically describes a *surface*; two equations typically describe a *curve*. This dimension count will recur throughout the course.

:::{prf:example} Describing Sets in $\R^3$
:label: l02-ex-sets
Describe each set geometrically: (a) $\{(x,y,z): z=-2\}$; (b) $\{(x,y,z): x=1,\ y=3\}$; (c) $\{(x,y,z): x^2+z^2=9,\ y=2\}$.

*Solution.* (a) A plane parallel to the $xy$-plane, two units below it.

(b) Both $x$ and $y$ are fixed while $z$ is free, so this is the line through $(1,3,0)$ parallel to the $z$-axis.

(c) The equation $x^2+z^2=9$ alone is a cylinder around the $y$-axis; adding $y=2$ cuts out the circle of radius $3$ centered at $(0,2,0)$ lying in the plane $y=2$.
:::

## Distance, Midpoints, and Spheres

:::{prf:theorem} Distance Formula in $\R^3$
:label: l02-thm-distance
The distance between $P(x_1,y_1,z_1)$ and $Q(x_2,y_2,z_2)$ is

$$
|PQ|=\sqrt{(x_2-x_1)^2+(y_2-y_1)^2+(z_2-z_1)^2}.
$$
:::

:::{prf:proof}
:nonumber:
Let $R=(x_2,y_2,z_1)$. The segment $PR$ lies in the horizontal plane $z=z_1$, so by the planar formula $|PR|^2=(x_2-x_1)^2+(y_2-y_1)^2$. The segment $RQ$ is vertical, of length $|z_2-z_1|$, and is perpendicular to $PR$. The Pythagorean theorem in triangle $PRQ$ gives $|PQ|^2=|PR|^2+|RQ|^2$, which is the formula.
:::

In Lang's notation, if $A$ and $B$ are points, the distance is $\|A-B\|=\sqrt{(A-B)\cdot(A-B)}$. The midpoint of $PQ$ is $M=\bigl(\tfrac{x_1+x_2}{2},\tfrac{y_1+y_2}{2},\tfrac{z_1+z_2}{2}\bigr)$, i.e., the position vector $\tfrac12(\vect{OP}+\vect{OQ})$.

:::{prf:definition} Sphere and Ball
:label: l02-def-sphere
The **sphere** with center $(a,b,c)$ and radius $r>0$ is the set of points at distance $r$ from the center:

$$
(x-a)^2+(y-b)^2+(z-c)^2=r^2.
$$

The **open ball** is the set where $(x-a)^2+(y-b)^2+(z-c)^2<r^2$, and the **closed ball** is the set where this quantity is $\le r^2$.
:::

Lang phrases this as: the sphere of radius $r$ centered at $P$ is $\{X:\|X-P\|=r\}$, the open ball is $\{X:\|X-P\|<r\}$, and the closed ball is $\{X:\|X-P\|\le r\}$. Open balls will be the basic neighborhoods when we define limits and continuity later in the course.

:::{prf:example} Distance
:label: l02-ex-distance
Find the distance between $P(-1,2,4)$ and $Q(3,-2,6)$.

*Solution.* $|PQ|=\sqrt{(3+1)^2+(-2-2)^2+(6-4)^2}=\sqrt{16+16+4}=\sqrt{36}=6$.
:::

:::{prf:example} Sphere with a Given Diameter
:label: l02-ex-diameter
Find an equation of the sphere having the segment from $A(2,-1,5)$ to $B(4,3,1)$ as a diameter.

*Solution.* The center is the midpoint $C=\bigl(\tfrac{2+4}{2},\tfrac{-1+3}{2},\tfrac{5+1}{2}\bigr)=(3,1,3)$. The radius is half the length of the diameter: $r=\tfrac12\sqrt{2^2+4^2+(-4)^2}=\tfrac12\sqrt{36}=3$. Hence

$$
(x-3)^2+(y-1)^2+(z-3)^2=9.
$$

Check: $A$ satisfies $1+4+4=9$. $\checkmark$
:::

:::{prf:example} Completing the Square
:label: l02-ex-complete-square
Decide whether each equation describes a sphere; if so, find its center and radius.
(a) $x^2+y^2+z^2-6x+4y-2z+5=0$; (b) $x^2+y^2+z^2+2z+5=0$.

*Solution.* (a) Group and complete the square in each variable:

$$
\begin{aligned}
&(x^2-6x+9)+(y^2+4y+4)+(z^2-2z+1)=-5+9+4+1\\
&\;\Longrightarrow\;(x-3)^2+(y+2)^2+(z-1)^2=9.
\end{aligned}
$$

This is the sphere with center $(3,-2,1)$ and radius $3$.

(b) $x^2+y^2+(z+1)^2=-5+1=-4$. A sum of squares cannot be negative, so *no* point satisfies the equation: the set is empty, not a sphere.
:::

:::{prf:example} Regions Defined by Inequalities
:label: l02-ex-regions
Describe $\{(x,y,z): 1<(x-1)^2+y^2+z^2\le4\}$ and $\{(x,y,z): x^2+y^2+z^2\le 9,\ z\ge0\}$.

*Solution.* The first set consists of points whose distance $d$ from $(1,0,0)$ satisfies $1<d\le2$: a spherical shell centered at $(1,0,0)$ that includes the outer sphere of radius $2$ but excludes the inner sphere of radius $1$. The second set is the closed upper half-ball of radius $3$ centered at the origin, including the flat disk $x^2+y^2\le9$ in the $xy$-plane.
:::

## Interactive Exploration

The figure shows two points $P$ and $Q$ in space, the vector $\vect{PQ}$, the midpoint $M$, and (optionally) the sphere having the segment $PQ$ as a diameter. The starting values are $A(2,-1,5)$ and $B(4,3,1)$ from {prf:ref}`l02-ex-diameter`. Type new coordinates, and drag the figure to rotate it. Things to try:

- Confirm the center $(3,1,3)$ and the equation $(x-3)^2+(y-1)^2+(z-3)^2=9$ in the readout, then rotate the view to see that $P$ and $Q$ are diametrically opposite.
- Enter $P(-1,2,4)$ and $Q(3,-2,6)$ from {prf:ref}`l02-ex-distance` and check that $|PQ|=6$.
- Turn on the coordinate box and move $P$ into different octants; watch which coordinates change sign.

:::{anywidget} ../interactive/mathviz.mjs
{"widget": "points3d", "P": [2, -1, 5], "Q": [4, 3, 1], "sphere": true}
:::

## Vectors in $\R^3$

A vector in $\R^3$ is written $\vv{v}=\ip{v_1,v_2,v_3}$, and the vector from $P(x_1,y_1,z_1)$ to $Q(x_2,y_2,z_2)$ is $\vect{PQ}=\ip{x_2-x_1,\,y_2-y_1,\,z_2-z_1}$. Addition, scalar multiplication, and all the properties from [Lecture 01](lecture-01.md) hold componentwise. The magnitude is

$$
|\vv{v}|=\sqrt{v_1^2+v_2^2+v_3^2},
$$

and $\vv{v}/|\vv{v}|$ is the unit vector in the direction of $\vv{v}\neq\vzero$. The **standard unit vectors** are $\vvi=\ip{1,0,0}$, $\vvj=\ip{0,1,0}$, $\vvk=\ip{0,0,1}$ (Lang writes $E_1,E_2,E_3$), and $\ip{v_1,v_2,v_3}=v_1\vvi+v_2\vvj+v_3\vvk$.

:::{prf:example} Vector Operations in $\R^3$
:label: l02-ex-operations
Let $\vv{u}=\ip{1,-2,2}$ and $\vv{v}=3\vvi-4\vvk$. Compute $\vv{u}+\vv{v}$, $3\vv{u}-2\vv{v}$, $|\vv{u}|$, $|\vv{v}|$, and the unit vector in the direction of $\vv{v}$.

*Solution.* First, $\vv{v}=\ip{3,0,-4}$. Then $\vv{u}+\vv{v}=\ip{4,-2,-2}$ and $3\vv{u}-2\vv{v}=\ip{3,-6,6}-\ip{6,0,-8}=\ip{-3,-6,14}$. Next, $|\vv{u}|=\sqrt{1+4+4}=3$ and $|\vv{v}|=\sqrt{9+0+16}=5$, so the unit vector is $\tfrac15\ip{3,0,-4}=\ip{\tfrac35,0,-\tfrac45}$.
:::

:::{prf:example} Velocity in Space
:label: l02-ex-velocity
An airplane's velocity relative to the air is $\ip{300,400,12}$ mph ($x$ east, $y$ north, $z$ up). The wind velocity is $\ip{-20,10,0}$ mph. Find the airplane's velocity relative to the ground and its speed.

*Solution.* Ground velocity $=\ip{300,400,12}+\ip{-20,10,0}=\ip{280,410,12}$. The speed is

$$
\begin{aligned}
\sqrt{280^2+410^2+12^2}&=\sqrt{78400+168100+144}\\
&=\sqrt{246644}\approx496.6\text{ mph}.
\end{aligned}
$$
:::

:::{prf:example} Collinear Points
:label: l02-ex-collinear
Show that $A(1,2,3)$, $B(3,5,4)$, and $C(7,11,6)$ lie on one line.

*Solution.* $\vect{AB}=\ip{2,3,1}$ and $\vect{AC}=\ip{6,9,3}=3\,\vect{AB}$. The located vectors $\vect{AB}$ and $\vect{AC}$ are parallel and share the point $A$, so $B$ and $C$ lie on the line through $A$ in the direction $\ip{2,3,1}$. Moreover, $B$ lies between $A$ and $C$ because $\vect{AC}=3\vect{AB}$ with $3>1$.
:::

::::{admonition} Concept Check
:class: hint
**(a)** What is the set $x^2+y^2+z^2=0$?

**(b)** What is the set $\{(x,y,z): y=x\}$ in $\R^3$? (In $\R^2$, $y=x$ is a line.)

:::{dropdown} Answer
(a) Only the origin: a sum of squares is $0$ only when each term is $0$. It is sometimes called a degenerate sphere of radius $0$.

(b) A plane. It contains the line $y=x$ in the $xy$-plane and every vertical line through a point of that line, because $z$ is unrestricted.
:::
::::

## Common Errors

:::{caution} Avoid these errors
- Drawing a left-handed system (for example, swapping the $x$- and $y$-axes). Interchanging two axes reverses orientation, which matters for cross products in [Lecture 04](lecture-04.md).
- Writing the radius instead of its square: the sphere of radius $4$ is $(x-a)^2+\cdots=16$, not $=4$.
- Completing the square on one side only: adding $9$ to form $(x-3)^2$ requires adding $9$ to the other side as well.
- Assuming every equation $x^2+y^2+z^2+Dx+Ey+Fz+G=0$ is a sphere. After completing the square the right side may be zero (a point) or negative (no points).
- Reading $x=1$ as a point or a line. In $\R^3$ it is a plane.
:::

## Summary

:::{admonition} Key takeaways
:class: summary
- $\R^3$ uses a right-handed coordinate system with three coordinate planes and eight octants.
- $|PQ|=\sqrt{(\Delta x)^2+(\Delta y)^2+(\Delta z)^2}$; midpoint = average of coordinates.
- Sphere: $(x-a)^2+(y-b)^2+(z-c)^2=r^2$; balls are defined by $<r^2$ (open) or $\le r^2$ (closed).
- Vectors in $\R^3$ have three components; all operations and properties from $\R^2$ carry over; $\vv{v}=v_1\vvi+v_2\vvj+v_3\vvk$.
:::

## In-Class Practice

Try each problem before opening its solution.

:::{exercise}
:label: l02-practice-1
Find the distance between $P(3,0,-5)$ and $Q(-1,4,3)$.
:::

:::{solution} l02-practice-1
:class: dropdown
$|PQ|=\sqrt{(-1-3)^2+(4-0)^2+(3+5)^2}=\sqrt{16+16+64}=\sqrt{96}=4\sqrt6$.
:::

:::{exercise}
:label: l02-practice-2
Write the equation of the sphere with center $(2,-1,3)$ that passes through the origin.
:::

:::{solution} l02-practice-2
:class: dropdown
The radius is the distance from the center to the origin: $r^2=2^2+(-1)^2+3^2=14$. The sphere is $(x-2)^2+(y+1)^2+(z-3)^2=14$.
:::

:::{exercise}
:label: l02-practice-3
Let $\vv{a}=3\vvi-\vvj+2\vvk$ and $\vv{b}=-\vvi+4\vvj-\vvk$. Compute $2\vv{a}+\vv{b}$, $|\vv{a}|$, and the unit vector in the direction of $\vv{a}$.
:::

:::{solution} l02-practice-3
:class: dropdown
$2\vv{a}+\vv{b}=\ip{6,-2,4}+\ip{-1,4,-1}=\ip{5,2,3}=5\vvi+2\vvj+3\vvk$. Next, $|\vv{a}|=\sqrt{9+1+4}=\sqrt{14}$, so the unit vector is

$$
\dfrac{1}{\sqrt{14}}\ip{3,-1,2}=\Bigl\langle\dfrac{3}{\sqrt{14}},-\dfrac{1}{\sqrt{14}},\dfrac{2}{\sqrt{14}}\Bigr\rangle.
$$
:::

:::{exercise}
:label: l02-practice-4
Determine whether the equation $x^2+y^2+z^2+2x-8y+1=0$ represents a sphere. If so, find its center and radius.
:::

:::{solution} l02-practice-4
:class: dropdown
Complete the square: $(x^2+2x+1)+(y^2-8y+16)+z^2=-1+1+16$, so $(x+1)^2+(y-4)^2+z^2=16$. Yes: it is the sphere with center $(-1,4,0)$ and radius $4$.
:::

## Before the Next Class

Read Briggs §13.3 and Lang, Ch. I, §3 (Scalar Product) and the rest of §4 (projection, angle, Schwarz and triangle inequalities). Review the law of cosines. Next: [Lecture 03 — Dot Products](lecture-03.md).
