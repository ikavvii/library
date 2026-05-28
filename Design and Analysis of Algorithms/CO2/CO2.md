**Course Outcome 2 (CO2):** _"Formulate algorithms to solve complex problems using divide and conquer and greedy method of algorithm design"_.

---

### **Part A: Theoretical Foundations & Control Abstractions (5 Marks)**

1. **Control Abstraction:** Write the control abstraction for the **Divide and Conquer** method of algorithm design.
2. **Greedy Principles:** Describe the Greedy approach to solve an optimization problem. Write the pseudo-code describing the **subset paradigm**.
3. **Complexity Analysis:** State the recurrence relation for the best and worst cases of **Merge Sort** and indicate their respective time complexities.
4. **Decision Trees:** Explain the concept of a **binary decision tree** for searching and draw one for $n=12$ elements.
5. **Algorithm Design:** Write an algorithm to find the **second maximum** integer in an array of $N$ integers without duplicates.
6. **Greedy vs. D&C:** Explain how the greedy principle is specifically used in Prim's algorithm for finding a Minimum Cost Spanning Tree.

---

### **Part B: Greedy Method Applications (8 Marks)**

1. **Huffman Coding (Compression):** A communication engineer is developing a compression algorithm. Given the character frequencies (A:40, P:9, Q:2, L:10, E:16, S:13), find the **Huffman codes**. Illustrate how the message "APPLE" would be encoded and decoded.
2. **Fractional Knapsack:** Solve the following instance of the Knapsack problem using the **Greedy method**: $n=5, m=60$. Weights $w={5, 10, 20, 30, 40}$ and profits $p={30, 20, 100, 90, 160}$. Identify which items maximize profit.
3. **Optimal Merge Patterns:** Find the optimal way to merge 10 files with lengths: 25, 29, 9, 2, 81, 50, 89, 32, 1, and 8. Describe the algorithm design paradigm used.
4. **Optimal Storage on Tapes:** Find an optimal placement for 9 programs of lengths ${12, 13, 10, 8, 7, 3, 20, 2, 5}$ on four tapes (T0, T1, T2, T3). Provide the algorithm.
5. **Binary Search Trace:** Write a recursive algorithm for **Binary Search**. State how Divide and Conquer is used, give the recurrence relation, and find the time complexity.

---

### **Part C: Advanced Problem Solving & Tracing (12 Marks)**

1. **Merge Sort Analysis:** Write the algorithm for **Merge Sort**. Trace the algorithm to sort the numbers ${31, 28, 17, 65, 35, 42, 86, 25, 45, 52}$. Additionally, draw the **tree of calls** for `mergeSort()`.
2. **Quick Sort Performance:** Write the algorithm for **Quick Sort**. Describe the best and worst-case recurrence relations. Illustrate the algorithm with a sample input of 10 elements, showing all intermediate passes.   
3. **Prim’s Algorithm (MST):** Write **Prim’s algorithm** to construct a Minimum Cost Spanning Tree. Trace the algorithm for a graph with 9 vertices (villages) to find the minimum length of cable needed for connection.
4. **Single Source Shortest Path (Dijkstra):** Write an algorithm to find the shortest distance from a starting vertex to all other vertices. Trace the algorithm for a given graph instance (e.g., a delivery map) to find the shortest paths from vertex 1.

---

### **High-Probability "Safe" Topics for CO2**

- **Numerical Guarantee:** You will almost certainly face a **Merge Sort** trace with a "tree of calls" and a **Prim's Algorithm** graph numerical.
- **Recursive Analysis:** Be prepared to write the recurrence relation $T(n) = 2T(n/2) + cn$ for Merge Sort and solve it using the Master Theorem or back-substitution to prove $O(n \log n)$.
- **Standard Tracing:** **Binary Search** questions often ask for a **Binary Decision Tree** for a specific $n$ (usually 12 or 14). Ensure you can draw these systematically.