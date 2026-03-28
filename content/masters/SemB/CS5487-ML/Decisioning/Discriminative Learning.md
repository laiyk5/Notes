Linear Classifiers

# Generative Classifier

1. Learn CCDs from data: $p(x|y)$
2. [[masters/SemB/CS5487-ML/Decisioning/Bayesian Decision Theory\|BDT]] to get decision  rule $p(y|x) \to g(x)$

Data used in step 1, decision is secondary.
- Density estimation is an ill-posed problem (difficult)
	- which density to use?

> [!quote] Vapnik's advice
> when solving a given problem, try to avoid solving a more difficult problem as an intermediate step.

Solve for decision rule directly

# Linear Classifier (binary)

- input: $X\in \mathbb{R}^{d}$
- output: $y \in \{ +1, -1 \}$
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
> = w^{T}x+b
> $$


Training Set $D=\{ x_{i}, y_{i} \}_{i=1}^{n} = \{ X,y \}$

Given a $w$: 

- $y_{i}(w^{T}x_{i}) > 0 \implies$ correctly classified $(x_{i}, y_{i})$
- $y_{i}(w^{T}x)<0 \implies$ misclassified $(x_{i},y_{i})$

Idea case: 0-1 loss failed because $f(x) = \begin{cases}0, & x>0 \\ 1, & x<0\end{cases}$ has only 0 or undefined gradient.

$$
w* = \argmax_{w} \sum_{i=1}^{n}
$$

# Least Squares Classification (Label Regression)

$$
\begin{align}
\hat{w} & = \argmin_{w} \sum_{i=1}^{n} (y_{i}-w^{T}x_{i})^{2} \\
 & = (XX^{T})^{-1}Xy
\end{align}
$$

FLD is a version of LSC

# Perceptron

Rosenblatt 1962

criteria: only look at misclassified points

M = set of misclassified points = $\{ i | y_{i}w^{T}x_{i} < 0 \}$

loss function, larger loss for for misclassified points far from boundary:
$$
E(w) = \sum_{i \in M} - y_{i} w^{T}x_{i}
$$

Perceptron Algorithm: $w^{*} = \argmin_{w}E(w)$

look at one sample at a time and minimize (gradient descent)
$$
w_{t+1} = w_{t} + \eta y_{i}x_{i}
$$
it's now called stochastic gradient descent, SGD

How to set the learning rate $\eta$

- rotate $w$ towards the misclassified point
- length of $w$ increases in each iteration, each update has less effect than prev

![[masters/SemB/CS5487-ML/Decisioning/Attachments/IMG_1495.jpg]]


Rosenblatt proved SGD converges in $\left( \frac{R}{\gamma} \right)^{2}$ iterations if the data is linearly separate
$R = \max_{i}||X_{i}||$

$\gamma$: for $||\hat{w}||=1$, $\forall i, y_{i}\hat{w}x_{i}>\gamma$
$\hat{w}$: the optimal unit weight vector that perfectly separates the two classes with the maximum possible margin.

- many possible solution, based on initialization
- does not converge if data is not linearly separable.

# Logistic Regression

(probabilistic Approach)

Binary class: $y \in \{ 0,1 \}$


PS6-7: when the CCD are Gaussian, $p(x|y) = N(x;\mu_{y,\Sigma_{y}})$, the posterior is $p(y|x)$ is a sigmoid function
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

let $\pi_{i} = \sigma(w^{T}x_{i})$
Bernoulli likelihood: $p(y_{i}|x_{i},w)=\pi_{i}^{y_{i}}(1-\pi_{i})^{1-y_{i}}$
Data log-likelihood:

$$
l(w) = \sum y_{i} \ln \pi_{i} + (1-y_{i})\ln (1-\pi_{i})
$$

MLE:

$$
\begin{align}
\hat{w} & = \argmax_{w} l(w) \\
 & = \argmin_{w} \sum_{i=1}^{n}\underbrace{  -y_{i}\log \pi_{i} - (1-y_i)\log(1-\pi_{i}) }_{ \text{Loss: Binary Cross Entropy} } \\
\end{align}
$$



Find zero-crossings of gradient:
Newton-Raphson Method

$$
w^{(\text{new})} = w^{(\text{old})} - [\underbrace{ \nabla^{2} l(w) }_{ \text{Hessian} }]^{-1}(\underbrace{ \nabla l(w) }_{ \text{gradient} })
$$


$$
\begin{align} \\
w^{(\text{new})} & = (XRX^{T})^{-1} XRz \\
R & = \mathrm{diag}(\pi_{i}(1-\pi_{i}), \dots, \pi_{n}(1-\pi_{n})) & \text{weights}\\
z & = X^{T}w^{(old)} - R^{-1}(\pi-y)
\end{align}
$$

weighted lesat squares: weights are $R$, target is $z$

R: weights depend on $w_{i}$, weight higher on unconfident predictions
z: $f^{old}w$ - error between pred $\pi_{i}$ and $y_{i}$
target depends on $w$



IRLS, IRWLS: iterative reweighted least squares



# Comparison of Error (loss) functions

all have the form:

$$
\hat{w} = \argmin_{w} \underbrace{ \sum_{i=1}^{n}L(f(x_{i}), y_{i}) }_{ \text{empirical risk} }
$$

"empirical risk minimization" - reduce the training error.



let $z_{i}=y_{i}w^{T}x_{i}$

Ideal 0-1 loss

$$
L = \begin{cases}
 0, & z_{i}>0 \\
 1, & z_{i}<0 & 
\end{cases}
$$

LSC:
$$
L = (z_{i}-1)^{2}
$$

penalizing too correct answers

Perceptron:

$$
L = \max(0, -Z_{i})
$$

[[masters/SemB/CS5487-ML/Decisioning/Discriminative Learning#Logistic Regression]]: 

$$
L = \frac{1}{\log(z)}\log(1 + e^{-z_{i}})
$$

some loss for correctly classified points: the effect is to push. the boundary away from the nearby points.
![[masters/SemB/CS5487-ML/Decisioning/Attachments/IMG_1498.jpg]]

Loss for LSC & LR are convex approx to 0-1 loss


