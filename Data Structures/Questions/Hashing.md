![](attachments/Pasted%20image%2020251218213341.png)

## Hashing and Collision Resolution

**Definition of Hashing:**
Hashing is a technique that converts a key into a table index using a hash function. It enables fast data retrieval in O(1) average time.

**Two Methods for Finding Hash Address:**

### 1. **Division Method (Modulo Function)**
```
h(key) = key mod m
where m = table size
```

### 2. **Multiplication Method**
```
h(key) = floor(m × (A × key - floor(A × key)))
where 0 < A < 1 (typically A ≈ 0.618)
```

---

## Problem Solution

**Given Data:**
- Hash table size: 11
- Elements to insert (in order): 11, 12, 31, 63, 89, 90, 78, 55, 21

**Using Division Method:  h(key) = key mod 11**

| Key | Calculation    | Hash Value         |
| --- | -------------- | ------------------ |
| 11  | 11 mod 11 = 0  | 0                  |
| 12  | 12 mod 11 = 1  | 1                  |
| 31  | 31 mod 11 = 9  | 9                  |
| 63  | 63 mod 11 = 8  | 8                  |
| 89  | 89 mod 11 = 1  | **1 (Collision!)** |
| 90  | 90 mod 11 = 2  | 2                  |
| 78  | 78 mod 11 = 1  | **1 (Collision!)** |
| 55  | 55 mod 11 = 0  | **0 (Collision!)** |
| 21  | 21 mod 11 = 10 | 10                 |

---

## Collision Resolution Methods

### **Method 1: Linear Probing (Open Addressing)**

When collision occurs, find the next available slot: 
```
h(key, i) = (h(key) + i) mod m, where i = 0, 1, 2, ...
```

**Hash Table Contents:**

| Index | 0   | 1   | 2   | 3   | 4   | 5   | 6   | 7   | 8   | 9   | 10  |
| ----- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Value | 11  | 12  | 90  | -   | -   | -   | -   | 89  | 63  | 31  | 21  |

**Insertion Process:**
- 11 → Index 0 ✓
- 12 → Index 1 ✓
- 31 → Index 9 ✓
- 63 → Index 8 ✓
- 89 → Index 1 (collision) → Index 2 (occupied) → Index 3 ✓ → **2 comparisons**
- 90 → Index 2 ✓
- 78 → Index 1 (collision) → Index 2 (occupied) → Index 3 (occupied) → Index 4 ✓ → **3 comparisons**
- 55 → Index 0 (collision) → Index 1 (occupied) → Index 2 (occupied) → Index 3 (occupied) → Index 4 (occupied) → Index 5 ✓ → **5 comparisons**
- 21 → Index 10 ✓

---

### **Method 2: Chaining (Closed Addressing)**

Use linked lists at each index to handle collisions: 

**Hash Table Contents:**

| Index | Value |
|-------|-------|
| 0 | 11 → 55 |
| 1 | 12 → 89 → 78 |
| 2 | 90 |
| 3 | - |
| 4 | - |
| 5 | - |
| 6 | - |
| 7 | - |
| 8 | 63 |
| 9 | 31 |
| 10 | 21 |

**Insertion Process:**
- 11 → Index 0 ✓ → **1 comparison**
- 12 → Index 1 ✓ → **1 comparison**
- 31 → Index 9 ✓ → **1 comparison**
- 63 → Index 8 ✓ → **1 comparison**
- 89 → Index 1 (collision) → Add to chain → **2 comparisons**
- 90 → Index 2 ✓ → **1 comparison**
- 78 → Index 1 (collision) → Add to chain → **2 comparisons**
- 55 → Index 0 (collision) → Add to chain → **2 comparisons**
- 21 → Index 10 ✓ → **1 comparison**

---

## Comparison Summary

| Method | Total Comparisons | Collisions |
|--------|-------------------|-----------|
| **Linear Probing** | 1+1+1+1+2+1+3+5+1 = **16 comparisons** | 4 collisions |
| **Chaining** | 1+1+1+1+2+1+2+2+1 = **12 comparisons** | 4 collisions |

**Key Observations:**
- **Linear Probing** suffers from clustering; each collision requires multiple probes
- **Chaining** is more efficient; collisions are resolved by adding to a linked list
- Chaining requires fewer comparisons overall