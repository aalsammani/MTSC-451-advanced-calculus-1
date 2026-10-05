---
title: Lecture 06 — Vector-Valued Functions and Their Derivatives
short_title: 06 · Vector-Valued Functions and Their Derivatives
description: Curves as vector-valued functions; componentwise limits and continuity; derivatives, tangent vectors, and smoothness; differentiation rules; curves of constant length; integrals and initial value problems.
date: 2026-09-10
numbering:
  enumerator: "6.%s"
---

:::{div}
:class: lecture-meta
**Class meeting:** Thursday, September 10, 2026  
**Reading:** Briggs §14.1–14.2; Lang, Ch. II (Differentiation of Vectors), derivative of a curve  
**Prerequisites:** Lecture 05: parametric lines $\vv{r}(t)=\vv{r}_0+t\vv{v}$; Lectures 03–04: dot and cross products; single-variable limits, derivatives, and integrals.  
**PDF version:** [Lecture 06 notes (PDF)](../downloads/MTSC451_Lecture_06.pdf)
:::

## Learning Objectives

After this lecture you should be able to:

1. describe a curve by a vector-valued function, find its domain, and identify its shape;
2. evaluate limits and decide continuity of vector-valued functions componentwise;
3. compute derivatives, tangent vectors, unit tangent vectors, and tangent lines;
4. apply and prove the differentiation rules for dot and cross products;
5. use the fact that a curve of constant length satisfies $\vv{r}\cdot\vv{r}'=0$;
6. compute indefinite and definite integrals and solve initial value problems.

## Motivation

In [Lecture 05](lecture-05.md) the line $\vv{r}(t)=\vv{r}_0+t\vv{v}$ assigned a point of $\R^3$ to each real number $t$. Most motion is not along a straight line: a particle on a spring, a satellite in orbit, a roller coaster. We now allow each coordinate to be an arbitrary function of $t$. The central question of this lecture is the one calculus always asks: *what is the instantaneous direction and rate of change?* The answer, the derivative $\vv{r}'(t)$, is computed one component at a time, but its interpretation as a tangent vector is genuinely geometric.

## Vector-Valued Functions and Curves

:::{prf:definition} Vector-Valued Function
:label: l06-def-vvf
A **vector-valued function** on a set $I\subseteq\R$ is a rule $\vv{r}$ assigning to each $t\in I$ a vector

$$
\vv{r}(t)=\ip{f(t),g(t),h(t)}=f(t)\vvi+g(t)\vvj+h(t)\vvk .
$$

The real functions $f,g,h$ are the **component functions**. Unless stated otherwise, the domain is the set of $t$ for which all three components are defined.
:::

As $t$ varies, the head of $\vv{r}(t)$ (in standard position) traces a **curve** $C$. The direction of increasing $t$ is the **orientation** of the curve.

:::{admonition} Notation: Briggs and Lang
:class: note notation
Briggs writes $\vv{r}(t)$. Lang writes $X(t)=(x_1(t),\dots,x_n(t))$ and calls the *map* $X:I\to\R^n$ itself a *curve*, thinking of $X(t)$ as the position of a moving particle at time $t$. The distinction matters: the different maps $\ip{\cos t,\sin t}$ and $\ip{\cos 2t,\sin 2t}$, $0\le t\le 2\pi$, trace the same circle (once and twice, respectively). In this course a *curve* is the traced set together with its parametrization when the parametrization matters; we use $\vv{r}(t)$.
:::

```{figure} ../assets/figures/lecture-06-fig-1.svg
:label: l06-fig-helix
:alt: Three-dimensional axes x, y, z with a helix winding upward around the z-axis. At one point on the helix, labeled r of t zero, a tangent vector labeled r prime of t zero points along the curve.
:width: 440px

A helix $\ip{a\cos t,\,a\sin t,\,bt}$ with the tangent vector $\vv{r}'(t_0)$ at the point $\vv{r}(t_0)$.
```

:::{prf:example} Domains and Shapes
:label: l06-ex-domains
(a) Find the domain of $\vv{r}(t)=\ip{\sqrt{4-t},\;\ln(t+1),\;1/t}$.

(b) Show that the curve $\vv{r}(t)=\ip{t\cos t,\;t\sin t,\;t}$ lies on the cone $z^2=x^2+y^2$, and describe it.

*Solution.* (a) We need $4-t\ge0$, $t+1>0$, and $t\ne0$: the domain is $(-1,0)\cup(0,4]$.

(b) With $x=t\cos t$, $y=t\sin t$, $z=t$, we get $x^2+y^2=t^2(\cos^2t+\sin^2t)=t^2=z^2$. So every point of the curve lies on the cone. The height $z=t$ increases while the point circles the $z$-axis at distance $|t|$ from it: for $t\ge0$ the curve is a spiral on the upper half of the cone that widens as it rises.
:::

## Limits and Continuity

:::{prf:definition} Limit and Continuity
:label: l06-def-limit
$\displaystyle\lim_{t\to a}\vv{r}(t)=\vv{L}$ means $|\vv{r}(t)-\vv{L}|\to0$ as $t\to a$. The function $\vv{r}$ is **continuous at $a$** if $\displaystyle\lim_{t\to a}\vv{r}(t)=\vv{r}(a)$.
:::

:::{prf:theorem} Limits Are Computed Componentwise
:label: l06-thm-limits
If $\vv{r}=\ip{f,g,h}$ and $\vv{L}=\ip{L_1,L_2,L_3}$, then $\lim_{t\to a}\vv{r}(t)=\vv{L}$ if and only if $\lim_{t\to a}f(t)=L_1$, $\lim_{t\to a}g(t)=L_2$, and $\lim_{t\to a}h(t)=L_3$. Consequently $\vv{r}$ is continuous at $a$ if and only if $f$, $g$, $h$ are.
:::

:::{prf:proof}
:nonumber:
For each component, $|f(t)-L_1|\le|\vv{r}(t)-\vv{L}|\le|f(t)-L_1|+|g(t)-L_2|+|h(t)-L_3|$. The left inequality holds because one term of a sum of squares is at most the sum; the right one is the triangle inequality applied to $\ip{f-L_1,0,0}+\ip{0,g-L_2,0}+\ip{0,0,h-L_3}$. If $|\vv{r}(t)-\vv{L}|\to0$, the left inequality forces each component difference to $0$; if each component difference tends to $0$, the right inequality forces $|\vv{r}(t)-\vv{L}|\to0$.
:::

:::{prf:example} A Componentwise Limit
:label: l06-ex-limit
Evaluate $\displaystyle\lim_{t\to0}\Bigl\langle\frac{\sin t}{t},\;\frac{e^t-1}{t},\;t^2+3\Bigr\rangle$. Where is this function continuous?

*Solution.* The component limits are $1$, $1$ (both are derivatives at $0$: of $\sin t$ and of $e^t$), and $3$, so the limit is $\ip{1,1,3}$. The function is continuous at every $t\neq0$ and is undefined at $t=0$. Redefining its value at $0$ to be $\ip{1,1,3}$ would make it continuous everywhere.
:::

## The Derivative and Tangent Vectors

:::{prf:definition} Derivative
:label: l06-def-derivative
The **derivative** of $\vv{r}$ at $t$ is

$$
\vv{r}'(t)=\lim_{\Delta t\to0}\frac{\vv{r}(t+\Delta t)-\vv{r}(t)}{\Delta t},
$$

provided the limit exists; then $\vv{r}$ is **differentiable** at $t$. By the componentwise limit theorem, $\vv{r}'(t)=\ip{f'(t),g'(t),h'(t)}$.
:::

```{figure} ../assets/figures/lecture-06-fig-2.svg
:label: l06-fig-derivative
:alt: A curve with two points labeled r of t and r of t plus delta t, each joined to the origin O by a gray position vector. The secant vector r of t plus delta t minus r of t joins the two points, and the tangent vector r prime of t starts at r of t and points along the curve.
:width: 380px

The secant vector $\vv{r}(t+\Delta t)-\vv{r}(t)$ and the tangent vector $\vv{r}'(t)$.
```

**Interpretation.** The vector $\vv{r}(t+\Delta t)-\vv{r}(t)$ is a secant vector. Dividing by $\Delta t$ and letting $\Delta t\to0$ turns it into a vector pointing along the curve in the direction of increasing $t$. If $\vv{r}$ describes motion, $\vv{r}'(t)$ is the **velocity**, $|\vv{r}'(t)|$ is the **speed**, and $\vv{r}''(t)$ is the **acceleration**.

:::{prf:definition} Tangent Vector, Unit Tangent, Smoothness
:label: l06-def-tangent
If $\vv{r}'(t)\neq\vzero$, then $\vv{r}'(t)$ is a **tangent vector** at $\vv{r}(t)$, and

$$
\vv{T}(t)=\frac{\vv{r}'(t)}{|\vv{r}'(t)|}
$$

is the **unit tangent vector**. The **tangent line** at $t_0$ is $\vv{\ell}(s)=\vv{r}(t_0)+s\,\vv{r}'(t_0)$. A function $\vv{r}$ is **smooth** on an interval if $\vv{r}'$ is continuous and $\vv{r}'(t)\neq\vzero$ there.
:::

:::{prf:example} Tangent Vector and Tangent Line
:label: l06-ex-tangent
Let $\vv{r}(t)=\ip{t^2,\;2t-1,\;e^{t-1}}$. Find the unit tangent vector and the tangent line at $t=1$.

*Solution.* $\vv{r}'(t)=\ip{2t,\;2,\;e^{t-1}}$, so $\vv{r}(1)=\ip{1,1,1}$ and $\vv{r}'(1)=\ip{2,2,1}$, with $|\vv{r}'(1)|=\sqrt{4+4+1}=3$. Hence

$$
\vv{T}(1)=\ip{\tfrac23,\tfrac23,\tfrac13},\qquad
\vv{\ell}(s)=\ip{1+2s,\;1+2s,\;1+s}.
$$
:::

:::{prf:example} The Helix Has Constant Speed
:label: l06-ex-helix
For $\vv{r}(t)=\ip{2\cos t,\;2\sin t,\;3t}$, find $\vv{r}'$, the speed, and $\vv{T}$. Show that $\vv{T}$ makes a constant angle with $\vvk$.

*Solution.* $\vv{r}'(t)=\ip{-2\sin t,\;2\cos t,\;3}$ and $|\vv{r}'(t)|=\sqrt{4\sin^2t+4\cos^2t+9}=\sqrt{13}$, a constant. Thus $\vv{T}(t)=\tfrac{1}{\sqrt{13}}\ip{-2\sin t,\;2\cos t,\;3}$. Since $\vv{T}\cdot\vvk=\tfrac{3}{\sqrt{13}}$ for every $t$ and both are unit vectors, the angle between $\vv{T}$ and $\vvk$ is always $\arccos(3/\sqrt{13})\approx33.7^\circ$.
:::

:::{prf:example} A Non-Smooth Curve
:label: l06-ex-cusp
Let $\vv{r}(t)=\ip{t^3,\;t^2}$. Show that $\vv{r}$ is differentiable everywhere but not smooth, and describe what happens at $t=0$.

*Solution.* $\vv{r}'(t)=\ip{3t^2,\;2t}$ exists and is continuous for all $t$, but $\vv{r}'(0)=\vzero$, so $\vv{r}$ is not smooth on any interval containing $0$. Eliminating $t$ gives $y=x^{2/3}$, a curve with a *cusp* at the origin. For $t\neq0$, $\vv{r}'(t)=t\ip{3t,2}$ and $|\vv{r}'(t)|=|t|\sqrt{9t^2+4}$, so $\vv{T}(t)=\dfrac{t}{|t|}\cdot\dfrac{\ip{3t,2}}{\sqrt{9t^2+4}}$, which tends to $\ip{0,1}$ as $t\to0^+$ and to $\ip{0,-1}$ as $t\to0^-$. The direction of motion reverses abruptly at the cusp: a zero derivative allows a corner even though every component is differentiable.
:::

## Interactive Exploration

Choose a curve, then move the $t$ slider or press Play. The arrow from the origin is the position $\vv{r}(t)$; the arrow at the moving point is the velocity $\vv{r}'(t)$ (or the unit tangent $\vv{T}(t)$, if you check that box), and the tangent line can be switched on. The readout lists $\vv{r}(t)$, $\vv{r}'(t)$, the speed, and $\vv{T}(t)$. Drag the figure to rotate it. Things to try:

- For the helix of {prf:ref}`l06-ex-helix`, move $t$ and watch the speed stay at $\sqrt{13}\approx3.606$ while the velocity turns.
- Choose the cusp $\ip{t^3,t^2}$ and move $t$ through $0$: the velocity shrinks to $\vzero$, $\vv{T}$ is undefined at $t=0$, and the direction of motion flips ({prf:ref}`l06-ex-cusp`).
- Choose the curve on the unit sphere: the readout shows $|\vv{r}(t)|=1$ and $\vv{r}(t)\cdot\vv{r}'(t)=0$ for every $t$, as the theorem on curves of constant length below predicts.

:::{anywidget} ../interactive/mathviz.mjs
{"widget": "curvemotion", "curve": "helix"}
:::

## Rules of Differentiation

:::{prf:theorem} Derivative Rules
:label: l06-thm-derivative-rules
Let $\vv{u}$ and $\vv{v}$ be differentiable vector-valued functions, $f$ a differentiable real function, and $\vv{c}$ a constant vector. Then

1. $\frac{d}{dt}\vv{c}=\vzero$ and $\frac{d}{dt}\bigl(\vv{u}+\vv{v}\bigr)=\vv{u}'+\vv{v}'$;
2. $\frac{d}{dt}\bigl(f(t)\vv{u}(t)\bigr)=f'(t)\vv{u}(t)+f(t)\vv{u}'(t)$;
3. $\frac{d}{dt}\bigl(\vv{u}\cdot\vv{v}\bigr)=\vv{u}'\cdot\vv{v}+\vv{u}\cdot\vv{v}'$;
4. $\frac{d}{dt}\bigl(\vv{u}\times\vv{v}\bigr)=\vv{u}'\times\vv{v}+\vv{u}\times\vv{v}'$ (order matters);
5. $\frac{d}{dt}\vv{u}\bigl(f(t)\bigr)=\vv{u}'\bigl(f(t)\bigr)\,f'(t)$ (chain rule).
:::

:::{prf:proof} Rule (3)
:nonumber:
With $\vv{u}\cdot\vv{v}=u_1v_1+u_2v_2+u_3v_3$, the single-variable product rule gives $\frac{d}{dt}(\vv{u}\cdot\vv{v})=\sum_i(u_i'v_i+u_iv_i')=\vv{u}'\cdot\vv{v}+\vv{u}\cdot\vv{v}'$. Rules (2) and (4) are proved the same way, applying the product rule to each term of each component. For (4) the order of each product must be kept, since the cross product is anticommutative.
:::

:::{prf:example} Checking the Product Rules
:label: l06-ex-product-rules
Let $\vv{u}(t)=\ip{t,1,t^2}$ and $\vv{v}(t)=\ip{1,t,-t}$. Compute $\frac{d}{dt}(\vv{u}\cdot\vv{v})$ and $\frac{d}{dt}(\vv{u}\times\vv{v})$ directly and by the product rules.

*Solution.* Here $\vv{u}'=\ip{1,0,2t}$ and $\vv{v}'=\ip{0,1,-1}$.

*Dot product.* Directly, $\vv{u}\cdot\vv{v}=t+t-t^3=2t-t^3$, with derivative $2-3t^2$. By the rule, $\vv{u}'\cdot\vv{v}+\vv{u}\cdot\vv{v}'=(1-2t^2)+(1-t^2)=2-3t^2$. $\checkmark$

*Cross product.* Directly, $\vv{u}\times\vv{v}=\ip{1(-t)-t^2\cdot t,\;t^2\cdot1-t(-t),\;t\cdot t-1\cdot1}=\ip{-t-t^3,\;2t^2,\;t^2-1}$, with derivative $\ip{-1-3t^2,\;4t,\;2t}$. By the rule,

$$
\vv{u}'\times\vv{v}=\ip{-2t^2,\;3t,\;t},\qquad
\vv{u}\times\vv{v}'=\ip{-1-t^2,\;t,\;t},
$$

and their sum is $\ip{-1-3t^2,\;4t,\;2t}$. $\checkmark$
:::

:::{prf:theorem} Curves of Constant Length
:label: l06-thm-constant-length
If $\vv{r}$ is differentiable and $|\vv{r}(t)|$ is constant on an interval, then $\vv{r}(t)\cdot\vv{r}'(t)=0$ for every $t$ in the interval.
:::

:::{prf:proof}
:nonumber:
$\vv{r}\cdot\vv{r}=|\vv{r}|^2=c^2$ is constant, so by rule (3), $0=\frac{d}{dt}(\vv{r}\cdot\vv{r})=\vv{r}'\cdot\vv{r}+\vv{r}\cdot\vv{r}'=2\,\vv{r}\cdot\vv{r}'$.
:::

*Geometric meaning.* A curve on a sphere centered at the origin has its velocity tangent to the sphere, i.e., perpendicular to the radius. Applied to $\vv{T}$ (which has constant length $1$), the theorem gives $\vv{T}\cdot\vv{T}'=0$.

:::{prf:example} A Curve on the Unit Sphere
:label: l06-ex-sphere
Let $\vv{r}(t)=\ip{\cos t,\;\sin t\cos t,\;\sin^2t}$. Show that the curve lies on the unit sphere and verify $\vv{r}\cdot\vv{r}'=0$ directly.

*Solution.* $|\vv{r}|^2=\cos^2t+\sin^2t\cos^2t+\sin^4t=\cos^2t+\sin^2t(\cos^2t+\sin^2t)=1$. Next, $\vv{r}'(t)=\ip{-\sin t,\;\cos2t,\;\sin2t}$, so

$$
\begin{aligned}
\vv{r}\cdot\vv{r}'&=-\sin t\cos t+\sin t\cos t\cos2t+2\sin^3t\cos t\\
&=\sin t\cos t\,\bigl(-1+\cos2t+2\sin^2t\bigr)=0,
\end{aligned}
$$

because $\cos2t=1-2\sin^2t$. $\checkmark$
:::

## Integrals of Vector-Valued Functions

Integration is also componentwise. For $\vv{r}=\ip{f,g,h}$ with integrable components,

$$
\begin{aligned}
\int\vv{r}(t)\,dt&=\ip{F(t),G(t),H(t)}+\vv{C},\\
\int_a^b\vv{r}(t)\,dt&=\Bigl\langle\int_a^bf,\;\int_a^bg,\;\int_a^bh\Bigr\rangle,
\end{aligned}
$$

where $F,G,H$ are antiderivatives of $f,g,h$ and $\vv{C}$ is an arbitrary *constant vector*. If $\vv{R}'=\vv{r}$ on $[a,b]$ and $\vv{r}$ is continuous, the Fundamental Theorem of Calculus applied to each component gives $\int_a^b\vv{r}(t)\,dt=\vv{R}(b)-\vv{R}(a)$.

:::{prf:example} Definite Integral and Initial Value Problem
:label: l06-ex-ivp
Let $\vv{r}'(t)=\ip{3t^2,\;e^t,\;\dfrac{4}{1+t^2}}$.

(a) Compute $\displaystyle\int_0^1\vv{r}'(t)\,dt$.

(b) Find $\vv{r}(t)$ if $\vv{r}(0)=\ip{1,0,2}$.

*Solution.* (a) $\displaystyle\int_0^1\vv{r}'(t)\,dt=\Bigl\langle t^3\Big|_0^1,\;e^t\Big|_0^1,\;4\arctan t\Big|_0^1\Bigr\rangle=\ip{1,\;e-1,\;\pi}$.

(b) Integrating, $\vv{r}(t)=\ip{t^3,\;e^t,\;4\arctan t}+\vv{C}$. At $t=0$: $\ip{0,1,0}+\vv{C}=\ip{1,0,2}$, so $\vv{C}=\ip{1,-1,2}$ and

$$
\vv{r}(t)=\ip{t^3+1,\;e^t-1,\;4\arctan t+2}.
$$

Consistency check: $\vv{r}(1)-\vv{r}(0)=\ip{2,e-1,\pi+2}-\ip{1,0,2}=\ip{1,e-1,\pi}$, matching (a). $\checkmark$
:::

::::{admonition} Concept Check
:class: hint
**(a)** If $|\vv{r}'(t)|=0$ for all $t$ in an interval, what can you say about the curve?

**(b)** True or false: if $|\vv{r}(t)|$ is constant, then $|\vv{r}'(t)|$ is constant.

:::{dropdown} Answer
(a) Then $\vv{r}'(t)=\vzero$, so each component has zero derivative and is constant on the interval (Mean Value Theorem). The "curve" is a single point.

(b) False. The theorem gives only $\vv{r}\perp\vv{r}'$, not constant speed. Example: $\vv{r}(t)=\ip{\cos t^2,\sin t^2}$ has $|\vv{r}|=1$ but $|\vv{r}'(t)|=2|t|$.
:::
::::

## Common Errors

:::{caution} Avoid these errors
- Taking the domain of only one component; the domain is the *intersection* of the component domains.
- Calling $\vv{r}'(t_0)$ a tangent vector when $\vv{r}'(t_0)=\vzero$; the zero vector has no direction (see {prf:ref}`l06-ex-cusp`).
- Reversing the order in the cross product rule: $\frac{d}{dt}(\vv{u}\times\vv{v})=\vv{u}'\times\vv{v}+\vv{u}\times\vv{v}'$, *not* $\vv{v}'\times\vv{u}+\cdots$.
- Forgetting that the constant of integration is a *vector* $\vv{C}$, so an initial condition determines three constants.
- Writing the tangent line with the unevaluated $\vv{r}'(t)$; the direction must be the fixed vector $\vv{r}'(t_0)$.
- Assuming the same curve has only one parametrization; speed depends on the parametrization, the traced set does not.
:::

## Summary

:::{admonition} Key takeaways
:class: summary
- $\vv{r}(t)=\ip{f(t),g(t),h(t)}$; limits, continuity, derivatives, and integrals are all componentwise.
- $\vv{r}'(t)=\lim_{\Delta t\to0}\frac{\vv{r}(t+\Delta t)-\vv{r}(t)}{\Delta t}$ is the velocity; $|\vv{r}'|$ is the speed; $\vv{T}=\vv{r}'/|\vv{r}'|$ when $\vv{r}'\neq\vzero$.
- Tangent line at $t_0$: $\vv{r}(t_0)+s\,\vv{r}'(t_0)$. Smooth means $\vv{r}'$ continuous and nonzero.
- Product rules for $f\vv{u}$, $\vv{u}\cdot\vv{v}$, $\vv{u}\times\vv{v}$ (keep the order), and the chain rule.
- $|\vv{r}|$ constant $\Longrightarrow\vv{r}\cdot\vv{r}'=0$.
- $\int\vv{r}\,dt$ includes a constant vector $\vv{C}$; $\int_a^b\vv{r}'\,dt=\vv{r}(b)-\vv{r}(a)$.
:::

## In-Class Practice

Try each problem before opening its solution.

:::{exercise}
:label: l06-practice-1
Find the domain of $\vv{r}(t)=\ip{\sqrt{t+2},\;\dfrac{1}{t-1},\;\ln(5-t)}$.
:::

:::{solution} l06-practice-1
:class: dropdown
We need $t+2\ge0$, $t\neq1$, and $5-t>0$. The domain is $[-2,1)\cup(1,5)$.
:::

:::{exercise}
:label: l06-practice-2
Evaluate $\displaystyle\lim_{t\to0}\Bigl\langle\frac{1-\cos t}{t},\;\frac{\sin3t}{t},\;e^{2t}\Bigr\rangle$.
:::

:::{solution} l06-practice-2
:class: dropdown
Componentwise:

$$
\lim_{t\to0}\frac{1-\cos t}{t}=\lim_{t\to0}\frac{\sin^2t}{t(1+\cos t)}=\lim_{t\to0}\frac{\sin t}{t}\cdot\frac{\sin t}{1+\cos t}=1\cdot0=0;
$$

$\displaystyle\lim_{t\to0}\frac{\sin3t}{t}=3\lim_{t\to0}\frac{\sin3t}{3t}=3$; and $e^{0}=1$. The limit is $\ip{0,3,1}$.
:::

:::{exercise}
:label: l06-practice-3
Find the unit tangent vector and the tangent line to $\vv{r}(t)=\ip{\ln t,\;t^2,\;\sqrt t}$ at $t=1$.
:::

:::{solution} l06-practice-3
:class: dropdown
$\vv{r}'(t)=\ip{\tfrac1t,\;2t,\;\tfrac{1}{2\sqrt t}}$, so $\vv{r}(1)=\ip{0,1,1}$ and $\vv{r}'(1)=\ip{1,2,\tfrac12}$, with $|\vv{r}'(1)|=\sqrt{1+4+\tfrac14}=\tfrac{\sqrt{21}}{2}$. Thus $\vv{T}(1)=\tfrac{2}{\sqrt{21}}\ip{1,2,\tfrac12}=\tfrac{1}{\sqrt{21}}\ip{2,4,1}$, and the tangent line is $\vv{\ell}(s)=\ip{s,\;1+2s,\;1+\tfrac{s}{2}}$ (or, with direction $\ip{2,4,1}$, $\ip{2s,1+4s,1+s}$).
:::

:::{exercise}
:label: l06-practice-4
Let $\vv{u}(t)=\ip{t,t^2,1}$ and $\vv{v}(t)=\ip{1,0,t}$. Compute $\frac{d}{dt}(\vv{u}\times\vv{v})$ in two ways and evaluate it at $t=1$.
:::

:::{solution} l06-practice-4
:class: dropdown
*Directly:* $\vv{u}\times\vv{v}=\ip{t^2\cdot t-1\cdot0,\;1\cdot1-t\cdot t,\;t\cdot0-t^2\cdot1}=\ip{t^3,\;1-t^2,\;-t^2}$, so $\frac{d}{dt}(\vv{u}\times\vv{v})=\ip{3t^2,-2t,-2t}$.

*By the rule:* $\vv{u}'=\ip{1,2t,0}$, $\vv{v}'=\ip{0,0,1}$; $\vv{u}'\times\vv{v}=\ip{2t^2,-t,-2t}$ and $\vv{u}\times\vv{v}'=\ip{t^2,-t,0}$, with sum $\ip{3t^2,-2t,-2t}$. $\checkmark$ At $t=1$: $\ip{3,-2,-2}$.
:::

:::{exercise}
:label: l06-practice-5
Solve the initial value problem $\vv{r}'(t)=\ip{\sin t,\;-\cos t,\;2t}$, $\vv{r}(0)=\ip{1,2,0}$.
:::

:::{solution} l06-practice-5
:class: dropdown
Integrating, $\vv{r}(t)=\ip{-\cos t,\;-\sin t,\;t^2}+\vv{C}$. At $t=0$: $\ip{-1,0,0}+\vv{C}=\ip{1,2,0}$, so $\vv{C}=\ip{2,2,0}$ and $\vv{r}(t)=\ip{2-\cos t,\;2-\sin t,\;t^2}$. Check: $\vv{r}'(t)=\ip{\sin t,-\cos t,2t}$ and $\vv{r}(0)=\ip{1,2,0}$. $\checkmark$
:::

:::{exercise}
:label: l06-practice-6
Prove that if $\vv{r}''(t)=\vzero$ for all $t\in\R$, then the curve is a line or a single point.
:::

:::{solution} l06-practice-6
:class: dropdown
Each component of $\vv{r}'$ has zero derivative on $\R$, so by the Mean Value Theorem each is constant: $\vv{r}'(t)=\vv{v}$ for a constant vector $\vv{v}$. Integrating again, $\vv{r}(t)=\vv{r}(0)+t\vv{v}$. If $\vv{v}\neq\vzero$ this is the line through $\vv{r}(0)$ with direction $\vv{v}$ ([Lecture 05](#l05-def-line)); if $\vv{v}=\vzero$ the curve is the single point $\vv{r}(0)$.
:::

:::{exercise}
:label: l06-practice-7
Prove that $\dfrac{d}{dt}\bigl(\vv{r}\times\vv{r}'\bigr)=\vv{r}\times\vv{r}''$.
:::

:::{solution} l06-practice-7
:class: dropdown
By the cross product rule, $\frac{d}{dt}(\vv{r}\times\vv{r}')=\vv{r}'\times\vv{r}'+\vv{r}\times\vv{r}''=\vzero+\vv{r}\times\vv{r}''$, since $\vv{a}\times\vv{a}=\vzero$ for every vector $\vv{a}$ ([Lecture 04](#l04-thm-properties)).
:::

## Before the Next Class

Read Briggs §14.4 (length of curves) and the part of Lang, Ch. II on the length of curves. Review integration techniques, especially $\int\sqrt{1+u^2}\,du$-type integrals and substitution. Next: [Lecture 07 — Length of Curves](lecture-07.md).
