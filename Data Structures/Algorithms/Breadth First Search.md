### Algorithm: Breadth-First Search (BFS)

**Input:**

- Graph G=(V,E)
- Starting vertex s∈V

**Output:**

- For each vertex v∈V, the shortest path from s to v (optionally)
- The order in which vertices are visited

---

**Procedure BFS(G,s)**

1. For each v∈V:  
      Set visited[v]←false
2. Create an empty queue Q
3. visited[s]←true
4. Enqueue s to Q
5. While Q is not empty:  
      a. Dequeue u from Q  
      b. For each neighbor w of u in G:  
        i. If visited[w]=false then  
          A. visited[w]←true  
          B. Enqueue w to Q   c. (Optionally) Output u as visited in order

---

**Notes:**

- The queue Q ensures vertices are processed in level-order (i.e., all neighbors of a vertex are visited before their neighbors).
- BFS does not use recursion; instead, it uses an explicit queue.