### **1. Quick Sort Algorithm**

Quick Sort is a **Divide and Conquer** algorithm that picks an element as a "pivot" and partitions the array around it.

**Algorithm `QuickSort(p, q)`**

```
Algorithm QuickSort(p, q)
// p is the lower bound, q is the upper bound
{
    if (p < q) then
    {
        j = Partition(p, q + 1); // Partition the array
        QuickSort(p, j - 1);     // Recursively sort the left sub-array
        QuickSort(j + 1, q);     // Recursively sort the right sub-array
    }
}
```

**Algorithm `Partition(m, p)`**

```
Algorithm Partition(m, p)
// m is the pivot index, p is the boundary
{
    v = A[m]; i = m; j = p;
    repeat
    {
        repeat i = i + 1; until (A[i] >= v);
        repeat j = j - 1; until (A[j] <= v);
        if (i < j) then InterChange(A, i, j);
    } until (i >= j);
    A[m] = A[j]; A[j] = v;
    return j;
}
```

---

### **2. Recurrence Relations and Complexity**

As required by Source, the performance of Quick Sort is highly dependent on the choice of the pivot:

- **Worst Case Performance:**
    
    - **Condition:** Occurs when the elements are already sorted (ascending or descending), leading to highly unbalanced partitions where one sub-array has $n-1$ elements and the other has $0$.
    - **Recurrence Relation:** $T(n) = T(n-1) + T(0) + cn \approx T(n-1) + cn$
    - **Complexity:** **$O(n^2)$**.
- **Best Case Performance:**
    
    - **Condition:** Occurs when the pivot always divides the array into two nearly equal halves.
    - **Recurrence Relation:** $T(n) = 2T(n/2) + cn$
    - **Complexity:** **$O(n \log n)$**.

---

### **3. Illustration with Sample Input (10 Elements)**

**Input Array:** 67, 12, 89, 43, 23, 78, 54, 36, 91 and 10

#### **Pass 1: Initial Partitioning**

- **Pivot ($v$):** 67 (First element)
- **Pointers:** $i$ moves right looking for $\geq 67$; $j$ moves left looking for $\leq 67$.
- $i$ stops at 89; $j$ stops at 10. Swap 89 and 10 $\rightarrow$ ``
- $i$ stops at 78; $j$ stops at 36. Swap 78 and 36 $\rightarrow$ ``
- $i$ stops at 78; $j$ stops at 54. Since $i \geq j$, pointers crossed.
- **Final Swap:** Swap Pivot (67) with $A[j]$ (54).
- **Result after Pass 1:** `, **67**,`

#### **Pass 2: Partitioning Sub-arrays**

- **Left Sub-array `:** Pivot 54. $i$ stops at end, $j$ stops at 36. Swap 54 and 36 $\rightarrow$`, **54**.
- **Right Sub-array `:** Pivot 78. $i$ stops at 91, $j$ stops at end (crosses back). Swap 78 with itself $\rightarrow$ **78**,`.

#### **Pass 3: Final Sorting**

- Left sub-array `partitions around 36 to result in`, **36**, ``.
- Right sub-array `` partitions around 91 to result in **89**, **91**.
- Recursion continues until single elements remain.

**Final Sorted Output:** `{10, 12, 23, 36, 43, 54, 67, 78, 89, 91}`.