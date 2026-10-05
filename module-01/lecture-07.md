---
title: Lecture 07 — Length of Curves
short_title: 07 · Length of Curves
description: Arc length as a limit of inscribed polygons, computing lengths, independence of parametrization, the arc length parameter, and lengths of polar curves.
date: 2026-09-15
numbering:
  enumerator: "7.%s"
---

:::{div}
:class: lecture-meta
**Class meeting:** Tuesday, September 15, 2026  
**Reading:** Briggs §14.4; Lang, Ch. II (Differentiation of Vectors), length of curves  
**Prerequisites:** Lecture 06: derivatives, speed $|\vv{r}'(t)|$, unit tangent vector; single-variable integration (substitution, Fundamental Theorem of Calculus).  
**PDF version:** [Lecture 07 notes (PDF)](../downloads/MTSC451_Lecture_07.pdf)
:::

## Learning Objectives

After this lecture you should be able to:

1. explain why the length of a curve is defined as $\int_a^b|\vv{r}'(t)|\,dt$, using polygonal approximations;
2. compute lengths of curves in the plane and in space;
3. prove that length does not depend on the choice of (monotone) parametrization;
4. construct the arc length function and reparametrize a curve by arc length;
5. compute the length of a curve given in polar coordinates.

## Motivation

In [Lecture 06](lecture-06.md) we computed the speed $|\vv{r}'(t)|$ of a moving point. A car's odometer integrates its speedometer: distance traveled is the integral of speed. This suggests that the length of a curve should be $\int_a^b|\vv{r}'(t)|\,dt$. We justify this by approximating the curve by inscribed polygons, then study two consequences: length is a geometric quantity that does not depend on how the curve is parametrized, and every smooth curve can be reparametrized so that its parameter *is* arc length. The arc length parameter is the natural "ruler" along a curve and will reappear with curve integrals later in the course.

(l07-sec-polygons)=
## From Polygons to an Integral

Let $\vv{r}(t)$, $a\le t\le b$, be smooth. Choose a partition $a=t_0<t_1<\cdots<t_n=b$ and join the points $\vv{r}(t_0),\vv{r}(t_1),\dots,\vv{r}(t_n)$ by segments. The inscribed polygon has length

$$
\sum_{k=1}^{n}\bigl|\vv{r}(t_k)-\vv{r}(t_{k-1})\bigr|
\;\approx\;\sum_{k=1}^{n}\bigl|\vv{r}'(t_k)\bigr|\,\Delta t_k ,
$$

since $\vv{r}(t_k)-\vv{r}(t_{k-1})\approx\vv{r}'(t_k)\,\Delta t_k$ for small $\Delta t_k$. The right side is a Riemann sum for $\int_a^b|\vv{r}'(t)|\,dt$.

```{figure} ../assets/figures/lecture-07-fig-1.svg
:label: l07-fig-polygon
:alt: A smooth curve labeled C with six marked points on it, from r of t zero through r of t two to r of t n. Consecutive points are joined by straight segments, forming an inscribed polygon that follows the curve closely.
:width: 440px

An inscribed polygon with vertices $\vv{r}(t_0),\vv{r}(t_1),\dots,\vv{r}(t_n)$ on the curve $C$.
```

:::{prf:remark} On rigor
:label: l07-rem-rigor
:nonumber:
The step "$\approx$" is a heuristic. Applying the Mean Value Theorem to each component produces a *different* intermediate point in each component, so the polygon sum is not exactly a Riemann sum. Using the uniform continuity of $\vv{r}'$ on $[a,b]$, one shows that the polygon lengths converge to the integral as the mesh $\max\Delta t_k\to0$. Lang takes the integral as the *definition* of length, which is what we do.
:::

:::{prf:definition} Arc Length
:label: l07-def-arc-length
Let $\vv{r}(t)$, $a\le t\le b$, have a continuous derivative. The **length** of the curve is

$$
L=\int_a^b|\vv{r}'(t)|\,dt=\int_a^b\sqrt{f'(t)^2+g'(t)^2+h'(t)^2}\;dt
$$

for $\vv{r}=\ip{f,g,h}$. For a plane curve, omit the third component.
:::

If the curve is traversed more than once (for instance, a circle traced twice), this integral counts the distance traveled, which is a multiple of the geometric length. To measure the length of the traced set, use a parametrization that is **one-to-one** on $[a,b)$.

:::{admonition} Notation: Briggs and Lang
:class: note notation
Lang writes the length as $\int_a^b\|X'(t)\|\,dt$. Briggs writes $\int_a^b|\vv{r}'(t)|\,dt$, and for motion interprets it as the distance traveled. We use $L$ for length and $s$ for the arc length parameter (see [The Arc Length Parameter](#l07-sec-arclength-param)).
:::

## Computing Lengths

:::{prf:example} One Turn of a Helix
:label: l07-ex-helix
Find the length of one turn of the helix $\vv{r}(t)=\ip{2\cos t,\;2\sin t,\;3t}$, $0\le t\le2\pi$.

*Solution.* From [Lecture 06](#l06-ex-helix), $|\vv{r}'(t)|=\sqrt{4\sin^2t+4\cos^2t+9}=\sqrt{13}$. So $L=\int_0^{2\pi}\sqrt{13}\,dt=2\pi\sqrt{13}\approx22.65$.

*Sanity check:* unrolling the cylinder of radius $2$ turns one turn of the helix into the hypotenuse of a right triangle with legs $4\pi$ (the circumference) and $6\pi$ (the rise), and $\sqrt{(4\pi)^2+(6\pi)^2}=2\pi\sqrt{13}$. $\checkmark$
:::

:::{prf:example} A Plane Curve
:label: l07-ex-plane-curve
Find the length of $\vv{r}(t)=\ip{t^2,\;t^3}$, $0\le t\le1$.

*Solution.* $\vv{r}'(t)=\ip{2t,3t^2}$ and $|\vv{r}'(t)|=\sqrt{4t^2+9t^4}=t\sqrt{4+9t^2}$ (since $t\ge0$). With $u=4+9t^2$, $du=18t\,dt$:

$$
\begin{aligned}
L&=\int_0^1t\sqrt{4+9t^2}\,dt=\frac{1}{18}\int_4^{13}u^{1/2}\,du\\
&=\frac{1}{27}\Bigl[u^{3/2}\Bigr]_4^{13}=\frac{13\sqrt{13}-8}{27}\approx1.440.
\end{aligned}
$$
:::

:::{prf:example} A Space Curve with a Perfect Square
:label: l07-ex-perfect-square
Find the length of $\vv{r}(t)=\ip{2t,\;t^2,\;\ln t}$, $1\le t\le e$.

*Solution.* $\vv{r}'(t)=\ip{2,\;2t,\;1/t}$, so

$$
|\vv{r}'(t)|^2=4+4t^2+\frac{1}{t^2}=\Bigl(2t+\frac1t\Bigr)^2,
\qquad |\vv{r}'(t)|=2t+\frac1t\quad(t>0).
$$

Hence $L=\int_1^e\bigl(2t+\tfrac1t\bigr)\,dt=\bigl[t^2+\ln t\bigr]_1^e=(e^2+1)-(1+0)=e^2$.
:::

:::{prf:example} A Conical Spiral
:label: l07-ex-conical-spiral
Find the length of $\vv{r}(t)=\ip{e^t\cos t,\;e^t\sin t,\;e^t}$, $0\le t\le\ln2$.

*Solution.* By the product rule, $\vv{r}'(t)=e^t\ip{\cos t-\sin t,\;\sin t+\cos t,\;1}$. Since $(\cos t-\sin t)^2+(\sin t+\cos t)^2=2$, we get $|\vv{r}'(t)|=e^t\sqrt{3}$. Thus $L=\sqrt3\int_0^{\ln2}e^t\,dt=\sqrt3\,(2-1)=\sqrt3$.
:::

## Interactive Exploration

Choose a curve and use the slider to change the number $n$ of segments in an inscribed polygon built on equally spaced parameter values. The readout compares the polygon length $\sum|\vv{r}(t_k)-\vv{r}(t_{k-1})|$ with the exact length $L$, and the table lists the polygon lengths for $n=1,2,4,\dots,64$. Drag the figure to rotate it. Things to try:

- For the helix of {prf:ref}`l07-ex-helix`, increase $n$ from $4$ and watch the polygon lengths approach $2\pi\sqrt{13}\approx22.654$ from below.
- Switch to $\ip{2t,t^2,\ln t}$ ({prf:ref}`l07-ex-perfect-square`, $L=e^2$) or to the cardioid of {prf:ref}`l07-ex-cardioid` ($L=8$). No polygon is ever longer than the curve; the Concept Check below explains why.
- After working {ref}`l07-practice-1`, choose the astroid to check your answer.

:::{anywidget} ../interactive/mathviz.mjs
{"widget": "arclength", "curve": "helix", "n": 4}
:::

## Independence of Parametrization

:::{prf:theorem} Length Does Not Depend on the Parametrization
:label: l07-thm-independence
Let $\vv{r}:[a,b]\to\R^3$ have a continuous derivative, and let $\varphi:[c,d]\to[a,b]$ be a bijection with a continuous derivative that is either positive everywhere or negative everywhere. Then $\boldsymbol{\rho}(u)=\vv{r}(\varphi(u))$ has the same length as $\vv{r}$:

$$
\int_c^d|\boldsymbol{\rho}'(u)|\,du=\int_a^b|\vv{r}'(t)|\,dt .
$$
:::

:::{prf:proof}
:nonumber:
By the chain rule ({prf:ref}`l06-thm-derivative-rules`), $\boldsymbol{\rho}'(u)=\vv{r}'(\varphi(u))\,\varphi'(u)$, so $|\boldsymbol{\rho}'(u)|=|\vv{r}'(\varphi(u))|\,|\varphi'(u)|$. If $\varphi'>0$, then $\varphi(c)=a$, $\varphi(d)=b$, and the substitution $t=\varphi(u)$ gives $\int_c^d|\vv{r}'(\varphi(u))|\varphi'(u)\,du=\int_a^b|\vv{r}'(t)|\,dt$. If $\varphi'<0$, then $\varphi(c)=b$, $\varphi(d)=a$, $|\varphi'|=-\varphi'$, and the same substitution gives $-\int_b^a|\vv{r}'(t)|\,dt=\int_a^b|\vv{r}'(t)|\,dt$.
:::

:::{prf:example} Same Set, Different Lengths?
:label: l07-ex-same-set
Compare the lengths computed from (a) $\ip{\cos t,\sin t}$, $0\le t\le2\pi$; (b) $\ip{\cos t^2,\sin t^2}$, $0\le t\le\sqrt{2\pi}$; (c) $\ip{\cos2t,\sin2t}$, $0\le t\le2\pi$.

*Solution.* (a) Speed $1$, so $L=2\pi$.

(b) Speed $|2t|=2t$, so $L=\int_0^{\sqrt{2\pi}}2t\,dt=2\pi$, as the theorem predicts ($\varphi(t)=t^2$ is an increasing bijection $[0,\sqrt{2\pi}]\to[0,2\pi]$).

(c) Speed $2$, so $\int_0^{2\pi}2\,dt=4\pi$. This is not a contradiction: the map $t\mapsto2t$ sends $[0,2\pi]$ onto $[0,4\pi]$, so the circle is traced *twice*. The integral measures distance traveled, which is twice the circumference.
:::

(l07-sec-arclength-param)=
## The Arc Length Parameter

:::{prf:definition} Arc Length Function
:label: l07-def-arc-length-function
For a smooth curve $\vv{r}(t)$, $t\ge a$, the **arc length function** is

$$
s(t)=\int_a^t|\vv{r}'(u)|\,du ,
$$

the length of the curve from $\vv{r}(a)$ to $\vv{r}(t)$.
:::

By the Fundamental Theorem of Calculus, $s'(t)=|\vv{r}'(t)|$: the rate at which arc length accumulates is the speed. For a smooth curve $s'(t)>0$, so $s$ is strictly increasing and has an inverse $t=t(s)$. Substituting gives the **arc length parametrization** $\tilde{\vv{r}}(s)=\vv{r}(t(s))$.

:::{prf:theorem} Unit Speed Characterizes Arc Length
:label: l07-thm-unit-speed
Let $\vv{r}(t)$, $t\ge a$, be smooth.

(a) The arc length parametrization satisfies $\left|\dfrac{d\tilde{\vv{r}}}{ds}\right|=1$.

(b) $|\vv{r}'(t)|=1$ for all $t$ if and only if $s(t)=t-a$, i.e., $t$ itself measures arc length from $\vv{r}(a)$.
:::

:::{prf:proof}
:nonumber:
(a) By the chain rule and the inverse function rule, $\dfrac{d\tilde{\vv{r}}}{ds}=\vv{r}'(t)\dfrac{dt}{ds}=\dfrac{\vv{r}'(t)}{s'(t)}=\dfrac{\vv{r}'(t)}{|\vv{r}'(t)|}$, a unit vector.

(b) If $|\vv{r}'|=1$, then $s(t)=\int_a^t1\,du=t-a$. Conversely, if $s(t)=t-a$, then $|\vv{r}'(t)|=s'(t)=1$.
:::

Part (a) says that $d\tilde{\vv{r}}/ds$ is exactly the [unit tangent vector $\vv{T}$](#l06-def-tangent) of Lecture 06.

:::{prf:example} Reparametrizing the Helix
:label: l07-ex-reparametrize
Reparametrize $\vv{r}(t)=\ip{2\cos t,\;2\sin t,\;3t}$ by arc length measured from $t=0$.

*Solution.* $s(t)=\int_0^t\sqrt{13}\,du=\sqrt{13}\,t$, so $t=s/\sqrt{13}$ and

$$
\tilde{\vv{r}}(s)=\Bigl\langle2\cos\frac{s}{\sqrt{13}},\;2\sin\frac{s}{\sqrt{13}},\;\frac{3s}{\sqrt{13}}\Bigr\rangle,\qquad s\ge0.
$$

Check: $\tilde{\vv{r}}'(s)=\tfrac{1}{\sqrt{13}}\ip{-2\sin\tfrac{s}{\sqrt{13}},\;2\cos\tfrac{s}{\sqrt{13}},\;3}$, with length $\tfrac{1}{\sqrt{13}}\sqrt{4+9}=1$. $\checkmark$
:::

In practice, explicit arc length parametrizations are rare: the integral for $s(t)$ often cannot be evaluated in closed form ({prf:ref}`l07-ex-plane-curve` can, but inverting $s(t)$ there is already awkward). The arc length parameter is mostly a *theoretical* tool.

## Curves in Polar Coordinates

A polar curve $r=f(\theta)$, $\alpha\le\theta\le\beta$, is the parametrized curve $x=f(\theta)\cos\theta$, $y=f(\theta)\sin\theta$. Differentiating,

$$
\begin{aligned}
&x'=f'\cos\theta-f\sin\theta,\qquad y'=f'\sin\theta+f\cos\theta,\\
&(x')^2+(y')^2=f(\theta)^2+f'(\theta)^2,
\end{aligned}
$$

because the cross terms cancel and $\cos^2\theta+\sin^2\theta=1$. Therefore

$$
L=\int_\alpha^\beta\sqrt{f(\theta)^2+f'(\theta)^2}\;d\theta .
$$

:::{prf:example} Length of a Cardioid
:label: l07-ex-cardioid
Find the length of the cardioid $r=1+\cos\theta$, $0\le\theta\le2\pi$.

*Solution.* $f^2+(f')^2=(1+\cos\theta)^2+\sin^2\theta=2+2\cos\theta=4\cos^2(\theta/2)$, using $1+\cos\theta=2\cos^2(\theta/2)$. Hence $\sqrt{f^2+(f')^2}=2|\cos(\theta/2)|$, and the absolute value matters: $\cos(\theta/2)<0$ for $\pi<\theta<2\pi$. By symmetry,

$$
L=2\int_0^{\pi}2\cos(\theta/2)\,d\theta=8\Bigl[\sin(\theta/2)\Bigr]_0^{\pi}=8.
$$
:::

::::{admonition} Concept Check
:class: hint
**(a)** A particle moves along a curve with constant speed $5$ for $3$ seconds. How long is the path?

**(b)** Can the polygon lengths in [From Polygons to an Integral](#l07-sec-polygons) ever exceed the length of the curve?

:::{dropdown} Answer
(a) $L=\int_0^3 5\,dt=15$, regardless of the shape of the curve.

(b) No. Each chord satisfies $|\vv{r}(t_k)-\vv{r}(t_{k-1})|=\bigl|\int_{t_{k-1}}^{t_k}\vv{r}'(t)\,dt\bigr|\le\int_{t_{k-1}}^{t_k}|\vv{r}'(t)|\,dt$ (a triangle inequality for integrals: a straight segment is the shortest path). Summing over $k$, every inscribed polygon is at most $L$; refining the partition never decreases the polygon length, and the lengths approach $L$.
:::
::::

## Common Errors

:::{caution} Avoid these errors
- Integrating $\vv{r}'(t)$ instead of $|\vv{r}'(t)|$; the length is a scalar and the integrand is the speed.
- Dropping absolute values when simplifying $\sqrt{\;\cdot\;}$; for example, $\sqrt{4\cos^2(\theta/2)}=2|\cos(\theta/2)|$, not $2\cos(\theta/2)$ on all of $[0,2\pi]$.
- Using a parametrization that traces part of the curve more than once and reporting the result as the length of the set.
- Forgetting the $f'(\theta)^2$ term in the polar formula, i.e., computing $\int f(\theta)\,d\theta$.
- Confusing $s(t)$ (a function of $t$) with $L$ (a number): $L=s(b)$.
:::

## Summary

:::{admonition} Key takeaways
:class: summary
- Length: $L=\int_a^b|\vv{r}'(t)|\,dt$, the limit of inscribed polygon lengths.
- Length is unchanged by monotone $C^1$ reparametrization; a parametrization that retraces part of the curve counts that part again.
- Arc length function $s(t)=\int_a^t|\vv{r}'(u)|\,du$ with $s'(t)=|\vv{r}'(t)|$.
- Parametrized by arc length $\iff$ unit speed; then $d\vv{r}/ds=\vv{T}$.
- Polar curves: $L=\int_\alpha^\beta\sqrt{f(\theta)^2+f'(\theta)^2}\,d\theta$.
:::

## In-Class Practice

Try each problem before opening its solution.

:::{exercise}
:label: l07-practice-1
Find the length of the astroid $\vv{r}(t)=\ip{\cos^3t,\;\sin^3t}$, $0\le t\le2\pi$. (Hint: use symmetry.)
:::

:::{solution} l07-practice-1
:class: dropdown
$\vv{r}'(t)=\ip{-3\cos^2t\sin t,\;3\sin^2t\cos t}$, so $|\vv{r}'(t)|=\sqrt{9\sin^2t\cos^2t(\cos^2t+\sin^2t)}=3|\sin t\cos t|$. The four quarters have equal length, and on $[0,\pi/2]$ the absolute value can be dropped:

$$
L=4\int_0^{\pi/2}3\sin t\cos t\,dt=12\Bigl[\tfrac12\sin^2t\Bigr]_0^{\pi/2}=6.
$$
:::

:::{exercise}
:label: l07-practice-2
Find the length of $\vv{r}(t)=\ip{\tfrac12t^2,\;\tfrac13t^3}$, $0\le t\le\sqrt3$.
:::

:::{solution} l07-practice-2
:class: dropdown
$\vv{r}'(t)=\ip{t,t^2}$, $|\vv{r}'(t)|=t\sqrt{1+t^2}$ for $t\ge0$. Then $L=\int_0^{\sqrt3}t\sqrt{1+t^2}\,dt=\Bigl[\tfrac13(1+t^2)^{3/2}\Bigr]_0^{\sqrt3}=\tfrac13(8-1)=\tfrac73$.
:::

:::{exercise}
:label: l07-practice-3
Find the length of $\vv{r}(t)=\ip{6t,\;3\sqrt2\,t^2,\;2t^3}$, $0\le t\le1$.
:::

:::{solution} l07-practice-3
:class: dropdown
$\vv{r}'(t)=\ip{6,\;6\sqrt2\,t,\;6t^2}$, so $|\vv{r}'(t)|^2=36+72t^2+36t^4=36(1+t^2)^2$ and $|\vv{r}'(t)|=6(1+t^2)$. Then $L=\int_0^1 6(1+t^2)\,dt=6\bigl(1+\tfrac13\bigr)=8$.
:::

:::{exercise}
:label: l07-practice-4
Reparametrize the line $\vv{r}(t)=\ip{1+2t,\;3-t,\;2t}$ by arc length measured from the point $(1,3,0)$.
:::

:::{solution} l07-practice-4
:class: dropdown
$(1,3,0)=\vv{r}(0)$ and $|\vv{r}'(t)|=|\ip{2,-1,2}|=3$, so $s=3t$ and $t=s/3$: $\tilde{\vv{r}}(s)=\ip{1+\tfrac{2s}{3},\;3-\tfrac{s}{3},\;\tfrac{2s}{3}}$, $s\ge0$ (or $s\in\R$ for the whole line, with $s<0$ measuring backward). Check: $|\tilde{\vv{r}}'(s)|=\tfrac13|\ip{2,-1,2}|=1$. $\checkmark$
:::

:::{exercise}
:label: l07-practice-5
Find the length of the polar curve $r=e^{\theta}$, $0\le\theta\le2\pi$.
:::

:::{solution} l07-practice-5
:class: dropdown
$f=f'=e^\theta$, so $\sqrt{f^2+(f')^2}=\sqrt2\,e^\theta$ and $L=\sqrt2\int_0^{2\pi}e^\theta\,d\theta=\sqrt2\,(e^{2\pi}-1)\approx755.9$.
:::

:::{exercise}
:label: l07-practice-6
Use the length formula to show that the segment $\vv{r}(t)=\vv{p}+t(\vv{q}-\vv{p})$, $0\le t\le1$, has length $|\vv{q}-\vv{p}|$.
:::

:::{solution} l07-practice-6
:class: dropdown
$\vv{r}'(t)=\vv{q}-\vv{p}$ is constant, so $L=\int_0^1|\vv{q}-\vv{p}|\,dt=|\vv{q}-\vv{p}|$, the distance from $\vv{p}$ to $\vv{q}$. The integral definition agrees with ordinary distance for segments.
:::

:::{exercise}
:label: l07-practice-7
Let $\vv{r}(s)$ be parametrized by arc length and twice differentiable. Prove that $\vv{T}'(s)$ is orthogonal to $\vv{T}(s)$.
:::

:::{solution} l07-practice-7
:class: dropdown
Since $\vv{r}$ is parametrized by arc length, $\vv{T}(s)=\vv{r}'(s)$ and $|\vv{T}(s)|=1$ for all $s$. By the constant-length theorem ({prf:ref}`l06-thm-constant-length`), $\vv{T}(s)\cdot\vv{T}'(s)=0$. (Equivalently: differentiate $\vv{T}\cdot\vv{T}=1$ to get $2\,\vv{T}\cdot\vv{T}'=0$.) The magnitude $|\vv{T}'(s)|$ is the *curvature*, which measures how fast the direction turns per unit length.
:::

## Before the Next Class

We begin [Module 2](../module-02/module-02.md). Read Briggs §15.1 (graphs and level curves) and §15.2 (limits and continuity). Review open balls from [Lecture 02](#l02-def-sphere): they are the neighborhoods used to define limits of functions of several variables.
