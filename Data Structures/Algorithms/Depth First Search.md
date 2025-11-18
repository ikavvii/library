### Algorithm: Depth-First Search (DFS)

**Input:**

- Graph G=(V,E) — where V is the set of vertices (nodes) and E is the set of edges
- Starting vertex s∈V

**Output:**

- The order in which vertices are visited (optional: path discovery)

---

**Procedure DFS(G,s)**

1. For each vertex v in V:  
      set visited[v]←false
2. Call DFS-Visit(s)

**Procedure DFS-Visit(u):**

1. visited[u]←true
2. (Optionally) Output u as visited in order
3. For each neighbor w of u in G:  
      if visited[w]=false then  
        Call DFS-Visit(w)

---

#### Explanations:

- **DFS(G,s)**: Initializes all nodes as unvisited, then calls the recursive DFS-Visit starting from s.
- **DFS-Visit(u)**: Recursively visits all reachable nodes from u.
- **visited[x]**: Boolean array marking nodes as visited.
- **u, v, w**: Variable names for vertices (nodes). They let us generalize for any graph and are not specific node labels.

---

**DFS uses recursion** (calls itself to visit neighbors).