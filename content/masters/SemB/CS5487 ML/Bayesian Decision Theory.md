
## Problem

optimal decisions in problems with uncertainty

## Framework

- states:
	- prior: $P(Y)$ = probability of a state
- observer
	- that measures features from r.v. $X$
	- class conditional distribution -- conditional on state (class)
		- one CCD for each states $P(X|Y)$
- Decision function: use observation to make a decision about the state
	- $g(x): X \to Y$
- Loss function - penalizes for deciding the wrong $Y$ (the state)
	- $L(g(X), Y) \geq 0$
	- 0-1 Loss: $\begin{cases} 0, & g(X) = Y \\ 1,  & g(X) \neq Y\end{cases}$

## Bayesian Decision Rule

Risk - expected value of the loss function

$$
\begin{align}
E_{XY}[L(g(X),Y)] & = \sum_{y}\int_{x} p(x,y)L(g(x),y) \, dx \\
 & = \int_{x} \sum_{y} p(x)p(y|x) L(g(x),y)\, dx \\
 & = \int_{x}p(x) \sum_{y}p(y|x) L(g(x),y) \, dx \\
 & = E_{X}[R(X)]
\end{align}
$$

Since $p(x) \geq 0$, $L(g(x),y) \geq 0$, then minimizing the risk can be achieved by minimizing the conditional risk for each $x$.

For a particular $X$, choose a class that minimize the risk:

$$
\begin{align}
g^*(x)  & = g^* = \arg\min_{j \in Y} R(x) \\
 & = \arg\min_{{j\in Y}} \sum_{y} p(y|x) L(j, y) \\
 & = \arg\min_{j\in Y} E_{Y|X} [L(j,y)]

\end{align}
$$
This is the Bayesian Deciison Rule.

## Classification and 0-1 loss

settings:

$$
\begin{align}
 & Y \in \left\{ 1, \dots, C \right\} \\
 & L(g(x), y) = \begin{cases}
 0, & g(x) = y \\
 1, & g(x) \neq y
 \end{cases}
\end{align}
$$

conditional risk:

$$
\begin{align}
R(X) = E_{Y|X}[L(g(X), Y)] & = P[g(X) \neq Y | X] \\
 & = 1 - P[g(X) = Y | X] \\
 & = 
\end{align}
$$
BDR:

$$
\begin{align}
y^* = \arg\min_{j \in Y} R(X) & = \arg\min_{j\in Y} 1 - P[g(X) = Y | X] \\
 & = \arg\max_{j\in Y}P[g(X) = Y | X]  & \text{same as MAP rule: selecting the largest posteriori}
\end{align}
$$

Equivalently:

$$
y^* = \arg\max_{j\in Y} P(X | Y=j) P(Y=j)
$$

Example - 2 class classification

given $x$: pick $0$ if $p(x|0)p(0) > p(x|1)p(1)$, evquivently:
$$
\underbrace{\frac{p(x|0)}{p(x|1)}}_{\text{LRT}} > \underbrace{\frac{p(1)}{p(0)}}_{\text{threshold}}= T
$$
Summary:

for 0-1 loss function

- BDR is the MAP rule (tells threshold for Likelihood Ratio Test)
- Risk = prob of error
- BDR minimizes prob of error (no other decision rule is better)
- caveats: assuming our models are corect! (the CCD and the prior)

This is called a generative model

1. Use data to learn the CCDs (modeling how features are generated)
2. use the CCD in decision rule

### Example: Noisy Channel

decode $x$: 
$$
g(x) = \begin{cases}
0, & x < T \\
1, & x \geq T
\end{cases}
$$

Goal: given $X$, recover the bit $Y$
Model:
- prior: $P(y=0) = P(y=1) = \frac{1}{2}$
- CCD: assume gaussian additive noise: $X = \mu_{y} + \epsilon, \epsilon \sim N(0, \sigma^{2})$
	- $P(x|y=0)=N(0, \mu_{0})$
	- $P(x|y=1) = N(1, \mu_{1})$

BDR for 0-1 Loss:

$$
\begin{align}
y^* & = \arg\max_{j \in Y} \ln p(X | Y=j)  + \ln p(Y=j) \\
 & = \arg\max_{j \in Y} -(x - \mu_{j})^{2} \\
 & = \arg\min_{j \in Y} (x - \mu_{j})^{2} \\
 &= \arg\min_{j\in Y} -2\mu_{j}x + \mu_{j}^{2}
\end{align}
$$

Hence: pick $0$ when:

$$
\begin{align}
-2\mu_{0}x + \mu_{0}^{2} &  < -2 \mu_{1}x + \mu_{1}^{2} \\
2x(\mu_{1} - \mu_{0}) & < \mu_{1}^{2} - \mu_{0}^{2} \\
x & > \frac{\mu_{1} + \mu_{0}}{2}
\end{align}
$$

## Gaussian Classifier

- CCD are Guassians
- No assumption on prior

Special case:

- Assume $\Sigma_{j} = \sigma^{2} I$ (shared isotropic covariance)
- $g_{j}(x) = w^T x + b_{j}$ (discriminant function)


$$
w^T (x - x_{0}) = 0
$$

define a hyper plane passes through $x_{0}$ that is normal to $w$



Goal: Find optimal $g^*(x)$ for the given assumptions (prior, CCD, Lossfunction)

Mode, Mean, Median

Loss function for every predict-true value pair

Conditional Risk

Given x, the risk of the system is:

$$
R(x)=\int_{Y} L(g(x), y)) p(y|x) dy
$$
Total Risk:
$$
\int_{x} R(x) p(x) dx
$$

choose the action $\alpha_{i}$ that gives the smallest possible value for $R(\alpha_{i}|x)$

likelihood, loss, prior

To minimize total risk, minimize conditional risk.

## Two class decisioning: Likelihood Ratio Test (LRT)

LRT:

L(g(x), y) p(y|x) 


## Dimensionality

### Weirdness of high dimensional 

volume of sphere = $\frac{\pi^{d/2} r^{d}}{\Gamma \left( \frac{d}{2} + 1 \right)}$

[[math/Mathematical Analysis/applications/Gamma Function#Gamma Function]]

Volume of hyper cube: $(2r)^{d}$

$$
f_{d} = \frac{\text{volume of sphere}}{\text{volume of cube}} = \frac{\pi^{d/2}}{2^{d} \Gamma\left( \frac{d}{2} + 1 \right)}
$$

$$
\lim_{ d \to \infty } f_{d} = 0
$$

corner vector $c$, and axis vector $\rho$

$$
\cos \theta = \frac{c^T\rho}{||c||\,||p||} = \frac{r^{2}}{r\sqrt{d} r} = \frac{1}{\sqrt{ d }}
$$

$$
\lim_{ d \to \infty } \cos \theta = 0 \implies \text{axis } \rho \perp \text{angle } c
$$


hypersphere shell of thickness $\epsilon$

outside sphere $s_{2}$, inside sphere $s_{1}$

$$
\begin{align}
V_{shell} &  = V(S_{2}) - V(S_{1}) \\
 & = \left( 1 - \frac{V(S_{1})}{V(S_{2})} \right) V(S_{2}) \\
\frac{V(S_{1})}{V(S_{2})} & = \left( 1- \frac{\epsilon}{r} \right)^{d}
\end{align}

$$

$$
	\lim_{ d \to \infty } \frac{V_{S_{1}}}{V_{S_{2}}} =  0 
$$

all the volume is inside the shell

### High dimensional Gaussian

$X \sim N(0, \sigma^{2}I_{d})$

$$
E[||x||^{2}] = E[x_{1}^{2}+x_{2}^{2} + \dots + x_{d}^{2}] = 
$$


[[math/Statistics/Central Limit Theorem]] the sum / average is concentrated around the mean s $d \to \infty$

$$
\frac{1}{d} ||X||^{2} \sim N\left( \sigma^{2}, \frac{1}{d} \right)
$$

as $d$ increases, the $\frac{1}{d}||X||^{2}$ converges to $\sigma^{2}$
Thus length of almost all samples vectors will be $\sigma^{2}$
Thus in high dim, a Gaussian is a shell of sphere $\sigma \sqrt{ d }$ and most of the density is in this shell.
The point of the max density is still the mean (0)



### Curse of Dimensionality

In theory, adding new features will not increase $\rho(\mathrm{error})$
informative feature 


informative features
uninformative feature CCDs still overlap


quality of CCD estimates
- density estimates for high-dim need more data! e.g. high-dim histogram $[0,1]^{d}$
- on average suppose we want 1 sample / bin


In general, desired training set size = $O(e^{p})$, $p$ is the number of parameters.

> [!note] CCD
> CCD = Class Conditional Desnity
> P(x | C_i)


- reduce number of parameters (complexity of model)
- reduce number of features (dimensionality reduction) reduce # parameters
- create more data
	- Bayesian formulation (virtual samples)
	- data augmentation


## Linear Dimensionality Reduction

- summarize correlated features with fewer features
- How?

The data lives in a low-dimensional subspace

linear operation

### Principal Component Analysis (PCA)

Idea: if the data lives in a subspace it will look flat in some directions.

if we fit a Gaussian, it will be highly skewed

eigen-decomposition: $\Sigma = V \Lambda V^{T}$
- each $v_{i}$ defines an axis of ellipse
- each $\lambda_{i}$ defines the width along axis.

keep the large eigenvalues

select $v_{i}$ with the largest eigenvalues (principle components) to find the subspace where data "lives"

Receipt of PCA:
1. calculate Gaussian: $\mu = \frac{1}{n} \sum_{i=1}^{N}x_{i}$, $\Sigma=\frac{1}{n} \sum_{i=}^{N}(x_{i}-\mu)(x_{i}-\mu)^T$
2. eigen decomp: $\Sigma=V\Lambda V^{T}$
3. sort eigenvalues for largest to smallest
4. select top-k eigenvectors: $\Phi = [v_{1}, \dots, v_{k}]$
5. project $X$ onto $\Phi$: $z = \Phi^{T}(x-\mu) \in \mathbb{R}^K$
6. $z$ as new feature vector, BDR as usual

Notes:
This selection of $\Phi$
1. maximizes the variance of the projected training data $\sum_{i=1}^{N}||z_{i}||^{2}$
2. minimizes the reconstruction error of training data

$$
\hat{x_{i}} = \Phi(z_{i} + \mu)
$$

can be implemented efficiently using SVD
pick a $k$ that works
pick $k$ to preserve $p\%$ of variance of data


Assumption - "noise" variance is smaller than the signal variance



PCA is optimal for representation (but not necessarily for classification)

no way to fit it! (we don't use class information)



## Linear Discriminant Analysis (Fisher Linear Discriminant)

- Find a linear projection that best separate the classes

input space (x)

class mean: $u_{j}= \frac{1}{n_{j}} \sum_{x_{i} \in x_{j}} x_{i}$

1-d space (z)

$m_{j} = w^T \mu_j$

|               | input space                                                             | 1-d space            |
| ------------- | ----------------------------------------------------------------------- | -------------------- |
| class mean    | $u_{j}= \frac{1}{n_{j}} \sum_{x_{i} \in x_{j}} x_{i}$                   | $m_{j} = w^T \mu_j$  |
| class scatter | $S_{j} = \sum_{x_{i} \in C_{j}} (x_{i} - \mu_{j}) (x_{i}- \mu_{j})^{T}$ | $s_{j} = w^T S_{j}w$ |
| input         | $x_{i}$                                                                 | $w^Tx_{i}$           |
|               |                                                                         |                      |


Idea: maximize distance between proj.



problem: $w$ is unconstrained $\implies$ need normalization

Fisher's Idea:
$$
\begin{align}
w^* & = \arg\max_{w} \frac{(m_{1}-m_{2})^{2}}{S_{1}+S_{2}} \\
 & = \arg\max_{w} \frac{(m_{1} - m_{2})^T(m_{1} - m_{2})}{S_{1} + S_{2}} \\
 & = \arg\max_{w} \frac{(\mu_{1} - \mu_{2})^{T} ww^T(\mu_{1} - \mu_{2})}{w^T(S_{1}+ S_{2}) w} \\
 & = 

\end{align}
$$

高内聚，低耦合

