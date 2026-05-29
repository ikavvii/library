### **Prim’s Algorithm (Minimum Cost Spanning Tree)**

Prim’s algorithm is a **Greedy method** used to find the Minimum Cost Spanning Tree (MST) of a connected, undirected graph. It works by growing the MST one vertex at a time, always choosing the cheapest edge that connects a vertex in the MST to a vertex outside of it.

#### **Algorithm: Prim(G, w, r)**

```
Algorithm Prim(V, E, cost, n, t)
// E is the set of edges, cost is the adjacency matrix
// n is the number of vertices, t is the result MST
{
    Let (u, v) be an edge of minimum cost in E;
    t[1,1] = u; t[1,2] = v;
    mincost = cost[u, v];
    for i = 1 to n do // Initialize near array
        if (cost[i, u] < cost[i, v]) then near[i] = u;
        else near[i] = v;
    near[u] = near[v] = 0;

    for i = 2 to n-1 do // Find n-2 additional edges
    {
        let j be an index such that near[j] != 0 and
            cost[j, near[j]] is minimum;
        t[i, 1] = j; t[i, 2] = near[j];
        mincost = mincost + cost[j, near[j]];
        near[j] = 0;
        for k = 1 to n do // Update near array
            if (near[k] != 0 and cost[k, near[k]] > cost[k, j])
                then near[k] = j;
    }
    return mincost;
}
```

---

### **Tracing for 9 Villages (Fig. 1)**

![](attachments/Pasted%20image%2020260528191001.png)


**Graph Data (Edge Weights):**

- (A, B): 4 | (A, H): 8
- (B, C): 8 | (B, H): 11
- (H, G): 1 | (H, I): 7
- (G, F): 2 | (G, I): 6
- (F, C): 4 | (F, D): 14 | (F, E): 10
- (I, C): 2
- (C, D): 7
- (D, E): 9

**Step-by-Step Trace (Starting from Village A):**

1. **Initialize:** Start at village **A**. The available edges are (A, B) = 4 and (A, H) = 8.
2. **Edge 1:** Select the minimum edge **(A, B)** with cost **4**. MST = {A, B}.
3. **Edge 2:** From {A, B}, the minimum edge to an outside village is **(A, H)** with cost **8** (or B-C which is also 8). Select **(A, H)**. MST = {A, B, H}.
4. **Edge 3:** From {A, B, H}, the minimum edge is **(H, G)** with cost **1**. MST = {A, B, H, G}.
5. **Edge 4:** From {A, B, H, G}, the minimum edge is **(G, F)** with cost **2**. MST = {A, B, H, G, F}.
6. **Edge 5:** From {A, B, H, G, F}, the minimum edge is **(F, C)** with cost **4**. MST = {A, B, H, G, F, C}.
7. **Edge 6:** From {A, B, H, G, F, C}, the minimum edge is **(C, I)** with cost **2**. MST = {A, B, H, G, F, C, I}.
8. **Edge 7:** From the current set, the minimum edge to connect village D is **(C, D)** with cost **7**. MST = {A, B, H, G, F, C, I, D}.
9. **Edge 8:** Finally, connect village E using **(D, E)** with cost **9**. MST = {All villages connected}.

---

### **Final Result**

- **Edges in MST:** (A,B), (A,H), (H,G), (G,F), (F,C), (C,I), (C,D), (D,E).
- **Total Cable Length Calculation:** $4 + 8 + 1 + 2 + 4 + 2 + 7 + 9 = \mathbf{37}$.

The minimum length of cable needed to connect all nine villages is **37 units**.


In Prim’s algorithm, the **greedy principle** is used to incrementally build a Minimum Cost Spanning Tree (MST) by making the best possible "local" choice at each step to achieve a "global" optimum. Unlike the **Divide and Conquer (D&C)** paradigm—which partitions a problem into smaller independent sub-problems to be solved and then merged—the Greedy method expands a single partial solution.

### **1. The Greedy Choice: Local Optimality**

The core of the greedy strategy in Prim’s is the selection of the next edge to add to the tree. At every iteration, the algorithm looks at all possible edges that connect a vertex **already in the MST** to a vertex **outside the MST**.

- **The Principle:** It chooses the edge with the **absolute minimum cost** among these candidates.
- **The Goal:** By always picking the cheapest available connection to the current tree, the algorithm aims to minimize the total weight of the final spanning tree.

### **2. Initialization via Global Minimum**

Consistent with the greedy paradigm’s "best first" logic, the algorithm typically starts by selecting an edge $(u, v)$ that has the **minimum cost in the entire set of edges** in the graph. This initial "greedy" selection provides the starting seed for the tree.

### **3. Iterative Expansion (The "Near" Logic)**

The algorithm maintains the greedy choice through a mechanism (often a `near` array) that tracks the closest vertex in the tree for every vertex outside the tree.

- **Selection Step:** It searches for an index $j$ such that $near[j] \neq 0$ and the cost of the edge $(j, near[j])$ is the **minimum**.
- **Feasibility and Update:** Once this minimum edge is added, the algorithm updates its records to see if the new vertex provides a "cheaper" way to connect other remaining villages or nodes. This ensures the next greedy choice is based on the most up-to-date local information.

### **Contrast with Divide and Conquer**

While D&C algorithms like **Merge Sort** or **Binary Search** rely on breaking the problem into halves (represented by recurrence relations like $T(n) = 2T(n/2) + cn$), Prim’s algorithm does not divide the graph. Instead:

- **Incremental vs. Recursive:** Prim’s builds the solution **one edge at a time** (requiring $n-1$ edges for $n$ vertices) rather than solving sub-graphs and merging them.
- **Decision Making:** D&C follows a pre-defined structural split; Greedy makes a decision based on the **cost-benefit** of available options at each specific step.

In summary, Prim's algorithm is a classic example of the **Greedy method** because it never reconsiders previous choices and always proceeds by adding the most cost-effective edge currently reachable.