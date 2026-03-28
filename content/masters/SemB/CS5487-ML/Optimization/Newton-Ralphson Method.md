iterative scheme for finding the zero of a function

1. guess
2. find the root of the tangent line as a new guess
3. go to 2 until convergence

$$
\begin{align}
f'(x\_{1}) & = \frac{f(x\_{1})-0}{x\_{1}-x\_{2}} \\
x\_{2}  & = x\_{1} - \frac{f(x\_{1})}{f'(x\_{1})} \\
& \dots \\
x^{(i+1)} & = x^{(i)} - \frac{f(x^{(i)})}{f'(x^{(i)})}
\end{align}
$$
