Here is the structured question bank for **CO3 — Propositional Logic, Predicate Logic, and Inference Techniques**. This outcome focuses on modeling real-world problems and applying reasoning techniques.

### **Part A: Knowledge & Short Conceptual (3 Marks)**

1. **Chaining Strategies:** Distinguish between **forward and backward chaining** strategies in the context of inferring new information from facts.
2. **Skolemization:**
    - Mention the importance or purpose of **Skolemization** in Predicate Logic.
    - Illustrate the process of Skolemization.
3. **Reasoning Types:** Distinguish between **induction and deduction**, providing apt examples for each.
4. **Propositional Laws:** State and prove three laws of **Propositional Logic** using truth tables.

### **Part B: Intermediate Calculus & Modeling (7 Marks)**

1. **Propositional Calculus (Simplification):** Solve or simplify the following using the laws of Propositional Calculus:
    - $\neg A \Rightarrow (\neg A \Rightarrow (\neg A \wedge B))$.
    - $(\neg X \vee \neg Y) \rightarrow \neg (\neg Y \wedge X)$.
2. **Skolem Standard Form:** Derive the Skolem standard form for the following expressions:
    - $\neg (\forall x P(x) \Rightarrow \exists y \forall z Q(y, z))$.
    - $\exists x \forall y \exists z (P(x, y) \wedge Q(y, z) \wedge R(z))$.
    - $(\exists x_1) (\exists x_2) (\forall y_2) (\exists x_3) (\forall y_3) P(x_1, x_2, y_2, x_3, y_3)$.
3. **Logical Equivalence:** Use propositional rules of inference or truth tables to justify that the following pairs are logically equivalent:
    - $(r \vee p) \rightarrow (r \vee q)$ and $r \vee (p \rightarrow q)$.
    - $p \rightarrow q$ and $[(p \wedge \neg q) \rightarrow \neg p]$.
    - State **De Morgan’s laws** and prove them using truth tables.
4. **Forward Chaining Application:** Apply **forward chaining reasoning** to a simple weather forecast rule set (e.g., pressure, clouds, cyclones) to predict weather status.

### **Part C: Advanced Reasoning & Resolution (15 Marks)**

1. **Resolution Principle (Story-based Deduction):** This is a high-frequency question requiring you to model predicates, convert facts into clauses, and use the **resolution principle** to deduce a goal.
    - **Case 1 (Reindeer/Santa):** Model facts about Santa Claus, Rudolph, and children to deduce if "Sam is not a clown".
    - **Case 2 (Vehicles):** Model facts about Skoda/Figo, Bala riding vehicles, and Ramu's survival to deduce "Bala rides a Sumo".
    - **Case 3 (Food/John):** Model facts about apples/chicken/bread and Bill eating peanuts to deduce "John likes peanuts".
    - **Case 4 (Bikes):** Model facts about Pulsar/Bullet bikes and Raji riding a KTM to deduce "Susi rides a KTM".
2. **Inference Rules & Theorems:**
    - Summarize the **three rules of inference** in Propositional Logic and apply the **deduction theorem** to a situation involving a sister's birthday and working late to determine if the agent worked late.
    - Compare the features of **Conjunctive Normal Form (CNF)** and **Disjunctive Normal Form (DNF)** and deduce the CNF for a given propositional formula.
3. **Advanced Logical Proofs:** Use logical equivalences of Propositional Calculus to show that $(x \wedge y) \Rightarrow z$ is logically equivalent to $x \Rightarrow (y \Rightarrow z)$.

---

### **Exam Intelligence for CO3**

- **The Resolution Pattern:** Part C almost always provides a choice between a **Resolution Principle** problem (story-based) and a **Propositional Logic/Rules of Inference** summary.
- **Resolution Steps:** For 15-mark resolution questions, marks are typically subdivided into:
    1. Modeling the **Predicates**.
    2. Modeling the **Facts and Goal** using Predicate Calculus.
    3. Transforming facts into **Clauses**.
    4. The actual **Resolution Trace** to deduce the goal.
- **Chaining Frequency:** Forward vs. Backward chaining is a consistent "Part A" (3-mark) or "Part B" (7-mark) question used to test conceptual understanding of inference strategies.
- **Skolemization:** You should be prepared to both define the purpose of skolemization and perform it on complex nested quantifiers.