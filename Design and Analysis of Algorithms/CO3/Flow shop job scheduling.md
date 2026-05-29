**flow shop job scheduling** is a problem of finding an optimal sequence to process $n$ jobs through $m$ processors.

### 1. Problem Definition

In a general flow shop, there are $n$ jobs, each requiring $m$ tasks ($T_{1i}, T_{2i}, \dots, T_{mi}$) to be performed in a specific order.

- **Processors:** Task $T_{ji}$ must be performed on processor $P_j$ for a duration $t_{ji}$.
- **Constraint:** For any job $i$, task $T_{ji}$ (where $j > 1$) cannot start until the preceding task $T_{j-1,i}$ is completed.
- **Objective:** Find an **Optimal Finish Time (OFT)** schedule, which is a nonpreemptive sequence $S$ that minimizes the total completion time $F(S) = \max_{1 \le i \le n} {f_i(S)}$, where $f_i(S)$ is the finish time of job $i$.

### 2. Two-Processor Flow Shop ($m=2$)

The Horowitz book focuses on the special case where $m=2$, which can be solved efficiently using **dynamic programming** and a greedy rule known as **Johnson's Rule**. For $m=2$, we use $a_i$ to represent the time for job $i$ on processor $P_1$ and $b_i$ for its time on $P_2$.

#### **The Scheduling Rule (Johnson's Rule):**

To achieve an optimal schedule, follow these steps:

1. **Sort** all $a_i$ and $b_j$ values into a single nondecreasing order.
2. Iterate through this sorted list. For the next number in the sequence:
    - If it is $a_j$ and job $j$ has not been scheduled, place job $j$ at the **leftmost** available spot.
    - If it is $b_j$ and job $j$ has not been scheduled, place job $j$ at the **rightmost** available spot.
    - If job $j$ is already scheduled, skip to the next number.

### 3. Solving the Dynamic Assignment Instance

The assignment asks for the optimal schedule for:

- $(a_1, a_2, a_3, a_4, a_5) = (4, 5, 9, 11, 14)$
- $(b_1, b_2, b_3, b_4, b_5) = (7, 3, 10, 16, 12)$

**Step 1: Sorted sequence of $a$'s and $b$'s:** $b_2(3), a_1(4), a_2(5), b_1(7), a_3(9), b_3(10), a_4(11), b_5(12), a_5(14), b_4(16)$.

**Step 2: Assign positions:**

1. Smallest is **$b_2 = 3$**: Place job 2 at the rightmost spot. Sequence: $(_, _, _, _, \mathbf{2})$.
2. Next is **$a_1 = 4$**: Place job 1 at the leftmost spot. Sequence: $(\mathbf{1}, _, _, _, 2)$.
3. Next is **$a_2 = 5$**: Job 2 is already scheduled. Skip.
4. Next is **$b_1 = 7$**: Job 1 is already scheduled. Skip.
5. Next is **$a_3 = 9$**: Place job 3 at the leftmost available spot. Sequence: $(1, \mathbf{3}, _, _, 2)$.
6. Next is **$b_3 = 10$**: Job 3 is already scheduled. Skip.
7. Next is **$a_4 = 11$**: Place job 4 at the leftmost available spot. Sequence: $(1, 3, \mathbf{4}, _, 2)$.
8. Next is **$b_5 = 12$**: Place job 5 at the rightmost available spot. Sequence: $(1, 3, 4, \mathbf{5}, 2)$.

**Optimal Schedule:** **$(1, 3, 4, 5, 2)$**.

### 4. Complexity and Limitations

- **Time Complexity:** The scheduling rule can be implemented in **$O(n \log n)$** time, primarily due to the initial sorting step.
- **General Case ($m > 2$):** Obtaining OFT schedules for more than two processors is **NP-hard**. In these cases, the problem is often approached using approximation algorithms like the Longest Processing Time (LPT) rule.

Would you like me to create a quiz to test your understanding of how to apply Johnson's Rule to different job sequencing instances?