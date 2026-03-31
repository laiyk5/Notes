Integration of Gaussian Function $e^{-x^{2}}$, a.k.a. Euler-Poisson integral

it's a constant $\sqrt{ \pi }$, you can get this by Integration by substitution

$$
\begin{align}
\int\_{-\infty}^{+\infty} e^{-x^2} dx  \int\_{-\infty}^{+\infty} e^{-y^2} dy
&= \int\_{-\infty}^{+\infty}\int\_{-\infty}^{+\infty} e^{-(x^2 + y^2)}, dx, dy \\
&= \int\_{0}^{2\pi} \int\_{0}^{+\infty} e^{-r^2} r,dr,d\theta \\
&= \int\_{0}^{2\pi} (-\frac{1}{2}) \int\_{0}^{+\infty} e^{-r^2} d (-r^2) d\theta \\
&= \int\_{0}^{2\pi} (-\frac{1}{2}) (e^{-r^2} |_{0}^{+\infty}) d\theta \\
&= \pi \\
\Longrightarrow \int_{-\infty}^{+\infty} e^{-x^2} dx & = \sqrt{\pi}
\end{align}
$$
