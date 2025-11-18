### Algorithm: Delete in Binary Search Tree (BST)

**Input:**

- T: The root node of the BST (can be **null**)
- x: The value to delete

**Output:**

- The BST with x removed (if it exists)

---

**Procedure DeleteBST(T,x):**

1. If T=null, return null
2. If x<T.value, then  
      T.left←DeleteBST(T.left,x)
3. Else if x>T.value, then  
      T.right←DeleteBST(T.right,x)
4. Else  
      // x=T.value, delete this node  
      a. If T.left=null, return T.right  
      b. Else if T.right=null, return T.left  
      c. Else  
        // Node has both left and right children  
        i. Find minimum value node M in T.right (inorder successor)  
        ii. T.value←M.value  
        iii. T.right←DeleteBST(T.right,M.value)
5. Return T
---

**Explanation:**

- The procedure recursively searches for the node to delete.
- If node has:
    - **No children**: simply remove the node.
    - **One child**: replace the node with its child.
    - **Two children**: find the node's in-order successor (the smallest node in its right subtree), copy its value, and recursively delete the successor.

When deleting a node in a BST with two children, you typically replace its value with either:

- The **in order successor** (smallest value in the right subtree), or
- The **in order predecessor** (largest value in the left subtree).