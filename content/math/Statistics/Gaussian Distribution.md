
# Gaussian Distribution

alias: Error Distribution, Gaussian Distribution, Normal Distribution

proposed by: German mathematician Johann Carl Friedrich **Gauss**

---

## background

to figuring out the distribution of error/observation bias

---

## Assumptions

1. sum up to zero (average of samples is the true value)
2. $p(e_1) \le p(e_2)$ if $e_1 \ge e_2$
3. errors are independent

---
## PDF of Error Distribution

---
### Induction of PDF of Error Distribution

---

[[masters/Sem B/CS5487 ML/Maximum Likelihood Estimation]] of the error:

$$
\begin{align}
\ln P =& \sum_i^n \ln f(x_i - L) & \text{log-lilkelihood} & \\
\frac{\partial \ln P}{\partial L} =& \sum_{i}^n \frac{f'(x_i - L)}{f(x_i -L)} (-1) \\
=&\sum_{i=1}^n g(x_i - L) = 0& \text{MLE L s.t. maximize P} & \\
\end{align}
$$

---

With the sample average assumption, we know $g$ can be $g(x) = Cx$:
$$
\begin{align}
\sum_{i=1}^n (x_i-L) =& 0 & \text{smaple average assumption} &\\
g(x) =& Cx & \text{the uniqueness is to be proven}& \\
\frac{f'(x)}{f(x)} =& -Cx  & \text{}
\end{align}
$$
---
Solve $f$ from the differential equation:

$$
\begin{align}
\int \frac{f'(x)}{f(x)} dx &= \int  (-Cx) dx & \text{continuous function has antidirevatives} & \\
\int \frac{1}{f(x)} d f(x) &= (-\frac{C}{2} x^2) + C' & \text{solve right side} & \\
\ln(f(x)) &= (-\frac{C}{2} x^2) + C'' & \text{solve left side with chain rule} & \\
f(x) &= A\left(e^{-\frac{C}{2}x^2}\right) & \text{power of e} &

\end{align}
$$

---

Let's represent the $P(R)$ with $A$ and $C$ first:

Here we use the [[math/Mathematical Analysis/integrals/Integration of Gaussian function]]

$$
\begin{align}
P(R) = & \int_{-\infty}^{+\infty} f(x) dx \\
=& A \int_{-\infty}^{+\infty} e^{-\frac{C}{2}x^2} dx \\
\overset{x = \sqrt{\frac{2}{C}}t}{=}& A\sqrt{\frac{2}{C}}  \int_{-\infty}^{+\infty} e^{-t^2} dt \\
=& A\sqrt{\frac{2\pi}{C}} & \text{integration of Gaussian function} \\
\end{align}
$$

---
Apply the normality of $P$:  $P(R) = 1$, so $A = \sqrt{\frac{C}{2\pi}}$, so
$$
f(x) = \sqrt{\frac{C}{2\pi}} e^{-\frac{C}{2}x^2} \overset{\sigma^2 = 1/C}= \frac{1}{\sigma\sqrt{2\pi}} \exp\left({-\frac{x^2}{2\sigma^2}}\right)
$$
