一个在$S$上定义的Permutation可以表示为一个$S \to S$的双射$\sigma$

# Notations

## Cauchy's two-line notation

Cauchy's two-line notation

$$
\sigma = \begin{pmatrix}
x\_1 & x\_2 & x\_3 & \dots & x\_n \\
\sigma(x\_1) & \sigma(x\_2) & \sigma(x\_3) & \dots & \sigma(x\_n) \\
\end{pmatrix}
$$

## one-line notation

one-line notation

$$
\sigma = \sigma(x\_1)\sigma(x\_2) \dots \sigma(x\_n)
$$

## cycle notation

a $k$-cycle is represented by $(x, \sigma(x), \sigma^2(x), \dots, \sigma^k(x)), \sigma^k(x) = x$

and a cycle notation is writing a permutation as all cycles of the permutation:

$$\sigma = (x, \sigma(x), \sigma^2(x) \dots)(y, \sigma(y), \dots)\dots$$

how to write down the cycle notation:

1. Pick one element that have not been picked, and build the cycle. With the cycle notation, every element in the cycle maps to that unique cycle.
2. 1-cycles are omitted.

Canonical Cycle notation

1. in each cycle the largest element is listed first
2. the cycles are sorted in increasing order of their first element

### inversion of permutation

inverting the permutation: inverting the cycles
$$
\sigma^{-1} = ((126)(35))^{-1} = (621)(53)
$$

### composition of permutation

function composition of permutation:

1. associative: $(\rho \sigma) \tau = \rho (\sigma \tau)$
2. identity permutation: $\rm{id}$
3. each permutation has an inverse that $\sigma^{-1} \sigma = \sigma \sigma^{-1} = \rm{id}$

### order of a permutation

the order of a permutation is the smallest positive number that $\sigma^m = \rm{id}$

The number is the least common multiple (lcm) of the lengths of its cycles, so every elements cycles back to its original position.
$$
m = \rm{lcm}(k\_1, k\_2, \dots, k\_n)
$$

### parity of permutation

every permutation of a finite set can be expressed as the product of transpositions since every cycle can be composed by transpositions:

For example:
$$
(a,c)(a,b) = (a,b,c)
$$
proof: $b \to a \to c \Rightarrow b \to c$, and $c\to c \to a \Rightarrow c \to a$, and $a \to b \to b \Rightarrow a \to b$

and:
$$
(a,b,c,d) = (a,d)(a,b,c)
$$

so any cycle can be decomposed into parities:

$$
(a,b,c,d) = (a,d)(a,b,c) = (a,d)(a,c)(a,b)
$$

And:

$$
\rm{sgn}(\sigma \pi) = \sgn(\sigma)\sgn(\pi)
$$

Proof:

1. both $\sigma$ and $\pi$ can be decomposed to transpositions. so $\sigma \pi$ can also be decomposed to the compositions of these transpositions.
2. odd + odd is even, odd + even is odd, even + even is even. This match with (-1)(-1) = 1, (-1)(1) = (-1), (1)(1) = 1.
3. This is what to be proven.

> [!note] Transposition
>
> a transposition is a single 2-cycle
