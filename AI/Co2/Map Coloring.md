**Constraint Satisfaction Problem (Modeling & Trace):**
    - Demonstrate the definition of a CSP on an instance of a **map coloring problem** (usually 6 states and 3 colors).
    - Model the **constraint graph** for the given problem.
    - Apply a **recursive depth-first backtracking strategy** to obtain the valid coloring solution.


A **Constraint Satisfaction Problem (CSP)** is defined by a set of variables, their respective domains of possible values, and a set of constraints that specify allowable combinations of those values. In the context of a **map coloring problem**, the goal is to assign a color to every state such that no two adjacent states share the same color.

Here is a demonstration of modeling and solving a CSP for a map coloring instance.

### **1. CSP Definition for Map Coloring**

To define the problem, we establish the three core components of a CSP:

- **Variables ($X$):** A set of 6 states of a country (e.g., $X = {S1, S2, S3, S4, S5, S6}$).
- **Domain ($D$):** A set of 3 available colors for each state (e.g., $D = {Red, Green, Blue}$).
- **Constraints ($C$):** A set of restrictions where adjacent states must have different colors (e.g., $S1 \neq S2$ if they share a border).

### **2. Modeling the Constraint Graph**

The **constraint graph** is a visual representation where nodes represent the variables (states) and edges represent the constraints (adjacency) between them.

**Example Adjacency Setup:** Assume a choice of neighbors for the 6 states:

- **S1** is adjacent to **S2, S3**.
- **S2** is adjacent to **S1, S3, S4**.
- **S3** is adjacent to **S1, S2, S4**.
- **S4** is adjacent to **S2, S3, S5**.
- **S5** is adjacent to **S4, S6**.
- **S6** is adjacent to **S5**.

**The Model:** In this graph, nodes $S1$ through $S6$ are connected by edges representing these borders. Any valid solution must ensure that for every edge $(u, v)$, the color assigned to node $u$ is not equal to the color assigned to node $v$.

### Formal Definition of Components

Based on the definition of a CSP found in the sources, we first define the sets involved:

- Let **$X$** be the set of variables (states or regions), where $X = {x_1, x_2, \dots, x_n}$.
- Let **$D$** be the domain of possible colors, where $D = {c_1, c_2, \dots, c_k}$.
- Let **$E$** be the set of edges in a constraint graph $G = (X, E)$, where an edge $(u, v) \in E$ exists if state $u$ and state $v$ are adjacent.
- Let **$f(x)$** be an assignment function that maps a variable $x \in X$ to a color $c \in D$.

### The Constraint Notation

The rule that any valid solution must ensure adjacent nodes have different colors is written as:

$$\forall (u, v) \in E, \quad f(u) \neq f(v)$$

### Explanation of Symbols

- **$\forall (u, v) \in E$**: This reads as "for all pairs of nodes $u$ and $v$ that share an edge in the set $E$".
- **$f(u) \neq f(v)$**: This states that the color assigned to node $u$ must not be equal to the color assigned to node $v$.


### **3. Recursive Depth-First Backtracking Strategy**

To obtain a valid solution, a **recursive depth-first backtracking strategy** is applied. This is an informed search that builds the solution one variable at a time.

**The Steps of the Trace:**

1. **Select a Variable:** Start with an unassigned state (e.g., $S1$) and assign the first color from the domain ($Red$).
2. **Check Constraints:** Move to the next state ($S2$). Attempt to assign a color. Since $S2$ is adjacent to $S1$ ($Red$), it cannot be $Red$. Assign $Green$.
3. **Recursion:** Move to $S3$. $S3$ is adjacent to $S1$ ($Red$) and $S2$ ($Green$). Assign the third color, $Blue$.
4. **Handling Conflicts (Backtracking):** Move to $S4$. $S4$ is adjacent to $S2$ ($Green$) and $S3$ ($Blue$). Assign $Red$.
    - If at any point a state has **no legal colors** left because of its neighbors, the algorithm **backtracks** to the previous state and attempts to assign it a different color.
5. **Continue Expansion:** Repeat the process for $S5$ and $S6$ until all states are colored legally.
6. **Success:** The algorithm terminates when all variables have an assigned value that satisfies all constraints.

**Final Valid Solution Example:**

- $S1: Red$
- $S2: Green$
- $S3: Blue$
- $S4: Red$
- $S5: Green$
- $S6: Red$

This approach ensures a complete search of the possible colorings while pruning branches that violate the adjacency rules.

|**State Variable**|**Assigned Color**|**Neighboring Constraints Verified**|**Status**|
|---|---|---|---|
|**$S_1$**|**Red ($R$)**|None (Initial Node)|Consistent|
|**$S_2$**|**Green ($G$)**|$S_1(R)$|Consistent|
|**$S_3$**|**Blue ($B$)**|$S_1(R), S_2(G)$|Consistent|
|**$S_4$**|**Red ($R$)**|$S_2(G), S_3(B)$|Consistent|
|**$S_5$**|**Green ($G$)**|$S_4(R)$|Consistent|
|**$S_6$**|**Red ($R$)**|$S_5(G)$|**Complete Solution**|