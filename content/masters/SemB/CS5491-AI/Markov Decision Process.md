- a set of states $s \in S$, a set of actions $a \in A$
- transition function $T(s,a,s')$
  - $P(s'|s, a)$
  - the model, the dynamics

Markov: given the present state, the future and the past are independent.

There are a set of states $S$ to transfer, and a set of actions $a \in A$ to takes to transfer among states.

Taking actions on a specific states $s$ might lead to different states $s'$, with probability $P(s'|a, s)$.

Transitioning between states by taking action $a$ would be assigned with a **reward** $R(s' | s, a)$.

A policy is a mapping from $s\in S$ to $a \in A$. To know which action to take on each state, one should know what action $a$ to take when in state $s$.

With a policy $\pi(s) = a$, given a starting point, there is a deterministic state sequence $\[s\_{0}, s\_{1}, s\_{2} \dots]$. To evaluate the policy, we use the concept **utility**. To focus more on near future, use a discount $\gamma$ to discount future rewards

$$
U(\[s\_{0},s\_{1},s\_{2}, \dots]) = R(s\_{0}) + \gamma R(s\_{1}) + \gamma^{2}R(s\_{2}) + \dots
$$

To find a policy, the key is to average the discounted utility of with probabilities.

$$
V(s) = \max\_{a} \sum\_{s'} P(s'|a,s) \[R(s'|a,s) + \gamma V(s')]
$$

This is called _Bellman Equation_.

To calculate $V(s)$, we need to search the whole tree.

Policy Iteration:

- Initialize Policy
- Repeat until the policy stop changing
  - for every states:
    - Policy evaluation: given a policy $\pi$, follow it and calculate the prob-averaged utility. (Bellman Equation without the $\max\_{a}$ operator): update the state values according to current policy.
    - Policy extraction: once you have the value of all states, you update the policy without iterate all actions: extract the policy from the converged value above
- return the converged policy

Value Iteration:

- Initialize Values
- Repeat until the value stop changing (converge)
  - for every states:
    - look all utilities with different actions, take the biggest utility.
- Extract the policy from the converged value.

The probability function $P$ means that action $a$ takes on $s$ will leads to different $s'$ with Probability $P(s, a, s')$.

stationary preferences

$\[a\_{1},a\_{2},\dots]$

Discounted utility

Infinite Utilities

Solutions:

$$
U(\[r\_{0}, \dots, r\_{\infty}]) = \sum\_{t=0}^{\infty} \gamma^{t}r\_{t} \leq \frac{R\_{\mathrm{max}}}{1-\gamma}
$$

Deterministic Policy:
$$
\pi(s) = a
$$

Stochastic Policy:

$$
\pi(a | s) = P(A\_{t}=a | S\_{t} = s)
$$

An optimal Policy $\pi^{\*}$: maximize the expected total discounted reward.

Policy Extraction:

$$
\pi^{_}(s) = \arg\max\_{a} \sum\_{s'} P(s, a, s')\[R(s,a,s') + \gamma V^{_}(s')]
$$

Q value
$Q(s,a)$: the value of taking action $a$ in state $s$

$V$ value
$V(s)$: the value of the state

Finding the policy:

The optimal policy $\pi^\*$

which action to take for every possible state to maximize the cumulative reward over time.

future rewards are less certain than immediate ones, use a discount factor $\gamma$ to prioritize sooner gains

Bellman Equation
$$
V(s) = \max\_{a} \sum\_{s'} P(s,a,s') \[R(s,a,s') + \gamma V(s')]
$$

$V$ is the values of states

Racing Search Tree

Time limited: $V\_{k}(s)$ to be the optimal value of $s$ if the game ends in $k$ more steps

Value Iteration algorithm

$V\_{0}(s) = 0$.

expectimax

- Policy evaluation: calculate utilities for some fixed policy until converges
- Policy improvement: update policy using one-step look-ahead with resulting converged utilities as future values
- repeat until converge

value iteration, policy iteration
policy evaluation
policy extraction (one-step lookahead)

variations of Bellman updates
