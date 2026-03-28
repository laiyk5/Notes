$$
\DeclareMathOperator\*{\argmin}{argmin}
\DeclareMathOperator\*{\argmax}{argmax}
\argmin
\argmax
\text{commands are defined here}
$$

**Idea of MLE**: "likelihood" is the probability of the dataset appears, so the parameter that maximizes the likelihood might be the true parameter.

# The Definition of MLE

Step 1, make assumptions:

- assume the distribution is ..., and the PDF/PMF is $p(x;\theta)$

Now estimate the parameters by maximizing the likelihood.

Likelihood: the product of the possibility / possibility density of the data / dataset.

Given a sample dataset $D$, the likelihood is a function of $\theta$:
$$
L(\theta) = \prod\_{x\in D} p(x;\theta)
$$
Since log is monotone, sometimes we use log-likelihood:
$$
LL(\theta) = \log L(\theta) = \sum\_{x\in D}\log p(x;\theta)
$$

Find the $\theta$ that maximize the possibility of $D$ occurs:
$$
\hat\theta\_{ML} = \argmax\_{\theta} L(\theta)
$$

# The property of MLE

## consistency of MLE

the optimized $\hat\theta\_{n}$ is converge in probability to the true parameter $\theta\_0$
$$
\lim\_{n\to +\infty} P(|\hat\theta\_{ML} - \theta\_0| \ge \epsilon) = 0
$$

## asymptotic normality of MLE

估计误差的分布会趋近于正态分布

## asymptotic efficiency of MLE

## Invariance of MLE

The MLE of $\eta = g(\theta)$ is $\hat\eta = g(\hat\theta)$

$$
\begin{align}
\eta = g(\theta) \\

M(\eta) = \sup\_{\theta:g(\theta) = \eta} L(\theta)\\

\hat\eta\_{ML} = \argmin\_{\theta} L(g(\theta))

\end{align}
$$

Define the likelihood of $\eta$ as the supremum of $L(\theta)$ with $\eta = g(\theta)$:
$$
M(\eta) = \sup\_{{\theta : g(\theta) = \eta}} L(\theta)
$$
And the optimized $\eta$ should be the one that makes $M(\hat\eta)$ be supremum of $M(\eta)$, which is the supremum of $L(\theta)$:
$$
M(\hat\eta) = \sup\_\eta M(\eta) = \sup\_\eta \left( \sup\_{{ \theta: g(\theta) = \eta }} L(\theta) \right) = \sup\_\theta L(\theta) = L(\hat\theta)
$$

and the likelihood of $\eta = g(\hat\theta)$ is:
$$
M(g(\hat\theta)) = \sup\_{{ \theta: g(\theta) = g(\hat\theta) }} L(\theta) = L(\hat\theta)
$$
which means $M(g(\hat\theta)) = \sup\_\eta M(\eta)$, so $\hat\eta$ can be $g(\hat\theta)$
