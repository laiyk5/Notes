- 依分布收敛：$X\_n \xrightarrow{d} X$，
- 依概率收敛：$X\_n \xrightarrow{P} a$，
- 几乎处处收敛：$X\_n \xrightarrow{a.s.} X$，

---

## Convergence in distribution

written as:

$$
X\_n \xrightarrow{d} X
$$
the distribution converges:
$$
\lim\_{n \to \infty }F\_n(x) \to  F(x)
$$

---

## Convergence in Probability

written as:

$$
X\_n \xrightarrow{P} a
$$

$X\_{n}$ is close to $x\_{0}$ with greater and greater probability.

$$
\lim\_{n\to \infty} P(|X\_n - x\_0| \ge \epsilon) = 0
$$

given a large $N$, the probability of being outlier will be very small, but still has a chance.

---

## almost sure convergence

Written as:
$$
X\_n \xrightarrow{a.s.} X
$$
The probability of the random sequence convergence is one.
$$
P(\omega \in \Omega : \lim\_{n \to \infty} X\_n(\omega) = X(\omega)) = 1
$$
It guarantees that any sample sequence would definitely converges.

收敛于分布$X$的事件概率为一

说的是随机变量序列收敛于某个确定实数的概率为1。
