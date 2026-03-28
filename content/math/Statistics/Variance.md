# Variance of Single RV

$$
\mathrm{Var}\[X] := \mathbb{E}\[(X-\mu)^{2}]
$$

applying [[Expectation#Linearity]] and [[Expectation#Distributivity w.r.t addition]]:

$$
\begin{align}
\mathrm{Var}\[X] &= \mathbb{E}\[X^{2} - 2\mu X + \mu^{2}] \\
&= \mathbb{E}\[X^{2}] - 2\mu \mathbb{E}\[X] + \mu^{2} \\
&= \mathbb{E}\[X^{2}] - \mu^{2}
\end{align}
$$

## Transformation

## $Y=CX$

$$
\sigma\_{CX}^{2} = C^{2}\sigma\_{X}^{2}
$$

Proof:

$$
\begin{align}
\sigma^{2}_{Y} & = E\[Y^{2}]- E^{2}\[Y] \\
& = E\[C^{2}X^{2}]-E\[CX]^{2} \\
& = C^{2}(E\[X^{2}] - E\[X]^{2}) \\
& = C^{2}\sigma_{X}^{2}
\end{align}
$$

## $Y=X+C$

Suppose $Y=X+C$, $C$ is a constant:

$$
\sigma\_{X+C}^{2} = \sigma\_{X}^{2}
$$

Proof 1:

Given (Proofs are in [[Expectation#Linearity]] and [[Distribution#Transformation]]):
$$
\begin{align}
\mu\_{Y} & = \mu\_{X} + C \\
f\_{Y}(y) & = f\_{X}(y-C)
\end{align}
$$

Thus:
$$
\begin{align}
\sigma\_{Y}^{2} & = E\_{Y}\[(Y-\mu\_{Y})^{2}] \\
& = \int\_{-\infty}^{\infty} (y-\mu\_{Y})^{2} f\_{Y}(y) , dy \\
& = \int\_{-\infty}^{\infty} (y - \mu\_{Y})^{2} f\_{X}(y-C) , dy \\
& = \int\_{-\infty}^{\infty} (s+C - (\mu\_{X}+C))^{2} f\_{X}(s) , ds \\
& = E\_{X}\left\[(X-\mu\_{X})^{2}\right] = \sigma\_{X}^{2}
\end{align}
$$

Proof2:

with [[Expectation#LOTUS]] the proof is simpler:

$$
\begin{align}
\sigma\_{Y}^{2} & = E\[(Y-\mu\_{Y})^{2}] \\
& = E\left{ \left\[ \left( X+C \right) - \left( \mu\_{X}+C \right) \right]^{2} \right} \\
& = E\left\[ \left( X-\mu\_{X} \right)^{2} \right] = \sigma\_{X}^{2}
\end{align}
$$

## Sum Rule

$$
\begin{align}
\mathrm{Var\[X+Y]} &= E\left{ \left\[ (X+Y) - (\mu\_{X}+\mu\_{Y})\right]^{2}  \right} \\
&= \sigma\_{X}^{2}+\sigma\_{Y}^{2}+2\mathrm{Cov}(X,Y)
\end{align}
$$

# Covariance

variance between two r.v.

$$
\mathrm{Cov}(X,Y) = \mathbb{E}\[(X-\mu\_{X})(Y-\mu\_{Y})]
$$

also:

$$
\begin{align}
\mathrm{Cov}(X,Y) &=  \mathbb{E}\[XY-\mu\_{X}Y - \mu\_{Y}X + \mu\_{X}\mu\_{Y}] \\
&= \mathbb{E}\[XY] - \mu\_{X}\mu\_{y}
\end{align}
$$

# Covariance Matrix
