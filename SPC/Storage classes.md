
| Feature                  | **auto**          | **static (internal)** | **static (external)** | **extern**          | **register**       |
| ------------------------ | ----------------- | --------------------- | --------------------- | ------------------- | ------------------ |
| **Scope**                | Block/Local       | Block/Function        | File                  | Global (multi-file) | Block/Local        |
| **Lifetime**             | Block execution   | Entire program        | Entire program        | Entire program      | Block execution    |
| **Default Value**        | Garbage           | 0                     | 0                     | 0                   | Garbage            |
| **Storage**              | Stack             | Data segment          | Data segment          | Data segment        | CPU Register/Stack |
| **Keyword**              | `auto` (optional) | `static`              | `static`              | `extern`            | `register`         |
| **Address operator (&)** | ✅ Yes             | ✅ Yes                 | ✅ Yes                 | ✅ Yes               | ❌ No               |
| **Initialization**       | Every call        | Once                  | Once                  | Once                | Every call         |
