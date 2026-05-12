```
Algorithm BellmanFord(v, cost, dist, n)
// v is the source vertex, n is the number of vertices.
// cost[i, j] is the edge weight from i to j.
// dist[i] stores the shortest distance from v to i.
{
    // Initialize distances with direct edges from the source
    for i := 1 to n do 
        dist[i] := cost[v, i];
        
    // Relax edges allowing paths up to length k
    for k := 2 to n - 1 do
        for each u such that u != v and u has at least one incoming edge do
            for each <i, u> in the graph do
                if dist[i] + cost[i, u] < dist[u] then
                    dist[u] := dist[i] + cost[i, u];
}
```


We define $dist^k[u]$ as the shortest path from $A$ to $u$ using at most $k$ edges. 

**Recurrence:** $dist^k[u] = \min \{ dist^{k-1}[u], \min_i \{ dist^{k-1}[i] + cost[i, u] \} \}$

