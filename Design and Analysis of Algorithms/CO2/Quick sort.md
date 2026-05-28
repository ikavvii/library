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


	Initial:  [ 67,  12,  89,  43,  23,  78,  54,  36,  91,  10 ]
		        P        i                                   j   -> i stops at 89 (>67), j stops at 10 (≤67). Swap!

	Swap 1:   [ 67,  12,  10,  43,  23,  78,  54,  36,  91,  89 ]
	            P                        i         j           -> i moves to 78 (>67), j moves to 36 (≤67). Swap!

	Swap 2:   [ 67,  12,  10,  43,  23,  36,  54,  78,  91,  89 ]
	            P                             j    i               -> Pointers cross! (i=7, j=6). 

Final Pass: Swap Pivot (67) with element at index j (54).

| **Step** | **Sub-Array Being Processed** | **Selected Pivot** | **Array State After Partitioning**                   | **Remarks / Next Step**         |
| -------- | ----------------------------- | ------------------ | ---------------------------------------------------- | ------------------------------- |
| **0**    | _Initial State_               | —                  | `[67, 12, 89, 43, 23, 78, 54, 36, 91, 10]`           | Start global partition.         |
| **1**    | Full Array                    | **67**             | `[54, 12, 10, 43, 23, 36,` **67**`, 78, 91, 89]`     | 67 is sorted. Split Left/Right. |
| **2**    | Left: Indices 0 to 5          | **54**             | `[36, 12, 10, 43, 23,` **54**`, 67, 78, 91, 89]`     | 54 is sorted.                   |
| **3**    | Left-Left: Indices 0 to 4     | **36**             | `[23, 12, 10,` **36**`, 43, 54, 67, 78, 91, 89]`     | 36 and 43 are sorted.           |
| **4**    | Left-3: Indices 0 to 2        | **23**             | `[10, 12,` **23**`, 36, 43, 54, 67, 78, 91, 89]`     | 23 is sorted.                   |
| **5**    | Left-4: Indices 0 to 1        | **10**             | `[`**10**`, 12, 23, 36, 43, 54, 67, 78, 91, 89]`     | Left side fully sorted.         |
| **6**    | Right: Indices 7 to 9         | **78**             | `[10, 12, 23, 36, 43, 54, 67,` **78**`, 91, 89]`     | 78 is sorted.                   |
| **7**    | Right-Right: Indices 8 to 9   | **91**             | `[10, 12, 23, 36, 43, 54, 67, 78,` **89**, **91**`]` | **Fully Sorted!**               |

The recurrence relation **$T(n) = T(n-1) + cn$** represents the **worst-case scenario** for algorithms like Quick Sort, and it results in **$O(n^2)$** because it describes a series of operations that sum up to an arithmetic progression.

### **Step-by-Step Derivation**

To see why this is $n^2$, we use the **Substitution Method** to expand the recurrence:

1. **Original Equation:**  
    $T(n) = T(n-1) + cn$
2. **Substitute for $T(n-1)$:**  
    Since $T(n-1) = T(n-2) + c(n-1)$, we plug this into the first equation:  
    $T(n) = [T(n-2) + c(n-1)] + cn$
3. **Substitute for $T(n-2)$:**  
    $T(n) = [T(n-3) + c(n-2) + c(n-1)] + cn$
4. **Continue the Pattern:**  
    If we continue this until we reach the base case $T(1)$ or $T(0)$, the equation looks like this:  
    $T(n) = cn + c(n-1) + c(n-2) + ... + c(1) + T(0)$
5. **Factor out the constant $c$:**  
    $T(n) = c [n + (n-1) + (n-2) + ... + 1] + T(0)$

### **Applying the Summation Formula**

The term in the brackets is the sum of the first $n$ natural integers. The mathematical formula for this sum is:  
$$\sum_{i=1}^{n} i = \frac{n(n+1)}{2}$$

So, the equation becomes:  
$$T(n) = c \cdot \frac{n(n+1)}{2} + T(0)$$  
$$T(n) = c \cdot \frac{n^2 + n}{2} + T(0)$$

### **Asymptotic Analysis ($O$ Notation)**

In Big Oh notation, we ignore constant coefficients (like $c$ and $1/2$) and lower-order terms (like $n$):

- The highest power of $n$ in the result is **$n^2$**.
- Therefore, **$T(n) = O(n^2)$**.

### **Context in Your Syllabus**

In the provided sources, this worst-case occurs in **Quick Sort** when the pivot is consistently the smallest or largest element (e.g., when the input is already sorted). Instead of dividing the problem into two equal halves (which would be $O(n \log n)$), the algorithm only reduces the problem size by **one** at each step, leading to this quadratic complexity.

_*_