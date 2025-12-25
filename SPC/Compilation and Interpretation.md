## Compiled vs Interpreted Languages

| **Aspect**          | **Compiled Languages**                     | **Interpreted Languages**                   |
|---------------------|--------------------------------------------|---------------------------------------------|
| **Execution Process** | Source code is translated to machine code before execution | Source code is executed line-by-line by an interpreter |
| **Output**          | Standalone executable/binary               | No standalone binary; interpreter runs the code |
| **Translation Time**| Compile time (before running)              | Runtime (while the program executes)        |
| **Performance**     | Faster execution; direct machine code      | Slower (extra overhead for interpretation)  |
| **Error Detection** | Errors caught at compile time              | Errors caught at runtime                    |
| **Portability**     | Executable is platform-specific            | Code is portable if interpreter exists      |
| **Examples**        | C, C++, Rust, Go, Java (to bytecode)       | Python, JavaScript, Ruby, PHP               |
| **Modification**    | Must recompile after code changes          | Can run modified code immediately           |
| **Distribution**    | Distribute executable                      | Distribute source code; needs interpreter   |
| **Debugging**       | May require recompilation after fixes      | Easier to debug (immediate feedback)        |
| **Use Cases**       | Large apps, performance-critical systems   | Scripting, rapid prototyping, web           |

---

## Summary

- **Compiled languages** translate code to machine instructions and run fast, but require compilation for changes and limited portability.
- **Interpreted languages** run code directly with slower performance, but offer flexibility, portability, and easier debugging.
- Use compiled for speed and performance; use interpreted for convenience and rapid development.