A **Constraint Satisfaction Problem (CSP)** is a mathematical problem defined by a set of **variables**, a set of **domains** representing possible values for those variables, and a set of **constraints** that restrict the values the variables can take simultaneously. The goal of a CSP is to find an assignment of values to all variables that satisfies every specified constraint.

The primary components involved in a CSP include:

- **Variables ($X$):** These are the entities or items that need to be assigned values. In the common exam example of a **map coloring problem**, the variables are the **states or regions** of a country (typically 6 states are specified in the prompts).
- **Domains ($D$):** This represents the set of **allowable values** for each variable. In map coloring, the domain consists of the **available colors** (typically 3 colors of your choice).
- **Constraints ($C$):** These are the **rules or restrictions** that specify which combinations of values are allowed. A standard constraint in these problems is that **adjacent states must have different colors**.

### **Modeling and Solving CSPs**

1. **Constraint Graph:** A model where **nodes represent variables** and **edges represent constraints** (adjacency) between them.
2. **Backtracking Strategy:** A **recursive depth-first backtracking strategy** is typically applied to systematically assign values and find a valid solution while respecting the constraints.