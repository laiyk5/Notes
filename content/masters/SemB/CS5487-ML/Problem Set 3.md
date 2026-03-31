# Problem 3.1 Gamma function

$$
\Gamma(x) = \int\_{0}^{\infty} u^{x-1} e^{-u} ,du
$$

Integrate by parts:

$$
\begin{align}
\Gamma (x+1) & = \int\_{0}^{\infty} u^{x} e^{-u} , du \\
& = \int\_{0}^{\infty} u^{x} (-e^{-u})' d u \\
& = \left\[ u^{x}(-e^{-u}) \right]_{0}^{\infty} - \int_{0}^{\infty} (-e^{-u}) (x u ^{x-1})  , du \\
& = - \lim\_{ u \to \infty }  \frac{u^{x}}{e^{u}} + x \int\_{0}^{\infty} e^{-u}u^{x-1} , du \\
& = x\Gamma(x)
\end{align}
$$

$$
\Gamma(1) = \int\_{0}^{\infty} e^{-u} , du \stackrel{s(u)=-u}= - \int\_{0}^{-\infty} e^s , ds = - \left\[ e^{s} \right]\_{0}^{-\infty} = 1
$$

[[Gamma Function]]

# Problem 3.2 MAP for the exponential density

let $x$ has an exponential density

$$
p(x|\theta) = \begin{cases}
\theta e^{-\theta x} & , & x>0 \\
0 & , & \text{otherwise}
\end{cases}
$$
the prior

# Problem 3.3 Invariance of MAP to linear transformations

# Problem 3.4 Bayesian estimation for the Gaussian mean

# Problem 3.6 Bayesian estimation for the precision of a Gaussian

# Problem 3.7 Bayesian estimation for a multivariate Gaussian

# Problem 3.8 Bayesian estimation for a multinomial distribution

$$
p(x|\pi) = \pi^{x}(1-\pi)^{1-x}
$$

$$
\begin{align}
p(D|\pi) &= \prod\_{i=1}^{n} p(x\_{i}|\pi) \\
&= \prod\_{i=1}^{n} \pi^{x\_{i}}(1-\pi)^{1-x\_{i}} \\
&= \pi^{\sum\_{i=1}^{n}  x\_{i}} (1-\pi)^{\sum\_{i=1}^{n} (1-x\_{i})} \\
&= \pi^{s}(1-\pi)^{1-x}
\end{align}
$$

$$
\begin{align}
p(\pi | D) &= \frac{ p(D|\pi) p(\pi)}{\int p(D|\pi)p(\pi) d\pi} \\
&=

\end{align}
$$

![[masters/SemB/CS5487-ML/Attachments/PS-3.pdf]]
