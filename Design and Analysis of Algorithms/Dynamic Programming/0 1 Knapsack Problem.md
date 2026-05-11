>In the 0/1 Knapsack problem, we build a 2D table V[i, j] where i represents the items considered (from 1 to $n$) and j represents the current weight capacity (from 0 to $m$).

The dynamic programming recurrence relation is: 
* If $w[i] \le j$: V[i, j] = max(V[i-1, j], V[i-1, j-w[i]] + p[i])
* If $w[i] > j$: V[i, j] = V[i-1, j]

**Description**: 
Dynamic programming solves the 0/1 Knapsack by relying on the principle of optimality. We build optimal solutions for smaller knapsack capacities using a subset of the items, then iteratively bring in new items, deciding whether including the current item yields a higher profit than leaving it out.

>The problem is viewed as a sequence of decisions where we either include or exclude an item $i$ to maximize total profit without exceeding the capacity $m$

**Time Complexity**: $\Theta(n \times m)$, where $n$ is the number of items and $m$ is the capacity.

```
Algorithm DKnap(p, w, x, n, m)
// p[1..n] and w[1..n] contain the profits and weights. m is capacity.
{
    for j := 0 to m do V[0, j] := 0;
    for i := 1 to n do
        for j := 0 to m do
            if w[i] <= j then 
                V[i, j] := max(V[i-1, j], V[i-1, j-w[i]] + p[i]);
            else 
                V[i, j] := V[i-1, j];
}
```

### Dynamic Programming Approach for 0/1 Knapsack

Dynamic programming solves the 0/1 Knapsack problem by applying the **Principle of Optimality**. The problem is viewed as a sequence of decisions where we either include or exclude an item $i$ to maximize total profit without exceeding the capacity $m$.

We define $V[i, w]$ as the maximum profit achievable using a subset of the first $i$ items with a total weight at most $w$. The recursive formula is:

* **Base Case:** $V[0, w] = 0$ for all $w$, and $V[i, 0] = 0$ for all $i$.
* **Recurrence:**
* If $w_i > w$: $V[i, w] = V[i-1, w]$ (The item is too heavy to fit).
* If $w_i \le w$: $V[i, w] = \max(V[i-1, w], V[i-1, w - w_i] + p_i)$ (Choose the better of including or excluding the item).

### Solving the Instance

**Instance Details:** $n=4, m=15$, weights $w=\{2, 4, 6, 9\}$, profits $p=\{10, 10, 12, 18\}$.

| Item ($i$) | Profit ($p_i$) | Weight ($w_i$) |
| --- | --- | --- |
| 1 | 10 | 2 |
| 2 | 10 | 4 |
| 3 | 12 | 6 |
| 4 | 18 | 9 |

**DP Table ($V[i, w]$):**
Rows represent items ($i=0$ to 4), columns represent capacity ($w=0$ to 15).

| $i \setminus w$ | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| **0** | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| **1** | 0 | 0 | 10 | 10 | 10 | 10 | 10 | 10 | 10 | 10 | 10 | 10 | 10 | 10 | 10 | 10 |
| **2** | 0 | 0 | 10 | 10 | 10 | 10 | 20 | 20 | 20 | 20 | 20 | 20 | 20 | 20 | 20 | 20 |
| **3** | 0 | 0 | 10 | 10 | 10 | 10 | 20 | 20 | 22 | 22 | 22 | 22 | 32 | 32 | 32 | 32 |
| **4** | 0 | 0 | 10 | 10 | 10 | 10 | 20 | 20 | 22 | 22 | 22 | 28 | 32 | 32 | 32 | **38** |

**Final Result:**

* **Maximum Profit:** **38** (at $V[4, 15]$).
* **Selected Items:** By backtracking from $V[4, 15]$, we find that items **1, 2, and 4** are included ($10 + 10 + 18 = 38$) with a total weight of $2 + 4 + 9 = 15$.
