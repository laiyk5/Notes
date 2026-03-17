---
publish: true
created: 2026-03-16T18:25:08.115+08:00
modified: 2026-03-17T07:55:30.584+08:00
---


# Big Three Ratio
## Big $O$

>[!quote] Big $O$: The Ceiling
>$f(n) = O(g(n))$ means $f(x)$ growth rate is upper-bounded by $g(x)$

$$
\lim_{ n \to \infty } \frac{f(n)}{g(n)} < \infty
$$

This saids: there exists a constant $M\geq0$ and a constant $\delta > 0$, as $x \in (a-\delta, a) \cup (a, a+\delta)$, $\left| \frac{f(x)}{g(x)} \right| \leq M$, or

$$
|f(x)| \leq M|g(x)|
$$

, $f(x)$ is bounded by $g(x)$

### Example 1

Prove that $f(n) = 3n^{2} + 5n + 2 = O(n^{2})$

$$
\left| \frac{f(n)}{n^{2}} \right| = \left| 3 + \frac{5}{n} + \frac{2}{n^{2}} \right|
$$
as $N\geq1$, $\left| \frac{f(n)}{n^{2}} \right|\leq 3 + 5 + 2= 10$, which saids $|f(n)| \leq 10 |n^{2}|$, it's bounded by $n^{2}$


## Big Theta Notation

> [!quote] Big Theta Notation: Same Growth Rate
> 
> $f(x) = \Theta (g(x))$ implies $f(x)$ has exactly the same growth rate as $g(x)$
> 

$$
0 < c_{1} \leq \left| \frac{f(n)}{g(n)} \right| \leq c_{2}
$$

## Big Omega Notation

$f(x) = \Omega(g(x))$ saids that $\exists N > 0$, as long as $n>N$

$$
\left| \frac{f(n)}{g(n)} \right| \geq c_{1} > 0
$$

# Little $o$

> [!quote] little $o$: strict ceiling
> $f(x) = o(g(x))$ means $f(x)$ becomes insignificant compared to $g(x)$

$$
\lim_{ x \to \infty } \frac{f(n)}{g(n)} = 0
$$

# Notations

| symbol              | Asymptotic meaning     | read it out                              | The algorithm is...    |
| ------------------- | ---------------------- | ---------------------------------------- | ---------------------- |
| $f(x)\prec g(x)$    | $f(x) = o(g(x))$       | $f(x)$ grows strictly slower than $g(x)$ | little o of g of x     |
| $f(x) \preceq g(x)$ | $f(x) = O(g(x))$       | $f(x)$ grows no faster than $g(x)$       | o of g of x            |
| $f(x) \succeq g(x)$ | $f(x) = \Omega (g(x))$ | $f(x)$ grows at least as fast as $g(x)$  | omega of g of x        |
| $f(x) \succ g(x)$   | $f(x) = \omega(g(x))$  | $f(x)$ grows strictly faster than $g(x)$ | little omega of g of x |
| $f(x) \asymp g(x)$  | $f(x) = \Theta (g(x))$ | $f(x)$ grows as fast as $g(x)$           | theta of g of x        |

