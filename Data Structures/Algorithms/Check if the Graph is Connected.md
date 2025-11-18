- To check if a graph is connected using DFS.  
- This works for **undirected graphs** and can be adapted for BFS if desired.
### Algorithm: Check if a Graph is Connected

**Input:**

- Graph G=(V,E)
- V: set of vertices
- E: set of edges

**Output:**

- Return **TRUE** if the graph is connected, **FALSE** otherwise.

---

**Procedure IsConnected(G):**

1. For each vertex v in V:  
      set visited[v]←false
2. Select any vertex s from V
3. Call DFS-Visit(s)

**Procedure DFS-Visit(u):**

1. visited[u]←true
    
2. For each neighbor w of u:  
      if visited[w]=false then  
        Call DFS-Visit(w)
    
3. After DFS-Visit is finished:  
     For each vertex v in V:  
      if visited[v]=false then  
        Return **FALSE**
    
4. Return **TRUE**
    

---

**Explanation:**

- The algorithm starts from a single vertex and marks all reachable vertices using DFS (can also use BFS).
- If any vertex remains **unvisited** after the traversal, the graph is **not connected**.
- If all vertices are visited, the graph is **connected**.