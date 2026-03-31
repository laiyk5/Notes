# Gamma Function

### Gamma function is an integral

$$
\Gamma(x+1) = x \Gamma(x)
$$
Euler found that the integral $\Gamma(n+1) = \int\_{0}^{1} (-\ln x)^{n},dx$ has the property $\Gamma(n+1) = n\Gamma(n)$ when he takes the integral by parts:

$$
\begin{align}
\int (-\ln x)^n dx &= x(-\ln x)^n - \int x d(-\ln x)^n \\
&= x(-\ln x)^n + n \int (-\ln x)^{n-1} dx \\
\implies \int\_{0}^{1}(-\ln x)^{n},dx  & = n \int\_{0}^{1}(-\ln x)^{n-1},dx
\end{align}
$$

let $u=-\ln x$, and define
$$
\begin{align}
\Gamma(n+1) & = \int\_{\infty}^{0} u^{n} ,d(e^{-u}) \\
& = \int\_{0}^{\infty} u^{n} e^{-u} , du
\end{align}
\int\_0^{\infty} u^{n-1}e^{-u} du
$$

redefine $x$ as  $n-1$, and we have:

$$
\Gamma(x) = \int\_{0}^{\infty} u^{x-1} e^{-u} , du
$$

> [!tips]
> $n$ here is a real number. I use the real number definition of power function here.

## Properties

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

$\Gamma(1) = 1$
$$
\Gamma(1) = \int\_{0}^{\infty} e^{-u} , du \stackrel{s(u)=-u}= - \int\_{0}^{-\infty} e^s , ds = - \left\[ e^{s} \right]\_{0}^{-\infty} = 1
$$

$\Gamma\left( \frac{1}{2} \right) = \sqrt{ \pi }$

let $u(t)=t^{2}$, and you would find that it's [[Gaussian Integral]]
$$
\begin{align}
\Gamma(1/2) & = \int\_0^{\infty} u^{-1/2}e^{-u} du \\
& = \int\_0^{\infty} t^{-1} e^{-t^2} d t^2 \\
& = 2 \int\_0^{\infty} e^{-x^2} dx \\
& = \int\_{-\infty}^{\infty} e^{-x^{2}} , dx = \sqrt{ \pi }
\end{align}
$$
