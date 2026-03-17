# Linearity

sums of integral is integrals of sums
$$
\begin{align}
U(x)+V(x)&=\int u + v \,dx \\
U(x) &= \int u \,dx \\
V(x) &= \int v \, dx \\
\implies \int u+v\,dx &= \int u\,dx+\int v\,dx
\end{align}
$$

Apply fundamental theory of calculus:

$$
\begin{align}
\left[U(b)+V(b) \right] - \left[  U(a)+V(b) \right] &= [U(b)-U(a)] + [V(b)-V(a)] \\

\int_{a}^{b} u+v \,dx&=\int_{a}^{b} u \,dx+\int_{a}^{b}v\,dx
\end{align}

$$


same as $aU(x)$

$$
\begin{align}
\int au \,dx & = aU(x)\\
\int u \,dx &= U(x) \\
\implies \int au\,dx&= a\int u\,dx
\end{align}

$$

applying fundamental theorem:

$$
\begin{align}
aU(x_{2})-aU(x_{1}) &= a\left( U(x_{2})-U(x_{1}) \right) \\
\int_{x_{1}}^{x_{2}}au\,dx&=a\int_{x_{1}}^{x_{2}} u\,dx
\end{align}

$$

> [!warning] $u$ always $=u$
> $$u=u(x)=u(v) = u(v(x)) = \dots$$
> $u=u$, no matter it’s written as $u(x)$, $u(v)$, or $u(v(x))$

> [!tip] abbreviation of integrals
> $$
> \begin{align}
> \int y \,dx & = \int y(x) \,dx \\
> \int u \,dv & = \int u(v) \,dv \\
> \dots
> \end{align}
> $$
# substituting variable

Composition of functions

differentiate w.r.t. $v$ or $x$: 
$$
\begin{align}
U(v) &= \int u(v) \,dv \\
U(v(x)) &= \int u(v)v’(x) \,dx \\
\int u(v) \,dv &= \int u(v) v’(x)\,dx
\end{align}
$$

or simply:
$$
\int uv'\,dx = \int u\,dv
$$
By applying Fundamental Theorem of Calculus:
$$
\begin{align}
U(v_{2})-U(v_{1})& =\int_{v_{1}}^{v_{2}} u \, dv \\
u(v(x_{2}))-U(v(x_{1})) &= \int_{x_{1}}^{x_{2}} uv’ \,dx \\
\int_{x_{1}}^{x_{2}} uv’ \,dx &= \int_{v_{1}}^{v_{2}} u \,dv
\end{align}
$$

# integration by parts

multiplying

$$
\begin{align}
u(x)v(x)& = \int u’(x)v(x) + u(x) v’(x) \, dx \\
&= \int v(u)\,du+\int u(v)\,dv \\
\int u(v) \,dv &= u(x)v(x) -\int v(u) \,dv
\end{align}
$$
Or simply:
$$
uv = \int u \, dv+ \int v \, du 
$$

by using Fundamental Theorem of Calculus:

$$
uv|_{a}^{b} = \int_{a}^{b}u'v+  uv' \, dx = \int_{v(a)}^{v(b)}u\,dv+ \int_{u(a)}^{u(b)}v\,du
$$

$$
\int_{a}^{b} u v' \,dx = (u \cdot v)|_{a}^{b} - \int_{a}^{b}u’x\,dx
$$

for example:
$$
\int_{a}^{b}u\,dx=(ux)_{a}^{b}-\int_{a}^{b}u’x\,dx
$$