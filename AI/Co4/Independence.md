To determine if Event ‘P’ and Event ‘Q’ are independent, we calculate their individual probabilities and the probability of their intersection. Two events are **independent** if the probability of both occurring is equal to the product of their individual probabilities: $P(P \cap Q) = P(P) \cdot P(Q)$.

### **1. Identify the Sample Space**

When rolling a pair of dice, there are $6 \times 6 = 36$ equally likely outcomes.

### **2. Calculate Probability of Event ‘P’ (Even Sum)**

A sum is even if both dice show even numbers or both show odd numbers.

- **Outcomes:** (1,1), (1,3), (1,5), (2,2), (2,4), (2,6), (3,1), (3,3), (3,5), (4,2), (4,4), (4,6), (5,1), (5,3), (5,5), (6,2), (6,4), (6,6).
- **Count:** 18
- **$P(P) = 18/36 = 1/2 = \mathbf{0.5}$**

### **3. Calculate Probability of Event ‘Q’ (Both Numbers > 4)**

For both numbers to be greater than 4, each die must show either a 5 or a 6.

- **Outcomes:** (5,5), (5,6), (6,5), (6,6).
- **Count:** 4
- **$P(Q) = 4/36 = 1/9 \approx \mathbf{0.111}$**

### **4. Calculate Probability of the Intersection ($P \cap Q$)**

We find the outcomes where the sum is even **and** both numbers are greater than 4.

- From the set of Event Q:
    - (5,5): Sum = 10 (**Even**)
    - (5,6): Sum = 11 (Odd)
    - (6,5): Sum = 11 (Odd)
    - (6,6): Sum = 12 (**Even**)
- **Outcomes:** (5,5), (6,6).
- **Count:** 2
- **$P(P \cap Q) = 2/36 = \mathbf{1/18} \approx \mathbf{0.0556}$**

### **5. Justification of Independence**

We compare the intersection probability with the product of the individual probabilities:

- $P(P) \cdot P(Q) = (1/2) \cdot (1/9) = \mathbf{1/18}$
- $P(P \cap Q) = \mathbf{1/18}$

**Conclusion:** Since $P(P \cap Q) = P(P) \cdot P(Q)$, the two events are **independent**. Knowing that the sum is even provides no additional information about the likelihood that both numbers are greater than 4, and vice-versa.