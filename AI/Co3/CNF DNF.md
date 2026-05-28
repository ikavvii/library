### **Comparison of CNF and DNF**

|Feature|Conjunctive Normal Form (CNF)|Disjunctive Normal Form (DNF)|
|:--|:--|:--|
|**Structure**|A **conjunction of clauses**, where each clause is a disjunction of literals (e.g., $(A \vee B) \wedge (C \vee D)$).|A **disjunction of clauses**, where each clause is a conjunction of literals (e.g., $(A \wedge B) \vee (C \wedge D)$).|
|**Logical Logic**|Often referred to as "Product of Sums".|Often referred to as "Sum of Products".|
|**Primary Use**|Highly efficient for **automated theorem proving** and the **Resolution Principle**.|Often used to represent truth tables directly or for circuit design.|
|**Standardization**|Every propositional formula has an equivalent CNF, which is a prerequisite for resolution-based reasoning.|Every propositional formula has an equivalent DNF, though it is less used in logic-based inference engines.|

---

### **Deducing CNF for a Propositional Formula**

Deduce the **Conjunctive Normal Form (CNF)** for the formula: **$(p \wedge (q \rightarrow r)) \rightarrow s$**.

#### **Step 1: Eliminate Implications**

Using the rule $A \rightarrow B \equiv \neg A \vee B$, we convert the implications:

- Inner Implication: $(p \wedge (\neg q \vee r)) \rightarrow s$
- Outer Implication: **$\neg (p \wedge (\neg q \vee r)) \vee s$**

#### **Step 2: Move Negations Inward (De Morgan’s Laws)**

Apply negations to the terms inside the parentheses:

- $\neg p \vee \neg (\neg q \vee r) \vee s$
- Applying De Morgan’s again to the second term: **$\neg p \vee (q \wedge \neg r) \vee s$**

#### **Step 3: Rearrange for Distribution**

Group the literals outside the conjunction for easier processing:

- **$(\neg p \vee s) \vee (q \wedge \neg r)$**

#### **Step 4: Distribute $\vee$ over $\wedge$**

Apply the distributive law $A \vee (B \wedge C) \equiv (A \vee B) \wedge (A \vee C)$:

- **$((\neg p \vee s) \vee q) \wedge ((\neg p \vee s) \vee \neg r)$**

#### **Final CNF Result**

The resulting formula is now a conjunction of disjunctions: **$(\neg p \vee s \vee q) \wedge (\neg p \vee s \vee \neg r)$**

This transformed version is now in the **Skolem Standard Form** or clausal form required for further inference techniques like the resolution principle.