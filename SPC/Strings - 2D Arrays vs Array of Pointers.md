## Memory Requirements: 2D Arrays vs. Array of Pointers for Strings

| **Aspect**               | **2D Array of Characters (Static)**                                     | **Array of Pointers to Strings (Dynamic)**                            |
| ------------------------ | ----------------------------------------------------------------------- | --------------------------------------------------------------------- |
| **Declaration Example**  | `char arr[n][m];` <br>(n = number of strings, m = max chars per string) | `char *arr[n];` <br>each `arr[i] = malloc(strlen + 1);`               |
| **Memory Allocated**     | Fixed at compile-time: **n × m bytes**                                  | n × (pointer size) + sum of string lengths + n (for null terminators) |
| **Allocation Type**      | Static (contiguous block for all chars)                                 | Dynamic (separate heap block for each string)                         |
| **Flexibility**          | Fixed number and length of strings                                      | Number of strings fixed, but string length can vary                   |
| **Space Waste?**         | Possible (if strings shorter than `m`, unused chars are wasted)         | No space wasted (each string uses only needed bytes)                  |
| **Access**               | `arr[i][j]`                                                             | `arr[i][j]` or with pointer arithmetic                                |
| **Pointer Storage**      | None (only characters stored)                                           | `n × (size of pointer)` (each pointer stored separately)              |
| **Total Memory Formula** | **n × m × size of char** (`sizeof(char)` usually 1 byte)                | **n × pointer_size** + <br>∑(length of each string + 1 for '\0')      |

---

### **Example**  
Suppose you need to store 3 strings: `"cat"`, `"tiger"`, `"panther"`

#### (i) **2D Array**  
Declaration: `char arr[3][10];`  
- Space allocated: 3 × 10 = **30 bytes** (regardless of actual string length—wasted space possible)

#### (ii) **Array of Pointers**  
Declaration: `char *arr[3];`  
Allocate memory per string:
* `"cat"` ... 4 bytes (3 chars + '\0')
* `"tiger"` ... 6 bytes (5 chars + '\0')
* `"panther"` ... 8 bytes (7 chars + '\0')

- Space for pointers: 3 × 8 = **24 bytes** (on 64-bit system, pointer size = 8 bytes)
- Space for strings: 4 + 6 + 8 = **18 bytes**
- **Total = 24 + 18 = 42 bytes**

---

#### **Summary Table**

| **Storage Method**          | **Case**                                      | **Memory Used**                    |
|----------------------------|-----------------------------------------------|------------------------------------|
| Fixed 2D array             | 3 strings, max 10 chars each                  | 3 × 10 = **30 bytes**              |
| Array of pointers (dynamic)| Same 3 strings, actual lengths                | Pointer storage: 24 bytes <br>String storage: 18 bytes <br>**Total: 42 bytes** |

---

**Note:**  
- **2D array** is simple but wastes space for short strings.  
- **Array of pointers** is more flexible but stores pointers and may be less contiguous in memory.  
- If string lengths and count are unpredictable, **array of pointers** (dynamic) is usually more efficient.

---

**Formulas to remember for exams:**

- 2D Array (static):                 `n × m × sizeof(char)`
- Array of Pointers (dynamic):    `n × sizeof(pointer) + sum(strlen(s_i) + 1) for all i`