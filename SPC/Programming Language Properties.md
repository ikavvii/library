| **Property**          | **Programmer Perspective**                                   | **Language Developer Perspective**                           |
| --------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| **Syntax**            | Prefer simplicity, readability, and minimal ambiguity        | Design for unambiguity, parser complexity, formal rules      |
| **Semantics**         | Consistency, predictability, minimal surprises               | Rigorous definition, formal semantics, corner case handling  |
| **Abstraction**       | Desirable for hiding complexity, easier code                 | Must define how abstractions map to lower-level constructs   |
| **Type System**       | Balance between safety and flexibility                       | Need consistency, completeness, type inference rules         |
| **Error Handling**    | Clear, helpful error messages; robust runtime behavior       | Mechanisms for reporting/handling errors in design/compile   |
| **Performance**       | Efficient execution, minimal overhead                        | Trade-off with complexity, must optimize implementation      |
| **Memory Management** | Automatic, safe, minimal manual intervention                 | Implement techniques (GC, RAII, manual) and integrations     |
| **Portability**       | Write once, run anywhere (across platforms)                  | Provide cross-platform runtime/standard library support      |
| **Tool Support**      | Availability of IDEs, debuggers, profilers, package managers | Develop toolchains, APIs, documentation, update support      |
| **Concurrency**       | Easy-to-use primitives (threads, async, etc.)                | Safe, scalable concurrency model, race conditions prevention |
| **Extensibility**     | Ability to use libraries/packages, maybe meta-programming    | Provide hooks for language growth (plugins, macros)          |
| **Documentation**     | Clear, helpful, updated, with examples                       | Must maintain official docs and ensure community clarity     |
| **Security**          | Safe defaults, protection from mistakes/vulnerabilities      | Embed safeguards, static/dynamic checking, sandboxing        |
| **Learning Curve**    | Prefer shallow learning curve, good tutorials                | Consider onboarding, provide learning resources              |
| **Community Support** | Active forums, libraries, tutorials available                | Foster adoption, maintain repository, help contributors      |
