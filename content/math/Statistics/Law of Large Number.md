# Chebyshev’s inequality

probability of being an outlier has an upper-bound
$$
\begin{align}
\sigma^2 &= \int\_{-\infty}^{+\infty} (x-\mu)^{2}f(x),dx \\
&\geq \int\_{|x-\mu|\geq \epsilon} (x-\mu)^{2} f(x),dx \\
&\geq\epsilon^{2}P(|x-\mu|\geq\epsilon)
\end{align}
$$
if outliers are identified by $k\sigma$, the probability is bounded by $\frac{1}{k^{2}}$:
$$
P(|x-\mu|\geq k\sigma) \leq \frac{1}{k^{2}}
$$

# Weak Law of Large Number

## Sample Mean

mean of $n$ i.i.d. random variable
$$
\bar{X\_{n}}= \frac{1}{n} \sum\_{i=1}^{n} X\_{i}
$$
has the properties:

- it’s expectation is: $\mu$
- It’s variance is: $\frac{\sigma^{2}}{n}$

by Chebyshev’s inequality,

$$
P(|X-\mu|\geq \epsilon) \leq \frac{\sigma^{2}}{n\epsilon^{2}}
$$

as $n \to +\infty$, $X$ converges to $\mu$ in probability.

$$
\lim\_{ n \to \infty } P(|X - \mu| < \epsilon) \leq \lim\_{ n \to \infty }  \frac{\sigma^{2}}{n\epsilon^{2}} = 0
$$

the probability of being an outlier would be very low.

Why it's called "weak": it converges in probability, which is weaker than almost sure converges, stated by SLLN

# Strong Law of Large Number

$$
P(\lim\_{ n \to \infty } \bar{X}\_{n} = \mu) = 1
$$

the sample mean definitely converges to the expectation as $n$ growths.
