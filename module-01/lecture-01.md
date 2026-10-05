---
title: Lecture 01 — Vectors in the Plane
short_title: 01 · Vectors in the Plane
description: Scalars and vectors, equality, addition and scalar multiplication, components, magnitude, unit vectors, and applications to velocity and force.
date: 2026-08-25
numbering:
  enumerator: "1.%s"
---

:::{div}
:class: lecture-meta
**Class meeting:** Tuesday, August 25, 2026  
**Reading:** Briggs §13.1; Lang, Ch. I, §1 (Definition of Points in Space) and §2 (Located Vectors)  
**Prerequisites:** Cartesian plane, Pythagorean theorem, basic trigonometry.  
**PDF version:** [Lecture 01 notes (PDF)](../downloads/MTSC451_Lecture_01.pdf)
:::

## Learning Objectives

After this lecture you should be able to:

1. distinguish scalars from vectors and decide when two vectors are equal;
2. add, subtract, and scale vectors geometrically and in components;
3. compute the components and magnitude of the vector between two points;
4. construct unit vectors and vectors of a prescribed length and direction;
5. model velocity and force problems with vectors.

## Motivation

Many quantities are described by a single number: temperature, mass, time. Others need both a size and a direction: the velocity of an airplane, the force on a beam, the displacement from one city to another. Two airplanes flying at 500 mph are not doing the same thing if one heads north and the other heads east. Vectors are the mathematical objects that record magnitude and direction together, and almost everything in this course—gradients, tangent planes, line integrals, Green's Theorem—is built on them.

:::{admonition} Notation: Briggs and Lang
:class: note notation
Briggs writes vectors in bold lowercase ($\vv{u},\vv{v}$), components in angle brackets $\ip{v_1,v_2}$, points in parentheses $(x,y)$, and magnitude as $|\vv{v}|$. Lang writes points and vectors as capital letters ($A=(a_1,a_2)$), uses parentheses for both, writes the norm as $\|A\|$, and writes the located vector from $A$ to $B$ as $\vect{AB}$. **In this course** we use Briggs's notation ($\vv{v}=\ip{v_1,v_2}$, $|\vv{v}|$) and Lang's $\vect{PQ}$ for the vector from $P$ to $Q$. When you read Lang, translate $A\leftrightarrow\vv{a}$ and $\|A\|\leftrightarrow|\vv{a}|$.
:::

## Vectors, Equality, and Scalar Multiplication

A **scalar** is a real number. A **vector** is a quantity with magnitude and direction, drawn as an arrow from a *tail* (initial point) to a *head* (terminal point). The vector from $P$ to $Q$ is written $\vect{PQ}$.

:::{prf:definition} Equal Vectors
:label: l01-def-equal
Two vectors are **equal** if they have the same magnitude and the same direction. Their locations in the plane are irrelevant.
:::

Lang makes this precise. A *located vector* $\vect{AB}$ is an ordered pair of points. Two located vectors $\vect{AB}$ and $\vect{CD}$ are **equivalent** if $B-A=D-C$. Every located vector is equivalent to exactly one located vector starting at the origin, namely $\vect{O(B-A)}$. A "vector" in Briggs's sense is exactly an equivalence class of located vectors, and we identify it with the single pair of numbers $B-A$.

:::{prf:definition} Scalar Multiple
:label: l01-def-scalar-multiple
For a scalar $c$ and a vector $\vv{v}$, the **scalar multiple** $c\vv{v}$ has magnitude $|c|\,|\vv{v}|$. It points in the direction of $\vv{v}$ if $c>0$ and in the opposite direction if $c<0$. If $c=0$ or $\vv{v}=\vzero$, then $c\vv{v}=\vzero$.
:::

Two nonzero vectors are **parallel** if one is a scalar multiple of the other. Following Lang, they have the *same direction* if $\vv{u}=c\vv{v}$ with $c>0$ and *opposite directions* if $c<0$. By convention the zero vector $\vzero$ is parallel to every vector.

## Addition and Subtraction

**Triangle Rule.** To form $\vv{u}+\vv{v}$, place the tail of $\vv{v}$ at the head of $\vv{u}$; the sum runs from the tail of $\vv{u}$ to the head of $\vv{v}$.

**Parallelogram Rule.** Place $\vv{u}$ and $\vv{v}$ tail to tail and complete the parallelogram; $\vv{u}+\vv{v}$ is the diagonal starting at the common tail.

```{figure} ../assets/figures/lecture-01-fig-1.svg
:label: l01-fig-addition
:alt: Two diagrams. Left, the triangle rule: vector v starts at the head of vector u, and u plus v runs from the tail of u to the head of v. Right, the parallelogram rule: u and v start at the same point, the parallelogram is completed with dashed sides, u plus v is the diagonal from the common tail, and the other diagonal, v minus u, runs from the head of u to the head of v.
:width: 640px

The triangle rule (left) and the parallelogram rule (right). The gray diagonal is $\vv{v}-\vv{u}$.
```

The difference $\vv{u}-\vv{v}$ means $\vv{u}+(-\vv{v})$. Geometrically, with $\vv{u}$ and $\vv{v}$ tail to tail, $\vv{u}-\vv{v}$ runs from the head of $\vv{v}$ to the head of $\vv{u}$ (in the figure, the gray diagonal is $\vv{v}-\vv{u}$).

## Components

A vector whose tail is at the origin is in **standard position**; if its head is at $(v_1,v_2)$, we write $\vv{v}=\ip{v_1,v_2}$ and call $v_1,v_2$ its **components**. This is the same as the position vector of the point $(v_1,v_2)$.

:::{admonition} Key Idea
:class: tip
If $P(x_1,y_1)$ and $Q(x_2,y_2)$, then

$$
\vect{PQ}=\ip{x_2-x_1,\;y_2-y_1},\qquad
|\vect{PQ}|=\sqrt{(x_2-x_1)^2+(y_2-y_1)^2}.
$$

In Lang's language: $\vect{PQ}$ is equivalent to the located vector from $O$ to $Q-P$.
:::

:::{prf:definition} Magnitude
:label: l01-def-magnitude
The **magnitude** (length, norm) of $\vv{v}=\ip{v_1,v_2}$ is $|\vv{v}|=\sqrt{v_1^2+v_2^2}$.
:::

In components, the operations become coordinatewise:

$$
\vv{u}\pm\vv{v}=\ip{u_1\pm v_1,\;u_2\pm v_2},\qquad c\vv{v}=\ip{cv_1,\;cv_2}.
$$

This is exactly Lang's definition of addition and scalar multiplication of $n$-tuples, specialized to $n=2$. A direct computation gives $|c\vv{v}|=\sqrt{c^2v_1^2+c^2v_2^2}=|c|\,|\vv{v}|$, consistent with the geometric definition.

:::{prf:example} Equivalent and Parallel Located Vectors
:label: l01-ex-equivalent
Let $P(1,-2)$, $Q(4,3)$, $R(-2,0)$, $S(1,5)$, $T(0,1)$, $U(6,11)$. Show that $\vect{PQ}=\vect{RS}$, and decide whether $\vect{TU}$ is parallel to $\vect{PQ}$.

*Solution.* $\vect{PQ}=\ip{4-1,\,3-(-2)}=\ip{3,5}$ and $\vect{RS}=\ip{1-(-2),\,5-0}=\ip{3,5}$, so the two located vectors are equivalent: same components, different locations. Next, $\vect{TU}=\ip{6,10}=2\ip{3,5}=2\,\vect{PQ}$. Since $2>0$, $\vect{TU}$ is parallel to $\vect{PQ}$ and has the same direction, with twice the length.
:::

:::{prf:example} Vector Arithmetic
:label: l01-ex-arithmetic
Let $\vv{u}=\ip{3,-1}$ and $\vv{v}=\ip{-2,4}$. Compute $\vv{u}+\vv{v}$, $2\vv{u}-3\vv{v}$, and $|2\vv{u}-3\vv{v}|$.

*Solution.* $\vv{u}+\vv{v}=\ip{3-2,\,-1+4}=\ip{1,3}$. Next, $2\vv{u}-3\vv{v}=\ip{6,-2}-\ip{-6,12}=\ip{12,-14}$, so

$$
|2\vv{u}-3\vv{v}|=\sqrt{12^2+(-14)^2}=\sqrt{340}=2\sqrt{85}.
$$
:::

## Interactive Exploration

Drag the heads of $\vv{u}$ and $\vv{v}$, or type their components. The figure draws the parallelogram for $\vv{u}+\vv{v}$ and the difference $\vv{u}-\vv{v}$ from the head of $\vv{v}$ to the head of $\vv{u}$; the slider scales $\vv{u}$ by $c$. Things to try:

- Make $\vv{v}$ a positive multiple of $\vv{u}$. When does $|\vv{u}+\vv{v}|=|\vv{u}|+|\vv{v}|$?
- Move the slider through $c=0$ and watch $c\vv{u}$ reverse direction, with length $|c|\,|\vv{u}|$.
- Set $\vv{u}=\ip{3,0}$ and $\vv{v}=\ip{0,4}$ and compare $|\vv{u}+\vv{v}|$ with $|\vv{u}|+|\vv{v}|$.

:::{anywidget} ../interactive/mathviz.mjs
{"widget": "vectors2d", "u": [3, 1], "v": [1, 2], "c": 1.5}
:::

## Unit Vectors and the Standard Basis

:::{prf:definition} Unit Vector
:label: l01-def-unit-vector
A **unit vector** is a vector of magnitude $1$. For any $\vv{v}\neq\vzero$, the vector $\dfrac{\vv{v}}{|\vv{v}|}$ is the unit vector in the direction of $\vv{v}$.
:::

It is a unit vector because $\bigl|\tfrac{1}{|\vv{v}|}\vv{v}\bigr|=\tfrac{1}{|\vv{v}|}|\vv{v}|=1$. Consequently the vector of length $L>0$ in the direction of $\vv{v}$ is $L\,\vv{v}/|\vv{v}|$, and in the opposite direction it is $-L\,\vv{v}/|\vv{v}|$.

The **standard unit vectors** are $\vvi=\ip{1,0}$ and $\vvj=\ip{0,1}$, and every vector decomposes uniquely as $\ip{v_1,v_2}=v_1\vvi+v_2\vvj$.

If $\vv{v}$ makes angle $\theta$ with the positive $x$-axis, then $\vv{v}=|\vv{v}|\ip{\cos\theta,\sin\theta}$.

:::{prf:example} Unit Vectors and Prescribed Length
:label: l01-ex-unit
Let $\vv{v}=\ip{5,-12}$. Find the unit vector in the direction of $\vv{v}$ and the vector of length $26$ in the same direction.

*Solution.* $|\vv{v}|=\sqrt{25+144}=13$, so the unit vector is $\tfrac{1}{13}\ip{5,-12}=\ip{\tfrac{5}{13},-\tfrac{12}{13}}$. The vector of length $26$ is $26\ip{\tfrac{5}{13},-\tfrac{12}{13}}=\ip{10,-24}=2\vv{v}$.
:::

:::{prf:example} From Magnitude and Direction to Components
:label: l01-ex-polar
A vector $\vv{v}$ has length $8$ and makes an angle of $150^\circ$ with the positive $x$-axis. Write $\vv{v}$ in components and in terms of $\vvi,\vvj$.

*Solution.* $\vv{v}=8\ip{\cos150^\circ,\sin150^\circ}=8\ip{-\tfrac{\sqrt3}{2},\tfrac12}=\ip{-4\sqrt3,\,4}=-4\sqrt3\,\vvi+4\vvj$. Check: $|\vv{v}|=\sqrt{48+16}=8$.
:::

## Properties of Vector Operations

:::{prf:theorem} Properties of Vector Operations
:label: l01-thm-properties
For vectors $\vv{u},\vv{v},\vv{w}$ and scalars $a,c$:

1. $\vv{u}+\vv{v}=\vv{v}+\vv{u}$ (commutative);
2. $(\vv{u}+\vv{v})+\vv{w}=\vv{u}+(\vv{v}+\vv{w})$ (associative);
3. $\vv{v}+\vzero=\vv{v}$ and $\vv{v}+(-\vv{v})=\vzero$;
4. $c(\vv{u}+\vv{v})=c\vv{u}+c\vv{v}$ and $(a+c)\vv{v}=a\vv{v}+c\vv{v}$ (distributive);
5. $a(c\vv{v})=(ac)\vv{v}$, $\;1\vv{v}=\vv{v}$, $\;0\vv{v}=\vzero$.
:::

*Proof idea.* Each property reduces, component by component, to the corresponding property of real numbers. For example, $\vv{u}+\vv{v}=\ip{u_1+v_1,u_2+v_2}=\ip{v_1+u_1,v_2+u_2}=\vv{v}+\vv{u}$. As Lang emphasizes, the same proofs work verbatim for $n$-tuples in $\R^n$.

:::{prf:example} A Vector Proof: Diagonals of a Parallelogram
:label: l01-ex-diagonals
Prove that the diagonals of a parallelogram bisect each other.

*Solution.* Place one vertex at the origin $O$ and let the adjacent sides be the position vectors $\vv{a}$ and $\vv{b}$. The vertices are $O$, $\vv{a}$, $\vv{b}$, and $\vv{a}+\vv{b}$. The diagonal from $O$ to $\vv{a}+\vv{b}$ has midpoint $\tfrac12(\vv{a}+\vv{b})$. The other diagonal joins $\vv{a}$ and $\vv{b}$; its midpoint is $\vv{a}+\tfrac12(\vv{b}-\vv{a})=\tfrac12(\vv{a}+\vv{b})$. The two midpoints coincide, so each diagonal bisects the other.
:::

## Applications: Velocity and Force

Velocities add as vectors: the velocity of an object relative to the ground equals its velocity relative to the medium (air or water) plus the velocity of the medium. Forces acting on an object add as vectors, and the object is in **equilibrium** when the sum of all forces is $\vzero$.

:::{prf:example} Airplane in a Crosswind
:label: l01-ex-airplane
An airplane flies due north with airspeed $400$ mph. A wind blows toward the northeast at $40\sqrt2$ mph. Find the ground speed and the direction of the airplane.

*Solution.* Take east as $\vvi$ and north as $\vvj$. The airplane's velocity relative to the air is $\ip{0,400}$. The wind has magnitude $40\sqrt2$ at $45^\circ$, so it is $40\sqrt2\ip{\tfrac{\sqrt2}{2},\tfrac{\sqrt2}{2}}=\ip{40,40}$. The ground velocity is

$$
\begin{aligned}
\vv{v}&=\ip{0,400}+\ip{40,40}=\ip{40,440},\\
|\vv{v}|&=\sqrt{40^2+440^2}=40\sqrt{122}\approx 441.8\text{ mph}.
\end{aligned}
$$

The heading east of north satisfies $\tan\phi=40/440=1/11$, so $\phi\approx5.19^\circ$ east of north.
:::

:::{prf:example} Equilibrium of Forces
:label: l01-ex-equilibrium
Two forces act on an object: $\vv{F}_1$ of magnitude $10$ lb at angle $30^\circ$ with the positive $x$-axis, and $\vv{F}_2=\ip{-6,8}$ lb. Find the third force $\vv{F}_3$ that keeps the object in equilibrium, and its magnitude.

*Solution.* $\vv{F}_1=10\ip{\cos30^\circ,\sin30^\circ}=\ip{5\sqrt3,5}$. Equilibrium requires $\vv{F}_1+\vv{F}_2+\vv{F}_3=\vzero$, so

$$
\vv{F}_3=-(\vv{F}_1+\vv{F}_2)=-\ip{5\sqrt3-6,\;13}=\ip{6-5\sqrt3,\;-13}.
$$

Since $(6-5\sqrt3)^2=36-60\sqrt3+75=111-60\sqrt3$, we get $|\vv{F}_3|=\sqrt{280-60\sqrt3}\approx13.27$ lb.
:::

::::{admonition} Concept Check
:class: hint
**(a)** If $\vv{u}$ and $\vv{v}$ are nonzero and parallel, must $\vv{u}+\vv{v}$ be parallel to $\vv{u}$?

**(b)** When does $|\vv{u}+\vv{v}|=|\vv{u}|+|\vv{v}|$?

:::{dropdown} Answer
(a) Write $\vv{v}=c\vv{u}$. Then $\vv{u}+\vv{v}=(1+c)\vv{u}$, which is parallel to $\vv{u}$; if $c=-1$ it is the zero vector, which is parallel to every vector by convention.

(b) Exactly when one vector is $\vzero$ or the two have the same direction. Geometrically, the triangle formed by $\vv{u}$, $\vv{v}$, $\vv{u}+\vv{v}$ must collapse to a segment. (A proof appears in [Lecture 03](#l03-thm-triangle) as the triangle inequality.)
:::
::::

## Common Errors

:::{caution} Avoid these errors
- Reversing the subtraction: $\vect{PQ}$ is *head minus tail*, $Q-P$, not $P-Q$.
- Writing $|\vv{u}+\vv{v}|=|\vv{u}|+|\vv{v}|$. In general only $|\vv{u}+\vv{v}|\le|\vv{u}|+|\vv{v}|$ holds; e.g., $|\ip{3,0}+\ip{0,4}|=5\ne7$.
- Writing $|c\vv{v}|=c|\vv{v}|$ for negative $c$; the correct formula is $|c\vv{v}|=|c|\,|\vv{v}|$.
- Normalizing the zero vector. $\vv{v}/|\vv{v}|$ is defined only for $\vv{v}\neq\vzero$.
- Confusing a point $(a,b)$ with the vector $\ip{a,b}$: a point is a location; a vector has no fixed location.
:::

## Summary

:::{admonition} Key takeaways
:class: summary
- A vector is determined by magnitude and direction; location is irrelevant (Lang: equivalence of located vectors).
- $\vect{PQ}=\ip{x_2-x_1,y_2-y_1}$ and $|\ip{v_1,v_2}|=\sqrt{v_1^2+v_2^2}$.
- Operations are componentwise; $|c\vv{v}|=|c|\,|\vv{v}|$.
- Unit vector: $\vv{v}/|\vv{v}|$; vector of length $L$ in direction $\vv{v}$: $L\vv{v}/|\vv{v}|$.
- $\vv{v}=|\vv{v}|\ip{\cos\theta,\sin\theta}=v_1\vvi+v_2\vvj$.
- Velocities and forces add as vectors; equilibrium means the net force is $\vzero$.
:::

## In-Class Practice

Try each problem before opening its solution.

:::{exercise}
:label: l01-practice-1
Let $\vv{u}=\ip{4,-3}$ and $\vv{v}=\ip{-2,5}$. Compute $\vv{u}+\vv{v}$, $3\vv{u}-2\vv{v}$, $|\vv{u}|$, and $|\vv{v}|$.
:::

:::{solution} l01-practice-1
:class: dropdown
$\vv{u}+\vv{v}=\ip{4-2,\,-3+5}=\ip{2,2}$.

$3\vv{u}-2\vv{v}=\ip{12,-9}-\ip{-4,10}=\ip{16,-19}$.

$|\vv{u}|=\sqrt{16+9}=5$ and $|\vv{v}|=\sqrt{4+25}=\sqrt{29}$.
:::

:::{exercise}
:label: l01-practice-2
Find the components and magnitude of the vector from $A(3,-1)$ to $B(-2,7)$.
:::

:::{solution} l01-practice-2
:class: dropdown
$\vect{AB}=\ip{-2-3,\;7-(-1)}=\ip{-5,8}$ and $|\vect{AB}|=\sqrt{25+64}=\sqrt{89}$.
:::

:::{exercise}
:label: l01-practice-3
Find a unit vector in the direction of $\ip{-6,8}$. Then find a vector of length $5$ pointing in the opposite direction.
:::

:::{solution} l01-practice-3
:class: dropdown
$|\ip{-6,8}|=\sqrt{36+64}=10$, so the unit vector is $\tfrac{1}{10}\ip{-6,8}=\ip{-\tfrac35,\tfrac45}$. The vector of length $5$ in the opposite direction is $-5\ip{-\tfrac35,\tfrac45}=\ip{3,-4}$. Check: $|\ip{3,-4}|=5$, and $\ip{3,-4}=-\tfrac12\ip{-6,8}$ with $-\tfrac12<0$.
:::

:::{exercise}
:label: l01-practice-4
A boat moves east at $12$ mph relative to the water. The river current flows south at $5$ mph. Find the speed and direction of the boat relative to the shore.
:::

:::{solution} l01-practice-4
:class: dropdown
With east as $\vvi$ and north as $\vvj$, the boat's velocity relative to the water is $\ip{12,0}$ and the current is $\ip{0,-5}$. The velocity relative to the shore is $\vv{v}=\ip{12,-5}$, with speed $|\vv{v}|=\sqrt{144+25}=13$ mph. The direction satisfies $\tan\phi=5/12$, so $\phi=\arctan(5/12)\approx22.6^\circ$ south of east.
:::

## Before the Next Class

Read Briggs §13.2 and Lang, Ch. I, §4 through the definition of distance and balls. Review the distance formula in the plane. Next: [Lecture 02 — Vectors in Three Dimensions](lecture-02.md).
