
# Variance of Single RV

$$
\mathrm{Var}[X] := \mathbb{E}[(X-\mu)^{2}]
$$

applying [[math/Statistics/Expectation#Linearity]] and [[math/Statistics/Expectation#Distributivity w.r.t addition]]:

$$
\begin{align}
\mathrm{Var}[X] &= \mathbb{E}[X^{2} - 2\mu X + \mu^{2}] \\
&= \mathbb{E}[X^{2}] - 2\mu \mathbb{E}[X] + \mu^{2} \\
&= \mathbb{E}[X^{2}] - \mu
\end{align}
$$


## Transformation

Suppose $Y=X+C$, $C$ is a constant:

$$
\begin{align}
\mu_{Y} & = \mu_{X} + C \\
f_{Y}(y) & = f_{X}(y-C)
\end{align}
$$

(Proofs are in [[math/Statistics/Expectation#Linearity]] and [[math/Statistics/Distribution#Transformation]])

Thus:
$$
\begin{align}
\sigma_{Y}^{2} & = E_{Y}[(Y-\mu_{Y})^{2}] \\
 & = \int_{-\infty}^{\infty} (y-\mu_{Y})^{2} f_{Y}(y) \, dy \\
 & = \int_{-\infty}^{\infty} (y - \mu_{Y})^{2} f_{X}(y-C) \, dy \\
 & = \int_{-\infty}^{\infty} (s+C - (\mu_{X}+C))^{2} f_{X}(s) \, ds \\
 & = E_{X}\left[(X-\mu_{X})^{2}\right] = \sigma_{X}^{2}
\end{align}
$$
Briefly:

$$
\sigma_{X+C}^{2} = \sigma_{X}^{2}
$$

# Covariance

variance between two r.v.

$$
\mathrm{Cov}(X,Y) = \mathbb{E}[(X-\mu_{X})(Y-\mu_{Y})]
$$

also:

$$
\begin{align}
\mathrm{Cov}(X,Y) &=  \mathbb{E}[XY-\mu_{X}Y - \mu_{Y}X + \mu_{X}\mu_{Y}] \\
&= \mathbb{E}[XY] - \mu_{X}\mu_{y}
\end{align}
$$

# Covariance Matrix

