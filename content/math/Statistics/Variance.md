
# Variance of Single RV

$$
\mathrm{Var}[X] := \mathbb{E}[(X-\mu)^{2}]
$$

applying [[math/Statistics/Expectation#Linearity]] and [[math/Statistics/Expectation#Distributivity w.r.t addition]]:

$$
\begin{align}
\mathrm{Var}[X] &= \mathbb{E}[X^{2} - 2\mu X + \mu^{2}] \\
&= \mathbb{E}[X^{2}] - 2\mu \mathbb{E}[X] + \mu^{2} \\
&= \mathbb{E}[X^{2}] - \mu^{2}
\end{align}
$$


## Transformation

## $Y=CX$

$$
\sigma_{CX}^{2} = C^{2}\sigma_{X}^{2}
$$

Proof:

$$
\begin{align}
\sigma^{2}_{Y} & = E[Y^{2}]- E^{2}[Y] \\
 & = E[C^{2}X^{2}]-E[CX]^{2} \\
 & = C^{2}(E[X^{2}] - E[X]^{2}) \\
 & = C^{2}\sigma_{X}^{2}
\end{align}
$$

## $Y=X+C$

Suppose $Y=X+C$, $C$ is a constant:

$$
\sigma_{X+C}^{2} = \sigma_{X}^{2}
$$

Proof 1:

Given (Proofs are in [[math/Statistics/Expectation#Linearity]] and [[math/Statistics/Distribution#Transformation]]):
$$
\begin{align}
\mu_{Y} & = \mu_{X} + C \\
f_{Y}(y) & = f_{X}(y-C)
\end{align}
$$


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

Proof2:

with [[math/Statistics/Expectation#LOTUS]] the proof is simpler:

$$
\begin{align}
\sigma_{Y}^{2} & = E[(Y-\mu_{Y})^{2}] \\
 & = E\left\{ \left[ \left( X+C \right) - \left( \mu_{X}+C \right) \right]^{2} \right\} \\
 & = E\left[ \left( X-\mu_{X} \right)^{2} \right] = \sigma_{X}^{2}
\end{align}
$$

## Sum Rule

$$
\begin{align}
\mathrm{Var[X+Y]} &= E\left\{ \left[ (X+Y) - (\mu_{X}+\mu_{Y})\right]^{2}  \right\} \\
&= \sigma_{X}^{2}+\sigma_{Y}^{2}+2\mathrm{Cov}(X,Y)
\end{align}
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

