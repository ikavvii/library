## Usage of Preprocessor Commands in C

Preprocessor commands (directives) are instructions to the compiler, executed before the actual compilation of code begins.

| **Preprocessor Command** | **Syntax**                    | **Usage/Purpose**                                               | **Example**                |
|-------------------------|-------------------------------|-----------------------------------------------------------------|----------------------------|
| Macro definition        | `#define`                     | Define constants or macros (code fragments)                      | `#define PI 3.14`<br>`#define SQUARE(x) ((x)*(x))` |
| File inclusion          | `#include`                    | Include header files (standard or user-defined)                  | `#include <stdio.h>`       |
| Conditional compilation | `#ifdef`, `#ifndef`, `#endif` | Compile certain parts of code conditionally                      | `#ifdef DEBUG ... #endif`  |
| Macro undefine          | `#undef`                      | Remove previously defined macro                                  | `#undef PI`                |
| Line control            | `#line`                       | Change line numbers for error messages                           | `#line 100 "myfile.c"`     |
| Error generation        | `#error`                      | Display custom error message during compilation                  | `#error Version not supported!` |
| Pragma directive        | `#pragma`                     | Special commands to the compiler (non-standard)                  | `#pragma once`             |

---

## Macros vs. Functions in C (Differences)

| **Aspect**           | **Macros**                                                  | **Functions**                                        |
|----------------------|-------------------------------------------------------------|------------------------------------------------------|
| **Definition**       | Defined using `#define` (preprocessor directive)            | Defined using `return_type name(args) { ... }`       |
| **Type Checking**    | No type checking; simple textual substitution               | Type checking is done by compiler                    |
| **Compilation Stage**| Replaced during preprocessing (before compilation)          | Compiled as part of source code                      |
| **Usage Example**    | `#define SQUARE(x) ((x)*(x))`                               | `int square(int x) { return x*x; }`                  |
| **Parameter Evaluation** | Parameters may be evaluated multiple times               | Parameters evaluated once                            |
| **Debugging**        | Harder to debug (no symbol table)                           | Easier to debug and trace                            |
| **Code Size**        | May increase due to code expansion for every macro call     | Code size less (function exists once, calls reused)  |
| **Scope**            | Global (unless undefined)                                   | Has local scope and variables                        |
| **Recursion**        | Not possible                                                | Possible                                             |
| **Speed**            | Often faster (no function call overhead)                    | Typically a function call involves overhead          |
| **Side Effects**     | Risky if arguments have side effects (`SQUARE(i++)`)        | Evaluated safely once per call                       |
| **Best Use**         | Small, frequently used code fragments and constants         | Reusable, complex, type-safe operations              |

---

#### **Summary Statement**

- **Macros** are handled by the preprocessor and simply replace code, offering no type safety or single-evaluation guarantees.  
- **Functions** are managed by the compiler, support type safety, scoping, and recursion, but might run slightly slower due to function call overhead.  
- Use **macros** for constants or very simple code snippets and **functions** for logic that requires type safety and debugging.