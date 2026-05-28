Define M-way search trees and explain how they differ from B-Trees. Specifically, describe how to determine how many keys are needed to increase or decrease a B-tree's height by one level.

Here is the definition and comparison of M-way search trees and B-trees, along with the mechanics of height changes in a B-tree.

### **1. M-way Search Trees Defined**

An **M-way search tree** is a generalization of a binary search tree where each node can have a maximum of $m$ children and $m-1$ keys. For any node with $k$ keys ($k < m$), the keys are stored in sorted order ($K_1 < K_2 < ... < K_k$), and the node has $k+1$ pointers to subtrees. These subtrees contain keys that fall within the ranges defined by the parent node's keys.

### **2. Differences Between M-way Search Trees and B-Trees**

While a B-tree is a type of M-way search tree, they differ in their structural constraints and balancing requirements:

- **Balancing:** A standard M-way search tree does not guarantee balance and can become skewed. A **B-tree** is a **balanced** M-way search tree where all leaf nodes must appear at the same level.
- **Occupancy Rules:** In a B-tree of order $m$, every node (except the root) must be at least half-full, containing at least $\lceil m/2 \rceil - 1$ keys. Standard M-way search trees have no such minimum occupancy requirement.
- **Search Efficiency:** Because B-trees maintain balance and minimum occupancy, they guarantee $O(\log_m n)$ performance for search, insertion, and deletion, whereas a standard M-way search tree could degrade to $O(n)$ in the worst case.

### **3. Determining B-Tree Height Changes**
 
 The height of a B-tree is strictly controlled by the root node.

#### **Increasing Height by One Level**

A B-tree's height **increases** only when the root node splits.

- **Mechanism:** For the height to increase, the root must already be full (containing $m-1$ keys). An insertion must occur in a leaf node that is also full, triggering a "split" that propagates upward through the tree. If this propagation reaches a full root, the root splits into two nodes, and the middle key is promoted to become a **new root**, thereby increasing the height of the entire tree by one level.
- **Calculation:** To determine how many keys are needed to increase the height, you must count how many additional keys are required to fill a leaf and every internal node on the path to the root, plus one final key to trigger the split.

#### **Decreasing Height by One Level**

A B-tree's height **decreases** only when the root node is eliminated.

- **Mechanism:** This occurs when the root contains only one key and its two children each contain the minimum number of keys ($\lceil m/2 \rceil - 1$). If a deletion occurs in one of these children that triggers a **merge**, the two children and the single key from the root are combined into a single node. The old root is then discarded, and the newly merged node becomes the new root, reducing the height by one level.
- **Calculation:** To determine how many keys must be deleted, you must identify the minimum deletions required to force the root's children to merge, eventually pulling the final key out of the root.

_**Note:** The specific mathematical derivations for the "number of keys" depend on the current occupancy of the tree shown in the exam's figure. Generally, a B-tree of height $h$ and order $m$ contains a minimum of $2 \lceil m/2 \rceil^{h-1} - 1$ keys and a maximum of $m^h - 1$ keys._