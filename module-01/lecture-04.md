---
title: Lecture 04 — Cross Products
short_title: 04 · Cross Products
description: The cross product by components and determinants, its algebraic properties, its magnitude and direction, areas of parallelograms and triangles, and torque.
date: 2026-09-03
numbering:
  enumerator: "4.%s"
---

:::{div}
:class: lecture-meta
**Class meeting:** Thursday, September 3, 2026  
**Reading:** Briggs §13.4; Lang, Ch. I, §7 (The Cross Product)  
**Prerequisites:** [Lecture 03](lecture-03.md): dot product, angle formula, orthogonality; $2\times2$ determinants.  
**PDF version:** [Lecture 04 notes (PDF)](../downloads/MTSC451_Lecture_04.pdf)
:::

## Learning Objectives

After this lecture you should be able to:

1. compute $\vv{u}\times\vv{v}$ by the component formula, the determinant, and the rules for $\vvi,\vvj,\vvk$;
2. use Lang's properties CP 1–CP 6 and prove the basic ones from the definition;
3. derive and apply $|\vv{u}\times\vv{v}|=|\vv{u}|\,|\vv{v}|\sin\theta$;
4. find areas of parallelograms and triangles and test vectors for parallelism;
5. compute torque as a cross product.

## Motivation

Many problems in $\R^3$ require a vector perpendicular to two given vectors: the normal vector of a plane through three points ([Lecture 05](lecture-05.md)), the axis of a rotation, the direction of a torque. Solving $\vv{n}\cdot\vv{u}=0$ and $\vv{n}\cdot\vv{v}=0$ by hand every time is tedious. The cross product produces such a vector directly, and its length turns out to measure area. Unlike the dot product, the cross product is special to $\R^3$.

## Definition

:::{prf:definition} Cross Product
:label: l04-def-cross
For $\vv{u}=\ip{u_1,u_2,u_3}$ and $\vv{v}=\ip{v_1,v_2,v_3}$ in $\R^3$,

$$
\vv{u}\times\vv{v}=\ip{\,u_2v_3-u_3v_2,\;\; u_3v_1-u_1v_3,\;\; u_1v_2-u_2v_1\,}.
$$

The result is a *vector* in $\R^3$.
:::

The formula is easiest to remember as a formal determinant expanded along the first row:

$$
\vv{u}\times\vv{v}=\begin{vmatrix}\vvi&\vvj&\vvk\\u_1&u_2&u_3\\v_1&v_2&v_3\end{vmatrix}
=\begin{vmatrix}u_2&u_3\\v_2&v_3\end{vmatrix}\vvi
-\begin{vmatrix}u_1&u_3\\v_1&v_3\end{vmatrix}\vvj
+\begin{vmatrix}u_1&u_2\\v_1&v_2\end{vmatrix}\vvk .
$$

Note the minus sign on the $\vvj$-term: $-(u_1v_3-u_3v_1)=u_3v_1-u_1v_3$.

:::{admonition} Notation: Briggs and Lang
:class: note notation
Lang defines $A\times B$ by the component formula above, as we do. Briggs introduces the cross product geometrically (magnitude $|\vv{u}|\,|\vv{v}|\sin\theta$, direction by the right-hand rule) and then derives the determinant formula. We take the component formula as the definition and *prove* the geometric description ([Geometric Meaning](#l04-sec-geometric)).
:::

:::{prf:example} Computing a Cross Product
:label: l04-ex-compute
Compute $\vv{u}\times\vv{v}$ for $\vv{u}=\ip{2,-1,3}$ and $\vv{v}=\ip{1,4,-2}$, and verify that the result is orthogonal to $\vv{u}$ and $\vv{v}$.

*Solution.*

$$
\begin{aligned}
\vv{u}\times\vv{v}&=\begin{vmatrix}\vvi&\vvj&\vvk\\2&-1&3\\1&4&-2\end{vmatrix}\\
&=\bigl((-1)(-2)-3\cdot4\bigr)\vvi-\bigl(2(-2)-3\cdot1\bigr)\vvj+\bigl(2\cdot4-(-1)\cdot1\bigr)\vvk\\
&=\ip{-10,\,7,\,9}.
\end{aligned}
$$

Check: $\ip{-10,7,9}\cdot\vv{u}=-20-7+27=0$ and $\ip{-10,7,9}\cdot\vv{v}=-10+28-18=0$. $\checkmark$
:::

**Standard unit vectors.** Directly from the definition,

$$
\vvi\times\vvj=\vvk,\qquad\vvj\times\vvk=\vvi,\qquad\vvk\times\vvi=\vvj,
$$

and reversing the order changes the sign ($\vvj\times\vvi=-\vvk$, etc.), while $\vvi\times\vvi=\vvj\times\vvj=\vvk\times\vvk=\vzero$. Going around the cycle $\vvi\to\vvj\to\vvk\to\vvi$ gives $+$; going against it gives $-$.

:::{prf:example} Using the $\vvi,\vvj,\vvk$ Rules
:label: l04-ex-unit-rules
Compute $(2\vvi-\vvj)\times(\vvi+3\vvk)$ using only the distributive law and the unit-vector rules, and confirm with the determinant.

*Solution.*

$$
\begin{aligned}
(2\vvi-\vvj)\times(\vvi+3\vvk)&=2(\vvi\times\vvi)+6(\vvi\times\vvk)-(\vvj\times\vvi)-3(\vvj\times\vvk)\\
&=\vzero-6\vvj+\vvk-3\vvi .
\end{aligned}
$$

So the result is $\ip{-3,-6,1}$. Determinant check with $\ip{2,-1,0}\times\ip{1,0,3}$: $\ip{(-1)(3)-0\cdot0,\;0\cdot1-2\cdot3,\;2\cdot0-(-1)\cdot1}=\ip{-3,-6,1}$. $\checkmark$
:::

## Algebraic Properties

:::{prf:theorem} Properties of the Cross Product (Lang's CP 1–CP 6)
:label: l04-thm-properties
For $\vv{u},\vv{v},\vv{w}\in\R^3$ and a scalar $a$:

- **CP 1** $\vv{u}\times\vv{v}=-(\vv{v}\times\vv{u})$ (anticommutativity).
- **CP 2** $\vv{u}\times(\vv{v}+\vv{w})=\vv{u}\times\vv{v}+\vv{u}\times\vv{w}$ and $(\vv{v}+\vv{w})\times\vv{u}=\vv{v}\times\vv{u}+\vv{w}\times\vv{u}$.
- **CP 3** $(a\vv{u})\times\vv{v}=a(\vv{u}\times\vv{v})=\vv{u}\times(a\vv{v})$.
- **CP 4** $(\vv{u}\times\vv{v})\times\vv{w}=(\vv{u}\cdot\vv{w})\vv{v}-(\vv{v}\cdot\vv{w})\vv{u}$.
- **CP 5** $\vv{u}\times\vv{v}$ is orthogonal to both $\vv{u}$ and $\vv{v}$.
- **CP 6** $|\vv{u}\times\vv{v}|^2=|\vv{u}|^2|\vv{v}|^2-(\vv{u}\cdot\vv{v})^2$ (Lagrange's identity).

Consequences: $\vv{u}\times\vv{u}=\vzero$; and the cross product is *not* associative.
:::

:::{prf:proof} of CP 1, CP 5, and $\vv{u}\times\vv{u}=\vzero$
:nonumber:
Interchanging $\vv{u}$ and $\vv{v}$ in each component, e.g. $u_2v_3-u_3v_2\mapsto v_2u_3-v_3u_2$, changes every sign; this is CP 1. Taking $\vv{v}=\vv{u}$ in CP 1 gives $\vv{u}\times\vv{u}=-(\vv{u}\times\vv{u})$, hence $\vv{u}\times\vv{u}=\vzero$. For CP 5,

$$
\begin{aligned}
\vv{u}\cdot(\vv{u}\times\vv{v})&=u_1(u_2v_3-u_3v_2)+u_2(u_3v_1-u_1v_3)\\
&\quad+u_3(u_1v_2-u_2v_1)=0,
\end{aligned}
$$

because the six terms cancel in pairs; the computation for $\vv{v}$ is identical. CP 2, CP 3, CP 4, and CP 6 are verified by expanding both sides in components (Lang leaves CP 1–CP 4 as exercises and checks CP 6 by direct expansion).
:::

*Non-associativity.* $\vvi\times(\vvi\times\vvj)=\vvi\times\vvk=-\vvj$, but $(\vvi\times\vvi)\times\vvj=\vzero\times\vvj=\vzero$. Parentheses matter.

(l04-sec-geometric)=
## Geometric Meaning

:::{prf:theorem} Magnitude of the Cross Product
:label: l04-thm-magnitude
If $\theta\in[0,\pi]$ is the angle between nonzero vectors $\vv{u}$ and $\vv{v}$, then

$$
|\vv{u}\times\vv{v}|=|\vv{u}|\,|\vv{v}|\sin\theta .
$$
:::

:::{prf:proof}
:nonumber:
By CP 6 and $\vv{u}\cdot\vv{v}=|\vv{u}|\,|\vv{v}|\cos\theta$,

$$
|\vv{u}\times\vv{v}|^2=|\vv{u}|^2|\vv{v}|^2(1-\cos^2\theta)=|\vv{u}|^2|\vv{v}|^2\sin^2\theta.
$$

Since $\sin\theta\ge0$ on $[0,\pi]$, take square roots.
:::

**Direction.** By CP 5, $\vv{u}\times\vv{v}$ is perpendicular to the plane spanned by $\vv{u}$ and $\vv{v}$. Of the two perpendicular directions, it is the one given by the **right-hand rule**: curl the fingers of the right hand from $\vv{u}$ toward $\vv{v}$; the thumb points along $\vv{u}\times\vv{v}$. (This is consistent with $\vvi\times\vvj=\vvk$ in a right-handed coordinate system.)

```{figure} ../assets/figures/lecture-04-fig-1.svg
:label: l04-fig-area
:alt: A shaded parallelogram with adjacent sides u along the bottom and v rising to the upper left from the same corner, with angle theta between them. A dashed vertical segment from the head of v down to the base marks the height h equal to the length of v times sine theta. The label below reads: Area equals the length of u times h, which equals the length of u cross v.
:width: 480px

The parallelogram spanned by $\vv{u}$ and $\vv{v}$ has base $|\vv{u}|$ and height $h=|\vv{v}|\sin\theta$.
```

:::{admonition} Key Idea
:class: tip
$|\vv{u}\times\vv{v}|$ is the **area of the parallelogram** with adjacent sides $\vv{u}$ and $\vv{v}$ (base $|\vv{u}|$, height $|\vv{v}|\sin\theta$). The triangle with these two sides has area $\tfrac12|\vv{u}\times\vv{v}|$.
:::

:::{prf:theorem} Parallel Vectors Test
:label: l04-thm-parallel
Two vectors $\vv{u},\vv{v}\in\R^3$ are parallel if and only if $\vv{u}\times\vv{v}=\vzero$.
:::

:::{prf:proof}
:nonumber:
If either vector is $\vzero$, both statements hold. Otherwise $|\vv{u}\times\vv{v}|=0\iff\sin\theta=0\iff\theta\in\{0,\pi\}$, which means the vectors are parallel.
:::

:::{prf:example} Area of a Triangle
:label: l04-ex-triangle
Find the area of the parallelogram and of the triangle determined by $P(1,0,2)$, $Q(3,1,1)$, $R(0,2,3)$, with $\vect{PQ}$ and $\vect{PR}$ as adjacent sides.

*Solution.* $\vect{PQ}=\ip{2,1,-1}$ and $\vect{PR}=\ip{-1,2,1}$, so

$$
\begin{aligned}
\vect{PQ}\times\vect{PR}&=\ip{1\cdot1-(-1)\cdot2,\;(-1)(-1)-2\cdot1,\;2\cdot2-1\cdot(-1)}\\
&=\ip{3,-1,5}.
\end{aligned}
$$

The parallelogram has area $|\ip{3,-1,5}|=\sqrt{9+1+25}=\sqrt{35}$, and triangle $PQR$ has area $\tfrac{\sqrt{35}}{2}$.
:::

:::{prf:example} Checking the Magnitude Formula
:label: l04-ex-magnitude
For $\vv{u}=\ip{1,1,0}$ and $\vv{v}=\ip{0,1,1}$, compute $|\vv{u}\times\vv{v}|$ two ways.

*Solution.* Directly, $\vv{u}\times\vv{v}=\ip{1\cdot1-0\cdot1,\;0\cdot0-1\cdot1,\;1\cdot1-1\cdot0}=\ip{1,-1,1}$, so $|\vv{u}\times\vv{v}|=\sqrt3$. Geometrically, $|\vv{u}|=|\vv{v}|=\sqrt2$ and $\cos\theta=\dfrac{1}{2}$, so $\theta=\pi/3$, $\sin\theta=\tfrac{\sqrt3}{2}$, and $|\vv{u}|\,|\vv{v}|\sin\theta=2\cdot\tfrac{\sqrt3}{2}=\sqrt3$. $\checkmark$
:::

## Interactive Exploration

The figure shows $\vv{u}$, $\vv{v}$, the parallelogram they span, and $\vv{u}\times\vv{v}$. The starting vectors are $\vect{PQ}=\ip{2,1,-1}$ and $\vect{PR}=\ip{-1,2,1}$ from {prf:ref}`l04-ex-triangle`. Type new components, and drag the figure to rotate it; the readout checks CP 5 and Lagrange's identity numerically. Things to try:

- Confirm $\vv{u}\times\vv{v}=\ip{3,-1,5}$ and the area $\sqrt{35}\approx5.916$, then turn on the triangle to see the area $\tfrac{\sqrt{35}}{2}$.
- Press "Swap u and v": the parallelogram is unchanged, but the cross product reverses direction (CP 1).
- Enter $\vv{u}=\ip{4,-2,6}$ and $\vv{v}=\ip{-6,3,-9}$ (In-Class Practice 5): the parallelogram collapses and $\vv{u}\times\vv{v}=\vzero$.

:::{anywidget} ../interactive/mathviz.mjs
{"widget": "crossproduct", "u": [2, 1, -1], "v": [-1, 2, 1]}
:::

## Application: Torque

If a force $\vv{F}$ is applied at the point with position vector $\vv{r}$ relative to a pivot $O$, the **torque** about $O$ is $\boldsymbol{\tau}=\vv{r}\times\vv{F}$. Its magnitude $|\vv{r}|\,|\vv{F}|\sin\theta$ measures the turning effect, and its direction is the axis of rotation given by the right-hand rule. Only the component of $\vv{F}$ perpendicular to $\vv{r}$ produces torque.

:::{prf:example} Torque on a Wrench
:label: l04-ex-torque
A wrench lies along the positive $x$-axis with the bolt at the origin. A force $\vv{F}=\ip{0,20,-10}$ N is applied $0.3$ m from the bolt. Find the torque and its magnitude.

*Solution.* $\vv{r}=\ip{0.3,0,0}$ and

$$
\begin{aligned}
\boldsymbol{\tau}=\vv{r}\times\vv{F}&=\ip{0\cdot(-10)-0\cdot20,\;0\cdot0-0.3(-10),\;0.3\cdot20-0\cdot0}\\
&=\ip{0,3,6}\text{ N}\cdot\text{m}.
\end{aligned}
$$

Its magnitude is $\sqrt{0+9+36}=\sqrt{45}=3\sqrt5\approx6.71$ N$\cdot$m. (The $x$-component of $\vv{F}$ is $0$; a force along the handle would produce no torque.)
:::

:::{prf:example} A Short Proof Using CP 6
:label: l04-ex-proof-cp6
Prove: if $\vv{u}\times\vv{v}=\vzero$ and $\vv{u}\cdot\vv{v}=0$, then $\vv{u}=\vzero$ or $\vv{v}=\vzero$.

*Solution.* Lagrange's identity CP 6 can be written $|\vv{u}\times\vv{v}|^2+(\vv{u}\cdot\vv{v})^2=|\vv{u}|^2|\vv{v}|^2$. Under the hypotheses the left side is $0$, so $|\vv{u}|\,|\vv{v}|=0$, and therefore $|\vv{u}|=0$ or $|\vv{v}|=0$. Geometrically: two nonzero vectors cannot be both parallel and perpendicular.
:::

::::{admonition} Concept Check
:class: hint
Is $\vv{u}\times\vv{v}$ the *only* vector perpendicular to both $\vv{u}$ and $\vv{v}$?

:::{dropdown} Answer
No. If $\vv{u}$ and $\vv{v}$ are not parallel, every scalar multiple $c(\vv{u}\times\vv{v})$ is perpendicular to both, and these are the only such vectors (the vectors perpendicular to a plane form a line through the origin). In particular, $\vv{v}\times\vv{u}=-(\vv{u}\times\vv{v})$ is the opposite choice. If $\vv{u}$ and $\vv{v}$ are parallel, many non-parallel vectors are perpendicular to both, while $\vv{u}\times\vv{v}=\vzero$.
:::
::::

## Dot Product vs. Cross Product

| | **Dot product** $\vv{u}\cdot\vv{v}$ | **Cross product** $\vv{u}\times\vv{v}$ |
|---|---|---|
| Output | scalar | vector |
| Defined in | $\R^n$ | $\R^3$ only |
| Geometric size | $\lvert\vv{u}\rvert\,\lvert\vv{v}\rvert\cos\theta$ | $\lvert\vv{u}\rvert\,\lvert\vv{v}\rvert\sin\theta$ |
| Order | commutative | anticommutative |
| Equals zero when | $\vv{u}\perp\vv{v}$ | $\vv{u}\parallel\vv{v}$ |
| Typical use | angles, projections, work | normals, area, torque |

## Common Errors

:::{caution} Avoid these errors
- Dropping the minus sign on the $\vvj$-component of the determinant.
- Reversing the order: $\vv{v}\times\vv{u}=-(\vv{u}\times\vv{v})$, which reverses the direction of a normal or torque.
- Assuming associativity: in general $\vv{u}\times(\vv{v}\times\vv{w})\neq(\vv{u}\times\vv{v})\times\vv{w}$.
- Using $|\vv{u}\times\vv{v}|$ for the area of a *triangle*; the triangle's area is half of it.
- Writing $|\vv{u}\times\vv{v}|=|\vv{u}|\,|\vv{v}|\cos\theta$ (that is the dot product).
- Taking cross products of vectors in $\R^2$. Embed them first as $\ip{a,b,0}$.
:::

## Summary

:::{admonition} Key takeaways
:class: summary
- $\vv{u}\times\vv{v}=\ip{u_2v_3-u_3v_2,\,u_3v_1-u_1v_3,\,u_1v_2-u_2v_1}$ (determinant form).
- $\vvi\times\vvj=\vvk$, $\vvj\times\vvk=\vvi$, $\vvk\times\vvi=\vvj$; reversing order changes sign.
- CP 1–CP 6; in particular $\vv{u}\times\vv{v}\perp\vv{u},\vv{v}$ and $|\vv{u}\times\vv{v}|^2=|\vv{u}|^2|\vv{v}|^2-(\vv{u}\cdot\vv{v})^2$.
- $|\vv{u}\times\vv{v}|=|\vv{u}|\,|\vv{v}|\sin\theta=$ area of the parallelogram; direction by the right-hand rule.
- $\vv{u}\parallel\vv{v}\iff\vv{u}\times\vv{v}=\vzero$. Torque: $\boldsymbol{\tau}=\vv{r}\times\vv{F}$.
:::

## In-Class Practice

Try each problem before opening its solution.

:::{exercise}
:label: l04-practice-1
Compute $\vv{u}\times\vv{v}$ for $\vv{u}=\ip{1,0,-3}$ and $\vv{v}=\ip{2,4,1}$. Verify that the result is perpendicular to both $\vv{u}$ and $\vv{v}$.
:::

:::{solution} l04-practice-1
:class: dropdown
$\vv{u}\times\vv{v}=\ip{0\cdot1-(-3)\cdot4,\;(-3)\cdot2-1\cdot1,\;1\cdot4-0\cdot2}=\ip{12,-7,4}$.

Check: $\ip{12,-7,4}\cdot\ip{1,0,-3}=12-12=0$ and $\ip{12,-7,4}\cdot\ip{2,4,1}=24-28+4=0$. $\checkmark$
:::

:::{exercise}
:label: l04-practice-2
Find the area of the parallelogram with adjacent sides $\vv{a}=\ip{3,1,-2}$ and $\vv{b}=\ip{0,4,1}$.
:::

:::{solution} l04-practice-2
:class: dropdown
$\vv{a}\times\vv{b}=\ip{1\cdot1-(-2)\cdot4,\;(-2)\cdot0-3\cdot1,\;3\cdot4-1\cdot0}=\ip{9,-3,12}$, so the area is $\sqrt{81+9+144}=\sqrt{234}=3\sqrt{26}\approx15.30$.
:::

:::{exercise}
:label: l04-practice-3
Find the area of the triangle with vertices $A(1,1,0)$, $B(2,0,3)$, $C(-1,1,2)$.
:::

:::{solution} l04-practice-3
:class: dropdown
$\vect{AB}=\ip{1,-1,3}$ and $\vect{AC}=\ip{-2,0,2}$. Then

$$
\begin{aligned}
\vect{AB}\times\vect{AC}&=\ip{(-1)(2)-3\cdot0,\;3(-2)-1\cdot2,\;1\cdot0-(-1)(-2)}\\
&=\ip{-2,-8,-2},
\end{aligned}
$$

with length $\sqrt{4+64+4}=\sqrt{72}=6\sqrt2$. The triangle's area is $\tfrac12\cdot6\sqrt2=3\sqrt2$.
:::

:::{exercise}
:label: l04-practice-4
Find a unit vector perpendicular to both $\ip{2,1,0}$ and $\ip{0,1,3}$.
:::

:::{solution} l04-practice-4
:class: dropdown
$\ip{2,1,0}\times\ip{0,1,3}=\ip{1\cdot3-0\cdot1,\;0\cdot0-2\cdot3,\;2\cdot1-1\cdot0}=\ip{3,-6,2}$, with length $\sqrt{9+36+4}=7$. A unit vector is $\ip{\tfrac37,-\tfrac67,\tfrac27}$; its negative $\ip{-\tfrac37,\tfrac67,-\tfrac27}$ is the other answer.
:::

:::{exercise}
:label: l04-practice-5
Show that $\ip{4,-2,6}$ and $\ip{-6,3,-9}$ are parallel by computing their cross product.
:::

:::{solution} l04-practice-5
:class: dropdown
$\ip{4,-2,6}\times\ip{-6,3,-9}=\ip{(-2)(-9)-6\cdot3,\;6(-6)-4(-9),\;4\cdot3-(-2)(-6)}=\ip{0,0,0}$. By the parallel vectors test ({prf:ref}`l04-thm-parallel`) the vectors are parallel; indeed $\ip{-6,3,-9}=-\tfrac32\ip{4,-2,6}$, so they point in opposite directions.
:::

## Before the Next Class

Read Briggs §13.5 and Lang, Ch. I, §5 (Parametric Lines) and §6 (Planes). Next: [Lecture 05 — Lines and Planes in Space](lecture-05.md).
