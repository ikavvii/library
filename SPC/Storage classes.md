## Storage Classes in C

| **Storage Class**            | **Keyword** | **Scope (Visibility)**  | **Lifetime (Duration)**  | **Default Value** | **Memory Location**               | **Example**                                 |
| ---------------------------- | ----------- | ----------------------- | ------------------------ | ----------------- | --------------------------------- | ------------------------------------------- |
| **Automatic**                | `auto`      | Local to block/function | Block/function execution | Garbage/undefined | Stack                             | `auto int a;`                               |
| **Register**                 | `register`  | Local to block/function | Block/function execution | Garbage/undefined | CPU Register/Stack                | `register int a;`                           |
| **Static (local/internal)**  | `static`    | Local to block/function | Entire program           | Zero (0)          | Data segment (global/static area) | `static int a;`                             |
| **Static (global/external)** | `static`    | File scope              | Entire program           | Zero (0)          | Data segment (global/static area) | `static int a = 5;` (outside all functions) |
| **Extern (External)**        | `extern`    | Global (across files)   | Entire program           | Zero (0)          | Data segment (global/static area) | `extern int a;`                             |

---

### **Key Points**

- **auto:** Default for local variables; rarely written explicitly; limited to block; uninitialized value.
- **register:** Suggests storing variable in CPU register for fast access; address cannot be taken.
- **static (local):** Variable retains value between function calls; initialized only once.
- **static (global):** Variable only visible within the file (file scope, not external linkage).
- **extern:** Used to declare a global variable defined in another file; does not allocate memory.

---

**Note:**  
- **Global variables** without any storage class specifier behave as `extern` by default.
- All static/extern variables are initialized to zero by default if not initialized explicitly.
- **auto** and **register** variables are typically allocated on the stack; **static** and **extern** use data segment.

| Feature                  | **auto**          | **static (internal)** | **static (external)** | **extern**          | **register**       |
| ------------------------ | ----------------- | --------------------- | --------------------- | ------------------- | ------------------ |
| **Scope**                | Block/Local       | Block/Function        | File                  | Global (multi-file) | Block/Local        |
| **Lifetime**             | Block execution   | Entire program        | Entire program        | Entire program      | Block execution    |
| **Default Value**        | Garbage           | 0                     | 0                     | 0                   | Garbage            |
| **Storage**              | Stack             | Data segment          | Data segment          | Data segment        | CPU Register/Stack |
| **Keyword**              | `auto` (optional) | `static`              | `static`              | `extern`            | `register`         |
| **Address operator (&)** | ✅ Yes             | ✅ Yes                 | ✅ Yes                 | ✅ Yes               | ❌ No               |
| **Initialization**       | Every call        | Once                  | Once                  | Once                | Every call         |
