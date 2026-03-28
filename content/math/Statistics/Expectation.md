# Definition of Expectation

For discrete random variable

$$
\mathbb{E}\[X] := \sum\_{x \in X} x P(X=x)
$$

For continuous random variable

$$
\mathbb{E}\[X] := \int\_{-\infty}^{\infty} xf(x) , dx
$$

# LOTUS

LOTUS (Law of the Unconscious Statistician) Theorem:

$$
\begin{align}
&\mathbb{E}\[g(X)] = \sum\_{x} g(x) P(X=x) & \text{if descrete} &\\
&\mathbb{E}\[g(X)] = \int\_{-\infty}^{\infty} g(x) f\_{X}(x) , dx & \text{if continuous} &
\end{align}
$$

### Lemma: Transformation of probability density

It's all about sign cancelling

the probability density function is defined as:
$$
p\_{Y}(y) = \frac{d}{dy} F\_{Y}(y) = \frac{d}{dy} P(Y \le y)
$$
given $y = g(x)$, to transform $P(Y \le y)$ to probability about $X$, slice $g$.

if $g$ is monotonically decrease in $\[y\_{1}, y\_{2}]$

$$
P(y\_{1} \lt Y \le y\_{2}) = P(g^{-1}(y\_{2}) \lt X \le g^{-1}(y\_{1}) ) = P(X \le g^{-1}(y\_{1}))  - P(X \le g^{-1}(y\_{2}))
$$

if $g$ is monotonically increase in $\[y\_{1}, y\_{2}]$:

$$
P(y\_{1} \lt Y \le y\_{2})  = P(X \le g^{-1}(y\_{2})) - P(X \le g^{-1}(y\_{1}))
$$

take derivative of $x$, apply chain rule:
$$
\frac{d}{dy}  \int\_{-\infty}^{x} p\_{x}(t)  , dt = p\_{x}(x) \frac{dx}{dy}
$$

and both cases generate the same expression:

$$
\frac{d}{dx} P(y\_{1} \lt Y \le y\_{2}) = \frac{p\_{x}(x\_{2})}{\left| g'(y\_{2}) \right| } - \frac{p\_{x}(x\_{1})}{\left| g'(y\_{1}) \right| }
$$
So for piecewise monotonic $g$:

$$
p\_{Y}(y) = \frac{d}{dy} \sum\_{k} P(a\_{k} \lt Y \le b\_{k}) = p\_X(x) \left| \frac{d x}{d y} \right|
$$

### Proof of LOTUS (continuous)

this leads to LOTUS for continuous variable:

the potential negative sign of $\frac{dy}{dx}$ also cancel with the potential flipping of integral limit caused by substituting variables in definite integral：

$$
\mathbb{E}\[y] = \int\_{-\infty}^{\infty} y p\_Y(y) , dy = \int\_{-\infty}^{\infty} g(x) p\_{X}(x) \left| \frac{dx}{dy} \right|  , d \left( \left| \frac{d y}{dx} \right|  x \right) = \int\_{-\infty}^{\infty} g(x) p\_{X}(x) , dx
$$

For discrete variable it's pretty intuitive:

Since:
$$
P(Y=y) = \sum\_{x \in X: g(x) = y} P(X=x)
$$
So:
$$
\mathbb{E}\[Y] = \sum\_{y \in Y} y P(Y=y) = \sum\_{x \in X} g(x)P(X=x)
$$

# Properties of Expectation

## Linearity

Given by [[#LOTUS]] and linearity of [[Riemann Integral]]

applying LOTUS:

$$
\mathbb{E}\[aX] = \int\_{X} axf(x) , dx = a \int\_{X} xf(x) , dx = a\mathbb{E}\[X]
$$
$$
\mathbb{E}\[aX] = \sum\_{x \in X} axf(x),dx = a\sum\_{x\in X} xf(x) dx = a\mathbb{E}\[X]
$$
$$
\mathbb{E}\[X+b] = \int\_{X} (x+b) f(x) , dx = \int\_{X}xf(x) dx + b\int\_{X}f(x) dx = \mathbb{E}\[x] + b
$$
$$
\mathbb{E}\[X+b] = \sum\_{x \in X} (x+b) f(x) = \sum\_{x\in X}xf(x) + b\sum\_{x \in X} f(x) = \mathbb{E}\[X] + b
$$

In conclusion:
$$
\mathbb{E}\[aX+b] = a\mathbb{E}\[X]+b
$$

## Sum Rule

Distributivity w.r.t addition

Expectation is also distributable w.r.t addition:
$$
\begin{align}
\mathbb{E}\[X+Y] &= \int\_{Y} \int\_{X} (x+y) f(x,y) dx dy  \\
&= \int\_{Y} \left(\int\_{X}x(fx,y)dx + y\int\_{X} f(x,y) dx \right) dy \\
&= \int\_{Y} \int\_{X} xf(x,y) dx dy + \int\_{Y} y f\_{Y}(y) dy \\
&= \int\_{X} \left( x\int\_{Y} (fx,y)dy\right) dx + \mathbb{E}\[Y] \\
&= \mathbb{E}\[X] + \mathbb{E}\[Y]
\end{align}
$$

## Product Rule

> [!warning] Independency required

Distributivity w.r.t. multiplication while independent

Given $f(x,y) = f\_{X}(x)f\_{Y}(y)$, Expectation is distributable w.r.t multiplication:

$$
\begin{align}
\mathbb{E}\[XY] &= \int\_{X} \int\_{Y} xy f(x,y) ,dx,dy \\
&= \int\_{X}x f\_{X}(x)\int\_{Y}yf\_{Y}(y) ,dy,dx \\
&= \mathbb{E}\[Y]\int\_{X} x  f\_{X}(x) dy \\
&= \mathbb{E}\[X] \mathbb{E}\[Y]

\end{align}
$$
