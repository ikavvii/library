![](attachments/Pasted%20image%2020251218211224.png)

## Binary Search Algorithm Solution

**Problem Analysis:**
- List of elements:  2, 4, 12, 22, 37, 39, 45, 48, 52, 64, 67, 69, 80
- Searching for: keys 67 and 15

**Binary Search Algorithm:**

```
BinarySearch(arr[], key, low, high)
1. While low ≤ high:
   a. mid = (low + high) / 2
   b. If arr[mid] == key:  return mid (Found)
   c. If arr[mid] < key: low = mid + 1 (Search right half)
   d. If arr[mid] > key: high = mid - 1 (Search left half)
2. Return -1 (Not Found)
```

**Searching for key 67:**

| Step | Low | High | Mid | arr[mid] | Comparison | Action |
|------|-----|------|-----|----------|------------|--------|
| 1 | 0 | 12 | 6 | 45 | 45 < 67 | Search right |
| 2 | 7 | 12 | 9 | 64 | 64 < 67 | Search right |
| 3 | 10 | 12 | 11 | 69 | 69 > 67 | Search left |
| 4 | 10 | 10 | 10 | 67 | **Found!** | Return 10 |

**Searching for key 15 (unsuccessful):**

| Step | Low | High | Mid        | arr[mid]      | Comparison | Action       |
| ---- | --- | ---- | ---------- | ------------- | ---------- | ------------ |
| 1    | 0   | 12   | 6          | 45            | 45 > 15    | Search left  |
| 2    | 0   | 5    | 2          | 12            | 12 < 15    | Search right |
| 3    | 3   | 5    | 4          | 37            | 37 > 15    | Search left  |
| 4    | 3   | 3    | 3          | 22            | 22 > 15    | Search left  |
| 5    | 3   | 2    | low > high | **Not Found** | Stop       |              |

**Time Complexity:**

- **Successful search (67):** O(log n) = **4 comparisons**
- **Unsuccessful search (15):** O(log n) = **5 comparisons**
- **General:** O(log n) for both successful and unsuccessful searches

Where n = 13 elements in the list.

**Order of Elements Compared:**
- **For 67:** 45 → 64 → 69 → 67 ✓
- **For 15:** 45 → 12 → 37 → 22 → (out of range)