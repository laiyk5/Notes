Traveling Salesman Problem
- $n$ cities, distance $d(i,j)$
- visit every cities with minimal total distance

indicator function

n-Queens Problem

- location of the queen in each column variable $x$
- Feasible set:
	- $F = \{ x,y : x, y \in \{1, \dots, 8 \}^8; \sum_{i} \mathbb{I}(x_i = k) = 1, \forall k \in \{1, \dots, 8\} \}$
	- or $F = \{x \in \{1, \dots, 8\}^8; x_i \neq x_j, x_i, \forall i,j \in \{1, \dots, 8\}\}$
- Objective function $f(x)=1$ (dummy)


## Optimization Problem

>[!warning] No general way to solve: No free launch theorem
>It's always possible to fabricate one problem that your problem solver can't solve

- Convex optimization problem (CO): GD, SGD
- Linear Program: simplex, interior point
- (Mixed) Integer Linear Program (MILP)

> [!note] Decoupling "representation" and "problem solving": Lazy mode
> - Formulate a problem as an optimization problem
> - Identify which class the formulation belongs to
> - Call the corresponding solver


