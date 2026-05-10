**State the Principle of Optimality. List a problem that satisfies the principle of optimality and a problem that does not satisfy it.**

- **Definition:** The principle of optimality states that "an optimal sequence of decisions has the property that whatever the initial state and decision are, the remaining decisions must constitute an optimal decision sequence with regard to the state resulting from the first decision."

- **Satisfies the Principle:** The **All-Pairs Shortest Path** problem and the **0/1 Knapsack** problem satisfy the principle because the sub-paths of shortest paths are themselves shortest paths, and the sub-problems of optimal knapsack subsets are themselves optimal.

- **Does NOT Satisfy the Principle:** The **Longest Simple Path** problem. If you take the longest simple path between two nodes, a sub-path between two intermediate nodes is not guaranteed to be the longest simple path between them (since picking the longest sub-path might violate the "simple" constraint by creating a cycle).