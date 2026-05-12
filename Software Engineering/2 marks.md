### **Software Design (CO3)**

- **Define Modularity:** Modularity is the degree to which a system's components may be separated and recombined. A design is considered simple and understandable if it is modular, as it allows developers to focus on smaller, manageable pieces.

- **Define Coupling:** Coupling refers to the degree of **interdependence** between software modules.
    - **Data Coupling:** Occurs when modules share data through parameters. This is considered the best/weakest form of coupling.
    - **Control Coupling:** Occurs when one module directs the flow of another by passing control information (like flags).

- **Define Cohesion:** Cohesion refers to the degree to which the elements within a module **belong together**.
    - **High Cohesion:** This is desirable because it means a module performs a single, well-defined task, making it easier to maintain and reuse.
    - **Functional Cohesion:** Considered the best type of cohesion as every part of the module contributes to a single function.

- **Fan-in vs. Fan-out:**
    - **Fan-in:** The number of modules that call a particular module. **High fan-in** is positive as it indicates high reuse of a component.
    - **Fan-out:** The number of modules called by a particular module. **Excessive fan-out** should be avoided because it indicates a module is too complex and depends on too many other components.

### **Software Testing Fundamentals (CO4)**

- **Exhaustive Testing is Impossible:** This principle states that testing all possible combinations of data and preconditions is mathematically and practically impossible due to the sheer volume of permutations.

- **Defect Clustering:** This background principle suggests that a small number of modules (approximately 20%) often contain the majority (80%) of the defects found during testing.

- **Pesticide Paradox:** This states that if the same tests are repeated over and over, they will eventually stop finding new bugs. To remain effective, test cases must be regularly reviewed and updated.

- **Verification vs. Validation:**
    - **Verification:** "Are we building the product right?" (Checking against specifications).
    - **Validation:** "Are we building the right product?" (Checking against user needs).

- **Cyclomatic Complexity Constant:** This is a quantitative measure of the number of **linearly independent paths** through a program's source code. It is significant because it provides the minimum number of test cases required for full path coverage.

- **Pareto Principle:** In testing, this refers to the 80/20 rule, where 80% of errors are typically found in 20% of the system's components.

- **Independent Third-Party Testing:** This is considered the most effective form of testing because it removes the "developer bias" and ensures that the software is tested objectively against the requirements.

### **General Software Engineering (CO1 & CO2)**

- **Coding Standards:** Problems arising from ignoring coding standards include poor code readability, difficulty in maintenance, increased debugging time, and lack of consistency across a team's work.
- **Systematic Approach:** Adopting a systematic engineering approach contributes to high quality and low cost by reducing rework, improving predictability, and ensuring that requirements are captured correctly early in the life cycle.
- **DevOps:** DevOps is a set of practices that combines software development (Dev) and IT operations (Ops) to shorten the systems development life cycle and provide continuous high-quality delivery.