### Algorithm: Insert in Binary Search Tree (BST)

**Input:**

- T: The root node of the BST (can be **null** if the tree is empty)
- x: The value to insert (assume values are comparable)

**Output:**

- The BST with x inserted

---

**Procedure InsertBST(T,x)**

1. If T=null then  
      Create a new node N with value x  
      Return N
2. If x<T.value then  
      T.left←InsertBST(T.left,x)
3. Else if x>T.value then  
      T.right←InsertBST(T.right,x)
4. Else  
      (Nothing to do; x already exists in the tree)
5. Return T

---

**Explanation:**

- The procedure starts at the root and recursively descends left or right based on value comparison.
- It inserts the node when a null subtree is found.
- For equal values, by convention, duplicates are not inserted. This can be changed if your BST allows duplicates.
- The function returns the (possibly updated) subtree root.