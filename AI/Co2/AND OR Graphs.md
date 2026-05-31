### **Primary Characteristics of AND/OR Graphs**

- **Problem Decomposition (Goal Reduction):** Unlike standard state-space graphs that represent paths, AND/OR graphs represent the decomposition of a complex problem into smaller, manageable sub-problems.
- **AND Nodes:** An AND node represents a problem that is solved only if **all** of its immediate sub-problems (children) are solved. In diagrams, these are often marked with an arc across the edges.
- **OR Nodes:** An OR node represents a problem that can be solved if **at least one** of its alternative sub-problems is solved. These represent different possible paths or methods to achieve a goal.
- **Solution Graph (not a path):** A solution to an AND/OR graph is not a single path from start to goal, but a **subgraph** that includes all necessary sub-problems identified by AND nodes and at least one alternative for each OR node.
- **Search Procedure:** The extraction of a solution graph is typically performed using **Depth First Search (DFS)**.

### **Exam Context**

- **Strategic Tip:** When listing these characteristics, examiners usually expect a small **diagram** illustrating the difference between an AND arc and an OR branch to secure full marks.


In Artificial Intelligence, **AND/OR graphs** are specialized state space representations used to model problems that can be decomposed into smaller sub-problems. An **appropriate solution graph** is a subgraph of the AND/OR graph that demonstrates a path from the start node to a set of goal nodes while satisfying all logical constraints of the structure.

### **Characteristics of AND/OR Graphs**

Before extracting a solution, it is essential to understand the node types defined in the sources:

- **OR Nodes:** These represent a choice. To solve the parent problem, the agent needs to solve only **one** of its children.
- **AND Nodes:** These represent decomposition. To solve the parent problem, the agent must solve **all** of its children. In diagrams, these are typically identified by an **arc** connecting the edges branching from the parent.

---

### **Procedure to Extract a Solution Graph (DFS Approach)**

The extraction of a solution graph typically employs a **Depth First Search (DFS)** strategy to navigate the hierarchy and verify which paths successfully terminate at goal states.

1. **Initialize from the Start Node:** Begin the search at the root node (e.g., node $S$ in Figure-4).
2. **Evaluate Node Type:**
    - **If an OR node is encountered:** The search explores one branch at a time. If a branch leads to a goal, the search for that specific OR node is complete. If it fails, the search **backtracks** to explore the next alternative child node.
    - **If AND nodes are encountered:** The search must recursively verify that **all** children connected by the arc can be solved. If even one child of an AND node cannot be solved, the entire AND branch is considered a failure.
3. **Trace Goal Success:** The process continues until a set of nodes is identified where every OR choice leads to a goal and every AND requirement is fully satisfied.
4. **Construct the Final Graph:** The solution graph is the resulting set of nodes and edges that successfully connect the start state to the required goal states.

---

### **Construction for a Sample Graph (Figure-4 Analysis)**

Based on the AND/OR graphs provided in the sources (Figure-4), a solution graph can be constructed by identifying the valid logical paths:

- **Structure:** The start node **$S$** has three potential branches: an **OR** choice between a set of **AND nodes (A and B)** and an alternative branch **$C$**.
- **Solution Option 1 (The AND Path):**
    - If the agent chooses the AND branch, it must include **both** $A$ and $B$ in the solution graph.
    - The search then continues down to their children: $A \rightarrow D$ and $B \rightarrow {E, F}$. For the solution to be valid, all leaf nodes in this path (like $D$, $E$, and $F$) must be goal states.
- **Solution Option 2 (The OR Path):**
    - The agent could alternatively choose the branch to node **$C$**.
    - Since $C$ is an OR alternative to the ${A, B}$ group, the solution graph would only need to contain $S \rightarrow C$ and the subsequent successful path from $C$ (such as $C \rightarrow G \rightarrow I$ or $C \rightarrow H \rightarrow K$).

**Final Solution Graph Selection:** An appropriate solution graph for this model would be the minimal subgraph starting at $S$ that satisfies these logical requirements. For example, if $G$ and $I$ are goal states, the solution graph consists of the nodes **${S, C, G, I}$**.