iterative scheme for finding the zero of a function

1. guess
2. find the root of the tangent line as a new guess
3. go to 2 until convergence

$$
\begin{align}
f'(x_{1}) & = \frac{f(x_{1})-0}{x_{1}-x_{2}} \\
x_{2}  & = x_{1} - \frac{f(x_{1})}{f'(x_{1})} \\
 & \dots \\
x^{(i+1)} & = x^{(i)} - \frac{f(x^{(i)})}{f'(x^{(i)})}
\end{align}
$$


