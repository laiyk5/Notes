Linear Classifiers

# Generative Classifier

1. Learn CCDs from data: $p(x|y)$
2. [[Bayesian Decision Theory|BDT]] to get decision  rule $p(y|x) \to g(x)$

Data used in step 1, decision is secondary.

- Density estimation is an ill-posed problem (difficult)
  - which density to use?

> [!quote] Vapnik's advice
> when solving a given problem, try to avoid solving a more difficult problem as an intermediate step.

Solve for decision rule directly

# Linear Classifier (binary)

- input: $X\in \mathbb{R}^{d}$
- output: $y \in { +1, -1 }$
- find a linear function: $f(x) = w^{T}x, w \in \mathbb{R}^{d}$
  - $w$ separate input space into 2 halp-spaces
  - $w$ points to into the pos-space
  - $f(x)=0$ is the dec boundary

Decision Rule

$$
g = \mathrm{sgn}(f(x)) = \begin{cases}
+1,  & f(x) > 0 \\
-1,  & f(x) < 0
\end{cases}
$$

> [!note] bias term can be included in $w$
> $$
> f(\tilde{x}) = \tilde{w}\tilde{x}= \begin{bmatrix}
> w \\
> b \\
> \end{bmatrix}
> \begin{bmatrix}
> x \\
> 1
> \end{bmatrix}
> \= w^{T}x+b
> $$

Training Set $D={ x\_{i}, y\_{i} }\_{i=1}^{n} = { X,y }$

Given a $w$:

- $y\_{i}(w^{T}x\_{i}) > 0 \implies$ correctly classified $(x\_{i}, y\_{i})$
- $y\_{i}(w^{T}x)<0 \implies$ misclassified $(x\_{i},y\_{i})$

Idea case: 0-1 loss failed because $f(x) = \begin{cases}0, & x>0 \ 1, & x<0\end{cases}$ has only 0 or undefined gradient.

$$
w\* = \argmax\_{w} \sum\_{i=1}^{n}
$$

# Least Squares Classification (Label Regression)

$$
\begin{align}
\hat{w} & = \argmin\_{w} \sum\_{i=1}^{n} (y\_{i}-w^{T}x\_{i})^{2} \\
& = (XX^{T})^{-1}Xy
\end{align}
$$

FLD is a version of LSC

# Perceptron

Rosenblatt 1962

criteria: only look at misclassified points

M = set of misclassified points = ${ i | y\_{i}w^{T}x\_{i} < 0 }$

loss function, larger loss for for misclassified points far from boundary:
$$
E(w) = \sum\_{i \in M} - y\_{i} w^{T}x\_{i}
$$

Perceptron Algorithm: $w^{\*} = \argmin\_{w}E(w)$

look at one sample at a time and minimize (gradient descent)
$$
w\_{t+1} = w\_{t} + \eta y\_{i}x\_{i}
$$
it's now called stochastic gradient descent, SGD

How to set the learning rate $\eta$

- rotate $w$ towards the misclassified point
- length of $w$ increases in each iteration, each update has less effect than prev

![[masters/SemB/CS5487-ML/Decisioning/Attachments/IMG_1495.jpg]]

Rosenblatt proved SGD converges in $\left( \frac{R}{\gamma} \right)^{2}$ iterations if the data is linearly separate
$R = \max\_{i}||X\_{i}||$

$\gamma$: for $||\hat{w}||=1$, $\forall i, y\_{i}\hat{w}x\_{i}>\gamma$
$\hat{w}$: the optimal unit weight vector that perfectly separates the two classes with the maximum possible margin.

- many possible solution, based on initialization
- does not converge if data is not linearly separable.

# Logistic Regression

(probabilistic Approach)

Binary class: $y \in { 0,1 }$

PS6-7: when the CCD are Gaussian, $p(x|y) = N(x;\mu\_{y,\Sigma\_{y}})$, the posterior is $p(y|x)$ is a sigmoid function
$$
p(y=1|x) = \frac{1}{1+e^{-f(x)}} = \sigma(f(x))
$$

where f(x) is linear

Sigmoid:

$$
\sigma(z) = \frac{1}{1+e^{-z}}
$$

with BDR, $f(x)$ was determined by CCD.
Now we directly learn $f(x)$

linear func: $f(x) = w^{T}x$
prob:

$$
\begin{align}
p(y=1|x) & = \sigma(w^{T}x) = \pi \\
& = \frac{1}{1+e^{-w^{T}x}}
\end{align}
$$

Decision Rule:

$$
\hat{y} = \begin{cases}
1, & p(y=1||x) > \frac{1}{2}, \text{or } w^{T}x > 0 \\
0, & \text{otherwise}
\end{cases}
$$

Look at # parameters

- BDR-Gauss: $O(d^{2})$
- Logistic Regression: $O(d)$, less likely to overfit.

Learning: parameter estimation

let $\pi\_{i} = \sigma(w^{T}x\_{i})$
Bernoulli likelihood: $p(y\_{i}|x\_{i},w)=\pi\_{i}^{y\_{i}}(1-\pi\_{i})^{1-y\_{i}}$
Data log-likelihood:

$$
l(w) = \sum y\_{i} \ln \pi\_{i} + (1-y\_{i})\ln (1-\pi\_{i})
$$

MLE:

$$
\begin{align}
\hat{w} & = \argmax\_{w} l(w) \\
& = \argmin\_{w} \sum\_{i=1}^{n}\underbrace{  -y\_{i}\log \pi\_{i} - (1-y\_i)\log(1-\pi\_{i}) }\_{ \text{Loss: Binary Cross Entropy} } \\
\end{align}
$$

Find zero-crossings of gradient:
Newton-Raphson Method

$$
w^{(\text{new})} = w^{(\text{old})} - \[\underbrace{ \nabla^{2} l(w) }_{ \text{Hessian} }]^{-1}(\underbrace{ \nabla l(w) }_{ \text{gradient} })
$$

$$
\begin{align} \\
w^{(\text{new})} & = (XRX^{T})^{-1} XRz \\
R & = \mathrm{diag}(\pi\_{i}(1-\pi\_{i}), \dots, \pi\_{n}(1-\pi\_{n})) & \text{weights}\\
z & = X^{T}w^{(old)} - R^{-1}(\pi-y)
\end{align}
$$

weighted lesat squares: weights are $R$, target is $z$

R: weights depend on $w\_{i}$, weight higher on unconfident predictions
z: $f^{old}w$ - error between pred $\pi\_{i}$ and $y\_{i}$
target depends on $w$

IRLS, IRWLS: iterative reweighted least squares

# Comparison of Error (loss) functions

all have the form:

$$
\hat{w} = \argmin\_{w} \underbrace{ \sum\_{i=1}^{n}L(f(x\_{i}), y\_{i}) }\_{ \text{empirical risk} }
$$

"empirical risk minimization" - reduce the training error.

let $z\_{i}=y\_{i}w^{T}x\_{i}$

Ideal 0-1 loss

$$
L = \begin{cases}
0, & z\_{i}>0 \\
1, & z\_{i}<0 &
\end{cases}
$$

LSC:
$$
L = (z\_{i}-1)^{2}
$$

penalizing too correct answers

Perceptron:

$$
L = \max(0, -Z\_{i})
$$

[[#Logistic Regression]]:

$$
L = \frac{1}{\log(z)}\log(1 + e^{-z\_{i}})
$$

some loss for correctly classified points: the effect is to push. the boundary away from the nearby points.
![[masters/SemB/CS5487-ML/Decisioning/Attachments/IMG_1498.jpg]]

Loss for LSC & LR are convex approx to 0-1 loss
