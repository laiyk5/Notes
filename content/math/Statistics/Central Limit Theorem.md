[[Gaussian Distribution]]

# CLT

while [[Law of Large Number]] saids the sample means almost surely converges to the population's mean, CLT saids the distribution of the $n$-th sample mean $\bar{X}\_{n}$ is a Gaussian distribution controlled by the population's expectation $\mu$ and variance $\sigma^{2}$

$$
\bar{X}\_{n} \sim N\left( \mu, \frac{\sigma^{2}}{n} \right)
$$

# Standardizing sample mean

$$
\bar{X}_{n}=\frac{1}{n}\sum_{i=1}^{n} X\_{i}
$$

according to the sum rules of [[Expectation#Sum Rule]] and [[Variance#Sum Rule]], for i.i.d. $X\_{i}$,

$$
\begin{align}
E(\bar{X}_{n})&=\mu \\
\mathrm{Var}(\bar{X}_{n})&=\frac{\sigma^{2}}{n}
\end{align}
$$
so to standardize sample mean, subtract $\mu$ and divide by $\frac{\sigma}{\sqrt{ n }}$

$$
\bar{Z}_{n} = \frac{X_{n} - \mu}{\sigma / \sqrt{ n }}
$$

and this is equivalent to summing up the standardized samples and dividing by $\sqrt{ n }$:

$$
\begin{align}
\bar{Z}_{n} & = \frac{ \frac{1}{n}\sum_{i=1}^{n} X\_{i} - \mu}{\sigma / \sqrt{ n }} \\
& = \frac{1}{\sqrt{ n }} \sum\_{i=1}^{n} \frac{X\_{i} - \mu}{\sigma} \\
& = \frac{1}{\sqrt{ n }} \sum\_{i=1}^{n} Y\_{i}
\end{align}
$$

# Moment Generating Function

Characteristics Function

$$
M\_{X}(t) = E\left\[ e^{tX} \right]
$$

Why it's called MGF:

1. Expanding  $e^{tX}$ as Maclaurin Series
2. take $n$-th derivatives
3. assign $0$ to $t$, you got the $n$-th moment

$$
\begin{align}
e^{tX} & = 1 + (tX) + \frac{t^{2}}{2!}X^{2} + \dots + \frac{t^{n}}{n!}X^{n} + \dots \\
E\[e^{tX}] & = 1 + tE\[X] + \frac{t^{2}}{2!}E\[X^{2}] + \dots + \frac{t^{n}}{n!}E\[X^{n}] + \dots \\
M^{(n)}_{X}(t) & = E\[X^{n}] + \frac{t}{1!}E\[X^{n+1}] + \frac{t^{2}}{2!}E\[X^{n+2}] +  \dots + \frac{t^{k}}{k!}E\[X^{n+k}] + \dots \\
M_{X}^{(n)}(0) & = E\[X^{n}]
\end{align}
$$

Given independencies of $X$ and $Y$, we have the "sum rule" of MGF
$$
\begin{align}
M\_{X+Y}(t) & = E\[e^{t(X+Y)}] \\
& = E\left\[ e^{tX} e^{tY} \right] \\
& = E\[e^{tX}] E\[e^{tY}] \\
& = M\_{X}(t) \cdot M\_{Y}(t)
\end{align}
$$

## The Scaling Rule

$$
\begin{align}
M\_{CX}(t) & = E\[e^{t(CX)}] \\
& = E\[e^{(Ct)X}] \\
& = M\_{X}(Ct)
\end{align}
$$

[[Expectation#LOTUS]] is used here.

## Uniqueness

MGF is also called characteristic function because the mapping from a function to its MGF is a one to one function.

### Laplace Transform

$$
\mathcal{L}\left{ f(x) \right} = \int\_{-\infty}^{\infty} f(x) e^{-sx} , dx
$$

Linearity leads to uniqueness:

> [!note] Linearity
>
> $$
> \begin{align} \\
> T(A+B) & = T(A) + T(B) \ \\
> T(cA) & = cT(A)
> \end{align}
> $$

$$
\mathcal{L}\left{ f(x) + g(x) \right} = \mathcal{L}\left{ f(x) \right} + \mathcal{L}\left{ g(x) \right}
$$
with linearity, same transformation implies $A-B$ is one of the root of the $T(X)=0$:
$$
T(A)=T(B) \implies T(A-B) = T(A) - T(B) = 0
$$
for Laplace Transform, since the set of function $\left{ e^{-sx} \right}$ forms a complete basis, for any $s$ to make $T(f(x))=T(g(x))$ hold, It must have that $f(x)-g(x)=0$

> [!note] complete basis
> the set of function $\left{ e^{-sx} \right}$ forms a complete basis. You cannot be "perpendicular" to every axis unless you have no "length".
>
> MGFs uses exponentials $e^{tx}$ as basis
> Taylor Series uses polynomials $(1, x^{2},x^{3}, \dots)$ as basis

The Fourier Inversion

$$
f(x) = \frac{1}{2\pi} \int\_{-\infty}^{\infty} e^{-itx} \phi\_{X}(t) , dt
$$

transforming

The Scaling Rule:

### Lerch's Theorem

### Lévy Continuity Theorem

# Proof

approach:

1. the MGF of the standardized sample mean converges to the MGF of the standardized Gaussian
2. the standardized sample mean converges to the standardized Gaussian
3. the sample mean converges to the Gaussian, parameterized by the population's $\mu$ and $\sigma^{2}$

MGF of standardized sample means:
$$
\begin{align}
M\_{\bar{Z}_{n}}(t)&=M_{\sum\_{i=1}^{n}Y\_{i}}\left( \frac{1}{\sqrt{ n }} t \right) \\
&= \prod\_{i=1}^{n} M\_{Y\_{i}}\left( \frac{1}{\sqrt{ n }} t \right) \\
& = \left( M\_{Y}\left( \frac{1}{\sqrt{n}} t \right) \right)^{n} \\
& = \left( 1 + \frac{t^{2}}{2!n}+\dots\right)^{n} \\
& =
\end{align}
$$
