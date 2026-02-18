While binary search splits an array into two halves, **ternary search** divides the search space into **three equal parts** using two middle points.

This is particularly useful when searching in sorted arrays or finding the maximum/minimum of unimodal functions.

---

### How it Works

Instead of one $mid$ point, we calculate two: $m_1$ and $m_2$.

1. **Divide:** Calculate the two midpoints:
    
    - $m_1 = low + \frac{high - low}{3}$
        
    - $m_2 = high - \frac{high - low}{3}$
        
2. **Compare:** * If the target is at $m_1$ or $m_2$, you're done.
    
    - If the target is less than the value at $m_1$, search the **left** third.
        
    - If the target is greater than the value at $m_2$, search the **right** third.
        
    - Otherwise, search the **middle** third.
        

### Python Implementation


``` python
def ternary_search(arr, low, high, target):
    if high >= low:
        # Calculate the two midpoints
        m1 = low + (high - low) // 3
        m2 = high - (high - low) // 3

        # Check if target is at either midpoint
        if arr[m1] == target:
            return m1
        if arr[m2] == target:
            return m2

        # Narrow down the search range
        if target < arr[m1]:
            # Target is in the leftmost third
            return ternary_search(arr, low, m1 - 1, target)
        elif target > arr[m2]:
            # Target is in the rightmost third
            return ternary_search(arr, m2 + 1, high, target)
        else:
            # Target is in the middle third
            return ternary_search(arr, m1 + 1, m2 - 1, target)

    return -1  # Target not found
```

---

### Complexity Comparison

|**Feature**|**Binary Search**|**Ternary Search**|
|---|---|---|
|**Time Complexity**|$O(\log_2 n)$|$O(\log_3 n)$|
|**Comparisons**|Fewer per iteration|More per iteration|
|**Best Case**|$O(1)$|$O(1)$|

> **Note:** Even though $\log_3 n$ is "smaller" than $\log_2 n$, ternary search is often **slower** in practice for standard arrays because it requires more comparisons (up to 4) within each recursive step to decide which third to move into.

Would you like me to show you how to use ternary search to find the maximum value of a parabolic function instead of an array?