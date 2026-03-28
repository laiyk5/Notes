# Bernoulli Distribution

单次概率$p$

$$

f(k;p) = \begin{cases}

p & \text{if } k=1, \\

q & \text{if } k=0

\end{cases}

$$

# Binomial Distribution

每次概率p，n次出现x次的概率
$$
P(X=x) = \begin{pmatrix} n \ x \end{pmatrix} p^x (1-p)^{n-x}
$$

# Poisson Process

当随机过程 ${N(t), t > 0}$ 被称为Poisson过程：

- 从零开始：$N(0) = 0$
- 无记忆：$N(t\_1+T) - N(t\_1) = N(t\_2 + T) - N(t\_2)$
- 独立性：事件的发生互不干扰
- 稀疏性：发生两个事件的概率几乎为0

Poisson Process: 随机事件在连续时间内发生的基础模型

发生率$\lambda$：单位时间发生率

- 计数视角：单位事件发生的次数分布（离散）possion分布
- 间隔视角：相邻两事件的时间间隔（连续），指数分布
- 等待视角：从零时刻到第n个事件发生所经历的总时间$S\_n$（连续）gamma分布

## Poisson Distribution

事件在任何时间发生的可能性相同，衡量一定时间发生的次数，使用到达率$\lambda$作为参数，将该段时间分为$n$份，每份发生的概率为$p = \frac{\lambda}{n}$，使用二项分布，并让$n \to \infty$

$$

\begin{align}

P(X = k) & = \lim\_{n \to \infty} \binom{n}{k} \left(\frac{\lambda}{n}\right)^k \left(1-\frac{\lambda}{n}\right)^{n-k} \\

&= \lim\_{n\to \infty} \frac{n!}{k!(n-k)!} \left(\frac{\lambda}{n}\right)^k \left(1-\frac{\lambda}{n}\right)^{n-k} \\

&= \frac{\lambda^k}{k!} \lim\_{n \to \infty} \frac{n!}{n^k (n-k)!} \lim\_{n \to \infty} \left(1-\frac{\lambda}{n}\right)^{n} \lim\_{n \to \infty} \left(1-\frac{\lambda}{n}\right)^{-k} \\

&= \frac{\lambda^k}{k!} \lim\_{n \to \infty} \left(1-\frac{1}{n / \lambda}\right)^{n / \lambda \* \lambda}\\

&= \frac{\lambda^k e^{-\lambda}}{k!}

\end{align}

$$

The expectation of Poisson distribution is:

$$
\begin{align}
\mathbb{E}\[X] &= \lim\_{ N \to \infty }  \sum\_{k=0}^{N} kP(X=k) = \lim\_{ k \to \infty } \sum\_{k=1}^{N} kP(X=k) \\
&= \lim\_{ N \to \infty } \sum\_{k=1}^{N} \frac{\lambda^k}{(k-1)!} e^{-\lambda} \\
&= \lambda e^{-\lambda} \lim\_{ N \to \infty } \sum\_{k=1}^{N} \frac{\lambda^{(k-1)}}{(k-1)!} \\
&= \lambda e^{-\lambda} \lim\_{ N \to \infty } \sum\_{k=0}^{N-1} \frac{\lambda^{k}}{k!} \\
&= \lambda
\end{align}
$$

The Variance of Poisson distribution is:

$$
\begin{align}
\mathrm{var}\[X] &= \mathbb{E}\[X^{2}] - \mathbb{E}\[X]^{2} \\
&= \mathbb{E}\[X^{2}]-\lambda^{2} \\
&= \mathbb{E}\[X\[X-1]] + \mathbb{E}\[X] - \lambda^{2} \\
&= \lambda^{2} + \lambda - \lambda^{2} = \lambda
\end{align}
$$

## Exponential Distribution

到时间$t$首次发生的概率/等待时间$t$发生的概率/时间$t$内发生次数为0的概率，单位时间到达率为$\lambda$

$$
P(X > s + t | X > s) = P(X > t)
$$

等待时间$X > t$，即在时间段$\[0, t]$内，事件发生的次数为0
$$
P(X > t) = P(N(t) = 0) = \frac{(\lambda t)^0 e^{-\lambda t}}{0!} = e^{-\lambda t}
$$
CDF就为：
$$
F(t) = P(X \le t) = 1 - e^{-\lambda t}
$$

PDF 就为:

$$
f(t) = \frac{d}{d t} F(t) = \lambda e^{-\lambda t}
$$

## Gamma Distribution

### Gamma Function: Factorial on Real Number

欧拉构造的能够让阶乘在实数上连续的函数

$$
\Gamma(x+1) = x \Gamma(x)
$$

$$
\begin{align}
\int (-\ln x)^n dx &= x(-\ln x)^n - \int x d(-\ln x)^n \\
&= x(-\ln x)^n + n \int (-\ln x)^{n-1} dx
\end{align}
$$
令$t=-\ln x$
$$
\Gamma(n) = \int\_0^{\infty} t^{n-1}e^{-t} dt
$$
令$n=-1/2$，再令$t=x^2$
$$
\Gamma(1/2) = \int\_0^{\infty} t^{-1/2}e^{-t} dt = \int\_0^{\infty} x^{-1} e^{-x^2} d x^2 = 2 \int\_0^{\infty} e^{-x^2} dx
$$
两次事件发生的时间间隔：指数分布

### Deduction of $\Gamma$ Distribution

- Deduction: from several general to a more specific conclusion
- Induction: from special cases to general form

等待n个事件发生所需要的时间

$$
F(t) = P(T\_n \le t) = P(N(t) \ge n) = \sum\_{k=n}^{\infty} \frac{(\lambda t)^k e^{-\lambda k}}{k!}
$$

$$
\begin{align}
f(t) &= \frac{d F(t)}{ dt} \\
&= \sum\_{k=n}^{\infty} \left\[ \frac{\lambda^k t^{k-1} e^{-\lambda k}}{(k-1)!} - \frac{\lambda^{k+1} t^k e^{-\lambda k}}{k!} \right] \\
&= \frac{\lambda^n t^{n-1} e^{-\lambda n}}{(n-1)!} \\
&= \frac{t^{\alpha-1} e^{-n/\beta}}{\Gamma(\alpha) \beta^{\alpha}}
\end{align}
$$

高斯积分
$$
\begin{align}
\int\_{-\infty}^{+\infty} e^{-x^2} dx  \int\_{-\infty}^{+\infty} e^{-y^2} dy
&= \int\_{-\infty}^{+\infty}\int\_{-\infty}^{+\infty} e^{-(x^2 + y^2)}, dx, dy \\
&= \int\_{0}^{2\pi} \int\_{0}^{+\infty} e^{-r^2} r,dr,d\theta \\
&= \int\_{0}^{2\pi} (-\frac{1}{2}) \int\_{0}^{+\infty} e^{-r^2} d (-r^2) d\theta \\
&= \int\_{0}^{2\pi} (-\frac{1}{2}) (e^{-r^2} |_{0}^{+\infty}) d\theta \\
&= \pi \\
\Longrightarrow \\
\int_{-\infty}^{+\infty} e^{-x^2} dx = \sqrt{\pi}
\end{align}
$$
