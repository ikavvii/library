## Call by Value vs. Call by Reference (Address) in C

| **Aspect**                | **Call by Value**                                   | **Call by Reference (Address)**                           |
| ------------------------- | --------------------------------------------------- | --------------------------------------------------------- |
| **Definition**            | Function receives a **copy** of the actual argument | Function receives the **address** of the actual argument  |
| **Original Value Change** | **Not affected** (changes local to function)        | **Can be changed** (modification affects caller variable) |
| **Parameter Type**        | Actual data values (e.g., `int`, `float`)           | Pointer types (e.g., `int*`, `float*`)                    |
| **Usage**                 | `func(x);` where `void func(int y)`                 | `func(&x);` where `void func(int *y)`                     |
| **Memory Address**        | Argument and parameter have **different addresses** | Argument and parameter can point to **same address**      |
| **Safety**                | Safer (no unintended side effects)                  | Need caution (can change caller’s data unintentionally)   |
| **Overhead**              | More overhead for large data                        | Less overhead for large data (only address passed)        |
| **Suitable For**          | When data should not change after function call     | When function should modify original variable             |

---

## **Illustrative C Code**

| **Call by Value Example**   | **Call by Reference Example** |
| --------------------------- | ----------------------------- |
|                             |                               |
| # include <stdio.h>         | # include <stdio.h>           |
| void increment(int a) {     | void increment(int *a) {      |
| a = a + 1;                  | \*a = \*a + 1;                |
| printf("Inside: %d\n", a);  | printf("Inside: %d\n", *a);   |
| }                           | }                             |
| int main() {                | int main() {                  |
| int x = 5;                  | int x = 5;                    |
| increment(x);               | increment(&x);                |
| printf("Outside: %d\n", x); | printf("Outside: %d\n", x);   |
| return 0;                   | return 0;                     |
| }                           | }                             |
|                             |                               |
| **Output:**                 | **Output:**                   |
| Inside: 6                   | Inside: 6                     |
| Outside: 5                  | Outside: 6                    |

---

**Summary:**  
- In **call by value**, changes in the function do **not** affect the original variable.  
- In **call by reference (address)**, changes in the function **do** affect the original variable, since the function works on its address.