---
title: Lecture 05 — Lines and Planes in Space
short_title: 05 · Lines and Planes in Space
description: Vector, parametric, and symmetric equations of lines; parallel, intersecting, and skew lines; equations of planes; angles and intersections; distances to lines and planes.
date: 2026-09-08
numbering:
  enumerator: "5.%s"
---

:::{div}
:class: lecture-meta
**Class meeting:** Tuesday, September 8, 2026  
**Reading:** Briggs §13.5; Lang, Ch. I, §5 (Parametric Lines) and §6 (Planes)  
**Prerequisites:** Lectures 03–04: dot product, projections, cross product.  
**PDF version:** [Lecture 05 notes (PDF)](../downloads/MTSC451_Lecture_05.pdf)
:::

## Learning Objectives

After this lecture you should be able to:

1. write vector, parametric, and symmetric equations of lines, and parametrize segments;
2. determine whether two lines are parallel, intersecting, or skew;
3. write the equation of a plane from a point and a normal vector, or from three points;
4. find the angle between planes, their line of intersection, and the intersection of a line with a plane;
5. compute distances from a point to a line and from a point to a plane.

## Motivation

In the plane, a line is described by one equation $ax+by=c$. In $\R^3$ one linear equation $ax+by+cz=d$ describes a *plane*, not a line, so lines need a different description. The natural one is dynamic: start at a point and move in a fixed direction. Planes, on the other hand, are described by a single equation built from a normal vector and the dot product. These are the linear objects of $\R^3$, and they will reappear as tangent lines to curves ([Lecture 06](lecture-06.md) onward) and tangent planes to surfaces.

## Lines

:::{prf:definition} Line in $\R^3$
:label: l05-def-line
The line through the point $P_0(x_0,y_0,z_0)$ (position vector $\vv{r}_0$) in the direction of a nonzero vector $\vv{v}=\ip{a,b,c}$ is the set of points with position vectors

$$
\vv{r}(t)=\vv{r}_0+t\vv{v},\qquad t\in\R,
$$

equivalently the **parametric equations** $x=x_0+at$, $y=y_0+bt$, $z=z_0+ct$.
:::

Lang writes $X=P+tA$ and interprets $t$ as time: a "bug" at $P$ when $t=0$ moving with constant velocity $A$. The **line through two points** $P$ and $Q$ uses $\vv{v}=\vect{PQ}$; restricting to $0\le t\le1$ gives the **segment** from $P$ to $Q$, with $t=0$ at $P$ and $t=1$ at $Q$. A line has infinitely many parametrizations: any point on it and any nonzero multiple of $\vv{v}$ work.

If $a,b,c$ are all nonzero, eliminating $t$ gives the **symmetric equations**

$$
\frac{x-x_0}{a}=\frac{y-y_0}{b}=\frac{z-z_0}{c}.
$$

(If, say, $c=0$, write $\frac{x-x_0}{a}=\frac{y-y_0}{b},\ z=z_0$.) Lang points out that in dimension $3$ and higher no single equation can describe a line; the parametric form is the natural description.

```{figure} ../assets/figures/lecture-05-fig-1.svg
:label: l05-fig-line
:alt: A line labeled ell. A point P zero on the line has a direction vector v drawn along the line. From the origin O, gray position vectors point to P zero (labeled r zero) and to a farther point on the line labeled r zero plus t v.
:width: 480px

The line $\ell$ through $P_0$ in the direction $\vv{v}$: each point of $\ell$ has position vector $\vv{r}_0+t\vv{v}$.
```

:::{prf:example} Line Through Two Points and a Segment
:label: l05-ex-two-points
Let $P(2,-1,3)$ and $Q(5,1,-1)$. Find parametric and symmetric equations of the line through $P$ and $Q$, and the point one third of the way from $P$ to $Q$.

*Solution.* $\vv{v}=\vect{PQ}=\ip{3,2,-4}$, so $x=2+3t$, $y=-1+2t$, $z=3-4t$, and the symmetric equations are $\dfrac{x-2}{3}=\dfrac{y+1}{2}=\dfrac{z-3}{-4}$. The segment $PQ$ corresponds to $0\le t\le1$, and the point one third of the way is at $t=\tfrac13$: $\bigl(2+1,\,-1+\tfrac23,\,3-\tfrac43\bigr)=\bigl(3,-\tfrac13,\tfrac53\bigr)$.
:::

### Relative position of two lines

Two lines in $\R^3$ are **parallel** if their direction vectors are parallel. Non-parallel lines either **intersect** in exactly one point or are **skew**: they do not meet and are not parallel (impossible in $\R^2$). To decide, use *different* parameters for the two lines and try to solve for a common point.

:::{prf:example} Intersecting or Skew?
:label: l05-ex-skew
Let $\ell_1:\ x=1+t,\ y=2-t,\ z=2t$. Classify $\ell_1$ relative to (a) $\ell_2:\ x=1+s,\ y=-1+2s,\ z=3-s$, and (b) $\ell_3:\ x=2s,\ y=1+s,\ z=4-s$.

*Solution.* Directions: $\vv{v}_1=\ip{1,-1,2}$, $\vv{v}_2=\ip{1,2,-1}$, $\vv{v}_3=\ip{2,1,-1}$. Neither $\vv{v}_2$ nor $\vv{v}_3$ is a multiple of $\vv{v}_1$, so neither line is parallel to $\ell_1$.

(a) Solve $1+t=1+s$, $2-t=-1+2s$, $2t=3-s$. The first gives $t=s$; then the second gives $2-s=-1+2s$, so $s=1$. The third equation: $2(1)=3-1$. $\checkmark$ The lines intersect at $t=s=1$, i.e., at $(2,1,2)$.

(b) Solve $1+t=2s$, $2-t=1+s$, $2t=4-s$. Adding the first two gives $3=1+3s$, so $s=\tfrac23$ and $t=\tfrac13$. The third equation would require $\tfrac23=4-\tfrac23=\tfrac{10}{3}$, which is false. The system has no solution, so $\ell_1$ and $\ell_3$ are skew.
:::

### Distance from a point to a line

:::{prf:theorem} Distance from a Point to a Line
:label: l05-thm-dist-line
The distance from a point $Q$ to the line through $P_0$ with direction $\vv{v}$ is

$$
d=\frac{|\vect{P_0Q}\times\vv{v}|}{|\vv{v}|}.
$$
:::

:::{prf:proof}
:nonumber:
The parallelogram with sides $\vect{P_0Q}$ and $\vv{v}$ has area $|\vect{P_0Q}\times\vv{v}|$. Its base is $|\vv{v}|$ and its height is the perpendicular distance $d$ from $Q$ to the line. So $|\vect{P_0Q}\times\vv{v}|=|\vv{v}|\,d$.
:::

:::{prf:example} Distance to a Line
:label: l05-ex-dist-line
Find the distance from $Q(1,0,3)$ to the line $\ell_1$ of {prf:ref}`l05-ex-skew`.

*Solution.* $P_0=(1,2,0)$ (at $t=0$) and $\vv{v}=\ip{1,-1,2}$, so $\vect{P_0Q}=\ip{0,-2,3}$ and $\vect{P_0Q}\times\vv{v}=\ip{(-2)(2)-3(-1),\;3\cdot1-0\cdot2,\;0\cdot(-1)-(-2)\cdot1}=\ip{-1,3,2}$. Thus $d=\dfrac{\sqrt{1+9+4}}{\sqrt{1+1+4}}=\sqrt{\dfrac{14}{6}}=\dfrac{\sqrt{21}}{3}\approx1.53$.
:::

## Planes

:::{prf:definition} Plane in $\R^3$
:label: l05-def-plane
The plane through $P_0(x_0,y_0,z_0)$ with **normal vector** $\vv{n}=\ip{a,b,c}\neq\vzero$ is the set of points $P(x,y,z)$ such that $\vect{P_0P}\perp\vv{n}$:

$$
\begin{aligned}
&\vv{n}\cdot(\vv{r}-\vv{r}_0)=0\\
\quad\Longleftrightarrow\quad &a(x-x_0)+b(y-y_0)+c(z-z_0)=0\\
\quad\Longleftrightarrow\quad &ax+by+cz=d,
\end{aligned}
$$

where $d=ax_0+by_0+cz_0$.
:::

Lang writes this as $(X-P)\cdot N=0$, or $X\cdot N=P\cdot N$. Conversely, every equation $ax+by+cz=d$ with $(a,b,c)\neq(0,0,0)$ is a plane with normal $\ip{a,b,c}$: *the normal vector can be read off from the coefficients*.

```{figure} ../assets/figures/lecture-05-fig-2.svg
:label: l05-fig-plane
:alt: A shaded parallelogram represents a plane. Two points P zero and P lie in the plane, with the vector from P zero to P drawn in the plane. A normal vector n rises from P zero perpendicular to the plane, with a right-angle mark between n and the vector P zero P.
:width: 360px

The normal vector $\vv{n}$ is orthogonal to $\vect{P_0P}$ for every point $P$ of the plane.
```

:::{prf:example} Point and Normal
:label: l05-ex-point-normal
Find the plane through $P_0(2,-1,4)$ with normal $\vv{n}=\ip{3,-2,5}$.

*Solution.* $3(x-2)-2(y+1)+5(z-4)=0$, i.e., $3x-2y+5z=6+2+20=28$. Check: $P_0$ gives $6+2+20=28$. $\checkmark$
:::

:::{prf:example} Plane Through Three Points
:label: l05-ex-three-points
Find the plane through $A(1,2,0)$, $B(3,0,1)$, $C(0,1,2)$.

*Solution.* The vectors $\vect{AB}=\ip{2,-2,1}$ and $\vect{AC}=\ip{-1,-1,2}$ lie in the plane, so a normal is $\vect{AB}\times\vect{AC}=\ip{(-2)(2)-1(-1),\;1(-1)-2\cdot2,\;2(-1)-(-2)(-1)}=\ip{-3,-5,-4}$. We may use $\vv{n}=\ip{3,5,4}$ instead. With the point $A$: $3(x-1)+5(y-2)+4z=0$, i.e.,

$$
3x+5y+4z=13.
$$

Check: $B$ gives $9+0+4=13$ and $C$ gives $0+5+8=13$. $\checkmark$ (If $\vect{AB}\times\vect{AC}=\vzero$, the three points would be collinear and would not determine a unique plane.)
:::

### Parallel planes, angles, and intersections

Two planes are **parallel** if their normals are parallel and **orthogonal** if their normals are orthogonal. Following Lang, the **angle between two planes** is defined through their normals; we take the acute angle,

$$
\cos\theta=\frac{|\vv{n}_1\cdot\vv{n}_2|}{|\vv{n}_1|\,|\vv{n}_2|},\qquad 0\le\theta\le\tfrac{\pi}{2}.
$$

Two non-parallel planes meet in a line. That line lies in both planes, so its direction is perpendicular to both normals; hence $\vv{v}=\vv{n}_1\times\vv{n}_2$ is a direction vector.

:::{prf:example} Angle and Line of Intersection
:label: l05-ex-angle-intersection
Find the angle between the planes $x+y-z=1$ and $2x-y+2z=4$, and parametric equations of their line of intersection.

*Solution.* $\vv{n}_1=\ip{1,1,-1}$, $\vv{n}_2=\ip{2,-1,2}$, $\vv{n}_1\cdot\vv{n}_2=2-1-2=-1$, $|\vv{n}_1|=\sqrt3$, $|\vv{n}_2|=3$. So $\cos\theta=\dfrac{1}{3\sqrt3}$ and $\theta\approx78.9^\circ$.

Direction: $\vv{v}=\vv{n}_1\times\vv{n}_2=\ip{1\cdot2-(-1)(-1),\;(-1)\cdot2-1\cdot2,\;1(-1)-1\cdot2}=\ip{1,-4,-3}$. A common point: from $x+y=1+z$ and $2x-y=4-2z$, adding gives $3x=5-z$; the choice $z=2$ gives $x=1$, $y=2$. Check: $1+2-2=1$ and $2-2+4=4$. $\checkmark$ The line is

$$
x=1+t,\qquad y=2-4t,\qquad z=2-3t .
$$
:::

:::{prf:example} Where a Line Meets a Plane
:label: l05-ex-line-meets-plane
Find the point where the line $x=1+2t$, $y=-1+t$, $z=3-t$ meets the plane $2x+y+z=10$.

*Solution.* Substitute the parametric equations into the plane: $2(1+2t)+(-1+t)+(3-t)=10$, so $4+4t=10$ and $t=\tfrac32$. The point is $\bigl(4,\tfrac12,\tfrac32\bigr)$. Check: $8+\tfrac12+\tfrac32=10$. $\checkmark$
:::

### Distance from a point to a plane

:::{prf:theorem} Distance from a Point to a Plane
:label: l05-thm-dist-plane
The distance from $Q(x_1,y_1,z_1)$ to the plane $ax+by+cz=d$ is

$$
D=\frac{|ax_1+by_1+cz_1-d|}{\sqrt{a^2+b^2+c^2}}.
$$
:::

:::{prf:proof} Lang
:nonumber:
Let $P_0$ be any point of the plane. The distance is the length of the projection of $\vect{P_0Q}$ onto the normal: $D=|\scal_{\vv{n}}\vect{P_0Q}|=\dfrac{|\vv{n}\cdot\vect{P_0Q}|}{|\vv{n}|}$. Since $\vv{n}\cdot\vect{P_0Q}=(ax_1+by_1+cz_1)-(ax_0+by_0+cz_0)=ax_1+by_1+cz_1-d$, the formula follows.
:::

:::{prf:example} Distance to a Plane
:label: l05-ex-dist-plane
Find the distance from $Q(3,1,-2)$ to the plane $x+2y-2z=1$.

*Solution.* $D=\dfrac{|3+2(1)-2(-2)-1|}{\sqrt{1+4+4}}=\dfrac{|8|}{3}=\dfrac83$.
:::

::::{admonition} Concept Check
:class: hint
Can two distinct planes in $\R^3$ intersect in exactly one point? Can a line and a plane?

:::{dropdown} Answer
Two distinct planes are either parallel (no common points) or meet in a line; never in a single point. A line and a plane can meet in exactly one point (when the line's direction is not perpendicular to the normal, as in {prf:ref}`l05-ex-line-meets-plane`); otherwise the line is parallel to the plane and either misses it or lies in it.
:::
::::

## Interactive Exploration

The figure shows the plane $ax+by+cz=d$ with its normal $\vv{n}=\ip{a,b,c}$ and the line $\vv{r}(t)=P_0+t\vv{v}$. The readout substitutes the line into the plane equation, reports the intersection point, and gives the distance from $P_0$ to the plane. Drag the figure to rotate it. Things to try:

- The starting values are those of {prf:ref}`l05-ex-line-meets-plane`; confirm that the line meets the plane at $t=\tfrac32$, at the point $\bigl(4,\tfrac12,\tfrac32\bigr)$.
- Change the direction to $\vv{v}=\ip{1,-2,0}$, so that $\vv{n}\cdot\vv{v}=0$. The line is now parallel to the plane. Then move $P_0$ to $(5,0,0)$, a point of the plane: the whole line lies in the plane.
- Enter the plane $x+2y-2z=1$ (so $\vv{n}=\ip{1,2,-2}$, $d=1$) and $P_0=(3,1,-2)$ to check the distance $\tfrac83$ of {prf:ref}`l05-ex-dist-plane`.

:::{anywidget} ../interactive/mathviz.mjs
{"widget": "lineplane", "n": [2, 1, 1], "d": 10, "r0": [1, -1, 3], "v": [2, 1, -1]}
:::

## Lines vs. Planes

| | **Line** | **Plane** |
|---|---|---|
| Determined by | point $+$ direction $\vv{v}$ | point $+$ normal $\vv{n}$ |
| Equation | $\vv{r}=\vv{r}_0+t\vv{v}$ | $\vv{n}\cdot(\vv{r}-\vv{r}_0)=0$ |
| Parallel when | directions parallel | normals parallel |
| Perpendicular when | $\vv{v}_1\cdot\vv{v}_2=0$ (if they meet) | $\vv{n}_1\cdot\vv{n}_2=0$ |
| Distance from $Q$ | $\lvert\vect{P_0Q}\times\vv{v}\rvert/\lvert\vv{v}\rvert$ | $\lvert\vv{n}\cdot\vect{P_0Q}\rvert/\lvert\vv{n}\rvert$ |

## Common Errors

:::{caution} Avoid these errors
- Confusing a line's direction vector (parallel to the line) with a plane's normal (perpendicular to the plane).
- Using the same parameter for two lines when testing for intersection; use $t$ for one and $s$ for the other.
- Concluding that non-parallel lines must intersect; in $\R^3$ they may be skew.
- Checking only two of the three equations when solving for an intersection point.
- Forgetting the absolute value in the distance formula, or forgetting to move $d$ to the left side first.
- Using three collinear points to define a plane; check that the cross product is nonzero.
:::

## Summary

:::{admonition} Key takeaways
:class: summary
- Line: $\vv{r}(t)=\vv{r}_0+t\vv{v}$; segment $PQ$: $\vv{r}_P+t\vect{PQ}$, $0\le t\le1$; symmetric form when $a,b,c\neq0$.
- Two lines are parallel, intersecting, or skew.
- Plane: $a(x-x_0)+b(y-y_0)+c(z-z_0)=0$ with normal $\ip{a,b,c}$; through three points use $\vv{n}=\vect{AB}\times\vect{AC}$.
- Angle between planes via normals; line of intersection has direction $\vv{n}_1\times\vv{n}_2$.
- Distances: to a line $|\vect{P_0Q}\times\vv{v}|/|\vv{v}|$; to a plane $|ax_1+by_1+cz_1-d|/\sqrt{a^2+b^2+c^2}$.
:::

## In-Class Practice

Try each problem before opening its solution.

:::{exercise}
:label: l05-practice-1
Find parametric and symmetric equations for the line through $(3,-1,4)$ in the direction $\ip{2,5,-1}$.
:::

:::{solution} l05-practice-1
:class: dropdown
$x=3+2t$, $y=-1+5t$, $z=4-t$; symmetric form $\dfrac{x-3}{2}=\dfrac{y+1}{5}=\dfrac{z-4}{-1}$.
:::

:::{exercise}
:label: l05-practice-2
Find parametric equations for the line through $P(1,0,-2)$ and $Q(4,3,1)$.
:::

:::{solution} l05-practice-2
:class: dropdown
$\vect{PQ}=\ip{3,3,3}$, so $x=1+3t$, $y=3t$, $z=-2+3t$. Equivalently, using the direction $\ip{1,1,1}$: $x=1+t$, $y=t$, $z=-2+t$.
:::

:::{exercise}
:label: l05-practice-3
Determine whether the lines $\ell_1:\ x=2+t,\ y=1-t,\ z=3+2t$ and $\ell_2:\ x=4-s,\ y=-1+s,\ z=1-2s$ are parallel, intersecting, or skew.
:::

:::{solution} l05-practice-3
:class: dropdown
$\vv{v}_1=\ip{1,-1,2}$ and $\vv{v}_2=\ip{-1,1,-2}=-\vv{v}_1$, so the lines are parallel. They are distinct: the point $(4,-1,1)$ of $\ell_2$ (at $s=0$) would require $2+t=4$, i.e., $t=2$, but then $\ell_1$ gives $(4,-1,7)\neq(4,-1,1)$. **Answer:** parallel and distinct (they do not intersect).
:::

:::{exercise}
:label: l05-practice-4
Find the equation of the plane through $(1,-2,3)$ with normal $\ip{4,1,-2}$.
:::

:::{solution} l05-practice-4
:class: dropdown
$4(x-1)+(y+2)-2(z-3)=0$, i.e., $4x+y-2z=-4$. Check: $4-2-6=-4$. $\checkmark$
:::

:::{exercise}
:label: l05-practice-5
Find the equation of the plane through $A(1,0,0)$, $B(0,2,0)$, and $C(0,0,3)$.
:::

:::{solution} l05-practice-5
:class: dropdown
$\vect{AB}=\ip{-1,2,0}$, $\vect{AC}=\ip{-1,0,3}$, and $\vect{AB}\times\vect{AC}=\ip{2\cdot3-0\cdot0,\;0(-1)-(-1)3,\;(-1)0-2(-1)}=\ip{6,3,2}$. With $A$: $6(x-1)+3y+2z=0$, i.e., $6x+3y+2z=6$ (equivalently $\tfrac{x}{1}+\tfrac{y}{2}+\tfrac{z}{3}=1$). Check: $B$ gives $6$ and $C$ gives $6$. $\checkmark$
:::

:::{exercise}
:label: l05-practice-6
Find the distance from the point $(1,2,3)$ to the plane $2x-y+2z=1$.
:::

:::{solution} l05-practice-6
:class: dropdown
$D=\dfrac{|2(1)-2+2(3)-1|}{\sqrt{4+1+4}}=\dfrac{|5|}{3}=\dfrac53$.
:::

## Before the Next Class

Begin Briggs §14.1 (vector-valued functions) and review this lecture's parametrization of lines: $\vv{r}(t)=\vv{r}_0+t\vv{v}$ is the simplest vector-valued function. Next: [Lecture 06 — Vector-Valued Functions and Their Derivatives](lecture-06.md).
