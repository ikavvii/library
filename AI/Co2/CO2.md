Question bank for **CO2 — Non-Classical AI Search Algorithms, Game Playing, and Constraint Satisfaction**.

### **Part A: Knowledge & Short Conceptual (3–5 Marks)**

1. **Simulated Annealing:**
    - What is Simulated Annealing and why is it named so?
    - Point out the significance of Simulated Annealing in AI and match the parameters of analogy between a physical system and an optimization problem.
2. **Constraint Satisfaction:**
    - Define a Constraint Satisfaction Problem (CSP) and mention the components involved.
3. **AND/OR Graphs:**
    - List the primary characteristics of AND/OR graphs.
4. **Genetic Algorithms:**
    - Sketch the cycle/phases of a Genetic Algorithm.

### **Part B: Intermediate Analysis & Procedures (7–10 Marks)**

1. **AND/OR Graph Solutions:**
    - For a given AND/OR graph, construct an appropriate solution graph and outline the procedure used to extract it (typically using Depth First Search).
2. **Genetic Algorithm Lifecycle:**
    - Specify the phases in the lifecycle of a Genetic Algorithm and provide a precise note on each phase.
3. **Game Playing Theory:**
    - Outline the Alpha-Beta pruning algorithm during a Minimax search on a game tree and explain how it improves efficiency.

### **Part C: Advanced Problem Solving & Tracing (15 Marks)**

1. **Alpha-Beta Pruning (Numerical Trace):**
    - Apply the Minimax algorithm with Alpha-Beta pruning on a provided game tree.
    - Identify all **$\alpha$-cuts** and **$\beta$-cuts** wherever applicable.
    - **Compare the result** with that obtained when a standard Minimax search is undertaken over the same tree.
2. **Constraint Satisfaction Problem (Modeling & Trace):**
    - Demonstrate the definition of a CSP on an instance of a **map coloring problem** (usually 6 states and 3 colors).
    - Model the **constraint graph** for the given problem.
    - Apply a **recursive depth-first backtracking strategy** to obtain the valid coloring solution.

---

### **Exam Intelligence & Strategy for CO2**

- **The "Binary Choice" Pattern:** In almost every paper, Part C for CO2 offers a direct choice between an **Alpha-Beta Pruning trace** and a **CSP/Map Coloring problem**. Mastering one of these two guarantees the 15-mark section.
- **Recursive Backtracking:** When solving the CSP map coloring problem, examiners specifically look for the "constraint graph" as an intermediate step before the final solution.
- **The Alpha-Beta Pruning Trace:** Ensure you specifically mark where the "pruning" occurs. Failing to explicitly label the $\alpha$-cuts and $\beta$-cuts often results in a 5-mark deduction even if the final value is correct.
- **AND/OR Graphs:** This is a "Fastest to Complete" topic. It consistently appears as a 7-8 mark question asking for characteristics and a solution graph.

### **Topic Frequency Table (CO2)**

|Topic|Probability|Typical Marks|Frequency|
|:--|:--|:--|:--|
|**Alpha-Beta Pruning Trace**|100%|15|4/4 Papers|
|**CSP Map Coloring**|100%|15|4/4 Papers|
|**AND/OR Graph Characteristics**|100%|7–8|4/4 Papers|
|**Simulated Annealing (Theory)**|50%|3–5|2/4 Papers|
|**Genetic Algorithm Phases**|50%|5–7|2/4 Papers|
