![](attachments/Pasted%20image%2020260122211243.png)
#### **1. Definition of a B-Tree of Order $m$**

A B-tree of order $m$ is a self-balancing search tree where each node can contain multiple keys and have multiple children. It is designed to work well on magnetic disks or other direct-access secondary storage devices.

**Properties of a B-Tree of Order $m$:**

- **Root Property:** The root has at least 2 children (unless it is a leaf).
    
- **Child Limit:** Every node has at most $m$ children.
    
- **Key Limit:** Every node has at most $m-1$ keys.
    
- **Minimum Children:** Every non-leaf node (except the root) has at least $\lceil m/2 \rceil$ children.
    
- **Minimum Keys:** Every node (except the root) has at least $\lceil m/2 \rceil - 1$ keys.
    
- **Leaf Level:** All leaves appear at the same level.
    
- **Sorting:** Keys in a node are sorted in increasing order.
    

#### **2. Rules for Insertion**

1. **Always Insert at Leaf:** New keys are always inserted into a leaf node.
    
2. **Overflow (Splitting):** If a node becomes full (contains $m-1$ keys) after insertion:
    
    - The node is split into two nodes.
        
    - The median key is promoted to the parent node.
        
    - If the parent becomes full, the split propagates upward.
        
    - If the root splits, a new root is created, increasing the tree height.
        

#### **3. Rules for Deletion**

1. **Leaf Deletion:**
    
    - If the node has more than the minimum number of keys, simply remove the key.
        
    - **Underflow:** If the node drops below the minimum number of keys:
        
        - **Borrow (Rotate):** If an immediate sibling has extra keys, borrow a key from the sibling through the parent.
            
        - **Merge:** If siblings have only the minimum number of keys, merge the node with a sibling and the separating key from the parent.
            
2. **Internal Node Deletion:**
    
    - Replace the key with its **in-order predecessor** (largest key in the left child) or **in-order successor** (smallest key in the right child).
        
    - Delete the predecessor/successor from the leaf node (which may trigger rebalancing).