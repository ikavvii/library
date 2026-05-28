>The rules for splitting and merging are governed by the tree's order ($m$) and the requirement to maintain balance.

### **1. Rules for Node Capacity**

For a B+ tree of order $m$ (where $m=5$ in source):

- **Maximum Keys:** A node can hold at most **$m - 1$** keys (e.g., 4 keys for order 5).
- **Minimum Keys:** Every node (except the root) must contain at least **$\lceil m/2 \rceil - 1$** keys (e.g., 2 keys for order 5).

---

### **2. Rules for Splits (Insertion)**

A split occurs when an insertion causes a node to exceed its maximum capacity of $m-1$ keys.

- **Leaf Node Split:**
    - When a leaf node overflows, it is split into two leaf nodes.
    - The first $\lceil m/2 \rceil$ elements stay in the left leaf, and the rest move to the right.
    - The middle key (the smallest value of the right leaf) is **copied** into the parent index node to act as a separator.
- **Internal Node Split:**
    - When an internal (index) node overflows, it is split into two.
    - The middle key is **moved** (promoted) up to the parent node, rather than copied, to maintain the index structure.

---

### **3. Rules for Merges (Deletion)**

A merge (or redistribution) occurs when a deletion causes a node to fall below the minimum occupancy of $\lceil m/2 \rceil - 1$ keys (an "underflow").

- **Step 1: Redistribution (Borrowing):**
    - If the underflowed node has an immediate sibling with more than the minimum number of keys, it **borrows** a key.
    - For leaves, the borrowed key is moved, and the parent's separator index is updated to reflect the new starting value of the leaf.
- **Step 2: Merging:**
    - If no sibling can lend a key without underflowing themselves, the node is **merged** with a sibling.
    - The keys from both nodes are combined into one.
    - Because two nodes become one, the separator key between them in the parent node is **removed** (which may trigger a recursive underflow and merge in the parent).

### **Summary of B+ Tree Characteristics**

- **Data Storage:** Unlike standard B-trees, in a B+ tree, all actual data (keys) must reside in the **leaf nodes**; the internal nodes only store copies of keys to serve as a roadmap (index).
- **Linked Leaves:** Though not explicitly described in the questions, the leaf nodes in a B+ tree are typically linked to allow for efficient sequential range queries.