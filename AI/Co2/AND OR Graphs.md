### **Primary Characteristics of AND/OR Graphs**

- **Problem Decomposition (Goal Reduction):** Unlike standard state-space graphs that represent paths, AND/OR graphs represent the decomposition of a complex problem into smaller, manageable sub-problems.
- **AND Nodes:** An AND node represents a problem that is solved only if **all** of its immediate sub-problems (children) are solved. In diagrams, these are often marked with an arc across the edges.
- **OR Nodes:** An OR node represents a problem that can be solved if **at least one** of its alternative sub-problems is solved. These represent different possible paths or methods to achieve a goal.
- **Solution Graph (not a path):** A solution to an AND/OR graph is not a single path from start to goal, but a **subgraph** that includes all necessary sub-problems identified by AND nodes and at least one alternative for each OR node.
- **Search Procedure:** The extraction of a solution graph is typically performed using **Depth First Search (DFS)**.

### **Exam Context**

- **Strategic Tip:** When listing these characteristics, examiners usually expect a small **diagram** illustrating the difference between an AND arc and an OR branch to secure full marks.