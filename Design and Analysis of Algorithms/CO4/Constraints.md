**Constraint Analysis:** Differentiate between **explicit and implicit constraints**. State both constraints for the **0/1 Knapsack** and **Sum of Subsets** problems.

constraints are categorized into two types to help define the solution space and find valid solutions.
### **1. Differentiating Constraints**

- **Explicit Constraints:** These are rules that restrict each variable $x_i$ to take values from a specific set (the range of the variable). They define the **size of the potential solution space** (e.g., a tuple of $n$ elements).
- **Implicit Constraints:** These are rules that determine which of the tuples that satisfy the explicit constraints actually satisfy the problem's requirements. They describe the **relationship between the variables** and serve as the "criterion function" to validate a solution.

---

### **2. Constraints for 0/1 Knapsack Problem**

In this optimization problem, the goal is to pack items into a truck or bag with a limited capacity $m$ to maximize profit $p$.

- **Explicit Constraints:** $x_i \in {0, 1}$ for $1 \leq i \leq n$.
    - _Explanation:_ This means for every item $i$, you have only two choices: either include the item ($x_i = 1$) or exclude it ($x_i = 0$).
- **Implicit Constraints:** $\sum_{i=1}^{n} w_i x_i \leq m$.
    - _Explanation:_ The total weight of all selected items must be less than or equal to the maximum capacity $m$ of the container (e.g., $m=12$ or $m=15$ in the provided exam instances).

---

### **3. Constraints for Sum of Subsets Problem**

In this problem, given a set of $n$ weights and a target sum $m$, you must find all subsets of weights that total exactly $m$.

- **Explicit Constraints:** $x_i \in {0, 1}$ for $1 \leq i \leq n$.
    - _Explanation:_ Each weight $w_i$ in the set is either included in the subset ($x_i = 1$) or not included ($x_i = 0$).
- **Implicit Constraints:** $\sum_{i=1}^{n} w_i x_i = m$.
    - _Explanation:_ The sum of the weights of the elements chosen for the subset must **exactly equal** the target value $m$ (e.g., $m=30$ for the set $w={5, 10, 12, 13, 15, 18}$ in your question bank).

**Note:** In backtracking, implicit constraints are used as **bounding functions** to "prune" the state space tree. If the sum of weights already exceeds $m$, or if the remaining weights are insufficient to reach $m$, that branch of the tree is killed early to improve efficiency.