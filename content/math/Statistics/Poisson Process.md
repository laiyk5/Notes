Models:

- Bernoulli: distribution of binary outcomes (happened/unhappened) experience, the parameter can be explained as its expectation / possibility.
- Binomial: number of times happened in $n$ i.i.d. Bernoulli experiments, parameterized by $p$, the possibility of happening in each experiment. Its formula is form by accumulate all situations of the specific times of experiment outcome is happened.
- Poisson: if the possibility is evenly distributed on a continuous space, and in that space the rate of arrival / number of happening is expected to be $\lambda$, then for each subspace, we test it and the possibility of happening on this subspace is $\frac{\lambda}{n}$, then the number of happening in this whole space can is the limit of Binomial Distribution.
- Exponential: Possibility of time of "First Happen". Rate of arrival in a time unit is $\lambda$, then the rate of arrival is $\lambda t$ in space $\[0,t]$, and possibility of nothing happened for $t$ time units is simply calculated by plug $k=0$ into the PMF of Poisson, transform,  take derivative, and boom, we get PDF of exponential distribution.
- Gamma Distribution: extension of Exponential Distribution: the Possibility of time of  "n-th event happen".

# Bernoulli Distribution

单次概率$p$

$$

f(k;p) = \begin{cases}

p & \text{if } k=1, \\

q & \text{if } k=0

\end{cases}

$$

# Binomial Distribution

每次概率$p$，$n$次出现$k$次的概率
$$
P(X=k) = \begin{pmatrix} n \ k \end{pmatrix} p^k (1-p)^{n-k}
$$

Why it's called binomial distribution?
$$
\sum\_{k=0}^{n} P(X=k) = \sum\_{k=0}^{n} \binom{n}{k} p^{k}(1-p)^{n-k} = \[(p + 1)-p]^{n} = 1
$$

# Poisson Process

当随机过程 ${N(t), t > 0}$ 被称为Poisson过程：

- 从零开始：
  - $N(0) = 0$
  - 零时刻事件发生次数为0
- 无记忆：
  - $N(t\_1+T) - N(t\_1) = N(t\_2 + T) - N(t\_2)$
  - 无论从哪里开始计时，分布都一样
- 独立性：事件的发生互不干扰
- 稀疏性：同一时刻发生两个事件的概率几乎为0
  - I think it could be written as: $\lim\_{ t \to 0 } P(N(t) > 1) = 0$

> [!tips] Notation Misuse
> $N(t)$ 可以看作一个随机变量，代表的是时间$t$内事情发生的次数。$t$ 是时长，而不是时刻，但默认时刻从零开始的时候，$t$又可以指代$\[0,t]$这个时长，此时为时刻。

Poisson Process: 随机事件在连续时间内发生的基础模型

发生率$\lambda$：单位时间发生率

- 计数视角：单位事件发生的次数分布（离散）possion分布
- 间隔视角：相邻两事件的时间间隔（连续），指数分布
- 等待视角：从零时刻到第n个事件发生所经历的总时间$S\_n$（连续）gamma分布

## Poisson Distribution

how to calculate the possibility of $k$ happening in a time interval, or formally how to calculate $P(N(1) = k)$?

define：$X=N(1)$ and we want:
$$
P(N(1) = k) = P(X=k)
$$

Approach: use binomial distribution.

### Poisson Distribution: Deduction

[[#Binomial Distribution]] describe the possibility of $k$ happening out of $n$ tests, if we divide a space (for example, the unit time interval we are interested in now) into $n$ small subspace, see if the event happen and take the limit of $n$, we got the possibility of $k$ happening in that continuous space.

as we divide the time unit into small even subspaces, as $n \to \infty$, every variable is Bernoulli distributed as defined by Poisson process:

$$
\begin{align}
P(N(1) = k), N(1) & = \lim\_{ n \to \infty }  \sum\_{i=1}^{n} N\_{i}\left( \frac{1}{n} \right) \\
\lim\_{ n \to \infty } P\left( N\_{i}\left( \frac{1}{n} \right) > 1\right) & = 0 \\
\implies \lim\_{ n \to \infty } P\left( N\_{i}\left( \frac{1}{n} \right) = 0 \right) & = 1-p \\
\lim\_{ n \to \infty } P\left( N\_{i}\left( \frac{1}{n} \right) = 1 \right) & = p \\
\end{align}
$$

and thus the event "happening $k$ times in a time unit" becomes "happening $k$ times in $n$ tests, $n \to \infty$", which makes the possibility being able to calculated by PMF of Binomial distribution.
$$
\begin{align}
P(N(1) = k) & = P\left( \lim\_{ n \to \infty }  \sum\_{i=1}^{n} N\_{i}\left( \frac{1}{n} \right) = k \right) \\
& = P\left{ \text{ $k$ out of $n$ i.i.d. tests success} \right} \implies \text{ use Binomial PMF}
\end{align}
$$

but what's $p$?

As all "test results" $N\_{i}\left( \frac{1}{n} \right)$ are i.i.d and [[#Bernoulli Distribution|Bernoulli distributed]], $N\_{i}\left( \frac{1}{n} \right) \sim B(1,p)$, so $E\left\[ N\_{i}\left( \frac{1}{n} \right) \right] = p$

$$
\begin{align}
E\left\[ N\left( \frac{1}{n} \right) \right] & = E\left\[ \sum\_{i=1}^{n}  N\_{i}\left( \frac{1}{n} \right) \right] \\
& = nE\left\[ N\_{i}\left( \frac{1}{n} \right) \right] \\
& = np
\end{align}
$$

let's said the $\lambda$ is the expectation of $N\left( 1\right)$, then $p=\frac{\lambda}{n}$.

so:

$$

\begin{align}

P(X = k) & = \lim\_{n \to \infty} \binom{n}{k} \left(\frac{\lambda}{n}\right)^k \left(1-\frac{\lambda}{n}\right)^{n-k} \\

&= \lim\_{n\to \infty} \frac{n!}{k!(n-k)!} \left(\frac{\lambda}{n}\right)^k \left(1-\frac{\lambda}{n}\right)^{n-k} \\

&= \frac{\lambda^k}{k!} \underbrace{ \lim\_{n \to \infty} \frac{n!}{n^k (n-k)!} }_{ \lim_{ n \to \infty } \frac{n}{n}\left( 1- \frac{1}{n} \right)\left( 1 - \frac{2}{n} \right) \dots = 1} \lim\_{n \to \infty} \left(1-\frac{\lambda}{n}\right)^{n} \underbrace{ \lim\_{n \to \infty} \left(1-\frac{\lambda}{n}\right)^{-k} }\_{ 1 } \\

&= \frac{\lambda^k}{k!} \lim\_{n \to \infty} \left(1-\frac{1}{n / \lambda}\right)^{n / \lambda \* \lambda}\\

&= \frac{\lambda^k e^{-\lambda}}{k!}

\end{align}

$$

### Poisson distribution: Properties

Apparently, the expectation of Poisson distribution should be $\lambda$:

$$
\begin{align}
\mathbb{E}\[X] &= \lim\_{ N \to \infty }  \sum\_{k=0}^{N} kP(X=k) = \lim\_{ k \to \infty } \sum\_{k=1}^{N} kP(X=k) \\
&= \lim\_{ N \to \infty } \sum\_{k=1}^{N} \frac{\lambda^k}{(k-1)!} e^{-\lambda} \\
&= \lambda e^{-\lambda} \lim\_{ N \to \infty } \sum\_{k=1}^{N} \frac{\lambda^{(k-1)}}{(k-1)!} \\
&= \lambda e^{-\lambda} \lim\_{ N \to \infty } \sum\_{k=0}^{N-1} \frac{\lambda^{k}}{k!} \\
&= \lambda
\end{align}
$$

The Variance of Poisson distribution is also $\lambda$:

$$
\begin{align}
\mathrm{var}\[X] &= \mathbb{E}\[X^{2}] - \mathbb{E}\[X]^{2} \\
&= \mathbb{E}\[X^{2}]-\lambda^{2} \\
&= \mathbb{E}\[X\[X-1]] + \mathbb{E}\[X] - \lambda^{2} \\
&= \lambda^{2} + \lambda - \lambda^{2} = \lambda
\end{align}
$$

and $\lambda$ is called "arrival rate".

## Exponential Distribution

What's the possibility of wait time? Or, since wait time is a continuous variable, what's the possibility of wait time is greater than some threshold $t$? Or formally: define $X$ as the wait time, what is $P(X > t)$?

if it's a poisson process, then basically it's saying that you wait $t$ and nothing happen, that event is $N(t)=0$.

$$
P(X > t) = P(N(t) = 0) = \frac{(\lambda t)^0 e^{-\lambda t}}{0!} = e^{-\lambda t}
$$
And the possibility has no memory:
$$
P(X > s + t | X > s) = P(X > t)
$$

It's straightforward to get the CDF and PDF of $X$:

CDF:
$$
F(t) = P(X \le t) = 1 - e^{-\lambda t}
$$

PDF:
$$
f(t) = \frac{d}{d t} F(t) = \lambda e^{-\lambda t}
$$

> [!tips] Pick the right tool
> These function -- PDF, CDF -- are just different aspects of how a random variable is distributed. You should pick the right tool to solve the problem you currently tackle with.

## Gamma Distribution

If a variable $X$ is describing the time for $n$ i.i.d. events to happen,

### Deduction of $\Gamma$ Distribution

- Deduction: from several general to a more specific conclusion
- Induction: from special cases to general form

The possibility of you wait for at least $t$ for the $n$ events to happen, then it's equivalent to say within time $t$, there's no more than $n$ events happen. Take the opposite event -- you wait for no more than $t$ time units, and more than $n$ events happen in $t$ -- this is the CDF of your wait time:

$$
F(t) = P(T\_n \le t) = P(N(t) \ge n) = \sum\_{k=n}^{\infty} \frac{(\lambda t)^k e^{-\lambda k}}{k!}
$$
take the derivate, you get an alternating series, all terms except the first term cancels out, so the PDF
$$
\begin{align}
f(t) &= \frac{d F(t)}{ dt} \\
&= \sum\_{k=n}^{\infty} \left\[ \frac{\lambda^k t^{k-1} e^{-\lambda k}}{(k-1)!} - \frac{\lambda^{k+1} t^k e^{-\lambda k}}{k!} \right] \\
&= \frac{\lambda^n t^{n-1} e^{-\lambda n}}{(n-1)!} \text{ only first term left} \\
&= \frac{t^{\alpha-1} e^{-n/\beta}}{\Gamma(\alpha) \beta^{\alpha}}, \beta = \frac{1}{\lambda}, \alpha = n, \Gamma(\alpha)=(\alpha-1)!
\end{align}
$$

Explanation:

- the [[Gamma Function]]: $\Gamma(x+1) = x\Gamma(x), \Gamma(1) = 1 \implies \Gamma(x)=(x-1)!$
- scale parameter: $\beta$, actually it's the reciprocal of arrival rate
- shape parameter: $\alpha$, actually it's the number of events to wait.
