## System Programming Languages vs Scripting Languages

| **Aspect**        | **System Programming Languages (e.g., C, C++)**    | **Scripting Languages (e.g., Python, Bash, JS)**      |
|-------------------|----------------------------------------------------|-------------------------------------------------------|
| **Purpose**       | Low-level programming, system-level tasks, OS/devices | High-level automation, rapid application and task scripting |
| **Features**      | - Compiled<br>- Static typing<br>- Direct memory & hardware access<br>- Manual memory management<br>- High speed/performance<br>- Strong type-checking | - Interpreted (usually)<br>- Dynamic typing<br>- Built-in high-level data types<br>- Automatic memory management<br>- Quick prototyping<br>- Easy syntax |
| **Flexibility**   | Less flexible, changes require recompilation; platform dependent | Highly flexible, modify at runtime; platform independent (portable) |
| **Performance**   | Very high (close to hardware)                      | Lower; depends on interpreter/runtime                 |
| **Development Speed** | Slower (write -> compile -> test cycle)          | Faster (write -> run immediately, interactive shells) |
| **Memory Management** | Manual (malloc/free in C)                         | Automatic (garbage-collected)                         |
| **Error Checking**| Compile-time (early detection)                      | Runtime (errors may appear during execution)           |
| **User Interface**| Limited (usually CLI/GUI libraries required)         | Strong built-in support for CLI/GUI/web                |
| **Portability**   | Less portable (machine/OS specific compilation)      | Highly portable (runs on any machine with interpreter) |
| **Integration**   | Calls OS- and hardware-level APIs, drivers, kernels  | Glues together system tools, APIs, and applications    |
| **Typical Use Cases** | OS, device drivers, embedded software, compilers, high-performance applications | Automation scripts, data processing, testing, website logic, task automation |
| **Examples**      | C, C++, Rust, ADA, assembly                         | Python, JavaScript, Bash, Perl, Ruby                  |

### **Exam Summary Points:**

- **System Programming Languages** (C) are used for performance-intensive, hardware-near, and OS-level tasks, where manual control is needed.
- **Scripting Languages** serve rapid development and gluing of programs, automating tasks, and lightweight applications where ease of use and speed of development are preferred.  
- Choice depends on requirements: speed, hardware control vs. productivity and flexibility.