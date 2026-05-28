### **1. Summary of the Three Rules of Inference**

The three primary rules used for logical reasoning are:

- **Modus Ponens:** If it is known that $P$ is true and the implication $P \rightarrow Q$ is true, then $Q$ must be true.
- **Modus Tollens:** If it is known that $P \rightarrow Q$ is true and $Q$ is false ($\neg Q$), then $P$ must be false ($\neg P$).
- **Hypothetical Syllogism (Chain Rule):** If $P \rightarrow Q$ is true and $Q \rightarrow R$ is true, then $P \rightarrow R$ is true.

---

### **2. Application of the Deduction Theorem**

Apply the **deduction theorem** (the principle that a conclusion follows logically from a set of premises) to determine if the agent worked late.

"If it is my sister's birthday, then I always bring her flowers. Either it is my sister's birthday or I work late in office (but not both). I did not bring my sister flowers today. Therefore, did I work late in office?"
#### **A. Modeling the Predicates and Facts**

We represent the facts from the problem as follows:

- **Let $B$**: It is my sister's birthday.
- **Let $F$**: I bring her flowers.
- **Let $L$**: I work late in the office.

**Premises from the Source:**

1. **If $B$, then $F$:** $B \Rightarrow F$ ("If it is my sister's birthday, then I always bring her flowers").
2. **Either $B$ or $L$ (but not both):** $(B \vee L) \wedge \neg(B \wedge L)$ (This is the **XOR** condition: one must be true, but they cannot both be true).
3. **Fact provided:** $\neg F$ ("I did not bring my sister flowers today").

#### **B. Step-by-Step Deduction**

1. **Analyze Premise 1 and Fact 3:** We have the implication $B \Rightarrow F$ and the knowledge that $F$ is false ($\neg F$). Using the rule of **Modus Tollens**, we conclude that **$\neg B$** is true (It is **not** the sister's birthday).
2. **Analyze Premise 2:** The second premise states that exactly one of ${B, L}$ must be true. Since we have already deduced that $B$ is false ($\neg B$), the "Either/Or" condition requires that **$L$** must be true to satisfy the premise.
3. **Final Conclusion:** By applying these logical steps, we deduce that the goal is **True**.

**Result:** Yes, the agent **worked late in the office**.