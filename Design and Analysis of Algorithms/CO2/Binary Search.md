Binary Search Trace:** Write a recursive algorithm for **Binary Search**. State how Divide and Conquer is used, give the recurrence relation, and find the time complexity.

### **Recursive Algorithm for Binary Search**

Based on the requirements in the examination papers for **Course Outcome 2 (CO2)**, the recursive algorithm for **Binary Search** is designed to locate a target key within a sorted array by repeatedly halving the search space.

**Algorithm `RecursiveBinarySearch(a, low, high, key)`**

```
Algorithm RecursiveBinarySearch(a, low, high, key)
// a is a sorted array, low and high are the bounds, key is the target
{
    if (low <= high) then
    {
        mid = (low + high) / 2; // Find the midpoint

        if (key == a[mid])
            return mid; // Key found

        if (key < a[mid])
            // Search in the left half
            return RecursiveBinarySearch(a, low, mid - 1, key);
        else
            // Search in the right half
            return RecursiveBinarySearch(a, mid + 1, high, key);
    }
    return -1; // Key not found
}
```

---

### **How Divide and Conquer is Used**

Binary Search is a classic application of the **Divide and Conquer** paradigm, as identified in your sources:

- **Divide:** The algorithm calculates the **midpoint** of the current array segment, effectively dividing the problem of size $n$ into two smaller sub-problems of size approximately $n/2$.
- **Conquer:** Instead of solving both sub-problems (like in Merge Sort), Binary Search "conquers" by **recursively searching only one** of the two halves based on the comparison between the key and the midpoint value.
- **Combine:** The "combine" step is trivial. Since the key is either found at a midpoint or determined to be absent, there is no need to merge results from different sub-problems.

---

### **Recurrence Relation**

The time taken by the algorithm, $T(n)$, is defined by the time to perform one comparison plus the time to solve one sub-problem of half the size:

- **Base Case:** $T(1) = 1$ (or a constant $a$)
- **Recurrence:** **$T(n) = T(n/2) + c$**

Where **$c$** represents the constant time taken for calculating the midpoint and performing the comparison.

---

### **Time Complexity**

By solving the recurrence relation (typically using the Master Theorem or substitution), we find the following time complexities for Binary Search:

|Case|Time Complexity|
|:--|:--|
|**Best Case**|**$O(1)$** (occurs if the key is at the first midpoint)|
|**Average Case**|**$O(\log n)$**|
|**Worst Case**|**$O(\log n)$** (occurs if the key is at the ends or not present)|

The **logarithmic complexity** makes Binary Search significantly more efficient than a linear search, which has a complexity of $O(n)$. The total number of comparisons in the worst case is approximately **$\lfloor \log_2 n \rfloor + 1$**, which can be visualized using a **binary decision tree**.

