## **Relationship between Arrays and Pointers in C**

| **Aspect**        | **Arrays**                                                       | **Pointers**                                         | **Relation/Explanation**                                       |
| ----------------- | ---------------------------------------------------------------- | ---------------------------------------------------- | -------------------------------------------------------------- |
| **Definition**    | Collection of elements of same type, stored at contiguous memory | Variable that stores the address of another variable | Array name gives base address (pointer to first element)       |
| **Declaration**   | `int arr[5];`                                                    | `int *ptr;`                                          | Can assign: `ptr = arr;`                                       |
| **Access**        | `arr[i]`                                                         | `*(ptr + i)`                                         | `arr[i]` is equal to `*(arr + i)`                              |
| **Array Name**    | Acts as constant pointer to first element (`&arr[0]`)            | Can point anywhere, value can change                 | `arr` & `&arr[0]` give the same value; `arr = ptr` not allowed |
| **Memory**        | Fixed, contiguous block allocated                                | Can point to any single variable or array element    | Pointer can traverse array using arithmetic                    |
| **Input Example** | `scanf("%d", &arr[0]);`                                          | `scanf("%d", ptr);` after `ptr = arr;`               | Both store value at same place                                 |

---

## **Pointer Arithmetic Table**

| **Operation**               | **Example**                                           | **Result/Explanation**                                          |
| --------------------------- | ----------------------------------------------------- | --------------------------------------------------------------- |
| Pointer increment (`ptr++`) | `ptr = arr; ptr++;`                                   | `ptr` now points to next element (`arr[1]`) (adds size of type) |
| Pointer decrement (`ptr--`) | `ptr = arr + 3; ptr--;`                               | `ptr` now points to previous element (`arr[2]`)                 |
| Addition (`ptr + n`)        | `ptr = arr; ptr = ptr + 2;`                           | `ptr` now points to `arr[2]`                                    |
| Subtraction (`ptr - n`)     | `ptr = arr + 4; ptr = ptr - 2;`                       | `ptr` now points to `arr[2]`                                    |
| Difference (`ptr2 - ptr1`)  | `ptr1 = &arr[1]; ptr2 = &arr[4]; diff = ptr2 - ptr1;` | `diff == 3` (number of elements apart, not bytes)               |
| Dereferencing (`*ptr`)      | `ptr = arr + 2; value = *ptr;`                        | `value` is `arr[2]`                                             |

### **Rules:**  
- Pointer arithmetic is based on the **size of the data type**.
- `ptr++` increases the address by `sizeof(type)`, not just by 1.

---

## **Example** (Code + Output)

```c
#include <stdio.h>
int main() {
    int arr[5] = {10, 20, 30, 40, 50};
    int *ptr = arr;
    // Access elements using pointer
    printf("%d %d\n", arr[2], *(arr + 2)); // Output: 30 30
    printf("%d %d\n", ptr[3], *(ptr + 3)); // Output: 40 40
    ptr++;  // Now points to arr[1]
    printf("%d\n", *ptr);                  // Output: 20
    ptr = ptr + 2; // Now points to arr[3]
    printf("%d\n", *ptr);                  // Output: 40
    printf("Difference: %ld\n", (arr+4) - ptr); // Output: 1
    return 0;
}
```
**Output:**
```
30 30
40 40
20
40
Difference: 1
```

---

### **Summary Table**

| Statement     | Meaning                         |
| ------------- | ------------------------------- |
| `arr[i]`      | Equivalent to `*(arr + i)`      |
| `ptr = arr;`  | Points to `arr[0]`              |
| `*(ptr + i)`  | Value at `arr[i]`               |
| `ptr++`       | Move pointer to next element    |
| `ptr2 - ptr1` | Number of elements between them |

---

**In short:** Arrays and pointers are closely related in C. Pointer arithmetic enables efficient array element access and manipulation using pointers.

## **Pointers vs Arrays in C**

| **Aspect**                | **Pointer**                                                 | **Array**                                               |
|---------------------------|-------------------------------------------------------------|---------------------------------------------------------|
| **Definition**            | Variable that stores address of another variable            | Collection of fixed-size, same-type elements            |
| **Declaration**           | `int *p;`                                                   | `int arr[5];`                                           |
| **Initialization**        | Needs to be assigned a valid address, e.g., `p = &x;`       | Allocated at definition; elements auto-allocated        |
| **Memory Allocation**     | Can be done at runtime using `malloc()`                     | Done at compile time, size must be known                |
| **Access**                | `*p` accesses value pointed to by `p`                       | `arr[i]` accesses element at index `i`                  |
| **Address**               | Value held is an address                                    | `arr` is address of first element (`&arr[0]`)           |
| **Indexing**              | Not inherently supported, but possible with arithmetic      | Directly supports indexing with brackets                |
| **Pointer Arithmetic**    | Supports arithmetic (`p+1`, `p++`, etc.)                   | Array name can be used in arithmetic; `arr+i`           |
| **Relationship**          | Can point to an array or its elements                       | Array name acts as a constant pointer to its first elem.|
| **Reassignment**          | Pointer variable can be reassigned to point elsewhere       | Array name/address cannot be changed after declaration  |
| **Size Flexibility**      | Flexible, can point to arrays of any size/dynamic memory    | Size fixed at declaration and cannot change             |
| **Example**               | `int *p = arr; p++;`                                       | Access via `arr[i]` or `*(arr + i)`                     |
| **Function Passing**      | Pointer can be passed to functions easily                   | Array decays to pointer when passed to functions        |
| **Address Operator**      | Can use `&p` (address of pointer itself)                    | `&arr[0]` gives address of first element                |
| **Multi-level**           | Can have pointer to pointer (`int **pp;`)                   | Arrays of pointers also possible (`int *arr[5];`)       |

---

### **Key Exam Points:**

- **Similarities:**  
  - Array name can be used as a pointer (`ptr = arr;`).
  - `arr[i]` is equivalent to `*(arr + i)`.

- **Differences:**  
  - Pointer can be reassigned, array name cannot.
  - Size of pointer variable is always fixed (usually 4/8 bytes), but array size is total element size.
  - Array elements are stored contiguously, pointer could point anywhere.

---

### **Sample Code**

```c
int arr[3] = {10, 20, 30};
int *p = arr;
printf("%d %d\n", arr[1], *(p + 1)); // Output: 20 20
p = &arr[2]; // OK
// arr = p; // ERROR: cannot assign to array name
```

---

**In summary:**  
- **Arrays** and **pointers** are closely related in C, but not the same.  
- Pointers are flexible and can point to any data, while arrays are fixed and always point to the same memory block.
- Understanding the differences is crucial for effective C programming, especially for memory management and function calls.