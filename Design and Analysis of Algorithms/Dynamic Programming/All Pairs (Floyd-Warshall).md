**Principle of Optimality:**
The all-pairs shortest path problem satisfies the Principle of Optimality. If $k$ is an intermediate vertex on the shortest path from $i$ to $j$, then the sub paths from $i$ to $k$ and from $k$ to $j$ must also be the shortest paths between those respective pairs of vertices.

**The recurrence relation is: $A^k[i, j] = \min(A^{k-1}[i, j], A^{k-1}[i, k] + A^{k-1}[k, j])$**

```
Algorithm AllPaths(Cost, A, n)
// Cost[1:n, 1:n] is the adjacency matrix
// A[1:n, 1:n] will hold the shortest distances
{
    for i := 1 to n do
        for j := 1 to n do
            A[i, j] := Cost[i, j];
            
    for k := 1 to n do
        for i := 1 to n do
            for j := 1 to n do
                A[i, j] := min(A[i, j], A[i, k] + A[k, j]);
}
```

**Time Complexity**: The algorithm has three nested loops, each executing $n$ times. Thus, the time complexity is $O(n^3)$.

