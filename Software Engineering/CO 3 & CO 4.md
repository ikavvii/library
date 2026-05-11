This comprehensive question bank for **Course Outcome 3 (CO3)** and **Course Outcome 4 (CO4)** is compiled from the provided MCA-level software engineering examination and practice materials.

### **Course Outcome 3 (CO3): Object-Oriented Analysis & Design (OOAD)**

_Focus: Applying UML for OOAD applications and preparing design documents._

#### **Conceptual and Short Questions (2-3 Marks)**

1. **Modularity and Simplicity:** Justify the statement: "A design solution is simple and understandable if it is modular."
2. **Maintenance Costs:** Comment on the assertion: "A design solution difficult to understand would lead to increased development and maintenance cost."
3. **Coupling:** Define coupling and differentiate between **data coupling** and **control coupling**.
4. **Cohesion:** Define cohesion and explain why **high cohesion** is desirable in software modules.
5. **Cohesion Types:** Differentiate between logical and functional cohesion. Which type is considered the best and why?
6. **Fan-in and Fan-out:** Define these terms. What does high fan-in indicate, and why should excessive fan-out be avoided?
7. **Achieving Modularity:** Explain the practical steps or methods used to achieve modularity in a design solution.

#### **Design and Modeling Questions (7-15 Marks)**

1. **State Chart - Radio Buttons:** Design a state chart for a device with three radio buttons (b1, b2, b3) where all are initially off, and pressing one turns it on while turning the others off.
2. **State Chart - Coffee Machine:** Create a state chart for a coffee machine that handles coins (values 5 and 10), provides tea (price 5) or coffee (price 10), and handles change or returned money based on user selection.
3. **Sequence Diagram - Coffee Machine:** Design a sequence diagram to depict the interactions in the Coffee Machine problem (GUI, coin slot, change verification, and drink delivery).
4. **Sequence and Collaboration Diagrams - ATM:** Design these diagrams to explain the withdrawal of cash from an ATM, assuming the customer is already authenticated.
5. **Sequence and Collaboration Diagrams - Gold Vending Machine:** Depict the process for a machine where a customer uses a GOLD card/PIN to buy coins, selects payment (Cash/Card), and receives coins and a receipt.
6. **Activity Model - ATM Withdrawal:** Narrate the complete procedure for withdrawing money, including card validation, PIN entry (handling 3 failed attempts), amount selection (multiples of 100), and fund verification.
7. **Activity Model - Online Services:**
    - Design an activity model for steps in an **online shopping** website using a mobile app.
    - Design an activity model for **ordering food** via a standard mobile app.
    - Design an activity chart for the **cancellation of booked train tickets**.
8. **Class Diagram:** Design a simple class diagram for **ATM Banking software**.

---

### **Course Outcome 4 (CO4): Software Testing**

_Focus: Selecting and applying testing methodologies and analyzing results._

#### **Conceptual and Short Questions (2-3 Marks)**

1. **Testing Principles:** State any two principles of software testing.
2. **Exhaustive Testing:** Defend the statement: "Exhaustive Testing is Impossible."
3. **Defect Clustering:** Explain the background and significance of the "Defect Clustering" principle.
4. **Pareto Principle:** What is the significance of the Pareto Principle in software testing?
5. **Pesticide Paradox:** Define the "Pesticide Paradox" in the context of testing.
6. **Verification vs. Validation:** Differentiate between these two fundamental testing concepts.
7. **Testing Strategy:** Comment on the recommended procedure: "Develop test cases using the black box method and then develop supplementary test cases as necessary by using the white box method."
8. **Cyclomatic Complexity:** What is the significance of the Cyclomatic Complexity Constant?

#### **Implementation and Problem-Solving Questions (7-15 Marks)**

1. **Basis Path Testing - Mathematical Logic:**
    - Write pseudo-code to determine the **largest of two numbers** within a loop that asks the user if they want to continue. Apply basis path testing to generate a test case report.
    - Write pseudo-code for a **business calculator** (Add, Subtract, Multiply, Divide) and apply path testing.
    - Write pseudo-code to read numbers until the user responds "NO," outputting the count of positive, negative, and zero values. Apply basis path testing.
2. **Path Testing - Banking Policy:** Implement pseudo-code for a bank's interest rate policy (12% for ₹50,000+ and 3+ years; 10% for ₹50,000+ and <3 years; 8% for <₹50,000). Test the logic using **path testing**.
3. **Black Box - Boundary Value Analysis (BVA):**
    - **Quadratic Solver:** Design test cases for a function solving $ax^2 + bx + c = 0$ using three input values.
    - **ASCII Matcher:** A program checks if a character matches its ASCII value (Lowercase 97-122; Uppercase 65-90). Apply BVA to test the program.
    - **Next Date Program:** Design test cases for a program that reads a date (DD/MM/YYYY) between 1900 and 2025 using **BVA and Robust Testing** methods.
4. **Black Box - Functional Testing:** Write sufficient test cases using a black box approach for the entire **ATM withdrawal procedure**, including card/PIN validation and dispensing logic.


### Practice Test - PYQ

- **Question 1 a):** What are the problems that might occur if the software engineers do not adhere to any of the **coding standards**? (3 Marks)
- **Question 1 b):** Draw one sample **Object Diagram** for the provided class diagram (which includes classes such as Customer, Order, Product, ShoppingCart, CartItem, and OrderItem). (7 Marks)
- **Question 1 c):** Design a neat **Sequence and Collaboration Diagram** to depict the **Coffee Vending Machine** described. The machine includes a GUI, a coin slot for change, a delivery slot, and selection buttons for coffee and tea. (15 Marks)



- **Question 2 a):** "The most effective testing is testing conducted by an independent third party" - **Justify this statement**. (3 Marks)
- **Question 2 b):** Write a minimum level **Pseudo code to handle withdrawing money** from a customer account based on specific assumptions (authenticated customer, balance of ₹73,500, and a daily limit of ₹15,000). **Apply Path testing** to test the code. (7 Marks)
- **Question 2 c) i):** This section provides the detailed functional requirements for a **GOLD vending machine** (including card validation, PIN entry, GST calculation, and transaction buttons) to be used for the question on the following page.



- **Question 2 c) i) [Continued]:** Write sufficient number of **test cases** required to test the **Gold Vending Machine** problem using the **Black Box Testing** approach. (15 Marks)
- **Question 2 c) ii) [Alternative]:** Show the **Test Cases Design** for the **Triangle Problem** using **BVA (Boundary Value Analysis) and Robust-based testing** methods. (15 Marks)
    - The problem requires identifying the triangle type (Scalene, Isosceles, Equilateral, or Not a Triangle) based on three sides (a, b, c) in the range.
    - You must select appropriate boundary conditions to cover all possible checks for the triangle conditions.