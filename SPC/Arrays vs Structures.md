## Arrays vs Structures in C

| **Aspect**             | **Arrays**                                                    | **Structures**                                               |
| ---------------------- | ------------------------------------------------------------- | ------------------------------------------------------------ |
| **Definition**         | Collection of elements of the **same data type**              | Collection of variables (**members**) of **different types** |
| **Syntax Example**     | `int arr[5];`                                                 | `struct Student { int roll; char name[20]; };`               |
| **Element Access**     | By index: `arr[0]`, `arr[1]`, ...                             | By member name: `s.roll`, `s.name`                           |
| **Memory Allocation**  | **Contiguous memory** for all elements                        | Memory layout depends on order and type of members           |
| **Homogeneity**        | Homogeneous (all elements must be same type)                  | Heterogeneous (members can be of different types)            |
| **Size Calculation**   | `n × size of datatype` (e.g., 5 × 4 bytes = 20 bytes)         | Sum of sizes of all members (plus padding, if any)           |
| **Example Use**        | Storing list of marks, temperatures, etc.                     | Representing an entity (student, employee, book, etc.)       |
| **Element Naming**     | Individual elements have **no special names** (just by index) | Each member has its **own name**                             |
| **Initialization**     | `int arr[3] = {1, 2, 3};`                                     | `struct Point p = {2, 3};`                                   |
| **Function Passing**   | Passed as single pointer to first element                     | Whole structure or address can be passed to function         |
| **Nested Definition**  | Multidimensional arrays allowed (e.g., `arr[3][4]`)           | Structures can have arrays and other structures as members   |
| **Data Structure Use** | Not suitable for complex/record-like data                     | Useful for designing records or user-defined data types      |
| **Flexibility**        | Less flexible (type fixed)                                    | More flexible (can mix types, arrays as members, etc.)       |

---

**Summary:**
- **Arrays** are simple and efficient for handling collections of same-type data.
- **Structures** provide flexibility to group related but different data types into a single unit for modeling real-world entities.