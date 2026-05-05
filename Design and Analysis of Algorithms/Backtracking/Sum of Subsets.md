The **Sum of Subsets** problem is a classic combinatorial problem that seeks to find all combinations of a given set of $n$ distinct positive numbers (usually called weights) that sum to a target value $m$. It is a primary application of the **backtracking** design paradigm.

### 1. Problem Formulation

There are two common ways to represent the solution space for this problem:

- **Variable-Sized Tuples:** A solution is represented as a $k$-tuple $(x_1, \dots, x_k)$, where each $x_i$ is the **index** of the weight selected. To avoid duplicate subsets (e.g., ${1, 2, 4}$ and ${1, 4, 2}$), an implicit constraint is added requiring indices to be in increasing order ($x_i < x_{i+1}$).
- **Fixed-Sized Tuples:** A solution is an $n$-tuple $(x_1, \dots, x_n)$ where each $x_i \in {0, 1}$. If $x_i = 1$, the $i$-th weight is included; if $x_i = 0$, it is excluded.

For both formulations, the **state space tree** contains $2^n$ distinct nodes, making a brute-force search exponential.

### 2. Backtracking and Bounding Functions

Backtracking improves efficiency by using **bounding functions** to prune branches of the state space tree that cannot lead to a solution. A node representing a partial selection $(x_1, \dots, x_k)$ is killed if:

1. The current sum plus the next weight exceeds $m$ (assuming weights are sorted in non-decreasing order).
2. The current sum plus all remaining weights is less than $m$.

The formal bounding function for the $k$-th node is: $$B_k(x_1, \dots, x_k) = \text{true iff } \sum_{i=1}^k w_i x_i + \sum_{i=k+1}^n w_i \ge m \text{ and } \sum_{i=1}^k w_i x_i + w_{k+1} \le m$$

### 3. The `SumOfSub` Algorithm

The sources provide a recursive backtracking algorithm specifically tailored for this problem. It uses three variables: `s` (current sum), `k` (index of the next weight to consider), and `r` (remaining sum of all weights from $k$ to $n$).

```
Algorithm SumOfSub(s, k, r)
// Find all subsets of w[1 : n] that sum to m.
// w[j]'s are in nondecreasing order.
{
    // Generate left child (include w[k])
    x[k] := 1;
    if (s + w[k] = m) then write (x[1 : k]); // Subset found
    else if (s + w[k] + w[k + 1] <= m)
        then SumOfSub(s + w[k], k + 1, r - w[k]);

    // Generate right child (exclude w[k]) and evaluate Bk
    if ((s + r - w[k] >= m) and (s + w[k + 1] <= m)) then
    {
        x[k] := 0;
        SumOfSub(s, k + 1, r - w[k]);
    }
}
```

### 4. Complexity and Related Problems

- **Efficiency:** Backtracking significantly reduces the number of nodes generated. For instance, in a problem with $n=6$, the full state space tree has 63 nodes, but backtracking may only need to explore 23 of them.
- **NP-Hardness:** The sum of subsets problem is **NP-hard**.
- **Reducibility:** It can be reduced to the **Partition Problem** (deciding if a set can be split into two equal-sum subsets). If the weights are integers, it can also be solved using **dynamic programming** in $O(nm)$ time.