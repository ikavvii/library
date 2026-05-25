### **CO 1 UNIT 1 — SEARCH TREES**

1. **Most Important Topics**
    
    - **AVL Trees (Rotations & Construction)**
        - Probability: **100%** (Appears in all 4 papers)
        - Toughness: Medium
        - Study Time Needed: 3 Hours
        - Type: Problem-solving-heavy
        - Importance Reason: The examiner consistently asks for the construction of an AVL tree followed by specific deletions to test rotation mastery.
    - **B-Trees (Order 5 Construction/Deletion)**
        - Probability: **100%** (Appears in all 4 papers)
        - Toughness: Medium
        - Study Time Needed: 2.5 Hours
        - Type: Concept-heavy / Problem-solving
        - Importance Reason: Every paper requires creating a B-tree of order 5 and performing deletions, which tests the core rules of multi-way search trees.
    - **Tries (Dictionary/Auto-complete)**
        - Probability: **50%** (Appears in 2/4 papers)
        - Toughness: Easy
        - Study Time Needed: 1 Hour
        - Type: Memory-heavy
        - Importance Reason: Frequently used as a Part B or a "Suggest a data structure" application question.
2. **Most Probable Part C Questions**
    
    - Construct an **AVL Tree** with 10-12 elements, performing specific deletions (e.g., 26, 53, 40) and showing all rotation types.
    - Create a **B-Tree of order 5** with a sequence of 15+ keys and demonstrate the resultant tree after 3-4 deletions.
3. **Most Probable Part B Questions**
    
    - Describe the various types of **AVL rotations** with examples.
    - Explain the rules for insertion and deletion in a **B-Tree**.
    - Illustrate **Trie** operations (Insert/Delete) using a set of strings like 'code', 'cope', 'cape'.
4. **High Priority Topics**
    
    - **AVL Rotations:** Guaranteed marks; focus on the "double rotations" (LR and RL).
5. **Low Priority Topics**
    
    - **Asymptotic Notations:** Only appeared once in Part A; skip deep derivations if time is short.

---

### **CO 2 UNIT 2 — DIVIDE AND CONQUER & GREEDY METHOD**

1. **Most Important Topics**
    
    - **Merge Sort & Quick Sort (Algorithms & Analysis)**
        - Probability: **100%** (Merge sort in 3 papers, Quick sort in 1)
        - Toughness: Medium
        - Study Time Needed: 3 Hours
        - Type: Formula-heavy / Concept-heavy
        - Importance Reason: Recurrence relations and "Tree of Calls" are high-frequency examiner favorites.
    - **Prim’s Algorithm (MST Construction)**
        - Probability: **75%** (Appears in 3/4 papers)
        - Toughness: Easy
        - Study Time Needed: 1.5 Hours
        - Type: Problem-solving-heavy
        - Importance Reason: Standard numerical for Greedy method weightage.
    - **Binary Search (Recursive & Decision Tree)**
        - Probability: **75%** (Appears in 3/4 papers)
        - Toughness: Easy
        - Study Time Needed: 1 Hour
        - Type: Concept-heavy
        - Importance Reason: Used to test Divide and Conquer principles and time complexity analysis ($O(\log n)$).
2. **Most Probable Part C Questions**
    
    - Write the algorithm for **Merge Sort**, trace it with a 10-element array, and draw the **Tree of Calls**.
    - Trace **Prim’s Algorithm** on a given graph (usually 6-9 vertices) to find the Minimum Cost Spanning Tree.
3. **Most Probable Part B Questions**
    
    - Recursive **Binary Search** algorithm and its recurrence relation derivation.
    - **Huffman Coding** numerical for message compression.
    - **Knapsack Problem** using the Greedy method.
4. **High Priority Topics**
    
    - **Merge Sort Tree of Calls:** Often specifically requested for $n=14$ or $n=12$.
5. **Low Priority Topics**
    
    - **Finding Max-Min:** Rarely appears as a standalone long question.

---

### **CO 3 UNIT 3 — DYNAMIC PROGRAMMING**

1. **Most Important Topics**
    
    - **Traveling Salesman Problem (TSP)**
        - Probability: **100%** (Appears in all 4 papers)
        - Toughness: Hard
        - Study Time Needed: 4 Hours
        - Type: Problem-solving-heavy
        - Importance Reason: The centerpiece numerical for Unit 3. Usually involves a 4x4 adjacency matrix.
    - **Longest Common Subsequence (LCS)**
        - Probability: **75%** (Appears in 3/4 papers)
        - Toughness: Medium
        - Study Time Needed: 2 Hours
        - Type: Problem-solving-heavy
        - Importance Reason: High mark-to-effort ratio; steps are algorithmic and repeatable.
    - **Multistage Decision Graph**
        - Probability: **75%** (Appears in 3/4 papers)
        - Toughness: Medium
        - Study Time Needed: 2 Hours
        - Type: Problem-solving-heavy
        - Importance Reason: Focus on both "Forward" and "Backward" approaches.
2. **Most Probable Part C Questions**
    
    - Solve the **TSP** for a given 4-city adjacency matrix using DP and show all intermediate cost calculations.
    - Find the shortest path in a **Multistage Graph** from source to destination (approx. 9-12 vertices).
3. **Most Probable Part B Questions**
    
    - **String Editing / Minimum Edit Distance** between two words (e.g., "rain" to "shine" or "intention" to "execution").
    - **All-Pairs Shortest Path** (Floyd-Warshall) for a given building or network map.
4. **High Priority Topics**
    
    - **Principle of Optimality:** Often asked as a theoretical justification for why DP works for a specific problem.
5. **Low Priority Topics**
    
    - **Flow Shop Scheduling:** Not seen in recent papers despite being in the syllabus.

---

### **CO 4 UNIT 4 — BACKTRACKING & BRANCH AND BOUND**

1. **Most Important Topics**
    
    - **0/1 Knapsack (LC Branch and Bound)**
        - Probability: **100%** (Appears in all 4 papers)
        - Toughness: Hard
        - Study Time Needed: 4 Hours
        - Type: Problem-solving-heavy
        - Importance Reason: This is the primary Unit 4 numerical. Focus specifically on **LC Search** (Least Cost Search) and state space trees.
    - **Sum of Subsets (Backtracking)**
        - Probability: **75%** (Appears in 3/4 papers)
        - Toughness: Medium
        - Study Time Needed: 2 Hours
        - Type: Problem-solving-heavy
        - Importance Reason: Requires drawing a large State Space Tree, which examiners use to evaluate systematic exploration.
    - **N-Queens Problem**
        - Probability: **50%** (Appears in 2/4 papers)
        - Toughness: Medium
        - Study Time Needed: 2 Hours
        - Type: Concept-heavy / Problem-solving
        - Importance Reason: Standard backtracking example; usually asks for the 4-queens state space tree.
2. **Most Probable Part C Questions**
    
    - Solve the **0/1 Knapsack** instance using **LC Branch and Bound**, providing the state space tree and the upper/lower bounds for each node.
    - Solve the **Sum of Subsets** problem for a given set of weights and a target sum $m$, showing the generated state space tree.
3. **Most Probable Part B Questions**
    
    - Define **State Space Tree** terms: Live node, Dead node, and E-node.
    - **Graph Coloring / M-Colorability** optimization problem and its state space tree.
4. **High Priority Topics**
    
    - **State Space Tree Definitions:** Easy 5-8 marks often repeated.
5. **Low Priority Topics**
    
    - **FIFO Branch and Bound:** Papers overwhelmingly prefer **LC Search**.

---

### **Final Strategic Summary**

- **Rank by Probability:**
    1. AVL Tree Construction (100%)
    2. B-Tree Construction (100%)
    3. Traveling Salesman Problem (100%)
    4. 0/1 Knapsack via LC Branch & Bound (100%)
    5. Merge Sort Trace & Analysis (75%)
- **Safest Scoring Topics:** **Prim's Algorithm**, **LCS**, and **Tries**. They are algorithmic and hard to get wrong if the method is known.
- **Hardest Topics:** **TSP** (due to calculation volume) and **LC Branch & Bound** (due to complex bounding functions).
- **Fastest Units to Complete:** **Unit 1** (Trees) and **Unit 2** (Greedy/D&C).
- **Highest Probability-to-Effort Ratio:** **Longest Common Subsequence (LCS)** and **State Space Tree Definitions**.
- **Top 20% Topics for 80% Marks:**
    - Unit 1: AVL & B-Trees
    - Unit 2: Merge Sort & Prim's
    - Unit 3: TSP & LCS
    - Unit 4: LC Branch & Bound (Knapsack) & Sum of Subsets.
- **Numerical Probability:** You are **95% certain** to face a Traveling Salesman numerical and an LC Branch & Bound Knapsack numerical. Ensure these are practiced extensively.