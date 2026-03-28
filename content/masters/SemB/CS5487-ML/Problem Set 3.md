
# Problem 3.8 Bayesian estimation for a multinomial distribution

$$
p(x|\pi) = \pi^{x}(1-\pi)^{1-x}
$$

$$
\begin{align}
p(D|\pi) &= \prod_{i=1}^{n} p(x_{i}|\pi) \\
&= \prod_{i=1}^{n} \pi^{x_{i}}(1-\pi)^{1-x_{i}} \\
&= \pi^{\sum_{i=1}^{n}  x_{i}} (1-\pi)^{\sum_{i=1}^{n} (1-x_{i})} \\
&= \pi^{s}(1-\pi)^{1-x}
\end{align}
$$

$$
\begin{align}
p(\pi | D) &= \frac{ p(D|\pi) p(\pi)}{\int p(D|\pi)p(\pi) d\pi} \\
&= 

\end{align}
$$


![[masters/SemB/CS5487-ML/Attachments/PS-3.pdf]]