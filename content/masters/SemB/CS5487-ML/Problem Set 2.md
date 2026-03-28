# Problem 2.1 The Poisson distribution and flying bombs

[[Poisson Process#Poisson Distribution]]

Poisson Distribution: the distribution of random variable that measure how many events happen given a period of time with a parameter $\lambda$ called arrival rate.
$$
p(x=k| \lambda) = \frac{1}{k!} e^{-\lambda}\lambda^{k}
$$

## maximum-likelihood estimator of $\lambda$

Likelihood function of $\lambda$ given samples $\left{  k\_{1}, \dots, k\_{N} \right}$
$$
\begin{align}
\mathcal{L}(\lambda) =& \prod\_{i=1}^{N} \frac{1}{k\_{i}!}e^{-\lambda}\lambda^{k\_{i}} \ \\
\=& \left( \prod\_{i=1}^{N} \frac{1}{k\_{i}!}  \right) \exp\left( -N \lambda \right) \lambda^{\sum\_{i=1}^{N} k\_{i}} \\
\ln\mathcal{L}(\lambda)=& -n\lambda  + \left( \sum\_{i=1}^{N} k\_{i}\right)  \ln \lambda - \ln \left( \prod\_{i=1}^{N} \frac{1}{k!} \right)  \\
\end{align}
$$

MLE of $\lambda$:
$$
\begin{align}
\hat{\lambda}_{ML} &= \argmax_{\lambda} \mathcal{L}(\lambda) \\
&= \argmax\_{\lambda} \ln\mathcal{L}(\lambda) \\
&= \argmax\_{\lambda} -n\lambda + \left( \sum\_{i=1}^{N} k\_{i}  \right) \ln \lambda \\
\end{align}
$$

find the stationary point:

$$
-n + \frac{\sum\_{i=1}^{N} k\_{i}}{\hat\lambda\_{ML}} = 0
$$

the second derivative of this function is

so the stationary point is: $\hat\lambda\_{ML} = \frac{1}{n} \sum\_{i=1}^{N}k\_{i}$, which is the sample mean.

## $\hat\lambda\_{ML}$ is unbiased

$$
\begin{align}
\mathbb{E}\[\hat{\lambda}_{{ML}}] &= \mathbb{E}\left\[ \frac{1}{n} \sum_{i=1}^{n} k\_{i} \right] \\
&= \frac{1}{n} \sum\_{i=1}^{n} \mathbb{E}\[k\_{i}] \\
&= \mathbb{E}\[k\_{i}] = \lambda
\end{align}
$$

## estimation of $\lambda$

Clark's data:

| $k$      | 0   | 1   | 2   | 3   | 4   | 5   |
| -------- | --- | --- | --- | --- | --- | --- |
| $P(X=k)$ | 229 | 211 | 93  | 35  | 7   | 1   |
$n=576$, the sample mean is:

$$
\lambda = \frac{1}{n}\sum\_{i=1}^{n} k\_{i} = \frac{1}{576} \left( 1 \times 211 + 2 \times 93 + 3 \times 35 + 4 \times 7 + 5 \times 1 \right) = \frac{535}{576} \approx 0.9288

$$

## predict with estimated $\lambda$

```python
from scipy.stats import poisson

n = 576
mu = 535/n

v_f = []
v_p = []
for i in range(0, 6):
	p = poisson.pmf(i, mu)
	v_p.append(p)
	f = p * n
	v_f.append(f)

print("Probabilities: ")

for i, p in enumerate(v_p):
	print(f"P(X={i}) = {p:.3}")

print("Expected Counts: ")
for i, f in enumerate(v_f):
	print(f"ec(X={i}) = {f:.3}")

```

the outputs are:

```txt
Probabilities:
P(X=0) = 0.395
P(X=1) = 0.367
P(X=2) = 0.17
P(X=3) = 0.0528
P(X=4) = 0.0122
P(X=5) = 0.00228

Expected Counts:
ec(X=0) = 2.28e+02
ec(X=1) = 2.11e+02
ec(X=2) = 98.1
ec(X=3) = 30.4
ec(X=4) = 7.06
ec(X=5) = 1.31
```

which remarkably close to the actual data, so my conclusion is that the assumption has great chance to be true.

# Attachments

## Problem Set 2

![[masters/SemB/CS5487-ML/Attachments/PS-2.pdf]]
