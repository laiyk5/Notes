# 拉格朗日乘数法

如果有一个约束条件$g(x,y) = c$，要求求出满足约束条件的$f(x,y)$的极值点，

那么把约束条件作为一个项构造一个连续的函数

$$
\mathcal{L}(x, y, \lambda) = f(x,y) - \lambda (g(x,y) - c)
$$

直观意义是$g$决定了最优的点集（惩罚为0），和在这些落在其他点的时候的惩罚力度。拉格朗日乘数用$\lambda$控制限制力度。求驻点：

$$
\begin{align}
\frac{\partial \mathcal{L}}{\partial x} = \frac{\partial f}{\partial x} - \lambda \frac{\partial g}{\partial x} \\
\frac{\partial \mathcal{L}}{\partial y}=\frac{\partial f}{\partial y} - \lambda \frac{\partial g}{\partial y}\\
\frac{\partial \mathcal{L}}{\partial \lambda} = g(x,y)-c
\end{align}
$$

让梯度为0求驻点，这样解出来的驻点既满足约束条件，且点上的$f$的梯度和约束$g$的梯度共线。