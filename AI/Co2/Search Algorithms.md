The search algorithms are categorized into **uninformed (blind)** and **informed (heuristic)** strategies.

### **Uninformed Search (Blind Search)**

Uninformed search algorithms explore the state space without any additional information about the distance or cost from the current state to the goal. They only use the information available in the problem definition to generate successors and distinguish goal states from non-goal states.

- **Breadth-First Search (BFS):** This algorithm explores all nodes at a given depth level before moving to the next level. In the exams, it is typically used to find the shallowest goal in a state space model.
- **Depth-First Search (DFS):** This algorithm explores a single branch to its maximum depth before backtracking to the nearest sibling. The sources frequently ask to trace DFS to see which goal state is reached first in a tree structure.
- **Brute Force/Trial and Error:** These are mentioned in the course syllabus as foundational classical search models.

### **Informed Search (Heuristic Search)**

Informed search algorithms use problem-specific knowledge, often in the form of a **heuristic function $h(n)$**, to find solutions more efficiently by estimating the cost to reach the goal.

- __A_ Algorithm:_* This is the most prominent informed search in your sources. It uses an evaluation function $f(n) = g(n) + h(n)$, where $g(n)$ is the actual path cost from the start and $h(n)$ is the heuristic estimate to the goal. It is used to find the **most cost-effective path**.
- **Hill Climbing:** This is a heuristic search that constantly moves "uphill" toward a state with a higher value. The sources highlight its pitfalls, such as local maxima, ridges, and plateaus.
- **Simulated Annealing:** A non-classical, stochastic version of informed search that uses an analogy from metallurgy to escape local optima by occasionally accepting "worse" moves based on a temperature parameter.
- **Genetic Algorithms:** These are non-classical searches that use phases like crossover and mutation to evolve towards an optimal solution.

### **Key Comparison in Exams**

| Feature          | Uninformed Search (BFS/DFS)                | Informed Search (A*)                           |
| :--------------- | :----------------------------------------- | :--------------------------------------------- |
| **Knowledge**    | No knowledge of goal distance.             | Uses heuristics ($h(n)$) to guide search.      |
| **Efficiency**   | Often performs exhaustive search; slower.  | Highly efficient; finds optimal paths faster.  |
| **Common Trace** | Identifying which goal is reached "first". | Calculating "optimal path" and "optimal cost". |
| **Complexity**   | Simple but can be memory-intensive.        | Requires a good heuristic to be effective.     |