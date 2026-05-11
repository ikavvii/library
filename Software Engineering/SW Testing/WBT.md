**Basis Path Testing** is a structural, **white-box testing** technique used to derive a logical complexity measure of a procedural design and use this measure as a guide for defining a set of execution paths. Its primary goal is to ensure that every statement, decision, and path within the software code has been executed at least once.

According to the sources, the methodology for conducting Basis Path Testing involves a systematic seven-step procedure:

### **1. Preparation of Pseudo-code and Flowchart**

The process begins by writing a complete set of numbered code or pseudo-code statements. This is followed by drawing an equivalent **flowchart** to visualize the logic.

### **2. Construction of the Control Flow Graph (CFG)**

The flowchart is converted into a **Control Flow Graph**, where nodes represent the numbered statements and edges represent the flow of control. This graph is the fundamental tool for identifying independent paths.

### **3. Calculation of Cyclomatic Complexity $L(G)$**

Cyclomatic Complexity is a quantitative measure of the logical complexity of the program. It is crucial because **$L(G)$ determines the number of unique, independent paths** in the code and, consequently, the minimum number of test cases required.

The sources identify several formulas to compute and cross-check $L(G)$:

- **$L(G) = \text{Number of Enclosed Areas} + 1$**.
- **$L(G) = \text{Number of Simple Decision Loops} + 1$**.
- **$L(G) = E - N + 2P$**, where $E$ is the number of edges, $N$ is the number of nodes, and $P$ is the number of exit points.

### **4. Identification of Independent Paths**

Using the CFG and the calculated $L(G)$, the tester writes out the specific unique paths. For example, in a simple program to find the largest of two numbers with one decision point, $L(G)$ would be 2, requiring two unique paths to cover all branches.

### **5. Test Case Design and Reporting**

For each identified path, a suitable test case must be designed with specific **inputs** and **expected outputs** to ensure that path is traversed during execution. The final stage is the preparation of a **Test Case Report Table**, which documents the inputs, expected vs. actual program outputs, and the final pass/fail result.

### **Key Strategic Value**

- **Logical Coverage:** It ensures that all internal logic structures are exercised.
- **Efficiency:** By calculating $L(G)$, testers know exactly how many test cases are sufficient to confirm the correctness of the code logic, preventing both under-testing and redundant testing.
- **Error Detection:** It is effective at finding logic errors and incorrect assumptions about the flow of control that black-box testing might miss.