---
title: Lecture 03 — Dot Products
short_title: 03 · Dot Products
description: The dot product and its properties, angles and orthogonality, scalar components and projections, the Cauchy–Schwarz and triangle inequalities, and work.
date: 2026-09-01
numbering:
  enumerator: "3.%s"
---

:::{div}
:class: lecture-meta
**Class meeting:** Tuesday, September 1, 2026  
**Reading:** Briggs §13.3; Lang, Ch. I, §3 (Scalar Product) and §4 (The Norm of a Vector)  
**Prerequisites:** [Lectures 01](lecture-01.md)–[02](lecture-02.md): vector operations and magnitude in $\R^2$ and $\R^3$; the law of cosines.  
**PDF version:** [Lecture 03 notes (PDF)](../downloads/MTSC451_Lecture_03.pdf)
:::

## Learning Objectives

After this lecture you should be able to:

1. compute dot products and use properties SP 1–SP 4 in algebraic arguments;
2. find the angle between two vectors and test for orthogonality;
3. compute scalar components and vector projections, and decompose a vector into parallel and orthogonal parts;
4. state and prove the Cauchy–Schwarz and triangle inequalities;
5. compute the work done by a constant force.

## Motivation

So far we can add vectors and scale them, but we cannot yet measure angles or decide when two vectors are perpendicular. The dot product supplies exactly this: a single algebraic operation that encodes length, angle, and perpendicularity. It is the tool behind projections, work, the equation of a plane ([Lecture 05](lecture-05.md)), and later the directional derivative $D_{\vv{u}}f=\nabla f\cdot\vv{u}$.

## Definition and Algebraic Properties

:::{prf:definition} Dot Product
:label: l03-def-dot
For $\vv{u}=\ip{u_1,\dots,u_n}$ and $\vv{v}=\ip{v_1,\dots,v_n}$ in $\R^n$ ($n=2$ or $3$ in practice),

$$
\vv{u}\cdot\vv{v}=u_1v_1+u_2v_2+\cdots+u_nv_n .
$$

The result is a *scalar*.
:::

:::{admonition} Notation: Briggs and Lang
:class: note notation
Lang calls this the *scalar product* and writes $A\cdot B$; he defines it by the component formula above and derives the angle formula afterward. Briggs introduces the dot product through $|\vv{u}|\,|\vv{v}|\cos\theta$ and derives the component formula. The two approaches give the same operation. We take the component formula as the definition because it works in every dimension and makes the algebraic properties immediate; the angle formula is then a theorem ([Angles and Orthogonality](#l03-sec-angles)).
:::

:::{prf:theorem} Properties of the Dot Product (Lang's SP 1–SP 4)
:label: l03-thm-properties
For vectors $\vv{u},\vv{v},\vv{w}$ and a scalar $c$:

- **SP 1** $\vv{u}\cdot\vv{v}=\vv{v}\cdot\vv{u}$.
- **SP 2** $\vv{u}\cdot(\vv{v}+\vv{w})=\vv{u}\cdot\vv{v}+\vv{u}\cdot\vv{w}$.
- **SP 3** $(c\vv{u})\cdot\vv{v}=c(\vv{u}\cdot\vv{v})=\vv{u}\cdot(c\vv{v})$.
- **SP 4** $\vv{u}\cdot\vv{u}\ge0$, with equality if and only if $\vv{u}=\vzero$.

In addition, $\vv{u}\cdot\vv{u}=|\vv{u}|^2$.
:::

:::{prf:proof}
:nonumber:
SP 1–SP 3 follow from commutativity and distributivity of real numbers in each term; e.g., $\vv{u}\cdot(\vv{v}+\vv{w})=\sum u_i(v_i+w_i)=\sum u_iv_i+\sum u_iw_i$. For SP 4, $\vv{u}\cdot\vv{u}=\sum u_i^2$ is a sum of squares, which is $\ge0$ and is $0$ only if every $u_i=0$.
:::

A useful consequence of SP 1–SP 3, used repeatedly below, is the expansion

$$
|\vv{u}\pm\vv{v}|^2=(\vv{u}\pm\vv{v})\cdot(\vv{u}\pm\vv{v})=|\vv{u}|^2\pm2\,\vv{u}\cdot\vv{v}+|\vv{v}|^2. \tag{$*$}
$$

(l03-sec-angles)=
## Angles and Orthogonality

The **angle** between nonzero vectors $\vv{u}$ and $\vv{v}$ is the angle $\theta\in[0,\pi]$ between them when they are placed tail to tail.

:::{prf:theorem} Geometric Form of the Dot Product
:label: l03-thm-geometric
If $\vv{u},\vv{v}\neq\vzero$ and $\theta$ is the angle between them, then

$$
\vv{u}\cdot\vv{v}=|\vv{u}|\,|\vv{v}|\cos\theta,\qquad\text{so}\qquad
\cos\theta=\frac{\vv{u}\cdot\vv{v}}{|\vv{u}|\,|\vv{v}|}.
$$
:::

:::{prf:proof}
:nonumber:
Place $\vv{u}$ and $\vv{v}$ tail to tail. The third side of the resulting triangle is $\vv{u}-\vv{v}$, and the side opposite $\theta$ has length $|\vv{u}-\vv{v}|$. The law of cosines gives $|\vv{u}-\vv{v}|^2=|\vv{u}|^2+|\vv{v}|^2-2|\vv{u}|\,|\vv{v}|\cos\theta$. Comparing with $(*)$ gives $-2\,\vv{u}\cdot\vv{v}=-2|\vv{u}|\,|\vv{v}|\cos\theta$. (If $\vv{u}$ and $\vv{v}$ are parallel the triangle is degenerate; then $\vv{v}=c\vv{u}$ and both sides equal $c|\vv{u}|^2$ directly.)
:::

Lang reverses the logic: in $\R^n$ with $n>3$ there is no picture, so he *defines* $\theta$ by the formula $\cos\theta=\vv{u}\cdot\vv{v}/(|\vv{u}|\,|\vv{v}|)$. This requires knowing that the right side lies in $[-1,1]$, which is exactly the Cauchy–Schwarz inequality ({prf:ref}`l03-thm-cauchy-schwarz`).

:::{prf:definition} Orthogonal Vectors
:label: l03-def-orthogonal
Vectors $\vv{u}$ and $\vv{v}$ are **orthogonal** (perpendicular), written $\vv{u}\perp\vv{v}$, if $\vv{u}\cdot\vv{v}=0$. The zero vector is orthogonal to every vector.
:::

:::{admonition} Key Idea
:class: tip
For nonzero $\vv{u},\vv{v}$, the sign of $\vv{u}\cdot\vv{v}$ is the sign of $\cos\theta$:

- $\vv{u}\cdot\vv{v}>0\iff\theta$ acute;
- $\vv{u}\cdot\vv{v}=0\iff\theta=\pi/2$;
- $\vv{u}\cdot\vv{v}<0\iff\theta$ obtuse.
:::

:::{prf:example} Dot Product and Angle
:label: l03-ex-angle
Find the angle between $\vv{u}=\ip{1,2,-2}$ and $\vv{v}=\ip{4,0,-3}$.

*Solution.* $\vv{u}\cdot\vv{v}=4+0+6=10$, $|\vv{u}|=\sqrt{1+4+4}=3$, $|\vv{v}|=\sqrt{16+0+9}=5$. Thus $\cos\theta=\dfrac{10}{15}=\dfrac23$ and $\theta=\arccos(2/3)\approx0.841$ rad $\approx48.2^\circ$.
:::

:::{prf:example} Classifying Angles by Sign
:label: l03-ex-classify
Let $\vv{a}=\ip{3,-1,2}$, $\vv{b}=\ip{1,5,1}$, $\vv{c}=\ip{2,2,-1}$, $\vv{d}=\ip{-1,0,1}$. Classify the angle between $\vv{a}$ and each of $\vv{b},\vv{c},\vv{d}$.

*Solution.* $\vv{a}\cdot\vv{b}=3-5+2=0$, so $\vv{a}\perp\vv{b}$. $\vv{a}\cdot\vv{c}=6-2-2=2>0$, so the angle is acute. $\vv{a}\cdot\vv{d}=-3+0+2=-1<0$, so the angle is obtuse.
:::

:::{prf:example} A Right Triangle in Space
:label: l03-ex-right-triangle
Show that the triangle with vertices $A(1,0,1)$, $B(2,1,0)$, $C(0,2,2)$ has a right angle, and find its area.

*Solution.* $\vect{AB}=\ip{1,1,-1}$ and $\vect{AC}=\ip{-1,2,1}$, so $\vect{AB}\cdot\vect{AC}=-1+2-1=0$. The angle at $A$ is a right angle. The legs have lengths $|\vect{AB}|=\sqrt3$ and $|\vect{AC}|=\sqrt6$, so the area is $\tfrac12\sqrt3\sqrt6=\tfrac12\sqrt{18}=\tfrac{3\sqrt2}{2}$.
:::

## Projections

Given $\vv{v}\neq\vzero$, we want to split $\vv{u}$ as $\vv{u}=\vv{p}+\vv{q}$ with $\vv{p}$ parallel to $\vv{v}$ and $\vv{q}$ orthogonal to $\vv{v}$.

```{figure} ../assets/figures/lecture-03-fig-1.svg
:label: l03-fig-projection
:alt: Vectors u and v drawn from a common tail with angle theta between them. The projection of u onto v is a thick arrow along v, and the vector u minus the projection rises vertically from the tip of the projection to the head of u, meeting v at a right angle.
:width: 480px

The projection $\proj_{\vv{v}}\vv{u}$ and the orthogonal part $\vv{u}-\proj_{\vv{v}}\vv{u}$.
```

*Derivation.* Write $\vv{p}=c\vv{v}$. The condition $(\vv{u}-c\vv{v})\cdot\vv{v}=0$ gives $\vv{u}\cdot\vv{v}-c\,\vv{v}\cdot\vv{v}=0$, so $c=\dfrac{\vv{u}\cdot\vv{v}}{\vv{v}\cdot\vv{v}}$. This value of $c$ is the unique one that works.

:::{prf:definition} Scalar Component and Vector Projection
:label: l03-def-projection
For $\vv{v}\neq\vzero$, the **vector projection** of $\vv{u}$ onto $\vv{v}$ and the **scalar component** of $\vv{u}$ in the direction of $\vv{v}$ are

$$
\proj_{\vv{v}}\vv{u}=\frac{\vv{u}\cdot\vv{v}}{\vv{v}\cdot\vv{v}}\,\vv{v}
=\frac{\vv{u}\cdot\vv{v}}{|\vv{v}|^2}\,\vv{v},\qquad
\scal_{\vv{v}}\vv{u}=\frac{\vv{u}\cdot\vv{v}}{|\vv{v}|}=|\vv{u}|\cos\theta .
$$

Thus $\proj_{\vv{v}}\vv{u}=(\scal_{\vv{v}}\vv{u})\,\dfrac{\vv{v}}{|\vv{v}|}$, and $\vv{u}-\proj_{\vv{v}}\vv{u}$ is orthogonal to $\vv{v}$.
:::

:::{admonition} Notation: Briggs and Lang
:class: note notation
Watch the word "component." Briggs's *scalar component* is $\scal_{\vv{v}}\vv{u}=\vv{u}\cdot\vv{v}/|\vv{v}|$ (a signed length). Lang's *component of $A$ along $B$* is $c=A\cdot B/B\cdot B$, the multiplier in $\proj=cB$. They agree when $\vv{v}$ is a unit vector and differ by the factor $|\vv{v}|$ otherwise. In this course "scalar component" means Briggs's $\scal_{\vv{v}}\vv{u}$.
:::

:::{prf:example} Orthogonal Decomposition
:label: l03-ex-decomposition
Let $\vv{u}=\ip{2,3,-1}$ and $\vv{v}=\ip{1,1,2}$. Find $\scal_{\vv{v}}\vv{u}$, $\proj_{\vv{v}}\vv{u}$, and write $\vv{u}$ as a sum of a vector parallel to $\vv{v}$ and a vector orthogonal to $\vv{v}$.

*Solution.* $\vv{u}\cdot\vv{v}=2+3-2=3$ and $|\vv{v}|^2=1+1+4=6$. Hence

$$
\scal_{\vv{v}}\vv{u}=\frac{3}{\sqrt6}=\frac{\sqrt6}{2},\qquad
\proj_{\vv{v}}\vv{u}=\frac36\ip{1,1,2}=\ip{\tfrac12,\tfrac12,1}.
$$

The orthogonal part is $\vv{u}-\proj_{\vv{v}}\vv{u}=\ip{\tfrac32,\tfrac52,-2}$. Check: $\ip{\tfrac32,\tfrac52,-2}\cdot\ip{1,1,2}=\tfrac32+\tfrac52-4=0$. $\checkmark$ So $\vv{u}=\ip{\tfrac12,\tfrac12,1}+\ip{\tfrac32,\tfrac52,-2}$. (Lang's component of $\vv{u}$ along $\vv{v}$ is $c=\tfrac12$.)
:::

## Interactive Exploration

Drag the heads of $\vv{u}$ and $\vv{v}$, or type their components. The readout compares $\vv{u}\cdot\vv{v}$ computed from components with $|\vv{u}|\,|\vv{v}|\cos\theta$, classifies the angle by the sign of the dot product, and shows $\proj_{\vv{v}}\vv{u}$ together with the orthogonal part $\vv{u}-\proj_{\vv{v}}\vv{u}$ (marked with a right-angle symbol). Things to try:

- Make the vectors orthogonal, e.g. $\vv{u}=\ip{2,1}$ and $\vv{v}=\ip{-1,2}$ (or press "Make v ⊥ u"): the dot product is $0$, $\theta=90^\circ$, and the projection collapses to $\vzero$.
- Enter $\vv{u}=\ip{4,3}$ and $\vv{v}=\ip{1,2}$ from In-Class Practice 4 and check that $\proj_{\vv{v}}\vv{u}=\ip{2,4}$ and $\vv{u}-\proj_{\vv{v}}\vv{u}=\ip{2,-1}$.
- Press "Make v = 2u" and "Make v = −u": in both cases $|\vv{u}\cdot\vv{v}|=|\vv{u}|\,|\vv{v}|$, so the Cauchy–Schwarz inequality below holds with equality.

:::{anywidget} ../interactive/mathviz.mjs
{"widget": "dotproduct", "u": [4, 1], "v": [1, 3]}
:::

(l03-sec-inequalities)=
## The Cauchy–Schwarz and Triangle Inequalities

:::{prf:theorem} Cauchy–Schwarz Inequality
:label: l03-thm-cauchy-schwarz
For all vectors $\vv{u},\vv{v}$ in $\R^n$, $\quad|\vv{u}\cdot\vv{v}|\le|\vv{u}|\,|\vv{v}|$.
:::

:::{prf:proof} Lang
:nonumber:
If $\vv{v}=\vzero$ both sides are $0$. Otherwise let $c=\vv{u}\cdot\vv{v}/|\vv{v}|^2$, so $\vv{u}=c\vv{v}+\vv{q}$ with $\vv{q}\perp\vv{v}$. By $(*)$ and $\vv{q}\cdot\vv{v}=0$,

$$
|\vv{u}|^2=c^2|\vv{v}|^2+|\vv{q}|^2\ge c^2|\vv{v}|^2=\dfrac{(\vv{u}\cdot\vv{v})^2}{|\vv{v}|^2}.
$$

Multiply by $|\vv{v}|^2$ and take square roots.
:::

:::{prf:theorem} Triangle Inequality
:label: l03-thm-triangle
For all vectors $\vv{u},\vv{v}$ in $\R^n$, $\quad|\vv{u}+\vv{v}|\le|\vv{u}|+|\vv{v}|$.
:::

:::{prf:proof}
:nonumber:
By $(*)$ and Cauchy–Schwarz,

$$
|\vv{u}+\vv{v}|^2=|\vv{u}|^2+2\,\vv{u}\cdot\vv{v}+|\vv{v}|^2\le|\vv{u}|^2+2|\vv{u}|\,|\vv{v}|+|\vv{v}|^2=(|\vv{u}|+|\vv{v}|)^2.
$$

Both sides of the original inequality are nonnegative, so take square roots.
:::

:::{prf:example} A Vector Proof: Rhombus Diagonals
:label: l03-ex-rhombus
(a) Prove that $(\vv{u}+\vv{v})\cdot(\vv{u}-\vv{v})=|\vv{u}|^2-|\vv{v}|^2$.
(b) Deduce that a parallelogram is a rhombus if and only if its diagonals are perpendicular.

*Solution.* (a) By SP 2 and SP 1,

$$
(\vv{u}+\vv{v})\cdot(\vv{u}-\vv{v})=\vv{u}\cdot\vv{u}-\vv{u}\cdot\vv{v}+\vv{v}\cdot\vv{u}-\vv{v}\cdot\vv{v}=|\vv{u}|^2-|\vv{v}|^2.
$$

(b) If the parallelogram has adjacent sides $\vv{u}$ and $\vv{v}$, its diagonals are $\vv{u}+\vv{v}$ and $\vv{u}-\vv{v}$. By (a), the diagonals are perpendicular $\iff(\vv{u}+\vv{v})\cdot(\vv{u}-\vv{v})=0\iff|\vv{u}|=|\vv{v}|$, i.e., all four sides are equal.
:::

## Application: Work

If a constant force $\vv{F}$ moves an object along a displacement $\vv{d}$, only the component of $\vv{F}$ along $\vv{d}$ does work:

$$
W=(\scal_{\vv{d}}\vv{F})\,|\vv{d}|=|\vv{F}|\,|\vv{d}|\cos\theta=\vv{F}\cdot\vv{d}.
$$

Units: newton-meters (joules) or foot-pounds. This formula is the constant-force case of the line integral $\int_C\vv{F}\cdot d\vv{r}$ later in the course.

:::{prf:example} Work Along a Displacement
:label: l03-ex-work
A constant force $\vv{F}=\ip{10,-4,6}$ N moves an object in a straight line from $P(1,1,0)$ to $Q(4,3,2)$, with distances in meters. Find the work done.

*Solution.* $\vv{d}=\vect{PQ}=\ip{3,2,2}$, so $W=\vv{F}\cdot\vv{d}=30-8+12=34$ J.
:::

::::{admonition} Concept Check
:class: hint
If $\vv{u}\cdot\vv{v}=\vv{u}\cdot\vv{w}$ and $\vv{u}\neq\vzero$, must $\vv{v}=\vv{w}$?

:::{dropdown} Answer
No. The hypothesis says only that $\vv{u}\cdot(\vv{v}-\vv{w})=0$, i.e., $\vv{v}-\vv{w}\perp\vv{u}$. Example: $\vv{u}=\ip{1,0}$, $\vv{v}=\ip{0,1}$, $\vv{w}=\ip{0,2}$ give $\vv{u}\cdot\vv{v}=\vv{u}\cdot\vv{w}=0$ but $\vv{v}\neq\vv{w}$. There is no "cancellation law" for the dot product.
:::
::::

## Common Errors

:::{caution} Avoid these errors
- Treating $\vv{u}\cdot\vv{v}$ as a vector. It is a scalar, so expressions like $(\vv{u}\cdot\vv{v})\cdot\vv{w}$ are meaningless.
- Dividing by $|\vv{v}|$ instead of $|\vv{v}|^2$ in $\proj_{\vv{v}}\vv{u}$. The result must be a vector parallel to $\vv{v}$.
- Projecting onto the wrong vector: $\proj_{\vv{v}}\vv{u}$ is parallel to $\vv{v}$, and in general $\proj_{\vv{v}}\vv{u}\neq\proj_{\vv{u}}\vv{v}$.
- Reporting an angle greater than $\pi$, or forgetting that $\arccos$ already returns a value in $[0,\pi]$.
- Confusing Briggs's scalar component $\vv{u}\cdot\vv{v}/|\vv{v}|$ with Lang's component $\vv{u}\cdot\vv{v}/(\vv{v}\cdot\vv{v})$.
:::

## Summary

:::{admonition} Key takeaways
:class: summary
- $\vv{u}\cdot\vv{v}=\sum u_iv_i=|\vv{u}|\,|\vv{v}|\cos\theta$; $\;\vv{u}\cdot\vv{u}=|\vv{u}|^2$; properties SP 1–SP 4.
- $\vv{u}\perp\vv{v}\iff\vv{u}\cdot\vv{v}=0$; the sign of $\vv{u}\cdot\vv{v}$ tells whether $\theta$ is acute or obtuse.
- $\scal_{\vv{v}}\vv{u}=\dfrac{\vv{u}\cdot\vv{v}}{|\vv{v}|}$, $\;\proj_{\vv{v}}\vv{u}=\dfrac{\vv{u}\cdot\vv{v}}{|\vv{v}|^2}\vv{v}$, and $\vv{u}-\proj_{\vv{v}}\vv{u}\perp\vv{v}$.
- Cauchy–Schwarz: $|\vv{u}\cdot\vv{v}|\le|\vv{u}|\,|\vv{v}|$; triangle inequality: $|\vv{u}+\vv{v}|\le|\vv{u}|+|\vv{v}|$.
- Work by a constant force: $W=\vv{F}\cdot\vv{d}$.
:::

## In-Class Practice

Try each problem before opening its solution.

:::{exercise}
:label: l03-practice-1
Compute $\vv{u}\cdot\vv{v}$ for $\vv{u}=\ip{2,-1,4}$ and $\vv{v}=\ip{-3,5,2}$.
:::

:::{solution} l03-practice-1
:class: dropdown
$\vv{u}\cdot\vv{v}=2(-3)+(-1)(5)+4(2)=-6-5+8=-3$. (Negative, so the angle between them is obtuse.)
:::

:::{exercise}
:label: l03-practice-2
Find the angle between $\vv{a}=\ip{1,0,-1}$ and $\vv{b}=\ip{0,1,1}$.
:::

:::{solution} l03-practice-2
:class: dropdown
$\vv{a}\cdot\vv{b}=0+0-1=-1$ and $|\vv{a}|=|\vv{b}|=\sqrt2$, so $\cos\theta=\dfrac{-1}{2}$ and $\theta=\dfrac{2\pi}{3}$ ($120^\circ$).
:::

:::{exercise}
:label: l03-practice-3
For which value of $t$ is $\ip{2,t,-3}$ orthogonal to $\ip{1,6,2}$?
:::

:::{solution} l03-practice-3
:class: dropdown
$\ip{2,t,-3}\cdot\ip{1,6,2}=2+6t-6=6t-4$. Setting $6t-4=0$ gives $t=\tfrac23$.
:::

:::{exercise}
:label: l03-practice-4
Find $\proj_{\vv{v}}\vv{u}$ and the orthogonal component $\vv{u}-\proj_{\vv{v}}\vv{u}$ for $\vv{u}=\ip{4,3}$ and $\vv{v}=\ip{1,2}$. Verify that the orthogonal component is perpendicular to $\vv{v}$.
:::

:::{solution} l03-practice-4
:class: dropdown
$\vv{u}\cdot\vv{v}=4+6=10$ and $|\vv{v}|^2=5$, so $\proj_{\vv{v}}\vv{u}=\tfrac{10}{5}\ip{1,2}=\ip{2,4}$. The orthogonal component is $\ip{4,3}-\ip{2,4}=\ip{2,-1}$, and $\ip{2,-1}\cdot\ip{1,2}=2-2=0$. $\checkmark$
:::

:::{exercise}
:label: l03-practice-5
A sled is pulled $50$ ft along level ground by a rope that makes a $40^\circ$ angle with the horizontal. The tension in the rope is $80$ lb. Find the work done.
:::

:::{solution} l03-practice-5
:class: dropdown
The displacement is horizontal with $|\vv{d}|=50$ ft, and the force has $|\vv{F}|=80$ lb at $\theta=40^\circ$ to $\vv{d}$. Hence $W=|\vv{F}|\,|\vv{d}|\cos\theta=80\cdot50\cos40^\circ=4000\cos40^\circ\approx3064$ ft-lb.
:::

## Before the Next Class

Read Briggs §13.4 and Lang, Ch. I, §7 (The Cross Product). Review $2\times2$ determinants. Next: [Lecture 04 — Cross Products](lecture-04.md).
