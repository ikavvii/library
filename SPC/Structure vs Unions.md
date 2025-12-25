## **Structures vs Unions in C**

| **Aspect**         | **Structure (`struct`)**                                  | **Union (`union`)**                                      |
| ------------------ | --------------------------------------------------------- | -------------------------------------------------------- |
| **Syntax**         | `struct Tag { ... }`                                      | `union Tag { ... }`                                      |
| **Memory Usage**   | Allocates **separate memory for each member**             | All members **share the same memory location**           |
| **Total Size**     | **Sum** of sizes of all members (plus padding)            | **Size of the largest member** (plus padding)            |
| **Member Access**  | Can access **all members at the same time**               | Can access **only one member at a time**                 |
| **Data Storage**   | Stores **multiple values simultaneously**                 | Stores **one value at a time**                           |
| **Example**        |                                                           |                                                          |
|                    | <pre>struct Example {<br> int a;<br> float b;<br>};</pre> | <pre>union Example {<br> int a;<br> float b;<br>};</pre> |
| **Access Example** | `ex.a = 5; ex.b = 3.2;` (both valid independently)        | `ex.a = 5; ex.b = 3.2;` (second access overwrites first) |
| **Usage Scenario** | When different types of data are needed **together**      | When only **one** variable is used at a time             |
| **Example Output** | Both `ex.a` and `ex.b` retain their values                | Only the last stored value is reliable                   |

---

### **Illustration Example**

```c
struct S { int x; float y; };
union U { int x; float y; };

struct S s1;
union U u1;

s1.x = 10; s1.y = 3.5; // both members valid
u1.x = 10;
u1.y = 3.5; // u1.x is now overwritten!
```

---

| **Features**        | **Structure**             | **Union**          |
| ------------------- | ------------------------- | ------------------ |
| Memory (int+float)  | 8 bytes (4+4, for 32-bit) | 4 bytes (max[4,4]) |
| All members valid?  | Yes                       | No                 |
| Simultaneous store? | Yes                       | No                 |

---

**Summary:**  
- **Structures:** Use more memory, access all members, store all data.  
- **Unions:** Use less memory, access one member at a time, store one value at a time.