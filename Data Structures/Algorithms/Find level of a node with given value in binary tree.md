 > Algorithm to find level of a node with given value in binary tree

 ● Here are two simple algorithms to find the level (depth) of a node with a given value in a binary tree.
   Assume the root is at level 1 (you can shift to 0 if your convention is different).

   -----------------------------------------------------------------------------------------------------------------------------------------------

   1. Recursive Algorithm (DFS)

   Idea:
   Pass the current level down the recursion; when you find the value, return that level, otherwise search left and right.

   Pseudocode

     // Node definition
     struct Node {
         int data;
         struct Node *left, *right;
     };

     // Helper: returns level of key if found, otherwise 0
     int getLevelUtil(struct Node *root, int key, int level) {
         if (root == NULL)
             return 0;                  // not found in this path
y
         if (root->data == key)
             return level;              // found at this level

         // search in left subtree
         int downlevel = getLevelUtil(root->left, key, level + 1);
         if (downlevel != 0)
             return downlevel;          // found in left

         // search in right subtree
         return getLevelUtil(root->right, key, level + 1);
     }

     // Public function: call with level = 1 for root
     int getLevel(struct Node *root, int key) {
         return getLevelUtil(root, key, 1);
     }

     - If the function returns 0, the key is not present.
     - Time complexity: O(n) in worst case; Space: O(h) recursion stack (h = height).

   -----------------------------------------------------------------------------------------------------------------------------------------------

   2. Iterative Algorithm Using Queue (BFS / Level-Order)

   Idea:
   Do a level-order traversal (BFS). For each level, process all nodes in the queue and then move to the next level.

   Pseudocode

     int getLevelBFS(struct Node *root, int key) {
         if (root == NULL)
             return 0;                 // empty tree

         Queue q;
         initQueue(&q);
         enqueue(&q, root);

         int level = 1;

         while (!isEmpty(&q)) {
             int nodeCount = size(&q); // number of nodes at current level

             // process all nodes at this level
             while (nodeCount > 0) {
                 struct Node *temp = dequeue(&q);

                 if (temp->data == key)
                     return level;      // found at this level

                 if (temp->left)
                     enqueue(&q, temp->left);
                 if (temp->right)
                     enqueue(&q, temp->right);

                 nodeCount--;
             }
             level++;                   // move to next level
         }

         return 0;                      // not found
     }

     - Also O(n) time, O(width) space, where width is max nodes in any level.
     - This version naturally works level by level, which some exam questions prefer if they mention “use level-order traversal”.

   You can use either algorithm depending on whether your question expects DFS (recursive) or BFS (queue-based) solution.
