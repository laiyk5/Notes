random variable: map random event to real number.

given any random event, measure the possibility.

we have many methods to represent the distribution:

- Cumulative Density Function: $F(x) = P(X < x), P([a,b]) = F(b) - F(a)$
- Possibility Density Function:  $f(x), P([a,b]) = \int_a^b f(x) dx$
- Possibility Mass Function: $P(x=k)$


# Probability Density Function

$$
f(x) = P'(X\leq x)
$$

# Cumulative Distribution Function

$$
P(X\leq x)
$$

according to [[math/Mathematical Analysis/Continuous Functions#Fundamental Theorem of Calculus]], we can briefly define CDF as

$$
P(X\leq x) = \int_{-\infty}^{x} f(t) \, dt
$$
Thus:
$$
\int_{-\infty}^{\infty} f(x) \, dx = P(X\leq +\infty) = 1
$$

# Transformation

$Y=X+C$

$$
\begin{align}
 & P(Y<y) = P(X < y-C) = \int_{-\infty}^{y-C} f(t) \, dt = \int_{-\infty}^{y} f(s-C) \,ds \\
\implies & f_{Y}(y) = P'(Y<y) = f(y-C)
\end{align}
$$


$Y = CX, C>0$

$$
\begin{align}
 & P(Y<y) = P\left( X< \frac{y}{C} \right) = \int_{-\infty}^{y/C} f(t)\,dt= \int_{-\infty}^{y}f\left( \frac{s}{C} \right) \,d\left( \frac{s}{C} \right) = \frac{1}{C} \int_{-\infty}^{y}f\left( \frac{s}{C} \right) \,ds \\
\implies & f_{Y}(y) = P'(Y < y) = \frac{1}{C}f\left( \frac{y}{C} \right)
\end{align}
$$

