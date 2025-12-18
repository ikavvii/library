recursive algorithm for Binary Search on a sorted array.

   Assumptions:

     - Array A[low..high] is sorted in ascending order.
     - We search for key.

   Recursive Binary Search – Pseudocode

     int binarySearchRecursive(int A[], int low, int high, int key) {
         if (low > high)                // base case: empty range
             return -1;                 // key not found

         int mid = (low + high) / 2;

         if (A[mid] == key)             // key found
             return mid;
         else if (key < A[mid])         // search left half
             return binarySearchRecursive(A, low, mid - 1, key);
         else                           // search right half
             return binarySearchRecursive(A, mid + 1, high, key);
     }

   To call it: index = binarySearchRecursive(A, 0, n-1, key);
   Time complexity: O(log n), Space complexity: O(log n) extra due to recursion stack.