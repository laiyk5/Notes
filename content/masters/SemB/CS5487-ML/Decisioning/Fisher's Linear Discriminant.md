
class mean: 

$$
\mu_{j} = \frac{1}{n_{j}}\sum_{x_{i} \in C_j} x_{i}
$$

class scatter:

$$
S_{j} =  \sum_{x_{i} \in C_{j}} (x_{i} - \mu_{j})(x_{i}-\mu_{j})^{T}
$$

> [!note] why not inner product?
> 

goal: the find the optimal project $w^{*}$ that maximize the between class distance and within class distance:
$$
\begin{align}
w^{*} & = \argmax_{w} \frac{(m_{1}- m_{2})^{2}}{S_{1}+S_{2}} \\
m_{j} & = w^{T}\mu_{j} \\
s_{j} & =w^{T}S_{j}w
\end{align}
$$

within class scatter:
$$

$$

$$
\begin{align}
w^{*} & = \argmax_{w}\frac{(m_{1}-m_{2})^{2}}{S_{1}+S_{2}} \\
 & = \argmax_{w} \frac{(w^{T}\mu_{1} - w^{T}\mu_{2})^{2}}{w^{T}(S_{1}+S_{2})w} \\
 & = \argmax_{w} \frac{w^{T}(\mu_{1}-\mu_{2})(\mu_{1}-\mu_{2})^{T}w}{w^{T}(S_{1}+S_{2})w} \\
 & = \argmax_{w} \frac{w^{T}S_{B}w}{w^{T}S_{w}w}
\end{align}
$$
