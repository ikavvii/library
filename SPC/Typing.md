## Static Typing vs Dynamic Typing

| **Aspect**           | **Static Typing**                                 | **Dynamic Typing**                               |
|----------------------|--------------------------------------------------|--------------------------------------------------|
| **Definition**       | Variable types are checked at compile-time       | Variable types are checked at runtime            |
| **Errors Found**     | Type errors detected before execution            | Type errors only appear during execution         |
| **Examples**         | C, C++, Java, Rust, Go                           | Python, JavaScript, Ruby, PHP                    |
| **Declaration**      | Types must be specified or inferred before running| No type declaration needed; types assigned as code runs |
| **Type Safety**      | Higher; bugs caught early                        | Lower; bugs can go unnoticed until runtime       |
| **Performance**      | Faster – compiler can optimize code using type info| Slower - types resolved during execution         |
| **Flexibility**      | Less flexible; strict type rules                 | More flexible; can change type of variable anytime|
| **Refactoring**      | Easier, with stronger tool support               | Harder; tools have less info for checks          |
| **Common Usage**     | Large-scale, critical systems                    | Rapid prototyping, scripting, smaller projects   |
| **Variable Example** | `int x = 10;` (C, statically typed)              | `x = 10` (Python, dynamically typed)             |
| **Error Example**    | `int x = "hello"; // Compile error`              | `x = 10; x = "hello" // No error initially`      |
| **Learning Curve**   | Steeper (need to understand types)               | Gentler for beginners                            |

---

## **Summary**

- **Static typing** enforces types at compile-time, leading to safer, faster, and more predictable code.
- **Dynamic typing** checks types as the code runs, giving flexibility and speed of development, but can lead to runtime errors.  
- Static typing prevents errors early; dynamic typing is easier for quick changes and experimentation.  
- Choose static for robust systems; dynamic for rapid or flexible programs.