### **Single Source Shortest Path (Dijkstra’s Algorithm)**

To find the shortest distance from a starting vertex to all other vertices in a directed graph, we use **Dijkstra’s algorithm**. This algorithm follows the **Greedy method** of design.

#### **1. Algorithm: ShortestPath(v, cost, dist, n)**

This algorithm calculates the shortest paths from a source vertex $v$ to all other $n$ vertices in a graph with non-negative edge costs.

```
Algorithm ShortestPath(v, cost, dist, n)
// v is the source vertex; dist[j] is the shortest distance from v to j
// cost is the adjacency matrix; n is the number of vertices
{
    for i = 1 to n do
    {
        S[i] = false;        // Initialize the set of visited vertices
        dist[i] = cost[v, i]; // Initial distance from source to all nodes
    }
    S[v] = true; dist[v] = 0;  // Source is visited; distance to itself is 0

    for num = 2 to n-1 do
    {
        Choose a vertex u such that S[u] is false and
            dist[u] is minimum; // Greedy choice
        S[u] = true;            // Mark u as visited

        for each vertex w such that S[w] is false do
            if (dist[w] > dist[u] + cost[u, w]) then
                dist[w] = dist[u] + cost[u, w]; // Relaxation step
    }
}
```

---

#### **2. Tracing the Algorithm (Delivery Map)**

![](attachments/Pasted%20image%2020260528214453.png)

Based on the **"delivery map"** instance provided in the source, starting from **vertex 1**, we trace the algorithm for $n=5$ vertices.

### 1. Graph Data

```
(1, 2) = 10 | (1, 4) = 30 | (1, 5) = 100
(2, 3) = 50
(3, 5) = 10
(4, 3) = 20 | (4, 5) = 60
```

### 2. Step-by-Step Trace

|**Iteration**|**Set S (Visited)**|**Vertex selected (u)**|**dist[2]**|**dist[3]**|**dist[4]**|**dist[5]**|
|---|---|---|---|---|---|---|
|**Initial**|$\{1\}$|—|10|$\infty$|30|100|
|**1**|$\{1, 2\}$|2|10|60|30|100|
|**2**|$\{1, 2, 4\}$|4|10|50|30|90|
|**3**|$\{1, 2, 4, 3\}$|3|10|50|30|60|
|**4**|$\{1, 2, 4, 3, 5\}$|5|10|50|30|60|

### 3. Detailed Logic for Updates

- **Iteration 1:** Vertex 2 is chosen (min dist 10). We check if $1 \rightarrow 2 \rightarrow x$ is shorter than the current path to $x$.
    
    - $\text{dist}[3]$ becomes $\min(\infty, 10 + 50) = 60$.
        
- **Iteration 2:** Vertex 4 is chosen (min dist 30). We check if $1 \rightarrow 4 \rightarrow x$ is shorter than the current path to $x$.
    
    - $\text{dist}[3]$ becomes $\min(60, 30 + 20) = 50$.
        
    - $\text{dist}[5]$ becomes $\min(100, 30 + 60) = 90$.
        
- **Iteration 3:** Vertex 3 is chosen (min dist 50). We check if $1 \rightarrow 4 \rightarrow 3 \rightarrow x$ is shorter than the current path to $x$.
    
    - $\text{dist}[5]$ becomes $\min(90, 50 + 10) = 60$.
        
- **Iteration 4:** Vertex 5 is chosen (min dist 60). Since it has no outgoing edges to unvisited vertices, no updates are made.
    

### 4. Final Shortest Paths from Vertex 1

- **To Vertex 2:** $1 \rightarrow 2$ (Distance: 10)
    
- **To Vertex 3:** $1 \rightarrow 4 \rightarrow 3$ (Distance: 50)
    
- **To Vertex 4:** $1 \rightarrow 4$ (Distance: 30)
    
- **To Vertex 5:** $1 \rightarrow 4 \rightarrow 3 \rightarrow 5$ (Distance: 60)