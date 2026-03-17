# Uninformed Search

State Space Graphs

- Nodes: abstracted word configurations
- Arcs: Successors
- Goal test: goal nodes

Traveling in Romania

- fringe of partial plans
- expand out potential plans (tree nodes, as few as possible)

> Fringe in tree search: the collections of all nodes that have been generated but not yet expanded.

## General Tree Search Algorithm:

- Initialize the tree with the start state.
- while having candidates nodes：
	- goal test
		- True：return solutions
		- False：add to tree and expand nodes, for expanded nodes, update the fringe.

each node has only one parent. parent is updated if the cost is lower.

Properties：

- Complete: Guaranteed to find a solution if one exists.
- Optimal: Guaranteed to find the least cost path
- Time complexity?
- Space complexity?

- $b$ is the branching factor
- $m$ is the max depth
- $O(\Sigma_{i}^{m}{b^{i}}) = O(\frac{b^{m+1} - 1}{b-1}) = O(b^m)$ nodes

## DFS, BFS, UCS

Depth First Search
- Strategy: explore the deepest node first
- Implementation: fringe is a LIFO stack
- $O(b * m)$

Breadth First Search
- Strategy: expand the shallowest node first
- Implementation: fringe is a FIFO queue
- $O(\Sigma_{i}^{s} b^i) = O(b^s)$

Run a DFS with an increasing depth limit
- depth limit: actually it's BFS
- space efficiency: use a stack costs $O(bm)$
- Properties:
	- waste: search with depth limit $n$ is re-executed as in search with limit $n+1$, but waste is managable as the time complexity is determined with $b^d$

Uniform cost search UCS
- Strategy: expand a cheapest node first
- Implementation: fringe is a priority queue( priority: cumulative cost)
- Properties:
	- UCS: Process all nodes with cost less than cheapest solution

Summary:
- DFS: space efficient, but might not be time efficient
- BFS: costs a lot of space, but can find the shallowest solution as soon as possible.
- UCS: greedily explore the cheapest solution. Explore increasing cost contours


## Search and Models 

- Search is simulated (not practice in real world)
- Your search is only as good as your models

# Informed Search

Uninformed search: DFS, BFS, UCS, search with your eye closed
Informed search: Greedy, A*, search with your eye open

Heuristics: A function that estimates how close a state is to a goal.


## Greedy search

- Strategy: pick the nodes according to the heuristic function
- Example: Romania
	- Heuristics function: straight-line distance to Bucharest
- Not work in many cases:
	- a common case: Best-first takes you to the wrong goal.

## A* Search

- Uniform-cost: backward cost $g(n)$
- Greedy: forward cost: $h(n)$
- A* Search: $f(n) = g(n) + h(n)$
- Property：
	- Actual goal cost < Optimal
	- Inadmissibility heuristics break optimality by trapping good plans on the fringe.
	- Admissible: optimistic (Actual goal cost > Optimal), ensuring that the solution is optimal.
		- Assume: A is an optimal goal node, B is an sub-optimal goal node $f(A) > f(B)$, $h$ is admissible
		- Claim: Optimal node A will exit the fringe before sub-optimal node B
		- **Admissible heuristics are solutions to relaxed problems**

查地图的时候：深圳-上海
- UCS：先查深圳去哪个交通枢纽花费时间最少，一圈圈查到上海
- Greedy：先查深圳哪个交通枢纽离上海最近，然后一个节点一个节点查到上海
- A*：查深圳到哪个交通枢纽的时间+交通枢纽离上海距离近。然后渐渐扩展到上海

### Optimality

- updated before dequeuing: 如果Goal Node还在Fringe，更新Goal Node
- Admissible：

Proof of Optimality of A* Tree Search

1. $f$ is the priority, $g$ is the cost from start to here, and $h$ is the heuristic from here to goal.
2. goal nodes:
	1. a goal node is a node in the search tree, can be the same node in the graph
	2. an optimal goal node $A$ is the node has the smallest $g$ value.
	3. a suboptimal goal node $B$ is the node that has $g(B) \ge g(A)$
3. admissible: for any node $n$, $f(n) = g(n) + h(n) < g(A)$, $g$ is decided, so $h$ should be choose.
4. any ancestor $n$ of $A$ will be expanded because $f(n) \le g(A) < g(B) \le f(B)$
	1. $f(n) < g(A)$ because $h$ is admissible
		1. more specifically, $g(n) + h(n) < g(A)$
	2. $g(A) < g(B)$ because $A$ is optimal and $B$ is suboptimal
	3. $g(B) < f(B)$ because $g(B) = f(B) - h(B)$ and $h(B) > 0$

# Online Bin Packing

- Bin Packing Problem
- Online Bin Packing: Search function with a well designed heuristic

FunSearch:
- Write a simple best-fit heuristics as the first heuristic
- loop:
	- let LLM modify based on the current heuristic (expand)
	- evaluate these heuristics, add them to the database



# Conclusion

Uniform search:
1. pick node
2. goal check, if goal, stop
3. span
4. go to 1

Three different searching algorithms are just uniform search guided by different priority:
- Uniform cost search: only cost
- Greedy: only heuristic
- A* Search: cost + heuristic

