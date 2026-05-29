### **Control Abstraction: Divide and Conquer**

The control abstraction for the **Divide and Conquer** method describes the general logic of partitioning a problem into smaller instances, solving them, and merging the results.

**Algorithm `DAndC(P)`**

```
Algorithm DAndC(P)
{
    if Small(P) then
        return S(P); // Solve the problem directly if it is small
    else
    {
        divide P into smaller instances P1, P2, ..., Pk, k ≥ 1; // Divide

        // Conquer by recursively solving subproblems
        Apply DAndC to each subproblem to get results;

        // Combine the results of subproblems to get the final solution
        return Combine(DAndC(P1), DAndC(P2), ..., DAndC(Pk));
    }
}
```

---

### **Components and Significance**

- **`Small(P)` and `S(P)`**: These represent the base case where the problem size is small enough to be solved directly without further division.
- **Divide**: This step partitions the original problem into **smaller subproblems**, which is the fundamental principle used in algorithms like **Merge Sort** and **Binary Search** featured in your sources.
- **Combine**: This function merges the individual solutions into a final answer. In **Merge Sort**, this is performed by the `Merge()` function, while in **Binary Search**, the "combine" step is often trivial as only one subproblem is solved.
- **Recurrence Relations**: The performance of algorithms following this abstraction is typically described by recurrence relations, such as $T(n) = 2T(n/2) + cn$ for Merge Sort.

By mastering this abstraction, you can apply the same logic to various "Divide and Conquer" problems listed in the syllabus, such as finding the **second maximum integer** in an array or performing a **Quick Sort**.


### **1. Small(P) - The Base Case**

The problem is considered "small" when the array segment contains only **two elements** (or one, though the second maximum requires at least two).

- **Direct Solution:** Simply compare the two elements; the larger is the maximum and the smaller is the second maximum.

### **2. Divide**

The array is split into two halves (Left and Right) by calculating the midpoint, identical to the division step in **Merge Sort** or **Binary Search**.

### **3. Conquer**

The algorithm is applied **recursively** to both halves.

- The left recursive call returns the pair `{max1_L, max2_L}`.
- The right recursive call returns the pair `{max1_R, max2_R}`.

### **4. Combine**

This is the most critical step for this specific problem. To find the global second maximum from the sub-results, you perform the following logic:

- **Global Maximum:** Compare `max1_L` and `max1_R`. The larger of the two is the global maximum.
- **Second Maximum:**
    - If `max1_L` is the global maximum, the potential candidates for the global second maximum are `max2_L` and `max1_R`.
    - If `max1_R` is the global maximum, the candidates are `max2_R` and `max1_L`.
    - Compare these candidates; the larger one is the overall **second maximum** for that segment of the array.

By following this structure, the algorithm maintains a time complexity of **$O(n)$**, but it performs fewer comparisons than a naive linear scan, often requiring approximately **$n + \log_2 n - 2$** comparisons in its optimal implementation. This problem serves as a practical demonstration of how the **Divide and Conquer** abstraction can be adapted beyond simple sorting or searching.

To find the **second maximum integer** in an array using the **Divide and Conquer** method (as per the abstraction discussed), the algorithm recursively splits the array and compares the local maximums and second maximums of each half.

### **Algorithm: FindSecondMax(A, low, high)**

```
Algorithm FindSecondMax(A, low, high)
// A is the array, low and high are the bounds
{
    if (low == high) then
        return {A[low], -infinity}; // Base case: one element

    else if (high == low + 1) then
    {
        // Base case: two elements
        if (A[low] > A[high]) then
            return {A[low], A[high]};
        else
            return {A[high], A[low]};
    }
    else
    {
        mid = (low + high) / 2; // Divide step

        // Conquer step: Recursively find results for both halves
        {max1L, max2L} = FindSecondMax(A, low, mid);
        {max1R, max2R} = FindSecondMax(A, mid + 1, high);

        // Combine step: Identify global max and second max
        if (max1L > max1R) then
        {
            max1 = max1L;
            max2 = max(max2L, max1R); // Winner's 2nd or the loser's 1st
        }
        else
        {
            max1 = max1R;
            max2 = max(max1L, max2R); // Winner's 2nd or the loser's 1st
        }
        return {max1, max2};
    }
}
```

### **Analysis of the Algorithm**

- **Divide:** The array is halved at each step, similar to the `MergeSort()` structure shown in the sources.
- **Conquer:** Recursive calls are made until the base case of 1 or 2 elements is reached.
- **Combine:** Instead of merging sorted lists, the "Combine" logic performs a comparison to update the global maximum and second maximum.
- **Complexity:** The time complexity for this approach is **$O(n)$**. While the asymptotic complexity is the same as a linear scan, this method is often used to minimize the total number of comparisons (approximately $n + \lceil \log_2 n \rceil - 2$).

This specific algorithm is requested in the **August/September 2024** paper to test your ability to apply the **Divide and Conquer** design paradigm to non-sorting problems.