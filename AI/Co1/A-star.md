The **A* (A-star) algorithm** is a heuristic search strategy that finds the least-cost path from a start node to a goal node by combining the actual cost to reach a node and the estimated cost to reach the goal.

### **1. Outline of the A* Search Algorithm**

Based on the procedural requirements in the sources, the algorithm follows these steps:

1. **Initialize:** Create two lists: **OPEN** (nodes to be evaluated) and **CLOSED** (nodes already evaluated). Place the start node $S$ in the OPEN list.
2. **Calculate $f(n)$:** For every node $n$, calculate the evaluation function: $$f(n) = g(n) + h(n)$$
    - $g(n)$: The actual cost from the start node to node $n$.
    - $h(n)$: The heuristic estimate of the cost from node $n$ to the goal.
3. **Selection:** Pick the node with the **lowest $f(n)$** from the OPEN list. If multiple nodes have the same value, use a tie-breaking rule (usually alphabetical).
4. **Goal Check:** If the selected node is the goal state, the search is complete.
5. **Expansion:**
    - Move the selected node to the **CLOSED** list.
    - Expand its neighbors. For each neighbor:
        - If it is not in OPEN or CLOSED, add it to OPEN.
        - If it is already in OPEN with a higher $f(n)$, update it with the lower cost.
6. **Repeat:** Return to Step 3 until the goal is reached or the OPEN list is empty.

---

### **2. Application on State Space Graph

Using the model provided, we trace the path from **Start (S)** to **Goal (G)**.

![](attachments/Pasted%20image%2020260525174909.png)

**Graph Data:**

- **Heuristics h(n):** S=10, A=9, B=8, H=8, C=6, W=7, X=5, F=4, G1=0, G2=0.
- **Edge Costs g(n):** S→A=1, S→B=2, S→H=3, A→C=3, B→C=5, H→B=3, H→W=4, C→G1=4, C→X=3, W→X=6, W→G2=3, X→G1=2, X→F=5, F→G2=3.

**Trace Table:**

| **Step** | **Node Popped** | **OPEN List (Node: g+h=f)**       | **CLOSED List**  | **Remarks**                                                                |
| -------- | --------------- | --------------------------------- | ---------------- | -------------------------------------------------------------------------- |
| 1        | —               | {S: 0+10=10}                      | —                | Initialize with Start node.                                                |
| 2        | S               | {A: 1+9=10, B: 2+8=10, H: 3+8=11} | {S}              | Expand S; A and B tie for lowest f(n). A is chosen alphabetically.         |
| 3        | A               | {B: 10, C: 4+6=10, H: 11}         | {S, A}           | Expand A; B and C tie. B is chosen alphabetically.                         |
| 4        | B               | {C: 10, H: 11}                    | {S, A, B}        | Expand B; new path to C is more expensive ($g=7, f=13$), so it is ignored. |
| 5        | C               | {G1: 8+0=8, H: 11, X: 7+5=12}     | {S, A, B, C}     | Expand C; G1 and X are added to OPEN. G1 has lowest f(n).                  |
| 6        | G1              | {H: 11, X: 12}                    | {S, A, B, C, G1} | Goal reached (8 is the lowest f in OPEN).                                  |

**3. Optimal Path and Cost**

- **Optimal Path:** Based on the trace, the algorithm reaches the goal via the path S → A → C → G1.
- **Optimal Cost:** The total path cost is 8 (1 + 3 + 4).