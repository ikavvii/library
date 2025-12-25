## Header Files vs Library Files

| **Aspect**             | **Header File (`.h`)**                           | **Library File (`.lib`, `.a`, `.so`, `.dll`)**           |
|------------------------|--------------------------------------------------|----------------------------------------------------------|
| **File Extension**     | `.h`                                             | `.lib`, `.a`, `.so`, `.dll`                              |
| **Contents**           | Function prototypes, macro definitions, datatype, constants, structure definitions | Function definitions (compiled code), object files, pre-compiled functions |
| **Purpose**            | Provides declarations and interface information  | Provides implementation (actual code) for functions      |
| **Usage**              | Included in source code via `#include`           | Linked at compile or runtime by linker or loader         |
| **Compilation**        | Not compiled separately; processed by preprocessor| Compiled separately into binary (object code or executable code) |
| **Required For**       | Checking syntax and allowing compiler to recognize symbols| Providing the actual code to execute linked functions     |
| **Example**            | `stdio.h`, `math.h`                              | `libm.a` (static), `msvcrt.dll`, `libc.so` (shared)      |
| **Visibility**         | Only visible to source files where included      | Can be shared by multiple programs                       |
| **Modification**       | Can be edited by programmer                      | Usually not modified; provided as part of development kits or OS |
| **Role in Compilation**| Included in stage before compilation (preprocessing) | Used by linker after compilation to resolve references   |

---

**Summary:**
- **Header files** describe "what" is in a library (prototypes/signatures/interface).
- **Library files** provide "how" things work (definitions/binary code/implementations).
- Both are essential for modular C programming.