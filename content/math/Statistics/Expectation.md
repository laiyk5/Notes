# Definition of Expectation

For discrete random variable 

$$
\mathbb{E}[X] := \sum_{x \in X} x P(X=x)
$$

For continuous random variable

$$
\mathbb{E}[X] := \int_{-\infty}^{\infty} xf(x) \, dx 
$$


# LOTUS

LOTUS (Law of the Unconscious Statistician) Theorem:

$$
\begin{align}
&\mathbb{E}[g(X)] = \sum_{x} g(x) P(X=x) & \text{if descrete} &\\
&\mathbb{E}[g(X)] = \int_{-\infty}^{\infty} g(x) f_{X}(x) \, dx & \text{if continuous} &
\end{align}
$$

### Lemma: Transformation of probability density

It's all about sign cancelling

the probability density function is defined as:
$$
p_{Y}(y) = \frac{d}{dy} F_{Y}(y) = \frac{d}{dy} P(Y \le y)
$$
given $y = g(x)$, to transform $P(Y \le y)$ to probability about $X$, slice $g$.

if $g$ is monotonically decrease in $[y_{1}, y_{2}]$

$$
P(y_{1} \lt Y \le y_{2}) = P(g^{-1}(y_{2}) \lt X \le g^{-1}(y_{1}) ) = P(X \le g^{-1}(y_{1}))  - P(X \le g^{-1}(y_{2}))
$$

if $g$ is monotonically increase in $[y_{1}, y_{2}]$:

$$
P(y_{1} \lt Y \le y_{2})  = P(X \le g^{-1}(y_{2})) - P(X \le g^{-1}(y_{1}))
$$

take derivative of $x$, apply chain rule:
$$
\frac{d}{dy}  \int_{-\infty}^{x} p_{x}(t)  \, dt = p_{x}(x) \frac{dx}{dy}
$$

and both cases generate the same expression:

$$
\frac{d}{dx} P(y_{1} \lt Y \le y_{2}) = \frac{p_{x}(x_{2})}{\left| g'(y_{2}) \right| } - \frac{p_{x}(x_{1})}{\left| g'(y_{1}) \right| }
$$
So for piecewise monotonic $g$: 

$$
p_{Y}(y) = \frac{d}{dy} \sum_{k} P(a_{k} \lt Y \le b_{k}) = p_X(x) \left| \frac{d x}{d y} \right|
$$

### Proof of LOTUS (continuous)

this leads to LOTUS for continuous variable:

the potential negative sign of $\frac{dy}{dx}$ also cancel with the potential flipping of integral limit caused by substituting variables in definite integral：

$$
\mathbb{E}[y] = \int_{-\infty}^{\infty} y p_Y(y) \, dy = \int_{-\infty}^{\infty} g(x) p_{X}(x) \left| \frac{dx}{dy} \right|  \, d \left( \left| \frac{d y}{dx} \right|  x \right) = \int_{-\infty}^{\infty} g(x) p_{X}(x) \, dx 
$$

For discrete variable it's pretty intuitive:

Since:
$$
P(Y=y) = \sum_{x \in X: g(x) = y} P(X=x)
$$
So:
$$
\mathbb{E}[Y] = \sum_{y \in Y} y P(Y=y) = \sum_{x \in X} g(x)P(X=x)
$$


# Properties of Expectation

## Linearity

Given by [[math/Statistics/Expectation#LOTUS]] and linearity of [[math/Mathematical Analysis/integrals/Riemann Integral]]

applying LOTUS:

$$
\mathbb{E}[aX] = \int_{X} axf(x) \, dx = a \int_{X} xf(x) \, dx = a\mathbb{E}[X]
$$
$$
\mathbb{E}[aX] = \sum_{x \in X} axf(x)\,dx = a\sum_{x\in X} xf(x) dx = a\mathbb{E}[X]
$$
$$
\mathbb{E}[X+b] = \int_{X} (x+b) f(x) \, dx = \int_{X}xf(x) dx + b\int_{X}f(x) dx = \mathbb{E}[x] + b
$$
$$
\mathbb{E}[X+b] = \sum_{x \in X} (x+b) f(x) = \sum_{x\in X}xf(x) + b\sum_{x \in X} f(x) = \mathbb{E}[X] + b 
$$

In conclusion:
$$
\mathbb{E}[aX+b] = a\mathbb{E}[X]+b
$$

## Sum Rule

Distributivity w.r.t addition

Expectation is also distributable w.r.t addition:
$$
\begin{align}
\mathbb{E}[X+Y] &= \int_{Y} \int_{X} (x+y) f(x,y) dx dy  \\
&= \int_{Y} \left(\int_{X}x(fx,y)dx + y\int_{X} f(x,y) dx \right) dy \\
&= \int_{Y} \int_{X} xf(x,y) dx dy + \int_{Y} y f_{Y}(y) dy \\
&= \int_{X} \left( x\int_{Y} (fx,y)dy\right) dx + \mathbb{E}[Y] \\
&= \mathbb{E}[X] + \mathbb{E}[Y]
\end{align}
$$


## Product Rule

> [!warning] Independency required

Distributivity w.r.t. multiplication while independent
 
Given $f(x,y) = f_{X}(x)f_{Y}(y)$, Expectation is distributable w.r.t multiplication:

$$
\begin{align}
\mathbb{E}[XY] &= \int_{X} \int_{Y} xy f(x,y) \,dx\,dy \\
&= \int_{X}x f_{X}(x)\int_{Y}yf_{Y}(y) \,dy\,dx \\
&= \mathbb{E}[Y]\int_{X} x  f_{X}(x) dy \\
&= \mathbb{E}[X] \mathbb{E}[Y]

\end{align}
$$
