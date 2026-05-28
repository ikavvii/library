To find the **optimal placement** for programs on multiple tapes, A **Greedy approach** is used where the primary goal is to minimize the mean retrieval time (MRT). 

### **Algorithm: Optimal Storage on Tapes**

The strategy involves sorting the programs in non-decreasing order of their lengths and distributing them across the available tapes in a round-robin (cyclic) fashion.

**Algorithm `OptimalStorage(n, m)`**

1. **Sort** the $n$ programs in non-decreasing order of their lengths such that: $l_1 \leq l_2 \leq \dots \leq l_n$.
2. **Initialize** tape index $j = 0$.
3. **Iterate** through the sorted programs $i = 1$ to $n$:
    - Assign program $i$ to tape $T_j$.
    - Update tape index: $j = (j + 1) \pmod m$.

---

### **Optimal Placement for the Given Instance**

**Input Data:**

- **Programs ($n=9$):** ${12, 13, 10, 8, 7, 3, 20, 2, 5}$
- **Tapes ($m=4$):** ${T_0, T_1, T_2, T_3}$

#### **Step 1: Sort Programs in Non-Decreasing Order**

The lengths in ascending order are: **${2, 3, 5, 7, 8, 10, 12, 13, 20}$**

#### **Step 2: Distribute Programs Across 4 Tapes (Round-Robin)**

|Program Length|Assigned Tape|
|:--|:--|
|2|**$T_0$**|
|3|**$T_1$**|
|5|**$T_2$**|
|7|**$T_3$**|
|8|**$T_0$**|
|10|**$T_1$**|
|12|**$T_2$**|
|13|**$T_3$**|
|20|**$T_0$**|

---

### **Final Optimal Tape Contents**

- **Tape $T_0$:** ${2, 8, 20}$
- **Tape $T_1$:** ${3, 10}$
- **Tape $T_2$:** ${5, 12}$
- **Tape $T_3$:** ${7, 13}$

By placing the shortest programs at the beginning of each tape, the average time required to retrieve any program is minimized, achieving the **optimal storage pattern** required by the greedy method.

To calculate the **Mean Retrieval Time (MRT)** for the **Optimal Storage on Tapes** problem—you must determine the average time required to access all programs stored on the tapes.

### **1. The Formula**

The retrieval time for a specific program is the sum of the lengths of that program and all programs stored before it on the same tape. The **MRT** is the average of these retrieval times for all $n$ programs: $$MRT = \frac{1}{n} \sum_{i=1}^{n} (\text{Retrieval Time for Program } i)$$

### **2. Calculation Steps**

Using the dataset from the **September 2024** paper (9 programs of lengths ${2, 3, 5, 7, 8, 10, 12, 13, 20}$ on 4 tapes), follow these steps:

- **Step 1: Organize the Tapes** Assign the sorted programs to tapes in a round-robin fashion:
    
    - **Tape 0:** ${2, 8, 20}$
    - **Tape 1:** ${3, 10}$
    - **Tape 2:** ${5, 12}$
    - **Tape 3:** ${7, 13}$
- **Step 2: Calculate Individual Retrieval Times** For each tape, the retrieval time for the $k$-th program is the cumulative sum of lengths:
    
    - **Tape 0:**
        - Prog 1 (2): **2**
        - Prog 2 (8): $2 + 8 = \mathbf{10}$
        - Prog 3 (20): $2 + 8 + 20 = \mathbf{30}$
    - **Tape 1:**
        - Prog 1 (3): **3**
        - Prog 2 (10): $3 + 10 = \mathbf{13}$
    - **Tape 2:**
        - Prog 1 (5): **5**
        - Prog 2 (12): $5 + 12 = \mathbf{17}$
    - **Tape 3:**
        - Prog 1 (7): **7**
        - Prog 2 (13): $7 + 13 = \mathbf{20}$
- **Step 3: Sum and Average** Add all the individual retrieval times and divide by the total number of programs ($n=9$):
    
    - **Total Time** = $2 + 10 + 30 + 3 + 13 + 5 + 17 + 7 + 20 = \mathbf{107}$
    - **MRT** = $107 / 9 = \mathbf{11.88}$

### **Summary of Logic**

The goal of the **Greedy approach** in this problem is to minimize the MRT by placing the **shortest programs first** on each tape. This ensures that the smallest lengths are added to the cumulative retrieval times of as many subsequent programs as possible, keeping the total sum (and thus the average) as low as possible.
