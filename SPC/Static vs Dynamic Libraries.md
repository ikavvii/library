## Static vs Dynamic Libraries in C

| **Aspect**                 | **Static Library (.lib / .a)**                        | **Dynamic Library (.dll / .so)**                |
|----------------------------|-------------------------------------------------------|-------------------------------------------------|
| **Extension (Windows/Unix)**| `.lib` (Windows), `.a` (Unix/Linux)                  | `.dll` (Windows), `.so` (Unix/Linux)            |
| **Linking Time**           | Compile/Link time                                     | Load/Run time                                   |
| **How Linked**             | Code from library is copied into executable at build   | Only references saved in executable; actual library loaded at runtime |
| **Resulting File Size**    | Larger (contains all needed library code)             | Smaller (code stays in separate file)           |
| **Memory Usage**           | Higher if multiple programs use the same library       | Lower; library code shared in memory            |
| **Update Process**         | Must recompile/relink app for library update           | Replacing `.dll`/`.so` file updates all apps    |
| **Portability**            | Self-contained executable; easier to distribute        | Needs library file present on destination system|
| **Performance**            | Slightly faster (no runtime linking)                  | Slightly slower (indirect calls, runtime linking)|
| **Dependency**             | No need for library at runtime                        | Needs the `.dll` or `.so` available at runtime  |
| **Usage Example**          | `gcc main.c mylib.a -o app`                           | `gcc main.c -lmylib -o app` and keep `libmylib.so` in search path   |
| **Function Export**        | All functions statically included                     | Can export only public symbols                  |
| **Typical Use Cases**      | Small utilities, embedded systems, static deployment  | Large applications, plug-ins, modular software  |

---

## Essential Explanations

### **Static Libraries:**
- **Created using:** `ar` (Unix `.a`), librarian (Windows `.lib`)
- **Usage in code:**  
  - Include library headers (`#include "lib.h"`)
  - Link at compile-time (`gcc main.c libfoo.a -o main`)
- **All required code is copied into your executable at build time.**
- **Result:** Big standalone executable, no need for external library at run.

### **Dynamic Libraries:**
- **Created using:** `gcc -shared -o libfoo.so foo.c` (Unix), or DLL tools on Windows
- **Usage in code:**  
  - Include library headers (`#include "lib.h"`)
  - Compile with linker flag (`gcc main.c -lfoo -o main`)
  - Make sure `.dll` (Windows) or `.so` (Linux) is available in system path at runtime
- **Only the reference is in your executable; actual code is loaded during execution.**
- **Can update/fix library without recompiling programs** (unless incompatible API).

---

## **Summary Table for Exams**

| **Static Library (.lib/.a)**               | **Dynamic Library (.dll/.so)**                 |
|--------------------------------------------|------------------------------------------------|
| Linked at compile-time                     | Linked at load/run-time                        |
| Becomes part of executable                 | Remains separate; loaded when needed           |
| No need for library at runtime             | Library must be present at execution           |
| Larger executable size                     | Smaller executable size                        |
| Update—must recompile all apps             | Update once; all apps benefit                  |

---

**Tip:**  
Static = code copied in, runs alone.  
Dynamic = code kept outside, runs with support.  
Use static for portability.  
Use dynamic for modularity and easy updates.