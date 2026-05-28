**Consider the following facts:**

- **Pulsar** is a bike.
- **Bullett** is a bike.
- **Bala** rides all kinds of bikes.
- **Raji** rides a **KTM** and is still alive after riding.
- Anything anyone rides and is alive after riding, is a bike.
- **Susi** rides everything **Bala** rides.

**Tasks:**

1. **Translate** the facts given into **Predicate Calculus statements**.
2. **Convert** these statements into **clauses**.
3. **Deduce the goal** that "**Susi rides a KTM**" using the **resolution principle**, providing a trace of the working in clear steps.

To deduce the goal that **"Susi rides a KTM"** using the **Resolution Principle**, we follow a systematic process of modeling predicates, translating facts into Predicate Calculus, converting them into clauses, and performing the resolution trace.

### **1. Model the Predicates**

We define the following predicates to represent the entities and relationships in the problem:

- $Bike(x)$: $x$ is a bike.
- $Rides(p, x)$: Person $p$ rides $x$.
- $Alive(p)$: Person $p$ is alive after riding.

### **2. Model the Facts and Goal (Predicate Calculus)**

Based on the real-world situation provided in the sources, we represent the facts as follows:

1. **F1:** $Bike(Pulsar)$
2. **F2:** $Bike(Bullet)$
3. **F3:** $\forall x (Bike(x) \Rightarrow Rides(Bala, x))$ (Bala rides all kinds of bikes).
4. **F4:** $Rides(Raji, KTM) \wedge Alive(Raji)$ (Raji rides a KTM and is still alive).
5. **F5:** $\forall p \forall x ((Rides(p, x) \wedge Alive(p)) \Rightarrow Bike(x))$ (Anything anyone rides and is alive after is a bike).
6. **F6:** $\forall x (Rides(Bala, x) \Rightarrow Rides(Susi, x))$ (Susi rides everything Bala rides).

- **Goal:** $Rides(Susi, KTM)$

### **3. Transform Facts into Clauses (Clausal Form)**

To apply resolution, we convert the formulas into clauses (disjunctions of literals) and **negate the goal**:

- **C1:** $Bike(Pulsar)$
- **C2:** $Bike(Bullet)$
- **C3:** $\neg Bike(x) \vee Rides(Bala, x)$ (From F3)
- **C4a:** $Rides(Raji, KTM)$ (From F4)
- **C4b:** $Alive(Raji)$ (From F4)
- **C5:** $\neg Rides(p, y) \vee \neg Alive(p) \vee Bike(y)$ (From F5)
- **C6:** $\neg Rides(Bala, z) \vee Rides(Susi, z)$ (From F6)
- **C7 (Negated Goal):** $\neg Rides(Susi, KTM)$

### **4. Resolution Trace**

We now resolve the clauses to find a contradiction (the empty clause $\square$), proving the goal is true:

|Step|Resolve Clause A|Resolve Clause B|Substitution|Resulting Clause|
|:--|:--|:--|:--|:--|
|**1**|**C7** ($\neg Rides(Susi, KTM)$)|**C6** ($\neg Rides(Bala, z) \vee Rides(Susi, z)$)|${z/KTM}$|**C8:** $\neg Rides(Bala, KTM)$|
|**2**|**C8** ($\neg Rides(Bala, KTM)$)|**C3** ($\neg Bike(x) \vee Rides(Bala, x)$)|${x/KTM}$|**C9:** $\neg Bike(KTM)$|
|**3**|**C9** ($\neg Bike(KTM)$)|**C5** ($\neg Rides(p, y) \vee \neg Alive(p) \vee Bike(y)$)|${y/KTM}$|**C10:** $\neg Rides(p, KTM) \vee \neg Alive(p)$|
|**4**|**C10** ($\neg Rides(p, KTM) \dots$)|**C4a** ($Rides(Raji, KTM)$)|${p/Raji}$|**C11:** $\neg Alive(Raji)$|
|**5**|**C11** ($\neg Alive(Raji)$)|**C4b** ($Alive(Raji)$)|None|**$\square$ (Contradiction)**|

**Conclusion:** Since we reached a contradiction by assuming the goal was false, we have successfully deduced that **"Susi rides a KTM"**.