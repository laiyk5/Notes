---
publish: true
created: 2026-03-15T18:11:20.840+08:00
modified: 2026-03-26T05:30:26.518+08:00
---

# Definition

if a function $f$ is continuous on $(a,b)$, it's saying that for any $x\_{0} \in (a,b)$, s.t.:

$$
\lim\_{ x \to x\_{0}} f(x) = f(x\_{0})
$$

# Boundedness Theorem

> [!quote] If a function is continuous on a close-interval $\[a,b]$, then its bounded on that interval.

Proof with [[Real Number#Bolzano-Weierstrass Theorem |Bolzano-Weierstrass Theorem]].

Suppose that: the function boundless on $\[a,b]$

If the function is boundless, loop this process, starts with $I\_{0} = \[a,b]$:

1. bisect the interval $I\_{n}$ with $c=\frac{a+b}{2}$
2. select the boundless half $I\_{n+1} =$ $\[a,c]$ or $\[c,b]$
3. select a point $x\_{n} \in I\_{n+1}$ making this half boundless to build a sequence $\left{ x\_{n} \right}$
4. continue this process with $I\_{n+1}$

And finally we have a infinite bounded sequence $\left{ x\_{n} \right}$ and an unbounded sequence $f(x\_{n})$ s.t.:

1. converge to some number $x\_{0} \in \[a,b]$ ([[Real Number#Bolzano-Weierstrass Theorem|Bolzano Weierstrass Theorem]])
2. $f(x\_{n})$ is unbounded, which contradicts to $\lim\_{ x \to x\_{0} } f(x) = f(x\_{0})$ ([[math/Mathematical Analysis/Limits#Heine's Theorem|Heine Theorem]])

So the function is bounded on $\[a,b]$

# Intermediate Value Theorem

> [!quote] IVT
> If a function is continuous on a close-interval $\[a,b]$, then for any intermediate value $u \in \[f(a),f(b)]$, there's some value $c \in \[a,b]$ making that $f(c) = u$

Proof

Build nested intervals with this process:

1. bisect the interval $\[a\_{n}, b\_{n}]$ with $c=\frac{a+b}{2}$
2. if $f(c) = u$, stop.
3. select the half $\[a\_{n+1},b\_{n+1}]$ making $u \in \left\[ f(a\_{n+1}), f(b\_{n+1}) \right]$
4. continue this process

So we get a nested interval $\left{ a\_{n}, b\_{n} \right}$, which locate exactly one real number $c$, and $a\_{n} \to c, b\_{n} \to c$ ([[Real Number#Nested Interval Theorem|Nested Interval Theorem]]). As the function is continuous on $\[a,b]$, with [[math/Mathematical Analysis/Limits#Heine's Theorem|Heine's Theorem]]:
$$
\begin{align}
\lim\_{ n \to \infty } f(a\_{n}) & = f(\lim\_{ n \to a\_{n} } a\_{n}) = f(c) \\
\lim\_{ n \to \infty } f(b\_{n}) & = f(\lim\_{ n \to b\_{n} } b\_{n}) = f(c) \\
\implies \lim\_{ n \to \infty } \left\[ f(a\_{n}) - f(b\_{n}) \right] & = \lim\_{ n \to \infty } f(a\_{n}) - \lim\_{ n \to \infty } f(b\_{n}) = 0
\end{align}
$$

So we have another set of nested intervals $\left{ f(a\_{n}), f(b\_{n}) \right}$ that locate a unique number, which can only be $u$ since $u \in \left\[ f(a\_{n}), f(b\_{n}) \right], \forall n \in \mathbb{Z}$. (Nested Interval Theorem)

# Extreme Value Theorem

> [!quote] Extreme Value Theorem
> If a function is continuous on $\[a,b]$, then there's a maxima and minima in $\[a,b]$.

As [[#Boundedness Theorem]] said, the function is bounded, so the function has a supremum and infimum, w.r.t. [[Real Number#Dedekind Completeness Theorem|Dedekind Completeness Theorem]]. If the supremum is $M$.

Suppose  $\forall x \in \[a,b], f(x) < M$. $g(x) = \frac{1}{M - f(x)}$ is also a continuous function, thus it's also bounded. Suppose $K>0$ is an upper bound of $g(x)$ on $\[a,b]$:

$$
\begin{align}
g(x) = \frac{1}{M - f(x)} \leq K \\
\implies f(x) \leq M - \frac{1}{K}
\end{align}
$$
so $M-\frac{1}{K}$ is also an upper bound for $f(x)$ on $\[a,b]$, which contradicts to the setting that $M$ is the supremum. So there must be some value $c \in \[a,b]$ s.t. $f(c) = M \geq f(x)$.

# Mean Value Theorems

## Fermat's Lemma

> [!quote] Fermat's Lemma
> derivative on maxima / minima must be zero

Proof:

Suppose $x\_{0}$ is a maxima.
$$
f'(x\_{0}) = \lim\_{ x \to x\_{0} } \frac{f(x) - f(x\_{0})}{x - x\_{0}}
$$
It said that:

$$
\begin{align}

\forall \epsilon > 0, \exists \delta > 0, \forall x \in (x\_{0} - \delta, x\_{0} + \delta), \left| \frac{f(x) - f(x\_{0})}{x- x\_{0}} - A\right| < \epsilon \\

\end{align}
$$

## Rolle's MVT

> [!quote] Rolle's MVT
> if function $f$ is continuous on $\[a,b]$ and $f(a) = f(b)$, then:
> $$\exists \xi \in \[a,b], f'(\xi)=0$$

A function is continuous on $\[a,b]$, then with [[#Extreme Value Theorem]], there must be a maxima $\xi \in \[a,b]$, and then with [[#Fermat's Lemma]], $f'(\xi) = 0$

## Lagrange MVT

> [!quote] Lagrange MVT
> If function $f$ is continuous on $\[a,b]$, then:
> $$
> \exists \xi \in \[a,b], f'(\xi) = \frac{f(b)-f(a)}{b - a}
> $$
> , which saids the derivative on some intermediate point concludes the change of endpoint.

Proof:

build a flat function $F$ containing $f(x)$ to apply [[#Rolle's MVT]]:
$$
F(x) = (f(x) - f(a)) - \frac{f(b)-f(a)}{b-a} (x-a)
$$
So that $F(b) = F(a) = 0$

So with Rolle's MVT, $\exists \xi \in \[a,b], F'(\xi) = 0$

$$
f'(\xi) = \frac{f(b) - f(a)}{b-a}
$$

## Cauchy MVT

> [!quote] Cauchy MVT
> if function $f,g$ are both continuous on $\[a,b]$, then:
> $$
> \exists \xi \in \[a,b], \frac{f'(\xi)}{g'(\xi)} = \frac{f(b)-f(a)}{g(b)-g(a)}
> $$

construct a function whose derivative is in the form that fit the theorem:

$$
\begin{align}
h(x) & = f(x) \left\[ g(b) - g(a) \right] - g(x)\left\[ f(b) - f(a) \right] \\
h(a) & = f(a)g(b) - f(b)g(a) \\
h(b) & = f(a)g(b) - f(b)g(a)
\end{align}
$$
so by [[#Rolle's MVT]]:
$$
\frac{f'(\xi)}{g'(\xi)} = \frac{f(b) - f(a)}{g(b) - g(a)}
$$

## MVT for Integrals

> [!quote] MVT for Integrals
> If function $f$ is continuous on $\[a,b]$, then the mean integral is an intermediate value of $f(x)$
> $$
> \frac{1}{b-a}\int\_{a}^{b}f(x),dx = f'(\xi)
> $$

$f(x)$ is continuous on $\[a,b]$, so with [[#Boundedness Theorem]], $f(x)$ is bounded:
$$
\begin{align}
\int\_{a}^{b}m ,dx \leq \int\_{a}^{b}f(x),dx \leq \int\_{a}^{b} M , dx \\
\frac{1}{b-a}\int\_{a}^{b}f(x),dx \in \[m, M]
\end{align}
$$
then with [[#Intermediate Value Theorem|IVT]]:

$$
f(c) = \frac{1}{b-a} \int\_{a}^{b}f(x),dt
$$

# Fundamental Theorem of Calculus

if $f$ is continuous at $x=a$

accumulation function is one of the antiderivative

$$
\left( \int\_{a}^{x} f(t) , dt \right)' = f(x)
$$
Integration is difference:
$$
\int\_{a}^{b} f(x),dx = F(b) - F(a)
$$

---

Proof:

Prove it by [[#MVT for Integrals]]:
$$
\frac{\int\_{a}^{x+\Delta x} f(t),dt - \int\_{a}^{x} f(t),dt}{\Delta x} = \lim\_{ \Delta x \to 0 }  f(\xi) = f(\lim\_{ \Delta x \to 0 } \xi) = f(a)
$$

So any original function of $f(x)$, denoted by $F(x)$, can be represented by adding some constant $C$ to $\int\_{a}^{x}f(t),dt$:
$$
F(x) = \int\_{a}^{x}f(t),dt + C
$$
substituting $x$ with $a$, we know the constant is $F(a)$
$$
F(a) = \int\_{a}^{a}f(t),dt + C = C
$$
substituting $x$ with $b$, then the integration of $f(t)$ from $a$ to $b$ is the difference of the value of the endpoints of any antiderivative $F$:

$$
\int\_{a}^{x} f(t),dt = F(x) - F(a)
\implies \int\_{a}^{b}f(t),dt = F(b) - F(a)
$$

# Prerequisite of differentiable

it must be continuous to be derivable, or equivalently, differentiable.

if $f$ is differentiable, then $\Delta y$ is also an infinitesimal -- which implies that $f$ is continuous.
$$
\lim\_{ \Delta x \to 0 } \Delta y = \lim\_{ \Delta x\to 0 } \left( f'(x)\Delta x  + o(\Delta x) \right) = 0
$$
