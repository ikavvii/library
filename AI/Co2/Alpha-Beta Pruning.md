![](attachments/Pasted%20image%2020260527102723.png)

| Feature             | Standard Minimax                      | Alpha-Beta Pruning                                                                     |
| ------------------- | ------------------------------------- | -------------------------------------------------------------------------------------- |
| **Final Result**    | Returns **-3**                        | Returns **-3**                                                                         |
| **Nodes Evaluated** | All 16 terminal leaves are evaluated. | Only 11 terminal leaves are evaluated                                                  |
| **Optimal Path**    | A → B → E → Right Child (-3).         | A → B → E → Right Child (-3).                                                          |
| **Efficiency**      | Slower; performs exhaustive search.   | **Faster**; significantly reduces the search space by eliminating irrelevant branches. |
The **Alpha-Beta pruning algorithm** is an optimization technique for the standard **Minimax search** used in two-player, zero-sum games. It identifies and "prunes" branches of the game tree that do not need to be searched because they cannot possibly influence the final decision.

### **Outline of the Alpha-Beta Pruning Algorithm**

The algorithm maintains two values, **Alpha ($\alpha$)** and **Beta ($\beta$)**, which represent the best-guaranteed scores for the Maximizing and Minimizing players, respectively.

1. **Initialization:** The search begins at the root node with **$\alpha = -\infty$** and **$\beta = +\infty$**.
2. **Recursive Traversal:** The algorithm performs a **depth-first search** of the game tree.
3. **MAX Node Operations:**
    - The node evaluates its children one by one.
    - It updates **$\alpha$** to be the maximum of its current value and the value returned by a child node.
    - **Pruning Condition:** If **$\alpha \ge \beta$**, the algorithm performs a **$\beta$-cut** and stops evaluating the remaining children of that MAX node, as the MIN player above would never allow the game to reach this branch.
4. **MIN Node Operations:**
    - The node evaluates its children one by one.
    - It updates **$\beta$** to be the minimum of its current value and the value returned by a child node.
    - **Pruning Condition:** If **$\beta \le \alpha$**, the algorithm performs an **$\alpha$-cut** and stops evaluating the remaining children of that MIN node, as the MAX player above already has a better guaranteed option elsewhere.
5. **Termination:** The process continues until the root node is assigned the optimal value, which is identical to the value a standard Minimax search would produce.


>**At a MAX Node:** When $\alpha \ge \beta$, the pruning that happens is called a **$\beta$-cut** (Beta-cut). This is because the execution is halted by the upper bound ($\beta$) dictated by a MIN ancestor above it.

>**At a MIN Node:** When $\beta \le \alpha$, the pruning that happens is called an **$\alpha$-cut** (Alpha-cut). This is because execution is halted by the lower bound ($\alpha$) dictated by a MAX ancestor above it.

### **How Alpha-Beta Pruning Improves Efficiency**

The primary advantage of Alpha-Beta pruning is its ability to reach an optimal decision while exploring significantly fewer nodes than standard Minimax.

- **Reduction of Search Space:** By skipping branches that are mathematically proven to be irrelevant, the algorithm **drastically reduces the number of terminal leaves** that must be evaluated.
- **Faster Decisions:** Because it visits fewer nodes, the algorithm can find the best move in a **fraction of the time** required by an exhaustive Minimax search.
- **Increased Depth:** The computational time saved by pruning allows the AI to **search deeper** into the game tree (looking ahead more moves) within the same time limit, which typically leads to more competitive and "intelligent" gameplay.
- **Maintained Optimality:** Crucially, Alpha-Beta pruning **does not change the outcome** of the search; it is guaranteed to return the same optimal value as standard Minimax, but with much higher efficiency.