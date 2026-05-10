The **Traveling Salesperson Problem (TSP)** is a classic permutation problem where the goal is to find a tour of minimum cost in a directed graph. A **tour** is defined as a directed simple cycle that includes every vertex in the graph exactly once and returns to the starting vertex.

### 1. Principle of Optimality

The TSP satisfies the **principle of optimality**, making it solvable via dynamic programming. For any optimal tour starting at vertex 1 and moving to some vertex $k$, the remaining path from $k$ back to 1 must be a shortest path that visits all remaining vertices exactly once.

### 2. DP Recurrence Formulation

Let **$g(i, S)$** be the length of a shortest path starting at vertex $i$, going through all vertices in the set $S$, and terminating at vertex 1.

- **Base Case:** When the set $S$ is empty, the distance is simply the cost of the edge from $i$ back to the starting vertex 1: **$g(i, \emptyset) = c_{i1}, \quad 1 \le i \le n$**.
    
- **General Recurrence:** For a non-empty set $S$, the algorithm chooses an intermediate vertex $j$ from $S$ that minimizes the sum of the cost from $i$ to $j$ and the shortest path from $j$ through the remaining vertices in $S$ back to 1: **$g(i, S) = \min_{j \in S} { c_{ij} + g(j, S - {j}) }$**.
    
- **Final Objective:** The length of the optimal tour is found by calculating **$g(1, V - {1})$**.
    

### 3. Step-by-Step Example (from Source)

Consider a 4-vertex graph with the following cost matrix: $$ \begin{bmatrix} 0 & 10 & 15 & 20 \ 5 & 0 & 9 & 10 \ 6 & 13 & 0 & 12 \ 8 & 8 & 9 & 0 \end{bmatrix} $$
1. **$|S| = 0$ (Base Case):** $g(2, \emptyset) = c_{21} = 5; \quad g(3, \emptyset) = c_{31} = 6; \quad g(4, \emptyset) = c_{41} = 8$.
2. **$|S| = 1$:** $g(2, {3}) = c_{23} + g(3, \emptyset) = 9 + 6 = 15$ $g(3, {2}) = c_{32} + g(2, \emptyset) = 13 + 5 = 18$ _(Other values like $g(2, {4})=18$ and $g(4, {3})=15$ are calculated similarly)_.
3. **$|S| = 2$:** $g(2, {3, 4}) = \min { c_{23} + g(3, {4}), c_{24} + g(4, {3}) } = \min { 9 + 20, 10 + 15 } = 25$.
4. **Final Tour $|S| = 3$:** $g(1, {2, 3, 4}) = \min { c_{12} + g(2, {3, 4}), c_{13} + g(3, {2, 4}), c_{14} + g(4, {2, 3}) }$ $= \min { 10 + 25, 15 + 25, 20 + 23 } = 35$.

**Optimal Tour Reconstruction:** By tracking which $j$ yielded the minimum at each step, the tour is identified as **1, 2, 4, 3, 1** with length **35**.

### 4. Complexity and Efficiency

- **Time Complexity:** The total number of $g(i, S)$ values to be computed is $(n-1)2^{n-2}$, and each requires $O(n)$ comparisons, resulting in **$O(n^2 2^n)$**.
- **Space Complexity:** The algorithm requires **$O(n 2^n)$** space to store the computed values, which becomes prohibitive even for modest values of $n$.
- **Comparison:** While $O(n^2 2^n)$ is superior to the brute-force **$O(n!)$** approach, the sources note that **Branch-and-Bound** techniques can often solve specific instances faster by using bounding functions to prune the search space.

### 5. Practical Applications

The sources highlight several real-world uses for TSP:

- **Postal Routing:** Planning the most efficient route for a postal van to visit sites and return to the post office.
- **Robotics:** Optimizing the movement of a robot arm tightening nuts on an assembly line to minimize time.
- **Production Scheduling:** Minimizing changeover costs between manufacturing different commodities in a cyclic environment.