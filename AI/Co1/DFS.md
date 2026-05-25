To trace the **Depth First Search (DFS)** algorithm for the state space model provided, we follow a Last-In-First-Out (LIFO) approach using a stack. DFS explores each branch to its maximum depth before backtracking to the next available sibling.

![](attachments/Pasted%20image%2020260525170505.png)

**Initial Setup:**

- **Start Node:** A
- **Goal States:** I (Goal-1), J (Goal-2)
- **Strategy:** Explore children in alphabetical order (Left-to-Right using a Depth-First Search approach).

| **Step** | **Node Popped** | **Stack (Fringe)** | **Nodes Expanded** | **Remarks**                                             |
| -------- | --------------- | ------------------ | ------------------ | ------------------------------------------------------- |
| 1        | —               | [A]                | —                  | Initial state.                                          |
| 2        | A               | [B, C, D]          | A                  | A is expanded; children B, C, D added. B is at the top. |
| 3        | B               | [E, F, G, C, D]    | A, B               | B is expanded; children E, F, G added to the top.       |
| 4        | E               | [I, J, F, G, C, D] | A, B, E            | E is expanded; children I, J added to the top.          |
| 5        | I               | [J, F, G, C, D]    | A, B, E, I         | Goal Reached.                                           |

**Result:**

- **Goal State Reached First:** I (Goal-1).
- **Path Followed:** A → B → E → I.

---

### **General Steps for DFS in Exam Tracing**

1. **Initialize the Stack:** Place the start node in the fringe (stack).
2. **LIFO Exploration:** Pop the top node from the stack. If it is the goal, terminate. If not, expand it and push its children onto the stack.
3. **Tie-breaking Rule:** Unless specified otherwise, always expand children in **alphabetical order** from left to right. In a stack, this means pushing the rightmost child first so the leftmost child remains at the top,.
4. **Avoid Cycles (Optional):** If a node has already been visited, do not add it back to the stack.
5. **Identify First Goal:** Explicitly state which goal node was encountered first in the stack's top position.

### **Exam Tip for CO1**

DFS questions are typically worth **7–8 marks**. To secure full marks:

- Always draw the **Stack (Fringe)** status at every step.
- Clearly list the **order of expansion** (the sequence in which nodes were popped).
- Even if the goal is obvious, do not skip steps; the "trace" refers to the mechanical process the algorithm follows,.