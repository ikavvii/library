To trace the **Breadth First Search (BFS)** algorithm for the state space model provided, we follow a First-In-First-Out (FIFO) approach using a **Queue**. BFS explores all nodes at a given depth level before moving on to the next level.

![](attachments/Pasted%20image%2020260525171527.png)

**Initial Setup:**

- **Start Node:** S
- **Goal States:** G1, G2
- **Strategy:** Breadth-First Search (BFS) using a Queue. Explore children in alphabetical order. To avoid infinite loops and redundancies (Graph Search), nodes already in the queue or expanded are not added again.

| **Step** | **Node Popped** | **Queue (Fringe)** | **Nodes Expanded**      | **Remarks**                                                                                    |
| -------- | --------------- | ------------------ | ----------------------- | ---------------------------------------------------------------------------------------------- |
| 1        | —               | [S]                | —                       | Initial state.                                                                                 |
| 2        | S               | [A, F, T]          | S                       | S is expanded; its children at Level 1 (A, F, T) are added to the queue in alphabetical order. |
| 3        | A               | [F, T, B]          | S, A                    | A is expanded; child B is added to the back. (T is already in queue).                          |
| 4        | F               | [T, B, C]          | S, A, F                 | F is expanded; child C is added to the back.                                                   |
| 5        | T               | [B, C]             | S, A, F, T              | T is expanded; no new children added (B is already in queue).                                  |
| 6        | B               | [C, D]             | S, A, F, T, B           | B is expanded; child D is added to the back. (C is already in queue).                          |
| 7        | C               | [D, G2]            | S, A, F, T, B, C        | C is expanded; Goal State G2 is added to the back. (D is already in queue).                    |
| 8        | D               | [G2, G1]           | S, A, F, T, B, C, D     | D is expanded; Goal State G1 is added to the back. (G2 is already in queue).                   |
| 9        | G2              | [G1]               | S, A, F, T, B, C, D, G2 | Goal Reached.                                                                                  |

**Result:**

- **Goal State Reached First:** G2.
    
- **Path Followed:** S → F → C → G2.
---

### **General Methodology for BFS Tracing**

1. **Level-by-Level Expansion:** Explicitly show that nodes at Depth 1 (A, B, C) are processed before their children at Depth 2 (D, E, F, G, H, I), and so on.
2. **Queue Status:** Maintain a clear record of the **Queue (Fringe)** at every step to demonstrate the FIFO (First-In-First-Out) property.
3. **Tie-breaking Logic:** In the absence of specific heuristics, expansion typically follows the visual order in the diagram (left to right).
4. **Goal Identification:** BFS identifies the goal at the **shallowest depth**. Even if multiple goals exist at the same depth (like G1 and G2 in this model), the expansion order of their parents determines which is reached first.
