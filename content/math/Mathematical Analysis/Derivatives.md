# Rules of Derivatives

## Constant Rule

$$
\[kf(x)]' = k f'(x)
$$

Proof:
$$
\begin{align}
\frac{kf(x+\Delta x) - kf(x)}{\Delta x} & = k \frac{f(x+ \Delta x) - f(x)}{\Delta x}
\end{align}
$$

## Sum Rule

$$
\left\[ f(x) + g(x) \right]' = f'(x) + g'(x)
$$

---

Proof

$$
\begin{align}
& \frac{\left( f(x+\Delta x) + g(x+\Delta x) \right) - \left( f(x) + g(x) \right) }{\Delta x} \\
& =  \frac{ f(x + \Delta x ) - f(x) }{\Delta x} + \frac{g(x + \Delta x) - g(x)}{\Delta x}
\end{align}
$$

## Product Rule

$$
\left\[ f(x)g(x) \right]' = f'(x)g(x) + f(x)g'(x)
$$
--

Proof

$$
\begin{align}
& \frac{f(x+\Delta x)g(x+\Delta x) - f(x)g(x)}{\Delta x} \\
& = \frac{f(x+\Delta x)g(x+\Delta x) - f(x+\Delta x)g(x) + f(x+\Delta x)g(x) - f(x)g(x)}{\Delta x} \\
& = f(x+\Delta x)\frac{g(x + \Delta x) - g(x)}{\Delta x} + g(x) \frac{f(x+\Delta x) - f(x)}{\Delta x}
\end{align}
$$

## Quotient Rule

$$
\left\[ \frac{f(x)}{g(x)} \right]' = \frac{f'(x)g(x) - f(x)g'(x)}{g^{2}(x)}
$$

---

Proof
$$
\begin{align}
\frac{\frac{f(x+\Delta x)}{g(x+\Delta x)} - \frac{f(x)}{g(x)}}{\Delta x}
& = \frac{f(x+\Delta x)g(x) - f(x)g(x+\Delta x)}{\Delta x g(x+\Delta x)g(x)} \\
& = \frac{f(x + \Delta x)g(x) - f(x)g(x) + f(x)g(x) - f(x)g(x+\Delta x)}{\Delta x g(x+\Delta x)g(x)} \\
& = \frac{g(x) \frac{f(x+\Delta x) - f(x)}{\Delta x} - f(x) \frac{g(x+\Delta x)- g(x)}{\Delta x}}{g(x+\Delta x)g(x)}
\end{align}
$$

## Chain Rule

$$
\frac{ \partial y }{ \partial x }  = \frac{ \partial y }{ \partial u } \frac{ \partial u }{ \partial x }
$$

---

Proof
$$
\begin{align}
f(x) - f(a) & = \phi(x) (x-a) \\
g(x) - g(a) & = \psi(x) (x - a) \\
\\
f(g(x)) - f(g(a)) & = \phi(g(x)) \cdot \[g(x) - g(a)] \\
& = \phi(g(x)) \cdot \psi(x)(x-a) \\
\end{align}
$$

By applying [[Limits#Composition Rule]]:

$$
\begin{align}

\lim\_{ x \to a } \frac{f(g(x)) - f(g(a))}{x-a} & = \lim\_{ x \to a }  \phi(g(x)) \cdot \psi(x) \\
& = \lim\_{ x \to a }\phi \left(  g(x) \right) \cdot \lim\_{ x \to a } \psi(x) \\
& = \lim\_{ u \to g(a) } \phi (u) \cdot \lim\_{ x \to a } \psi(x) \\
& = \lim\_{ u \to g(a) } \frac{f(u) - f(g(a))}{u-g(a)}\lim\_{ x \to a } \frac{g(x) - g(a)}{x-a} \\
& = f'(g(a)) g'(a)
\end{align}
$$

# Differential

if $y$ is determined by $x$, ($y=f(x)$) then the differential of y ($dy$) is $f'(x),dx$.
if $x$ is a free variable, then $dx$ is an independent variable, representing a change of $x$.

$$
\Delta y = A(x) \Delta x + o(\Delta x)
$$

the little o here represent an infinitesimal which is strictly higher order of $\Delta x$. [[Asymptotic Notations#Little $o$|little o]]

if $f$ is differentiable then it's derivable
$$
f'(x) := \lim\_{ \Delta x \to 0 } \frac{\Delta y}{\Delta x} = A(x)
$$
if $f$ is derivable then it's differentiable:
$$
\frac{\Delta y}{\Delta x}= f'(x) + o(1) \implies \Delta y = f'(x)\Delta x + o(\Delta x)
$$
thus, derivable is equivalent to differentiable.

# Total Derivative

# Total Differential

Total differentiable，if：

$$
\Delta z = \nabla f \cdot \Delta P + o(\rho)
$$

if all partial derivatives are continuous, then total differentiable
$$
\begin{align}
\Delta z & = f(P+\Delta P) - f(P) \\
& = f\_{x}(P)\Delta x + f\_{y}(P)\Delta y + (\epsilon\_{1} \Delta x + \epsilon\_{2} \Delta y) \\
& = f\_{x}(P)\Delta x + f\_{y}(P)\Delta y + o(\rho) \\
& = \nabla f \cdot \Delta P + o(\rho)
\end{align}
$$

# Directional Derivative

rate of change along this line/direction $u$:
$$
D\_{u}f = \lim\_{ h \to 0 } \frac{\Delta z}{h} = \lim\_{ h \to 0 } \frac{f(P+ hu)-f(P)}{h} =  \nabla f \cdot u
$$

# Gradient

gradient is a partial derivative vector

$$
\begin{bmatrix}
\frac{ \partial y }{ \partial x\_{1} } \\
\frac{ \partial y }{ \partial x\_{2} } \\
\vdots \\
\frac{ \partial y }{ \partial x\_{n} }
\end{bmatrix}
$$

# Hessian Matrix

> [!quote] Hessian Matrix
> Elements of Hessian Matrix is the second derivative of $i$-th then $j$-th input.

$$
H\_{i,j} = \frac{ \partial^{2} f }{ \partial x\_{i}x\_{j} }
$$

# Jacobian Matrix

> [!quote] Jacobian matrix
> Jacobian matrix is the partial derivative matrix for a multi-input-output function.
> The $i,j$ elementh is the the derivative of $i$-th output w.r.t $j$-th input

$$
J\_{i,j} = \frac{ \partial f\_{i} }{ \partial x\_{j} }
$$
