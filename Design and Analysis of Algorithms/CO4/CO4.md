**CO4: Apply backtracking and branch and bound techniques to solve complex problems by systematically exploring possible solutions.**

---

### **Part A: Theoretical Foundations & Short Numericals (5 Marks)**

1. **State Space Tree Terminology:** Define the terms **live node**, **dead node**, and **E-node** in the context of state space exploration.
2. **Methodological Comparison:** Explain how the **E-node** is chosen differently in **backtracking** versus **branch and bound** methods.
3. **Constraint Analysis:** Differentiate between **explicit and implicit constraints**. State both constraints for the **0/1 Knapsack** and **Sum of Subsets** problems.
4. **Graph Coloring Basics:** Define the **m-colorability optimization problem**. What is meant by the **chromatic number** of a graph?
5. **Search Strategies:** Briefly describe the **LC (Least Cost) search** strategy used in branch and bound and explain why it is preferred for optimization problems.

---

### **Part B: Algorithms & Application Problems (8 Marks)**

1. **Sum of Subsets Algorithm:** Write a backtracking algorithm to solve the **Sum of Subsets** problem.
2. **4-Queens Logic:** Write a recursive backtracking algorithm specifically to print **all solutions** to the 4-Queens problem.
3. **Sum of Subsets Tracing:** Draw the state space tree generated using backtracking for the instance: $N=3, m=10,$ and weights $w = {3, 7, 10}$.
4. **Map Coloring (m-colorability):** A logistics planner needs to color a map of six districts (A, B, C, D, E, F) such that no two adjacent districts have the same color. Explain the algorithm design technique and illustrate the steps to find the minimum number of colors needed.
5. **Branch and Bound Logic:** Describe the specific steps involved in generating a state space tree using the **LC Branch and Bound** approach for a maximization problem.

---

### **Part C: Advanced Problem Solving & Tracing (12 Marks)**

1. **N-Queens Comprehensive:** Explain how the N-Queens problem is solved using backtracking. Draw the complete **state space tree for the 4-Queens problem** as generated during the search.
2. **CargoMax Knapsack (LCBB):** A logistics company, **CargoMax**, must load a truck with capacity $m=12$. Given 5 packages with weights $w = {4, 6, 3, 4, 2}$ and profits $p = {10, 15, 6, 8, 4}$, solve the problem using **LC Branch and Bound**. Draw the state space tree and identify the optimal selection.
3. **0/1 Knapsack Optimization:** Solve the following instance of the Knapsack problem using **LC Branch and Bound**: $n=4, m=15,$ weights $w = {2, 4, 6, 9},$ and profits $p = {10, 10, 12, 18}$. Find the optimal solution and show the state space tree.
4. **Large Scale Sum of Subsets:** Applying backtracking principles, solve the Sum of Subsets problem for $N=6$ and $m=30$ with weights $w = {5, 10, 12, 13, 15, 18}$. Write the algorithm and draw the resulting state space tree.
5. **m-colorability Tracing:** For a given graph (e.g., Fig. 5 in your sources), write an algorithm to color the graph with the minimum number of colors. Draw the state space tree used to determine the **chromatic number**.

---

### **High-Priority Strategy for CO4**

- **100% Probability Concept:** **State Space Trees** are required for almost every answer in this unit. You must be able to draw them clearly, labeling live, dead, and E-nodes.
- **Recurring Numerical Pattern:** The **Sum of Subsets** problem with $N=6$ and $m=30$ has appeared in multiple recent papers (August/September 2024 and 2025).
- **Mark-Efficiency Tip:** The **N-Queens** problem is a "standard" 12-mark question. Mastering the state space tree for $n=4$ is the easiest way to secure these marks.
- **Branch and Bound Focus:** For the **Knapsack problem**, the examiners specifically look for the **LC (Least Cost)** approach. Ensure your state space tree shows the calculation of upper bounds at each node to justify which path the E-node takes.