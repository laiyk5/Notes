class mean:

$$
\mu\_{j} = \frac{1}{n\_{j}}\sum\_{x\_{i} \in C\_j} x\_{i}
$$

class scatter:

$$
S\_{j} =  \sum\_{x\_{i} \in C\_{j}} (x\_{i} - \mu\_{j})(x\_{i}-\mu\_{j})^{T}
$$

> [!note] why not inner product?

goal: the find the optimal project $w^{_}$ that maximize the between class distance and within class distance:
$$
\begin{align}
w^{_} & = \argmax\_{w} \frac{(m\_{1}- m\_{2})^{2}}{S\_{1}+S\_{2}} \\
m\_{j} & = w^{T}\mu\_{j} \\
s\_{j} & =w^{T}S\_{j}w
\end{align}
$$

within class scatter:
$$

$$

$$
\begin{align}
w^{\*} & = \argmax\_{w}\frac{(m\_{1}-m\_{2})^{2}}{S\_{1}+S\_{2}} \\
& = \argmax\_{w} \frac{(w^{T}\mu\_{1} - w^{T}\mu\_{2})^{2}}{w^{T}(S\_{1}+S\_{2})w} \\
& = \argmax\_{w} \frac{w^{T}(\mu\_{1}-\mu\_{2})(\mu\_{1}-\mu\_{2})^{T}w}{w^{T}(S\_{1}+S\_{2})w} \\
& = \argmax\_{w} \frac{w^{T}S\_{B}w}{w^{T}S\_{w}w}
\end{align}
$$
