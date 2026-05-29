To find the **minimum and maximum** elements in an array using the **Divide and Conquer** method, we follow the same **control abstraction** found in your examination papers.

By recursively dividing the array, the algorithm reduces the number of comparisons compared to a simple linear scan.

### **Algorithm: MaxMin(a, i, j, max, min)**

```
Algorithm MaxMin(i, j, max, min)
// a[i:j] is the array; i is low, j is high
// max and min are the results passed by reference
{
    if (i == j) then
        max = min = a[i]; // Base Case 1: One element

    else if (i == j - 1) then
    {
        // Base Case 2: Two elements
        if (a[i] < a[j]) then
        {
            max = a[j];
            min = a[i];
        }
        else
        {
            max = a[i];
            min = a[j];
        }
    }
    else
    {
        // Divide step
        mid = (i + j) / 2;

        // Conquer step: Recursively find results for both halves
        MaxMin(i, mid, max1, min1);
        MaxMin(mid + 1, j, max2, min2);

        // Combine step: Compare sub-results to find global values
        if (max1 < max2) then max = max2; else max = max1;
        if (min1 < min2) then min = min1; else min = min2;
    }
}
```

---

### **How the Principles are Applied**

Based on the **Divide and Conquer** paradigm described in your syllabus:

1. **Divide:** The problem of size $n$ is split into two subproblems of size $n/2$ at each level of recursion.
2. **Conquer:** The algorithm continues to split the array until it reaches the base cases:
    - **One element:** The element is both the min and the max.
    - **Two elements:** A single comparison determines which is min and which is max.
3. **Combine:** Once the recursive calls return, the algorithm performs two additional comparisons to merge the local results: one for the maximums and one for the minimums.

### **Performance Analysis**

While the sources do not provide the specific recurrence for MaxMin, it follows the standard pattern for balanced D&C algorithms:

- **Recurrence Relation:** $T(n) = 2T(n/2) + 2$ (for the two comparisons in the combine step).
- **Time Complexity:** The complexity is **$O(n)$**.
- **Comparison Efficiency:** In a linear scan, you would perform $2n-2$ comparisons. This Divide and Conquer method is more efficient, requiring only **$\lceil 3n/2 \rceil - 2$** comparisons, which is why it is featured as a significant optimization problem in this course.