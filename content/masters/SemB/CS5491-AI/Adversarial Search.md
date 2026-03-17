

Mini-Max: 反向搜索：假设两个玩家完全理性，而且都知道对方完全理性，从结果倒推，每一步两个对抗的玩家会怎么选择。

一直轮流span节点，直到结束状态，比较当前路径得分和已有的得分，根据每一层执行者的利益，选择是否更新得分并向上传递路径。

## $\alpha$-$\beta$ pruning

- Set initial value to the worse case
- update the value to be returned by querying values from descendents and reduce unnecessary search(pruning) by passing the feasible set of values ($[alpha, \beta]$) to its children.
	- max node: prune if $v \ge \beta$. No need to search more, the value return is deemed to be cast by its min parent.
	- min node: prune if $v \le \alpha$.

What minimax search is saying is: for each internal node: collect optimal results from its descendants, delegate this task to its children, then the node concludes the result collected and return to its parent.

To optimize the search, we need to pass information down. These internal nodes can specify what kinds of results is acceptable to let its children know when to stop.

In this minimax search case, a max node can issue the "result collecting request" with this "requirement": only explore routes that would produce score between $\alpha$ and $\beta$. And we let the node issues this request to its children iteratively, so it can adjust its requirement parameter $\alpha$ (assigned with the current potential max score) and $\beta$ (which would not actually be adjusted).

So what max node is doing when it is calling is children is just like saying: "hey boy, I've asked your brothers and found that the biggest value is $\alpha_{new}$, and my parent say he wants a score smaller than $\beta$, so go find it!". What's more, when the max node found $\alpha > \beta$, it knows no more legal value would be found, so it simply stops and returns.

