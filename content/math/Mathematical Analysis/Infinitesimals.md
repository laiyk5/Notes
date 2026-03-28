---
publish: true
created: 2026-03-16T19:16:10.917+08:00
modified: 2026-03-17T07:55:11.562+08:00
---

# Equivalent Infinitesimals

$\alpha(x)$ and $\beta(x)$ are equivalent infinitesimals, written as $\alpha(x) \sim \beta(x)$ saids that
$$
\lim\_{ x \to a } \frac{\alpha(x)}{\beta(x)}= 1
$$

> [!warning] oscillating function
> $\alpha$ and $\beta$ should not cross zero "near" $a$, otherwise, the quotient is not defined.

## Transitivity of equivalent

As for [[Limits#Product Rule|Product Rule]], so the equivalent relation has transitivity:

$$
\alpha \sim \beta, \beta\sim \gamma \implies \alpha \sim \gamma
$$

Proof:

$$
\lim\_{ x \to a } \frac{\alpha(x)}{\gamma(x)} = \lim\_{ x \to a } \frac{\alpha(x)}{\beta(x)} \frac{\beta(x)}{\gamma(x)} = \lim\_{ x \to a } \frac{\alpha(x)}{\beta(x)} \lim\_{ x \to a } \frac{\beta(x)}{\gamma(x)} = 1 \cdot 1 = 1
$$

## Equivalent Infinitesimal Trick

$$
\begin{align}
\lim\_{ x \to a } \frac{\alpha(x)}{\beta(x)} & = \lim\_{ x \to a } \frac{\tilde{\alpha}(x)}{\beta(x)} \\
\lim\_{ x \to a } \frac{\alpha(x)}{\beta(x)} & = \lim\_{ x \to a } \frac{\alpha(x)}{\tilde{\beta}(x)}
\end{align}
$$
