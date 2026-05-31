This question bank for **CO2 — Enterprise Data Enabling** is compiled based on an analysis of the provided semester papers (June 2024, June 2025, Aug/Sept 2024, and Aug/Sept 2025).

### **Part A: Knowledge & Definitions (3 Marks)**

1. **SQL Injection:** What is SQL injection? Describe its impact on enterprise data and the primary prevention solution provided by JDBC APIs.
2. **Prepared Statements:** Define a `PreparedStatement` in JDBC and explain how it effectively mitigates SQL injection risks compared to a standard `Statement`.
3. **JDBC Methods:** Differentiate between `executeQuery()` and `executeUpdate()` methods in JDBC, providing a simple example of when to use each.
4. **NoSQL Foundations:** Define NoSQL and mention its primary role in handling unstructured or high-velocity data in modern enterprise applications.
5. **SQL API Comparison:** Briefly compare and contrast the CLI form SQL API and the SLI form Embedded SQL API.

### **Part B: Conceptual & Intermediate Analysis (10 Marks)**

1. **NoSQL vs. SQL Role:** Explain the necessity for **NoSQL in Enterprise Applications**. Compare and contrast the roles of SQL and NoSQL in the data-enabling aspects of large-scale systems.
2. **JDBC Method Matrix:** Compare the `execute()`, `executeUpdate()`, and `executeQuery()` methods in terms of their functionality, return types, and specific enterprise use cases.
3. **Data Architecture Longevity:** Discuss the **JDBC application architecture** and provide a defense of how JDBC increases the longevity of enterprise database application code compared to embedded forms like SQLJ.
4. **NoSQL Case Study:** A retail company wants to move from relational databases to NoSQL for handling customer transactions and personalized recommendations. **Justify the use of NoSQL** for this specific scenario.

### **Part C: Advanced Problem Solving & Tracing (12 Marks)**

1. **High-Traffic Performance:**
    - Discuss the advanced JDBC features **"Connection Pooling"** and **"Distributed Transactions"**.
    - Emphasize their implementation in a high-traffic e-commerce context (e.g., handling thousands of concurrent requests and multi-step orders involving stock, payment, and invoices).
2. **Security Redesign & Logic:**
    - Demonstrate how a standard `Statement` object is vulnerable to SQL injection during a login process.
    - **Redesign the login process** using `PreparedStatement` to ensure security.
3. **Practical JDBC Programming:**
    - Write a complete Java program/snippet to connect to a database using specific parameters (Driver, DBURL, Username, Password).
    - Write the specific **JDBC statements** required to retrieve data based on complex conditions (e.g., retrieving faculty members whose courses have >70% students with marks >60%).
4. **Data Access Layer (DAL) Design:**
    - Design the **Data Access Layer** for a banking system required to handle account creation, deposits, and withdrawals.
    - Explain the implementation of **CRUD operations** using JDBC with proper architectural justification.

---

### **Exam Strategy for CO2**

- **The "Guaranteed" Question:** Be prepared to explain **SQL Injection and its prevention via PreparedStatement**. Every paper analyzes this security aspect in either Part A or Part C.
- **The "Easy Wins" Topic:** Master the comparison between **SQL and NoSQL**. This is a recurring 5–10 mark topic that relies on clear theoretical differences (Schema-based vs. Schema-less, Scalability, etc.).
- **Coding Precision:** When writing JDBC code, the examiners look for the correct sequence of object creation: **Connection $\rightarrow$ Statement/PreparedStatement $\rightarrow$ ResultSet**. Always mention the importance of closing these objects or using connection pooling.
- **Advanced Features:** Focus on **Connection Pooling**. It is the standard answer for scenarios involving "high-traffic," "millions of users," or "scalability" in the data layer.

### **Frequency Analysis Table**

|Topic|Frequency in Papers|Typical Marks|
|:--|:--|:--|
|**SQL Injection / PreparedStatement**|100% (4/4 papers)|3–12|
|**SQL vs. NoSQL Role/Comparison**|100% (4/4 papers)|5–10|
|**Connection Pooling & Distributed Transactions**|75% (3/4 papers)|6–12|
|**JDBC Architecture vs. SQLJ**|50% (2/4 papers)|5–6|
|**JDBC Method Comparison (executeQuery, etc.)**|75% (3/4 papers)|3–10|
|**Practical JDBC Coding (CRUD/Queries)**|50% (2/4 papers)|6–12|

### CO 2 UNIT 2 — Enterprise Data Enabling

**1. Most Important Topics**

- **NoSQL in Enterprise Applications**
    - Probability: **98%**
    - Toughness: Easy
    - Study Time Needed: 1.5 Hours
    - Type: Concept-heavy
    - Importance Reason: This is a staple question appearing in every paper, either as a comparison between SQL and NoSQL or as a justification for a specific enterprise scenario (e.g., e-commerce, retail).
- **SQL Injection & Prepared Statements**
    - Probability: **95%**
    - Toughness: Medium
    - Study Time Needed: 2 Hours
    - Type: Concept-heavy / Problem-solving-heavy
    - Importance Reason: Appears consistently in Part A (3 marks) or Part C (6–12 marks). Candidates are often asked to explain the risk and provide a code-based solution using `PreparedStatement`.
- **Advanced JDBC (Connection Pooling & Distributed Transactions)**
    - Probability: **90%**
    - Toughness: Medium
    - Study Time Needed: 2 Hours
    - Type: Concept-heavy / Formula-heavy (logic)
    - Importance Reason: Frequently asked in Part C, specifically regarding high-traffic scenarios and multi-step transaction handling (e.g., e-commerce orders).
- **JDBC Application Architecture vs. Embedded SQL (SQLJ)**
    - Probability: **85%**
    - Toughness: Medium
    - Study Time Needed: 2 Hours
    - Type: Concept-heavy
    - Importance Reason: Multiple papers ask to defend why JDBC increases the longevity of code compared to embedded forms like SQLJ and requires sketching the architecture.

**2. Most Probable Part C Questions (12 Marks)**

- **JDBC Features Case Study:** Discuss Connection Pooling and Distributed Transactions in the context of a high-traffic e-commerce platform.
- **Security Redesign:** Demonstrate how a standard `Statement` object is vulnerable to SQL injection and redesign the login/query process using `PreparedStatement`.
- **Data Access Design:** Design the Data Access Layer (DAL) for a specific scenario (e.g., Bank CRUD operations or Student Portal) using JDBC, providing justifications for object choices.
- **Database Migration:** Justify the shift from Relational Databases to NoSQL for an enterprise application (e.g., a retail company handling transactions and recommendations).

**3. Most Probable Part B Questions (10 Marks)**

- **Method Comparison:** Compare and contrast `execute()`, `executeUpdate()`, and `executeQuery()` in terms of functionality, return types, and use cases.
- **NoSQL vs. SQL Role:** Explain the need for NoSQL and compare the roles of SQL and NoSQL in the data-enabling aspects of enterprise applications.
- **Architecture Analysis:** Compare JDBC application architecture with embedded SQL forms like SQLJ, focusing on modularity and longevity.

**4. High Priority Topics**

- **PreparedStatement Implementation:** High probability of being asked as a 3-mark theory question OR a 6-mark coding task.
- **Connection Pooling Logic:** Essential for scoring in Part C, as it is the standard answer for "handling concurrent requests".

**5. Low Priority Topics**

- Static SQL vs. Dynamic SQL (Appeared once, usually secondary to JDBC specific questions).
- CLI SQL API vs. SLI Embedded SQL API.

---

### Final Output Requirements

- **Ranked Topics by Probability:**
    1. NoSQL Justification/SQL vs. NoSQL (98%)
    2. SQL Injection prevention via PreparedStatement (95%)
    3. Connection Pooling & Distributed Transactions (90%)
    4. JDBC Architecture vs. SQLJ (85%)
    5. JDBC Methods (executeQuery vs. executeUpdate) (85%)
- **Safest Scoring Topics:** Comparison of SQL vs. NoSQL and the definition/impact of SQL Injection. These are pure theory and appear in almost every paper.
- **Hardest Topics:** Writing a full Java program to connect to a database and retrieve specific data (e.g., Student marks filtering) due to syntax requirements.
- **Fastest Units to Complete:** **CO2** is relatively fast because the "Data Enabling" concepts are finite (JDBC, SQL, NoSQL) compared to the vast frameworks in CO3.
- **Highest Probability-to-Effort Ratio:** **NoSQL Advantages**. Understanding the four types of NoSQL and their use cases takes 30 minutes and is nearly guaranteed to appear.
- **Top 20% Topics that can score 80% marks:**
    - NoSQL vs. SQL comparison.
    - PreparedStatement for SQL Injection prevention.
    - Connection Pooling mechanism.
    - JDBC Architecture flow.
- **Numerical/Coding Probability:** **40%**. There is a significant chance (at least one "OR" option in Part C) that you will be asked to write JDBC code snippets or a full CRUD method.