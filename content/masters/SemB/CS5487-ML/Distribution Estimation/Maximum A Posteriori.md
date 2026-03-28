Prior: the initialized parameter for the assumed distribution of parameter

$$
\begin{align}
p(\theta | D) &= \frac{p(D | \theta) p(\theta)}{p(D)} \\
&= \frac{\prod p(x  | \theta) p(\theta)}{\int p(D|\theta) p(\theta) d\theta} \\
\end{align}
$$

Given a dataset, adjust the distribution of parameter. Find the parameter that maximizes the probability of the parameter. It can be written as:

$$
\begin{align}
\hat \theta\_{MAP} (x) =& \operatorname\*{argmax}_\theta p(\theta | x) \\
\=& \operatorname\*{argmax}_\theta \frac{f(x | \theta) g(\theta)}{\int f(x | \theta') g(\theta') d\theta'} \\
\=& \argmax\_\theta f(x|\theta)g(\theta)
\end{align}
$$
