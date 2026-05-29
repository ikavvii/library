v### **Definition of a B-Tree of Order $m$**

A B-tree of order $m$ is a self-balancing, multi-way search tree designed to handle large amounts of data efficiently. It maintains sorted data and allows for searches, sequential access, insertions, and deletions in logarithmic time.

### **Fundamental Rules for a B-Tree**

- **Node Capacity:** Every node (except the root) must have at least $\lceil m/2 \rceil - 1$ keys and at most $m-1$ keys.
- **Children:** A non-leaf node with $k$ keys has exactly $k+1$ children.
- **Balance:** All leaf nodes must appear at the same level.
- **Root Property:** The root has at least two children if it is not a leaf node.

---

### **Rules for Insertion**

Insertion in a B-tree is always performed at the leaf level:

1. **Search:** Find the appropriate leaf node where the key should be inserted.
2. **Insert:** If the leaf has fewer than $m-1$ keys, insert the key in sorted order.
3. **Split:** If the leaf is full (contains $m-1$ keys), it must be split:
    - The middle key is identified.
    - The remaining keys are split into two new nodes (left and right of the middle key).
    - The middle key is **promoted** up to the parent node.
    - If the parent node also becomes full, the split process repeats recursively upward toward the root.

---

### **Rules for Deletion**

Deletion is more complex as it must maintain the minimum occupancy of the nodes:

1. **Leaf Deletion:** If the key is in a leaf node and the node still has at least the minimum number of keys after removal, simply delete it.
2. **Internal Node Deletion:** If the key is in an internal node, replace it with its **in-order predecessor** or **in-order successor** (which will be in a leaf), then delete that key from the leaf.
3. **Underflow Handling (Borrowing/Merging):** If a deletion causes a node to have fewer than the minimum keys ($\lceil m/2 \rceil - 1$):
    - **Borrowing (Redistribution):** If an immediate sibling has more than the minimum keys, "borrow" a key by rotating it through the parent.
    - **Merging:** If no sibling can lend a key, **merge** the underflowed node with an immediate sibling and the separator key from the parent. This may cause the parent to underflow, requiring a recursive rebalance.