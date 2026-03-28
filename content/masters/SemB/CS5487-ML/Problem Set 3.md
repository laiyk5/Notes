# Problem 3.8 Bayesian estimation for a multinomial distribution

$$
p(x|\pi) = \pi^{x}(1-\pi)^{1-x}
$$

$$
\begin{align}
p(D|\pi) &= \prod\_{i=1}^{n} p(x\_{i}|\pi) \\
&= \prod\_{i=1}^{n} \pi^{x\_{i}}(1-\pi)^{1-x\_{i}} \\
&= \pi^{\sum\_{i=1}^{n}  x\_{i}} (1-\pi)^{\sum\_{i=1}^{n} (1-x\_{i})} \\
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
