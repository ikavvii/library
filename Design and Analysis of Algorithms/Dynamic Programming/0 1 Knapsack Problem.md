>In the 0/1 Knapsack problem, we build a 2D table V[i, j] where i represents the items considered (from 1 to $n$) and j represents the current weight capacity (from 0 to $m$).

The dynamic programming recurrence relation is: 
* If $w[i] \le j$: V[i, j] = max(V[i-1, j], V[i-1, j-w[i]] + p[i])
* If $w[i] > j$: V[i, j] = V[i-1, j]

**Description**: 
Dynamic programming solves the 0/1 Knapsack by relying on the principle of optimality. We build optimal solutions for smaller knapsack capacities using a subset of the items, then iteratively bring in new items, deciding whether including the current item yields a higher profit than leaving it out.

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

