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


# AVL Trees: Significance and Operations

## Significance of AVL Trees over Binary Search Trees

### Binary Search Tree (BST) Problems:

- **Worst case**: O(n) for search, insertion, and deletion (when tree becomes skewed/linear)
- **No balance guarantee**: Inserting sorted data creates a linked list
- **Performance degrades** with unbalanced structure

### AVL Tree Advantages:

- **Guaranteed O(log n)** time complexity for all operations
- **Self-balancing**: Automatically maintains height balance
- **Balance Factor**: For every node, heights of left and right subtrees differ by at most 1
- **Better for search-heavy applications**: Maintains optimal search performance

**Balance Factor (BF) = Height(Left Subtree) - Height(Right Subtree)**

- Valid values: -1, 0, +1
- If |BF| > 1, rotations are needed to restore balance

---

## Types of Rotations in AVL Trees

### 1. **Left-Left (LL) Rotation** - Single Right Rotation

**When**: Left subtree of left child causes imbalance (BF = +2)

Code

```
      z (BF=+2)                y
     /                        / \
    y (BF=+1)      →         x   z
   /
  x
```

### 2. **Right-Right (RR) Rotation** - Single Left Rotation

**When**: Right subtree of right child causes imbalance (BF = -2)

Code

```
  z (BF=-2)                  y
   \                        / \
    y (BF=-1)      →       z   x
     \
      x
```

### 3. **Left-Right (LR) Rotation** - Double Rotation

**When**: Right subtree of left child causes imbalance (BF = +2, left child BF = -1)

Code

```
    z (BF=+2)              z              x
   /                      /              / \
  y (BF=-1)      →       x      →       y   z
   \                    /
    x                  y
```

(Left rotate on y, then right rotate on z)

### 4. **Right-Left (RL) Rotation** - Double Rotation

**When**: Left subtree of right child causes imbalance (BF = -2, right child BF = +1)

Code

```
  z (BF=-2)              z                x
   \                      \              / \
    y (BF=+1)     →        x     →      z   y
   /                        \
  x                          y
```

(Right rotate on y, then left rotate on z)