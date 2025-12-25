## Specified vs Unspecified vs Undefined Behavior in C

| **Aspect**                | **Specified Behavior**                                    | **Unspecified Behavior**                                      | **Undefined Behavior**                               |
|---------------------------|----------------------------------------------------------|----------------------------------------------------------------|------------------------------------------------------|
| **Definition**            | Behavior that is **precisely defined** by the C standard | Behavior where the C standard allows **multiple possibilities**, but does not require which will occur | Behavior that is **not defined** by the C standard; anything can happen                |
| **Predictability**        | Fully predictable, consistent across all platforms        | Predictable, but may vary between implementations/runs        | Unpredictable; may crash, incorrect result, or seem to work, etc.                      |
| **Examples**              | Value of `x` after `x = 10;`                             | Order in which function arguments are evaluated                | Division by zero; using uninitialized variables; modifying a variable multiple times without sequence point |
| **Result**                | Always the same result                                   | Varies between compilers/platforms                             | No guarantee; could result in errors or security flaws                                 |
| **C Standard Status**     | Standard **guarantees** outcome                          | Standard allows different behaviors, but all are valid         | Standard allows "anything"; program may not work as intended                           |
| **Safe to Rely On?**      | Yes                                                      | Only if you don’t depend on which outcome occurs               | Never; should be avoided                                                               |
| **Sample Code**           | `int a = 5; a = a + 2;`  /* always 7 */                  | `printf("%d %d\n", f(), g());` <br/>(order of `f()` vs `g()` unspecified) | `int x; printf("%d", x);` (use of uninitialized variable)                   |

---

### **Short definitions:**
- **Specified:** Defined and guaranteed by the C standard.
- **Unspecified:** The standard allows several valid behaviors, but does not specify which one should occur.
- **Undefined:** The standard does not define what happens; the program could behave unexpectedly.

---

**Exam Tip:**  
Always write code that avoids unspecified and undefined behavior to ensure portable, safe, and predictable outcomes.