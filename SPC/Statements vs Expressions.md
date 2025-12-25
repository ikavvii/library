## Statement vs. Expression

| **Aspect**       | **Expression**                                                               | **Statement**                                                                          |
| ---------------- | ---------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| **Definition**   | A combination of variables, constants, and operators that **yields a value** | An instruction in a program that **performs an action** (may or may not yield a value) |
| **Purpose**      | To compute and produce a value                                               | To execute a task such as assignment, decision, looping, etc.                          |
| **Example**      | `a + b * 5`, `x - 7`, `(m > n)`                                              | `x = 10;`, `if (a > b) { ... }`, `return x;`                                           |
| **Result**       | Always produces a single value                                               | May not produce a value; causes an effect                                              |
| **Terminator**   | Not required to end with a semicolon                                         | Usually ends with a semicolon (except compound statements, blocks, control structures) |
| **Used In**      | Assignments, conditions, return statements, function arguments               | Anywhere an action/instruction is needed                                               |
| **Evaluated By** | Evaluated for their value                                                    | Executed for their effect                                                              |
| **Can Contain**  | Only expressions (cannot contain statements)                                 | May contain expressions                                                                |

---

### **In Short:**

- An **expression** computes a value.  
  *Example:* `x + y`, `a * (b + 2)`, `m > n`  
- A **statement** performs an action (it may contain expressions, but is a complete instruction).  
  *Example:* `z = x + y;`, `while (i < 10) { ... }`

---

**Easy rule:**  
- *Expressions* form the building blocks (values),  
- *Statements* are the complete sentences (actions) of the program.