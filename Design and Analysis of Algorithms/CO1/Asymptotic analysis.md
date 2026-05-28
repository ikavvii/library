### **Definitions of Asymptotic Notations**

- **Big Oh ($O$): Upper Bound** Describes the **worst-case** scenario for an algorithm. It provides an asymptotic upper bound, ensuring that the algorithm's growth rate will not exceed a certain level.
    - _Mathematical Definition:_ $f(n) = O(g(n))$ if there exist positive constants $c$ and $n_0$ such that $0 \leq f(n) \leq c \cdot g(n)$ for all $n \geq n_0$.
- **Omega ($\Omega$): Lower Bound** Describes the **best-case** scenario. It provides an asymptotic lower bound, ensuring that an algorithm will take at least a certain amount of time for all input sizes beyond a threshold.
    - _Mathematical Definition:_ $f(n) = \Omega(g(n))$ if there exist positive constants $c$ and $n_0$ such that $0 \leq c \cdot g(n) \leq f(n)$ for all $n \geq n_0$.
- **Theta ($\Theta$): Tight Bound** Describes the **average-case** or precise behavior of an algorithm when the upper and lower bounds grow at the same rate.
    - _Mathematical Definition:_ $f(n) = \Theta(g(n))$ if there exist positive constants $c_1, c_2,$ and $n_0$ such that $c_1 \cdot g(n) \leq f(n) \leq c_2 \cdot g(n)$ for all $n \geq n_0$.

---

### **Significance in Algorithmic Analysis**

The significance of these notations lies in their ability to:

1. **Characterize Growth Rates:** They allow analysts to focus on how the execution time or space requirements of an algorithm increase as the input size ($n$) grows toward infinity, rather than focusing on exact step counts.
2. **Machine Independence:** They provide a way to compare the efficiency of algorithms (like **Merge Sort** vs. **Quick Sort**) regardless of the specific hardware or software environment used to run them.
3. **Performance Classification:** The sources frequently use these notations to classify algorithm performance. For example, **Merge Sort** is consistently identified as having a complexity of **$O(n \log n)$** in both its best and worst cases, while **Binary Search** is associated with **$O(\log n)$** complexity.
4. **Worst-Case Guarantees:** By defining the **Big Oh** notation, examiners test your ability to provide upper-bound guarantees, which is critical for real-world application reliability where "worst-case" performance must be managed.