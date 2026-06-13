This question bank for **CO4 (Software Testing Fundamentals)** is compiled from the provided previous year semester papers. In accordance with the exam pattern, CO4 is always evaluated in **Question 4 (25 Marks)**, following a (a) 3-mark, (b) 7-mark, and (c) 15-mark structure.

### **Part A: Testing Principles & Theory (3 Marks)**

_These questions typically ask for justifications or comments on fundamental testing axioms._

1. **Exhaustive Testing:** "It is practically impossible to exhaustively test a program." Provide your comments or defend this statement with an appropriate example.
2. **Pareto Principle:** Explain the significance of the **Pareto Principle** in the context of software testing.
3. **Cyclomatic Complexity:** What is the significance of the **Cyclomatic Complexity Constant**?.
4. **Testing Strategy:** Comment on the following recommended procedure: "Develop test cases using the blackbox method and then develop supplementary test cases as necessary by using the whitebox method.".

### **Part B: Black-Box & Principle Applications (7 Marks)**

_These questions focus on specific testing principles or applying Black-Box methods to common modules._

1. **Defect Clustering:** Explain the background and significance of the **"Defect Clustering"** principle.
2. **ATM Authentication:** Apply Black-Box testing methods to test a module developed for **customer authentication** in an ATM Banking Software.
3. **Boundary Value Analysis (BVA) - ASCII:** A program reads an alphabet and a random ASCII value to check for a match. Apply Black-Box testing using **BVA** (Hint: Lowercase 97–122, Uppercase 65–90).
4. **Quadratic Solver:** Design suitable test cases using Black-Box testing for a function `QuadraticSolver` that solves $ax^2 + bx + c = 0$. Tabulate results in a standard format.

### **Part C: White-Box (Path Testing) & Advanced BVA (15 Marks)**

_This section is heavily weighted toward Basis Path testing (White-Box) or complex Boundary Value Analysis problems._

**Option 1: Basis Path Testing (Pseudo-code Analysis)**

1. **Arithmetic Operations:** Write a complete pseudo-code for four simple arithmetic operations (+, -, *, /). Apply **Basis Path testing** to this code and present the test case report.
2. **Bank Interest Logic:** A bank pays interest based on deposit amount (threshold: ₹50,000) and period (threshold: 3 years). Write the pseudo-code for this logic and test it using **PATH Testing**.
3. **Counter Loop:** Write pseudo-code to read numbers from a user until they respond "NO," counting positive, negative, and zero values. Apply **Basis Path testing** and generate the test case report.
4. **Largest Number Loop:** Given a code snippet that finds the largest of two numbers and asks "DO you want to continue?", apply **Basis Path testing** to determine the number of test cases and generate the report.

**Option 2: Advanced Black-Box (BVA & Robustness)**

1. **Next Date Problem:** A program determines the next date in DD/MM/YYYY format for the year range . Design test cases using **Boundary Value Analysis (BVA)** and **Robustness Testing** methods. Tabulate the results.

---

### **Strategic Preparation Tips for CO4**

- **The Guaranteed Numerical:** **Basis Path Testing** appears in some form in every paper analyzed. You must be able to draw a flow graph from pseudo-code, calculate Cyclomatic Complexity, and list independent paths.
- **High-Probability Black-Box:** The **"Next Date"** problem and **ATM Authentication** are the most recurring scenarios for Black-Box testing applications.
- **Safe Theory Marks:** Memorize the definitions and justifications for **Exhaustive Testing** and the **Pareto Principle**, as these are the "go-to" questions for the 3-mark subdivision.
- **Difficulty Note:** Basis Path Testing is considered "Hard" because it requires high logical accuracy; ensure your pseudo-code is clear before attempting to map the paths.