To show that **$(x \wedge y) \Rightarrow z$** is logically equivalent to **$x \Rightarrow (y \Rightarrow z)$** (a principle often referred to in logic as the **Exportation Law**), we apply the standard laws of **Propositional Calculus**

### **Step-by-Step Logical Derivation**

We will transform both sides of the expression into the same logical form to prove their equivalence.

#### **1. Transform the Left-Hand Side (LHS): $(x \wedge y) \Rightarrow z$**

- **Apply the Implication Law:** $p \Rightarrow q \equiv \neg p \vee q$.
    - $\neg (x \wedge y) \vee z$
- **Apply De Morgan’s Law:** $\neg(p \wedge q) \equiv \neg p \vee \neg q$.
    - **$(\neg x \vee \neg y) \vee z$**

#### **2. Transform the Right-Hand Side (RHS): $x \Rightarrow (y \Rightarrow z)$**

- **Apply the Implication Law** to the inner expression $(y \Rightarrow z)$:
    - $x \Rightarrow (\neg y \vee z)$
- **Apply the Implication Law** to the outer expression:
    - $\neg x \vee (\neg y \vee z)$
- **Apply the Associative Law:** $(p \vee q) \vee r \equiv p \vee (q \vee r)$.
    - **$\neg x \vee \neg y \vee z$**

### **Conclusion**

Since both the LHS and the RHS simplify to the exact same logical expression (**$\neg x \vee \neg y \vee z$**), the two statements are **logically equivalent**.

This equivalence demonstrates that a condition requiring two simultaneous factors ($x$ and $y$) to lead to a result ($z$) is logically identical to a nested condition where if $x$ is true, then $y$ leading to $z$ must also be true.