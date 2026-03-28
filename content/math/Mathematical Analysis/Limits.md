---
publish: true
created: 2026-03-15T18:21:42.299+08:00
modified: 2026-03-26T07:25:49.106+08:00
---

If by selecting a small _punctuated neighborhood_ of $x$, a variable $y$ determined by $x$ can close enough to a fix value in any level, then that variable $y$ is converge to that fix value.

# Definition of Limits

## Limits of Sequence

$$
\lim\_{ n \to \infty } x\_{n}= A
$$
is saying:
$$
\forall \epsilon > 0, \exists N >0, \forall n >N, |x\_{n} - A| \leq \epsilon
$$

## Limits of function

the limit of $f$ of $x$ as $x$ approaches $c$
$$
\lim\_{ x \to a } f(x) = A
$$
it means that the value of the function $f$ can be made arbitrary close to $L$ by choosing x close to $c$
$$
\forall \epsilon > 0, \exists \delta > 0, \forall x \in \left{ x : 0 < |x - a| < \delta \right}, |f(x) - A| < \epsilon
$$

$$
\lim\_{ x \to \infty } f(x) = A
$$

is saying:

$$
\forall \epsilon > 0, \exists x\_{0} > 0, \forall x > x\_{0}, |f(x) - A| < \epsilon
$$

# Heine's Theorem

人话：所有路径都收敛于一个值，那么就在该区域无死角收敛了。

证明：

- 如果函数收敛，自然每一条路径都收敛
- 如果函数不收敛，那么能够构造不收敛的坏数列

# Sign-Preserving Property

> [!quote] Sign-Preserving Property
> If a function $f$ has a limit $A$ on $a$ , then there's a punctured neighborhood $I\_{a}$ of $a$, one that set, $f$ keeps the same sign with the limit $A$

Suppose $\lim\_{ x \to a }f(x) = A > 0$

Set $\epsilon=\frac{A}{2}$, then $\exists \delta > 0$, $\forall x \in (a - \delta, a) \cup (a, a+\delta)$, $\left| f(x) - A \right| < \epsilon = \frac{A}{2} \implies f(x) > \frac{A}{2} > 0$

So as when $\lim\_{ x \to a } f(x) = A < 0$

# Squeeze Theorem

> [!quote] Squeeze Theorem
> if $g(x) \leq f(x) \leq h(x)$, and $g(x)$ and $h(x)$ has same limitation $A$ on $a$, then $f(x)$ also has limitation $A$ on $a$

$$
\begin{align}
& \lim\_{ x \to a } g(x) = \lim\_{ x \to a } h(x) = A \\
\implies & \forall \epsilon > 0, \exists\delta\_{1}, \delta\_{2} > 0, \delta = \min(\delta\_{1}, \delta\_{2}), \forall x \in (a-\delta, a) \cup (a, a + \delta), |g(x) - A| < \epsilon, |h(x) - A| < \epsilon \\
\implies &  A - \epsilon < g(x) < A + \epsilon, A - \epsilon < h(x) < A + \epsilon \\
\implies & A- \epsilon < g(x)\leq f(x) \leq h(x) < A+\epsilon \\
\implies & |f(x) - A| < \epsilon \\
\implies & \lim\_{ x \to a } f(x) = A
\end{align}
$$

# Order Property of Limits

> [!quote] Order Property of Limits
> If $f(x) \leq g(x)$, and $\lim\_{ x \to a }f(x) = A, \lim\_{ x \to a }g(x) = B$, then $A \leq B$

if $A > B$, then for $\epsilon=\frac{A-B}{2}$, $\exists \delta\_{1}, \delta\_{2} > 0, \delta=\min(\delta\_{1},\delta\_{2}), \forall x \in (a-\delta,a) \cup (a, a + \delta)$:

$$
\begin{align}
& |f(x) - A| < \frac{A-B}{2}, |g(x) - B| < \frac{A-B}{2} \\
\implies & f(x) > \frac{A + B}{2}, g(x) < \frac{A+B}{2} \\
\implies & g(x) < f(x)
\end{align}
$$
which contradicts with $f(x) \leq g(x)$. So $A \leq B$

# Local Boundedness

> [!quote] Local Boundness
> If $\lim\_{ x \to a }f(x) = A$, $f(x)$ is bounded in some punctured neighborhood of $a$

# Rules with Real Number Operations

$$
\lim\_{ x \to a } f(x) = A, \lim\_{ x \to a } g(x) = B
$$

## Constant Rule

swappable to scalar product
$$
\lim\_{ x \to a } k f(x) = k \lim\_{ x \to a } f(x)
$$

---

Proof

with $\delta$, $|f(x) - L| \leq \frac{\epsilon}{|k|}$, thus:

$$
|kf(x) - kL| = |k| |f(x) - L | \le \epsilon
$$

## Sum Rule

distributive to function addition
$$
\lim\_{ x \to a } \left\[ f(x) + g(x) \right] = \lim\_{ x \to a } f(x) + \lim\_{ x \to a } g(x)
$$

---

Proof: (triangular Inequality)

with $\delta\_{1}$, $|f(x) - L| \leq \frac{\epsilon}{2}$
with $\delta\_{2}$, $|g(x) - M| \leq \frac{\epsilon}{2}$
Thus
$$
\begin{align}
|f(x) + g(x) - (L + M)| \leq & |f(x) - L| + |g(x) - M| \\
\leq & \frac{\epsilon}{2} + \frac{\epsilon}{2} = \epsilon
\end{align}
$$

$$
\lim\_{ x \to a }\left\[ f(x) + g(x) \right] = \lim\_{ x \to a } f(x) + \lim\_{ x \to a } g(x)
$$

## Product Rule

distributive to function product

$$
\lim\_{ x \to a } \left\[ f(x)g(x) \right] = \lim\_{ x \to a } f(x) \lim\_{ x \to a } g(x)
$$

Proof:

1. involve a trick of constructing $|f(x) - L|$ and $|g(x) - M|$
2. be aware that $f(x)$ is locally bounded due to the [[#Local Boundness]]

$\forall \epsilon > 0$:

- with $\delta\_{1}$, $|f(x) - L| < \frac{\epsilon}{2(|M| + 1)}$, thus $|f(x)| < |f(x) - L| + |L| < \frac{\epsilon}{2(|M| + 1)} + |L| = K$
- with $\delta\_{2}, |g(x) - M| < \frac{\epsilon}{2K}$,

so, with $\delta = \min(\delta\_{1}, \delta\_{2})$,
$$
\begin{align}
|f(x)g(x) - ML | & = |f(x) g(x) - Mf(x) + Mf(x) - ML| \\
& \leq |f(x)||g(x) - M|+ |M||f(x) - L| \\
& \leq K \frac{\epsilon}{2K} + |M|\frac{\epsilon}{2(|M| + 1)} \\
& \leq \epsilon
\end{align}
$$

## Quotient Rule

distributive to function devision
$$
\lim\_{ x \to a } \frac{f(x)}{g(x)} = \frac{\lim\_{ x \to a } f(x)}{\lim\_{ x \to a } g(x)}
$$

---

Proof

key steps:

step1: Proof $\lim\_{ x \to a } \frac{1}{g(x)} = \frac{1}{B}$
$$
\begin{align}
\left| \frac{1}{g(x)} - \frac{1}{B} \right| & = \left| \frac{B - g(x)}{Bg(x)} \right| \\
& =  \frac{|B-g(x)|}{|B||g(x)|}
\end{align}
$$

step2: use [[#distributive to function product]]:

$$
\lim\_{ x \to a } \frac{f(x)}{g(x)} = \lim\_{ x \to a } f(x) \frac{1}{g(x)} = \frac{A}{B}
$$

---

Detail Proof

This proof is divided into two steps:

1. proof $\lim\_{ x \to a } \frac{1}{ g(x)} = \frac{1}{M}$ and reverse triangular inequality
2. product rule

with $\delta\_{1}$, $|g(x) - M| \le \frac{|M|}{2}$, which saids:

$$
\begin{align}
||g(x)| - |M|| \leq |g(x) - M| \leq \frac{|M|}{2} \\
-\frac{|M|}{2} \leq |g(x)| - |M| \leq \frac{|M|}{2} \\
\frac{|M|}{2} \leq |g(x)| \leq \frac{3}{2} |M|
\end{align}
$$
with $\delta\_{2}$, $|g(x) - M| \leq \frac{|M|^{2}\epsilon}{2}$

Thus:
$$
\left| \frac{1}{g(x)} -  \frac{1}{M} \right| = \left| \frac{M - g(x)}{Mg(x)} \right| = \frac{|g(x) - M|}{|M||g(x)|} \leq \epsilon
$$

Thus:
$$
\lim\_{ x \to c } \frac{1}{g(x)} = \frac{1}{M}
$$
applying the product rule:

$$
\lim\_{ x \to c } \frac{f(x)}{g(x)} = \lim\_{ x \to c } f(x) \lim\_{ x \to c } \frac{1}{g(x)} = \frac{L}{M}
$$

## Composition Rule

> [!quote] composition rule
> if $f$ is continuous, then
> $$
> \lim\_{ x \to x\_{0} } f(g(x)) = f\left( \lim\_{ x \to x\_{0} } g(x) ) \right)
> $$

$$
\begin{align}
\forall x \in \dot{U}(x\_{0}, \delta\_{x}), u=g(x) \in U(u\_{0}, \delta\_{u}) \\
\forall u \in \dot{U}(u\_{0}, \delta\_{u}), y=f(x) \in U(y\_{0}, \epsilon) \\
f(u\_{0})=\underbrace{ y\_{0} }_{ \text{ the limit} } \\
\implies \forall x \in \dot{U}(x_{0}, \delta\_{x}), y=f(x) \in U(y\_{0}, \epsilon)
\end{align}
$$
