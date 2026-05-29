
### **State Space Tree Terminology**

- **State Space Tree:** A tree representation of all possible states or configurations that can be reached from the initial state of a problem. Each path from the root represents a sequence of decisions.
- **Live Node:** A node that has been generated and has the potential to be expanded, but **whose children have not yet been generated**.
- **Dead Node:** A generated node that is **not to be expanded further**. A node becomes "dead" if it violates a problem constraint (becoming an infeasible path), if it is a leaf node that has already been processed, or if all its possible children have already been explored.
- **E-node (Expansion Node):** The specific **live node that is currently being expanded** to generate its children.

---

### **E-node Selection in Backtracking vs. Branch and Bound**

The key difference between these two design paradigms lies in how the next E-node is selected from the set of live nodes:

1. **Backtracking:**
    
    - **Selection Strategy:** Uses a **Depth-First Search (DFS)** approach.
    - **Logic:** As soon as a new child (live node) is generated, it immediately becomes the new E-node. The search continues deep into the tree before backtracking to previous live nodes.
2. **Branch and Bound:**
    
    - **Selection Strategy:** Uses a **Breadth-First Search (BFS)** or **Least Cost (LC) search** approach.
    - **Logic:** In a BFS approach (FIFO), nodes are expanded level by level. In the **Least Cost (LC)** approach, which is common for optimization problems like the **0/1 Knapsack**, the live node with the "best" estimated bound (lowest cost or highest potential profit) is chosen as the next E-node to prioritize the most promising branches.