While the provided sources do not explicitly describe **Ternary Search**, it is a direct extension of the **Divide and Conquer** principle used for Binary Search in your curriculum,,. By applying the **control abstraction** for Divide and Conquer found in the sources, we can adapt the logic to divide the problem into three sub-problems instead of two.


### **Recursive Algorithm for Ternary Search**

In Ternary Search, the array is divided into three parts using two midpoints, `mid1` and `mid2`.

**Algorithm `RecursiveTernarySearch(a, low, high, key)`**

```
Algorithm RecursiveTernarySearch(a, low, high, key)
{
    if (low <= high) then
    {
        // Divide into three parts
        mid1 = low + (high - low) / 3;
        mid2 = high - (high - low) / 3;

        if (key == a[mid1]) return mid1;
        if (key == a[mid2]) return mid2;

        if (key < a[mid1])
            // Search in the first third
            return RecursiveTernarySearch(a, low, mid1 - 1, key);
        else if (key > a[mid2])
            // Search in the last third
            return RecursiveTernarySearch(a, mid2 + 1, high, key);
        else
            // Search in the middle third
            return RecursiveTernarySearch(a, mid1 + 1, mid2 - 1, key);
    }
    return -1;
}
```

---

### **Application of Divide and Conquer**

Following the paradigm described in your syllabus for "formulating algorithms to solve complex problems",:

- **Divide:** The problem of size $n$ is divided into **three equal sub-problems** of size $n/3$.
- **Conquer:** The algorithm determines which of the three segments could contain the key and **recursively solves only that one sub-problem**.
- **Combine:** Like Binary Search, there is no "combine" step as the result is returned directly once the key is located.

---

### **Recurrence Relation**

The recurrence relation for Ternary Search describes the time taken to perform comparisons and then solve one sub-problem that is one-third the size of the original:

- **Base Case:** $T(1) = 1$
- **Recurrence:** **$T(n) = T(n/3) + c$**

Where **$c$** represents the constant time for the two midpoint calculations and the comparisons needed to decide which branch to take.

---

### **Time Complexity**

|Case|Time Complexity|
|:--|:--|
|**Best Case**|**$O(1)$** (Key found at `mid1` or `mid2` on the first try)|
|**Average Case**|**$O(\log_3 n)$**|
|**Worst Case**|**$O(\log_3 n)$**|

**Comparison with Binary Search:** While the base of the logarithm is 3, making the tree shallower, Ternary Search requires more comparisons at each node (up to 4 comparisons to decide the branch) compared to Binary Search (which requires 2). In practice, this often makes **Binary Search** faster on most hardware despite the similar logarithmic growth. Both remain within the **Divide and Conquer** family of efficient searching algorithms highlighted in your course outcomes,.