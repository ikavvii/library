**20 Random Numbers for AVL Tree Practice:**

```
47, 23, 89, 12, 56, 34, 78, 91, 5, 67, 29, 82, 15, 41, 73, 98, 26, 53, 8, 64
```

**Tips for building your AVL tree:**
1. Insert these numbers one at a time in the order given
2. After each insertion, check the balance factor of each node (height of left subtree - height of right subtree)
3. If any node has a balance factor of +2 or -2, perform the appropriate rotation: 
   - **Left-Left (LL)**: Single right rotation
   - **Right-Right (RR)**: Single left rotation
   - **Left-Right (LR)**: Left rotation on left child, then right rotation on parent
   - **Right-Left (RL)**: Right rotation on right child, then left rotation on parent