> [!quote] Gaussian Distribution
> Named after Gaussian, with some assumptions on error, describe the uncertainty of samples.

# Distribution of Errors

## Assumptions

1. sum up to zero (average of samples is the true value)
2. $p(e\_1) \le p(e\_2)$ if $e\_1 \ge e\_2$
3. errors are independent

## Solving the probability density of the error

Suppose:

- the probability (density) function of error is $f$
- the true value is $L$
- the observed values are $X=\left{ x\_{i} \right}$
- the errors are $\left{ z = x-L | x \in X \right}$

Then the [[Maximum Likelihood Estimation]] of the true value $L$ give the first constraint

$$
\begin{align}
\ln P =& \sum\_i^n \ln f(x\_i - L) & \text{log-lilkelihood} & \\
\frac{\partial \ln P}{\partial L} =& \sum\_{i}^n \frac{f'(x\_i - L)}{f(x\_i -L)} (-1) \\
\=&\sum\_{i=1}^n g(x\_i - L) = 0& \text{MLE L s.t. maximize P} & \\
\end{align}
$$

This process says: to maximize the likelihood of $L$, function $g(z) = -\frac{f'(z)}{f(z)}$ should sums up to $0$.

Now with the assumption that all errors sums to $0$, we have two constraints:

$$
\begin{align}
\sum\_{i=1}^{n} g(z\_{i}) = 0 \\
\sum\_{i=1}^{n} z\_{i} = 0
\end{align}
$$

$g(z) = Cz$ can be one solution, thus:

$$
g(z) = Cz \implies \frac{f'(z)}{f(z)} = -Cz
$$

Solve $f$ from the differential equation:

$$
\begin{align}
\int \frac{f'(z)}{f(z)} dz &= \int  (-Cz) dz & \text{continuous function has antidirevatives} & \\
\int \frac{1}{f(z)} d f(z) &= (-\frac{C}{2} z^2) + C' & \text{solve right side} & \\
\ln(f(z)) &= (-\frac{C}{2} z^2) + C'' & \text{solve left side with chain rule} & \\
f(z) &= A\left(e^{-\frac{C}{2}z^2}\right) & \text{power of e} &

\end{align}
$$

So the distribution of error is parameterized by $A$ and $C$, and the parameterized probability density is:

$$
f(z) = A \left( e^{ -Cz^{2}/2} \right)
$$

> [!note] why not $g(x) = x^{3}$?
> IDK, TODO

### Solving A

As probability density is the derivative of accumulation function, integration of $f(z)$ on $\[-\infty, +\infty]$ should be $1$:

$$
\begin{align}
1 = & \int\_{-\infty}^{+\infty} f(z) dx \\
\=& A \int\_{-\infty}^{+\infty} e^{-\frac{C}{2}z^2} dx \\
\overset{x = \sqrt{\frac{2}{C}}t}{=}& A\sqrt{\frac{2}{C}}  \int\_{-\infty}^{+\infty} e^{-t^2} dt \\
\end{align}
$$

with [[Gaussian Integral]]:

$$
1 = A\sqrt{\frac{2\pi}{C}} \implies A = \sqrt{ \frac{C}{2\pi} }
$$

## Interpreting $C$

### Variation of Error

$$
\begin{align}
\sigma^{2} & = \int\_{-\infty}^{+\infty} x^{2}f(x),dx \\
& = -\frac{1}{C} \int\_{-\infty}^{+\infty} x \left((-Cx)  A \exp\left( -\frac{Cx^{2}}{2} \right) \right) , dx \\
& = -\frac{1}{C} \int\_{-\infty}^{\infty} x \left\[ A \exp\left( -\frac{Cx^{2}}{2} \right) \right]'   , dx \\
& = -\frac{1}{C} \left{ \left\[ f(x) \right]_{-\infty}^{+\infty} - \int_{-\infty}^{\infty} f(x) , dx  \right} \\
& = -\frac{1}{C} \left\[ 0 - 1 \right] = \frac{1}{C}
\end{align}
$$

with $\sigma^{2}=\frac{1}{C}$, then:

$$
f(x) =  \frac{1}{\sigma\sqrt{ 2\pi }} \exp\left( -\frac{x^{2}}{2\sigma^{2}} \right)
$$

## Expectation of Error

For any function symmetric w.r.t. $(a,0)$, its integral on $\[-\infty, +\infty]$ is $0$:

$$
\begin{align}
\int\_{-\infty}^{\infty} f(x) , dx & = \int\_{-\infty}^{a} f(x) , dx + \int\_{a}^{\infty} f(x) , dx \\
& = -\int\_{0}^{\infty} f(a-t) , dt + \int\_{0}^{\infty} f(a+s) , ds \\
& = 0
\end{align}
$$

as $xf(x)$ is symmetric w.r.t. $(0,0)$:

$$
\mu = \int\_{-\infty}^{\infty} xf(x) , dx = 0
$$

# Distribution of the Samples

## PDF of Samples

substituting the observed variable $Z=X-L$ back, then:

$$
P(X\<x) = P(Z+L\<x) = P(Z\<x-L) = \int\_{-\infty}^{x-L} f(z) , dz = \int\_{-\infty}^{x} f(t-L),dt
$$
thus the density function of distribution $Z$ is

$$
f\_{X}(x) = \left( \int\_{-\infty}^{x} f(t-L),dt \right)' = f(x-L) = A(e^{-C(x-L)^{2}/2})
$$

## Expectation of Samples

expectation of $X$ would be:
$$
\mu\_{X}= \mu + L = L
$$

## Variance of Samples

according to [[Variance#Transformation]], variation of $X$ would be the same, which is $\sigma^{2}$.

# Conclusion

In conclusion, with the assumption of error, the distribution of sample would be described as:

$$
f(x) = \frac{1}{\sqrt{ 2\pi }\sigma}\exp\left( -\frac{(x-\mu)^{2}}{2\sigma^{2}} \right)
$$

where: $\mu$ is the expectation and $\sigma^{2}$ is the variance.
