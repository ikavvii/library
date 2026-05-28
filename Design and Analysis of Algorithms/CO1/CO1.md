**Course Outcome 1 (CO1)**: _"Efficiently use balanced binary and multi-way search trees to store and retrieve data"_.

---

### **Part A: Fundamental Concepts & Theory (5 Marks)**

1. **Asymptotic Notations:** Define Omega ($\Omega$), Theta ($\Theta$), and Big Oh ($O$) notations. Explain the significance of these notations in algorithmic analysis.
2. **B-Tree Foundations:** Define a B-Tree of order $m$ and list the fundamental rules for its insertion and deletion.
3. **AVL Tree Significance:** Explain the significance of AVL trees over standard Binary Search Trees (BST) in performing insertion and deletion operations.
4. **Tree Comparisons:** Define M-way search trees and explain how they differ from B-Trees. Specifically, describe how to determine how many keys are needed to increase or decrease a B-tree's height by one level.
5. **Application Identification:** Suggest a suitable data structure for building a search engine with an "auto-complete" feature. Briefly describe how insertion, deletion, and searching are performed in it.

---

### **Part B: Multi-Way Search Trees & Tries (8 Marks)**

1. **B-Tree Construction (Order 5):** Create a B-Tree of order 5 by inserting the following sequence: 76, 19, 12, 9, 95, 83, 72, 61, 43, 40, 55, 18, 14, 17, 50, 28, and 20. Show the resultant tree after deleting 18, 40, and 55.
2. **B-Tree Alternative Dataset:** Construct a B-Tree of order 5 with keys: 48, 81, 125, 43, 93, 4, 8, 10, 11, 31, 70, 92, 39, 82, 127, 28, 38, and 143. Demonstrate the tree after deleting 92 and 38.
3. **B+ Tree Operations:** Create a B+ tree of order 5 by inserting: 16, 18, 14, 20, 12, 22, 10, 24, 8, 6, 15, 11, 26, and 30. Show the tree after deleting 16, 8, and 15.
4. **Trie Construction:** Create a Trie with the words: _file, fill, car, cat, rose, star, stare_. Illustrate the Trie after inserting _care_ and deleting _star_ and _fill_.
5. **Trie Dictionary Application:** Insert the following words into a dictionary Trie: _desk, deck, dog, dock, dogs, code, cope,_ and _cape_. Show the deletions of _dogs_ and _cope_.

---

### **Part C: Balanced Search Trees - AVL (12 Marks)**

1. **Comprehensive AVL Construction:** Define an AVL tree and describe various types of rotations (LL, RR, LR, RL). Construct an AVL tree using the elements: 50, 53, 58, 40, 34, 30, 32, 65, 60, 25, and 26. Delete keys 26, 53, and 40, showing the tree at each stage.
2. **AVL Rotations & Balance Factors:** Construct an AVL tree with the following keys: 22, 68, 12, 79, 30, 46, 103, 258, 55, and 102. After insertion, delete 46, 68, 22, and 102. You must show intermediate steps, balance factors, and indicate the specific type of rotation used in each step.
3. **AVL Depth & Deletion:** What is the height of an AVL tree with $n$ nodes? Construct an AVL tree from an empty tree for the keys: 15, 19, 21, 13, 10, 23, 22, 5, and 7. Successively delete 22, 21, 13, and 10.
4. **Complex AVL Construction:** Create an AVL tree by inserting the following elements in order: 15, 20, 24, 10, 13, 7, 30, 36, 45, 54, 8, 11, 12, and 25. Delete 10, 30, and 12 and show the final resultant tree.

---

### **Strategic Preparation Tips for CO1**

- **Priority 1 (Part C):** Master **AVL Rotations**. This is a guaranteed 12-mark question. You must be able to label every rotation type and calculate balance factors ($-1, 0, +1$) accurately.
- **Priority 2 (Part B):** Master **B-Tree of Order 5**. This appears in nearly every paper. Ensure you understand the "split" and "merge" rules for order 5 specifically.
- **Safety Topic:** **Tries** are the most common "application" question. If the question asks for a "suitable data structure" for strings or auto-complete, the answer is always a Trie.