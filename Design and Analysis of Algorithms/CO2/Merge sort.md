### **1. Merge Sort Algorithm**

Based on the standard divide-and-conquer approach required by the syllabus and sources, the algorithm is composed of two primary functions: the recursive divider and the merging utility.

**Algorithm `MergeSort(low, high)`**

```
Algorithm MergeSort(low, high)
// low and high are the lower and upper bounds of the array indices
{
    if (low < high) then
    {
        mid = floor((low + high) / 2); // Divide the problem into subproblems
        MergeSort(low, mid);           // Recursively sort the first half
        MergeSort(mid + 1, high);       // Recursively sort the second half
        Merge(low, mid, high);         // Combine the solutions
    }
}
```

**Algorithm `Merge(low, mid, high)`**

```
Algorithm Merge(low, mid, high)
// Merges two sorted subarrays into one sorted array
{
    h = low; i = low; j = mid + 1;
    while ((h <= mid) and (j <= high)) do
    {
        if (A[h] <= A[j]) then { B[i] = A[h]; h = h + 1; }
        else { B[i] = A[j]; j = j + 1; }
        i = i + 1;
    }
    if (h > mid) then
        for k = j to high do { B[i] = A[k]; i = i + 1; }
    else
        for k = h to mid do { B[i] = A[k]; i = i + 1; }
    for k = low to high do A[k] = B[k];
}
```

---

### **2. Tracing the Algorithm**

**Dataset:** `{31, 28, 17, 65, 35, 42, 86, 25, 45, 52}` ($n=10$).

#### **Divide Phase (Splitting the array)**
	Level 0:                 [31, 28, 17, 65, 35, 42, 86, 25, 45, 52]
                                  /                      \
	Level 1:            [31, 28, 17, 65, 35]            [42, 86, 25, 45, 52]
                       /            \                  /            \
	Level 2:        [31, 28, 17]      [65, 35]        [42, 86, 25]      [45, 52]
	                 /       \         /    \          /       \         /    \
	Level 3:     [31, 28]    [17]    [65]  [35]    [42, 86]    [25]    [45]  [52]
	              /    \                            /    \
	Level 4:    [31]  [28]                        [42]  [86]
#### **Merge Phase (Combining in sorted order)**
	Level 4:    [31]  [28]                        [42]  [86]
	              \    /                              \    /
	Level 3:     [28, 31]    [17]    [65]  [35]    [42, 86]    [25]    [45]  [52]
	                 \       /         \    /          \       /         \    /
	Level 2:        [17, 28, 31]      [35, 65]        [25, 42, 86]      [45, 52]
	                       \            /                  \            /
	Level 1:            [17, 28, 31, 35, 65]            [25, 42, 45, 52, 86]
                                  \                      /
	Level 0:                 [17, 25, 28, 31, 35, 42, 45, 52, 65, 86]
---

> Top down decomposition, bottom up sorting
### **3. Tree of Calls for `mergeSort(1, 10)`**

The tree of calls represents the recursive activation records of the function.

```
                        MS(1, 10)
                      /           \
             MS(1, 5)               MS(6, 10)
            /        \             /         \
      MS(1, 3)      MS(4, 5)     MS(6, 8)     MS(9, 10)
     /      \       /      \    /       \      /      \
 MS(1, 2)  MS(3,3) MS(4,4) MS(5,5) MS(6,7) MS(8,8) MS(9,9) MS(10,10)
  /      \                        /      \
MS(1,1) MS(2,2)                 MS(6,6) MS(7,7)
```

---

### **4. Performance Analysis**

- **Recurrence Relation:** The time complexity is described by the recurrence relation $T(n) = 2T(n/2) + cn$, where $cn$ is the time taken for the `Merge` step.
- **Complexity:**
    - **Best Case:** $\mathbf{O(n \log n)}$.
    - **Worst Case:** $\mathbf{O(n \log n)}$.
- **Significance:** Unlike Quick Sort, Merge Sort maintains the same time complexity regardless of the initial order of the elements.