**Baye’s Rule** (or Bayes' Theorem) is a fundamental principle in probability theory used to update the likelihood of an event or hypothesis based on new evidence or prior conditions. It is a key tool in Artificial Intelligence for reasoning under uncertainty, such as in medical diagnosis or industrial quality control.

### **Mathematical Representation**

Based on the application and logic presented in the sources, the mathematical representation of Baye’s Rule is:

$$P(A|B) = \frac{P(B|A) \cdot P(A)}{P(B)}$$

### **Definition of Terms**

The sources identify several key terms involved in this representation through diagnostic scenarios (such as identifying the source of a late computer or a medical condition):

- **$P(A|B)$ — Posterior Probability:** This is the probability of a hypothesis ($A$) being true given that the evidence ($B$) has occurred.
    - _Example from source:_ The probability that a child has measles **given** that they have developed rashes.
- **$P(B|A)$ — Likelihood (Conditional Probability):** This is the probability of observing the evidence ($B$) given that the hypothesis ($A$) is true.
    - _Example from source:_ The probability of observing rashes **if** a child has measles (0.95).
- **$P(A)$ — Prior Probability:** This is the initial probability of the hypothesis before any evidence is considered.
    - _Example from source:_ The general percentage of children in a neighborhood falling sick due to measles (10%).
- **$P(B)$ — Evidence (Total Probability):** This represents the total probability of the evidence occurring under all possible hypotheses. In the calculation, this is the sum of all conditional probabilities multiplied by their respective priors.
    - _Example from source:_ The total probability of any child developing rashes, whether from flu or measles ($[P(Rashes|Flu) \cdot P(Flu)] + [P(Rashes|Measles) \cdot P(Measles)]$).

By using these terms, the rule allows an agent to move from a known "cause-to-effect" probability (Likelihood) to a "predicted-cause" probability (Posterior).

Both of these high-value questions are solved using **Baye’s Rule**, which allows us to update the probability of a hypothesis (the cause) based on observed evidence (the effect).

### **Case 1: Late Delivery (Industrial Scenario)**

To determine the probability that a late computer was supplied by Company A, we use the market shares as prior probabilities and the late rates as conditional probabilities.

**1. Identify Probabilities:**

- **Prior Probabilities (Market Share):**
    - $P(A) = 0.40$
    - $P(B) = 0.30$
    - $P(C) = 0.30$
- **Conditional Probabilities (Late Delivery Rates):**
    - $P(Late|A) = 0.05$
    - $P(Late|B) = 0.03$
    - $P(Late|C) = 0.025$

**2. Step-by-Step Calculation:**

- **Numerator ($P(Late|A) \cdot P(A)$):** $0.05 \times 0.40 = \mathbf{0.02}$
- **Denominator (Total Probability of Late Delivery):**
    - $(0.40 \times 0.05) + (0.30 \times 0.03) + (0.30 \times 0.025)$
    - $0.02 + 0.009 + 0.0075 = \mathbf{0.0365}$
- **Posterior Probability ($P(A|Late)$):**
    - $0.02 / 0.0365 \approx \mathbf{0.5479}$

**Result:** If a computer arrives late, there is a **54.79% probability** that it was supplied by **Company A**.

---

### **Case 2: Medical Diagnosis (Healthcare Scenario)**

This scenario requires calculating the probability that a child has measles specifically because they have developed rashes, despite flu being much more common in the neighborhood.

**1. Identify Probabilities:**

- **Prior Probabilities (Disease Prevalence):**
    - $P(Flu) = 0.90$
    - $P(Measles) = 0.10$
- **Conditional Probabilities (Likelihood of Rashes):**
    - $P(Rashes|Measles) = 0.95$
    - $P(Rashes|Flu) = 0.08$

**2. Step-by-Step Calculation:**

- **Numerator ($P(Rashes|Measles) \cdot P(Measles)$):** $0.95 \times 0.10 = \mathbf{0.095}$
- **Denominator (Total Probability of Rashes):**
    - $(P(Rashes|Measles) \cdot P(Measles)) + (P(Rashes|Flu) \cdot P(Flu))$
    - $(0.95 \times 0.10) + (0.08 \times 0.90)$
    - $0.095 + 0.072 = \mathbf{0.167}$
- **Posterior Probability ($P(Measles|Rashes)$):**
    - $0.095 / 0.167 \approx \mathbf{0.5689}$

**Result:** If a child develops rashes, the probability that the child has **measles is 56.89%**. Even though flu is nine times more common, the high correlation between rashes and measles makes it the more likely diagnosis once that specific symptom is observed.

