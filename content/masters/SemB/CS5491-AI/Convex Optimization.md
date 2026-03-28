# Convexity

$$
\begin{align}
\min\_x f(x) \\
s.t.\ x \in \mathcal{F}
\end{align}
$$

- $\mathcal{F}$ is a convex set.
- $f$ is a convex function.

## Convex combination

Given: Point x, Point y

Convex combination of x and y: A point between two points

### Case 1: Given $x, y \in R^n$

a convex combination of them is any point of the form $z = \theta x + (1 - \theta) y, \theta \in \[0, 1]$
strict convex combination: $\theta \in (0, 1)$

> [!note] another name: Interpolation
> any point between x and y is called interpolation, any point outside is called extrapolation

## Convex set

All there convex combination of two points in the set is also in the set.

A set $F$ is convex if $\forall x, y \in \mathcal{F}, \forall \theta \in \[0, 1]$,
$$
z = \theta x + ( 1 - \theta ) y \in \mathcal{F}
$$

## Convex function

Conceptually: the value on the mid point is lower than average value

$$
\underbrace{f(\theta x + (1 - \theta) y)}_\text{value of conv-comb of the points} \le \underbrace{ \theta f(x) + (1 - \theta) f(y)}_{\text{conv comb of values of the points}}
$$

Convexities is preserved:

- Sum of convex functions is convex
- Convexity is preserved under a linear transformation $f(x) = g(Ax + b)$

second partial derivatives is positive semidefinite on the interior of $\mathcal{F}$

> [!note] SPD (Semi-Positive Definite)
> $x^TAx \ge 0\ \forall x$
> eigen-decomposition
> eigenvalues, eigenvectors: $A v = \lambda v$
> $A = V \Lambda V^{-1}$
> all eigenvalues of $H$ are non-negative
> alternatively: check $z^TH(x) z = \sum\_ig\_i^2(x,z)$

Descrete:

- Search
- Iteratively improving an assignment
  Continuous:
- gradient

Gradient Descent:

```
initialize $x \leftarrow$ x_0:
repeat
	$x \leftarrow x - \alpha \nabla _x f(x)$;
unti convergence;
```

- how to choose initial point
- how to choose and update step-size
- how to define convergence

$$
P\_\mathcal{F} = \operatorname\*{argmin}\_{x' \in \mathcal{F}} ||x-x'||\_2^2
$$

Newton-Raphson Method: if twice-differentiable

iterate until convergence:
$$
x\_{n+1} = x\_n - \frac{f(x\_n)}{f'(x\_n)}
$$

1. Model a problem as a convex optimization problem
   1. define variable, feasible set, objective function
   2. prove it its convex (convex function + convex set)
2. Build up the model
3. Call a solver
4. fmincon, cvxpy, cvxopt, cvx
