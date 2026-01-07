## Difference between Static and Dynamic Memory Allocation in C

| **Aspect**                  | **Static Memory Allocation**                  | **Dynamic Memory Allocation**                      |
| --------------------------- | --------------------------------------------- | -------------------------------------------------- |
| **Definition**              | Memory size is decided at compile time        | Memory size is determined at run time              |
| **Allocation Done By**      | Compiler                                      | User/programmer via functions                      |
| **Memory Allocation Time**  | Compile time                                  | Run time (during program execution)                |
| **Memory Size**             | Fixed, cannot be changed during execution     | Flexible, can be changed while program runs        |
| **Memory Allocation Place** | Stack or data segment                         | Heap segment                                       |
| **Lifetime**                | Entire program or till block/function ends    | Till memory is freed (using `free()`/`delete`)     |
| **Access Method**           | Direct (using variable names)                 | Indirect (using pointers)                          |
| **Example Declaration**     | `int arr[10];`                                | `int *arr = (int*)malloc(10 * sizeof(int));`       |
| **Functions Used**          | Not required (compiler handles automatically) | `malloc()`, `calloc()`, `realloc()`, `free()`      |
| **Deallocation Required**   | No (handled automatically)                    | Yes (must explicitly call `free()`/`delete`)       |
| **Storage Class Example**   | `auto`, `static`                              | Variables created with memory allocation functions |
| **Risk**                    | Less, but can waste memory                    | Possible memory leaks if not freed                 |
| **Speed**                   | Faster (less overhead)                        | Slightly slower (overhead due to allocation)       |

---

## Functions Used for Dynamic Memory Allocation in C

| **Function** | **Purpose**                                 | **Header File** | **Syntax Example**                     |
| ------------ | ------------------------------------------- | --------------- | -------------------------------------- |
| `malloc()`   | Allocates single block of memory            | `<stdlib.h>`    | `ptr = (int*)malloc(n * sizeof(int));` |
| `calloc()`   | Allocates multiple blocks, initialized to 0 | `<stdlib.h>`    | `ptr = (int*)calloc(n, sizeof(int));`  |
| `realloc()`  | Changes size of previously allocated block  | `<stdlib.h>`    | `ptr = realloc(ptr, new_size);`        |
| `free()`     | Releases previously allocated memory        | `<stdlib.h>`    | `free(ptr);`                           |

---

**Note:**  
- *Static allocation is suitable when the memory size is known in advance.*
- *Dynamic allocation is flexible and suitable when memory needs vary at runtime, but must be managed carefully to avoid leaks.*