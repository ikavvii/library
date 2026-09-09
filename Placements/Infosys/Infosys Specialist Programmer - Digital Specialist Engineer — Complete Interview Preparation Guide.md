# Infosys Specialist Programmer / Digital Specialist Engineer  
## Complete Interview-Ready Preparation and Study Guide — 2027 Campus Hiring

---

# Target Role and Preparation Scope

Infosys currently describes the **Specialist Programmer** role as providing in-depth programming solutions across multiple technologies using strong coding and technical skills. Its Power Programmer hiring material also emphasizes coding assessments and **hands-on live coding interviews** covering a broad range of technologies.

Infosys also states that campus hires including **Digital Specialist Engineers and Specialist Programmers** undergo its Foundation Program, which covers technical fundamentals, enterprise technologies, professional skills, generative AI, and prompt engineering.

Recent August–September 2026 SP/DSE campus interview reports consistently describe:

- Live coding on Wingspan.
- Often two problems presented, with the candidate required to complete at least one within roughly 30 minutes.
- Follow-up optimization and complexity discussion.
- SQL queries and DBMS concepts.
- OOP and programming-language fundamentals.
- OS and computer-network questions.
- Project architecture and implementation discussion.
- REST/API questions.
- Dynamic programming, trees, graphs and other DSA topics.
- Generative AI, RAG, embeddings, prompt engineering and ML questions.
- Additional architecture/system-design depth for stronger SP evaluations.

## Preparation Priority

| Priority | Area | Required depth |
|---|---|---|
| **Critical** | DSA + live coding | Strong implementation and optimization ability |
| **Critical** | SQL + DBMS | Write queries without assistance and explain internals |
| **Critical** | Resume + projects | End-to-end technical defense |
| **High** | OOP + primary programming language | Concepts plus practical implementation |
| **High** | Operating Systems | Interview-level fundamentals |
| **High** | Computer Networks + REST | Fundamentals plus request-flow understanding |
| **High** | Generative AI + ML | Strong conceptual understanding |
| **High for SP** | System design | Fresher/intermediate architecture reasoning |
| **Supporting** | Behavioral | Clear evidence-based communication |

## Scope Boundary

### Prepare deeply

- Arrays and strings
- Hashing
- Two pointers
- Sliding window
- Binary search
- Sorting
- Linked lists
- Stack and queue
- Trees and BSTs
- Heaps
- Graphs
- Recursion
- Backtracking
- Greedy algorithms
- Dynamic programming
- SQL
- DBMS
- OOP
- Java or your declared primary language
- OS
- Networking
- REST APIs
- Basic system design
- Generative AI
- ML fundamentals
- Projects
- Behavioral interview

### Know at introductory level

- Tries
- Union-Find
- Minimum spanning trees
- Bellman-Ford
- Floyd-Warshall
- Strongly connected components
- Database sharding
- Distributed caching
- Message queues
- CAP theorem
- Microservices
- Vector databases
- Transformer architecture
- Model fine-tuning

### Usually unnecessary for this interview unless present on your resume

- Advanced competitive-programming mathematics
- Segment trees
- Fenwick trees
- Advanced network flow
- Computational geometry
- Advanced compiler construction
- Kernel programming
- Advanced distributed consensus such as Raft/Paxos
- Training large neural networks from scratch
- Detailed transformer mathematics

---

# Interview Preparation Method

For every technical subject, reach four levels of understanding:

- **Definition** — explain what the concept means.
- **Mechanism** — explain how it works.
- **Decision** — explain when you would use it.
- **Trade-off** — explain why another option might be better.

For example, knowing that a hash table provides average O(1) lookup is not enough.

You should also be able to explain:

- Why it is average rather than guaranteed O(1).
- What collisions are.
- How collisions are handled.
- Why hashing may be preferable to a balanced BST.
- When a BST is preferable.
- Memory implications.
- Language-specific implementations such as `HashMap`.

That depth is the standard to target throughout this guide.

---

# Data Structures and Algorithms

# Complexity Analysis

## Big-O

Big-O describes how resource consumption grows as input size grows.

Know these common classes:

| Complexity | Typical example |
|---|---|
| O(1) | Array index access |
| O(log n) | Binary search |
| O(n) | Linear scan |
| O(n log n) | Merge sort |
| O(n²) | Nested comparison loops |
| O(2ⁿ) | Many subset recursion problems |
| O(n!) | Generating all permutations |

## Time vs Space Complexity

Be prepared to discuss both.

Example:

- Storing elements in a `HashSet` may reduce an O(n²) duplicate check to approximately O(n).
- The improvement uses O(n) additional memory.

Interviewers often expect you to recognize this **time-space trade-off**.

## Amortized Complexity

Some operations are occasionally expensive but cheap on average across many operations.

Example:

- Appending to a dynamic array is amortized O(1).
- Occasionally the backing array must be resized and copied.

## Interview standard

For every coding solution state:

- Time complexity.
- Auxiliary space complexity.
- Why those complexities hold.
- Whether an asymptotically better solution exists.

---

# Arrays and Strings

## Core concepts

Arrays provide:

- Contiguous logical storage.
- O(1) indexing.
- O(n) insertion/deletion in the middle when shifting is required.

Strings require additional attention to:

- Immutability.
- Character frequencies.
- Substrings vs subsequences.
- Prefixes and suffixes.
- Palindromes.
- String builders.

## Essential patterns

- Linear scanning.
- Prefix sums.
- Frequency counting.
- Hashing.
- Sorting.
- Two pointers.
- Sliding window.
- Kadane's algorithm.

## Problems to master

- Two Sum.
- Maximum Subarray.
- Best Time to Buy and Sell Stock.
- Product of Array Except Self.
- Majority Element.
- Rotate Array.
- Merge Intervals.
- Longest Consecutive Sequence.
- Valid Anagram.
- Group Anagrams.
- Longest Common Prefix.
- Longest Substring Without Repeating Characters.

## Decision questions

### Hashing vs sorting

**Hashing**

- Usually O(n) expected time.
- Uses additional memory.
- Does not naturally preserve ordering.

**Sorting**

- Usually O(n log n).
- May allow lower auxiliary space depending on algorithm.
- Provides ordered data useful for subsequent two-pointer processing.

---

# Hashing

## Core idea

A hash function transforms a key into an index or bucket location.

Typical structures:

- Hash map.
- Hash set.

Typical use cases:

- Frequency counts.
- Duplicate detection.
- Lookup tables.
- Caching.
- Grouping.

## Collisions

Different keys can map to the same location.

Common strategies:

- Separate chaining.
- Open addressing.

## Hash table vs balanced BST

| Property | Hash table | Balanced BST |
|---|---|---|
| Search | Average O(1) | O(log n) |
| Ordering | No | Yes |
| Range queries | Poor | Good |
| Worst-case guarantee | Depends on implementation | O(log n) |
| Memory overhead | Often higher | Tree-node overhead |

## Java preparation

Know:

- `HashMap`
- `HashSet`
- `LinkedHashMap`
- `TreeMap`
- `TreeSet`

Oracle's Java collection documentation provides the standard collection implementations and their intended use.

Resource: [Java Collections implementations — Oracle](https://docs.oracle.com/javase/tutorial/collections/implementations/index.html?utm_source=chatgpt.com)

---

# Two Pointers

## Core idea

Maintain two indices instead of repeatedly examining every pair.

Common forms:

- One pointer at each end.
- Slow and fast pointers.
- Two arrays traversed simultaneously.

## Common problems

- Two Sum in sorted array.
- Remove duplicates.
- Move zeroes.
- Container With Most Water.
- Three Sum.
- Palindrome checking.
- Linked-list cycle detection.

## When it works

Two pointers are particularly useful when:

- The data is sorted.
- A monotonic relationship exists.
- You need to maintain boundaries.
- Repeated work can be avoided.

---

# Sliding Window

Recent Infosys campus experiences have included sliding-window style problems, so this deserves high priority.

## Fixed-size window

Used when the problem specifies exactly `k` consecutive elements.

Examples:

- Maximum sum subarray of size `k`.
- Average of each length-`k` window.

## Variable-size window

Used when the window expands and contracts according to a condition.

Examples:

- Longest substring without repeated characters.
- Minimum window satisfying a target.
- Longest subarray under a constraint.

## Core invariant

Always know:

- What information the current window stores.
- What makes the window invalid.
- When the left pointer should move.
- When the answer should update.

## Sliding window vs two pointers

Sliding window is a specialized two-pointer pattern where the region between the pointers represents a meaningful active range.

---

# Prefix Sum

## Core idea

Precompute cumulative sums.

For an array:

`prefix[i] = sum of elements from 0 through i`

Then a range sum can be answered in O(1).

## Useful for

- Range-sum queries.
- Subarray sums.
- Counting subarrays.
- Difference-array techniques.

## Alternative

Without preprocessing:

- Each range sum may require O(n).

With prefix sums:

- O(n) preprocessing.
- O(1) query.

---

# Binary Search

## Standard binary search

Applicable to sorted data.

Complexity:

- O(log n) time.
- O(1) iterative auxiliary space.

## More important interview pattern: binary search on answer

Sometimes the array itself is not being searched.

Instead, search a range of possible answers where a monotonic condition exists.

Examples:

- Minimum capacity required to ship packages.
- Minimum eating speed.
- Allocate books.
- Aggressive cows.
- Minimum maximum workload.

## Must understand

- Lower bound.
- Upper bound.
- First occurrence.
- Last occurrence.
- Search in rotated sorted array.
- Peak element.
- Binary search on answer.

## Common bug

Incorrect boundary updates can create infinite loops.

Be very clear about whether your interval is:

- Closed: `[low, high]`
- Half-open: `[low, high)`

---

# Sorting Algorithms

Know the mechanism, complexity and stability of the important algorithms.

| Algorithm | Best | Average | Worst | Stable | Extra space |
|---|---:|---:|---:|---|---|
| Bubble sort | O(n) | O(n²) | O(n²) | Yes | O(1) |
| Selection sort | O(n²) | O(n²) | O(n²) | Usually no | O(1) |
| Insertion sort | O(n) | O(n²) | O(n²) | Yes | O(1) |
| Merge sort | O(n log n) | O(n log n) | O(n log n) | Yes | O(n) |
| Quick sort | O(n log n) | O(n log n) | O(n²) | Usually no | Depends on recursion |
| Heap sort | O(n log n) | O(n log n) | O(n log n) | No | O(1) |

## Merge sort

Understand:

- Divide array.
- Sort both halves recursively.
- Merge sorted halves.

Advantages:

- Guaranteed O(n log n).
- Stable.

Disadvantages:

- O(n) additional array storage in conventional implementations.

Recent Infosys candidates have specifically reported being asked to dry-run merge sort.

## Quick sort

Advantages:

- Excellent practical performance.
- Usually in-place apart from recursion.

Disadvantages:

- Poor pivot selection can produce O(n²).

---

# Linked Lists

## Concepts

- Singly linked list.
- Doubly linked list.
- Circular list.
- Head and tail.
- Pointer/reference manipulation.

## Complexity

| Operation | Array | Linked list |
|---|---:|---:|
| Random access | O(1) | O(n) |
| Insert at known node | O(n) shifting | O(1) |
| Search | O(n) | O(n) |

## Essential problems

- Reverse linked list.
- Middle node.
- Detect cycle.
- Find cycle start.
- Merge sorted lists.
- Remove nth node from end.
- Intersection of two lists.
- Palindrome linked list.

## Floyd cycle detection

Use:

- Slow pointer moving one step.
- Fast pointer moving two steps.

If a cycle exists, they eventually meet.

Advantages:

- O(n) time.
- O(1) space.

Alternative:

- Store visited nodes in a hash set.
- Easier conceptually but requires O(n) space.

---

# Stack

## Principle

Last In, First Out.

## Applications

- Function calls.
- Parentheses matching.
- Expression evaluation.
- Undo operations.
- DFS.
- Monotonic stacks.

## Essential problems

- Valid Parentheses.
- Min Stack.
- Next Greater Element.
- Largest Rectangle in Histogram.
- Daily Temperatures.

Recent SP/DSE interview reports include Valid Parentheses as a live-coding problem.

---

# Queue and Deque

## Queue

First In, First Out.

Used in:

- BFS.
- Task scheduling.
- Producer-consumer systems.

## Deque

Allows insertion/removal from both ends.

Used in:

- Sliding Window Maximum.
- Monotonic queue techniques.

---

# Trees

Trees are explicitly part of the Infosys preparation scope and remain a common coding-interview topic.

## Terminology

Know:

- Root.
- Parent.
- Child.
- Leaf.
- Height.
- Depth.
- Subtree.
- Balanced tree.

## Binary tree

Each node has at most two children.

## Binary Search Tree

For a valid BST:

- Left subtree values are smaller according to the chosen ordering.
- Right subtree values are larger.

Average operations can be O(log n) when balanced.

An unbalanced BST may degrade to O(n).

## Traversals

### DFS

- Preorder: root → left → right.
- Inorder: left → root → right.
- Postorder: left → right → root.

### BFS

- Level-order traversal using a queue.

## Essential problems

- Tree traversals.
- Maximum depth.
- Balanced binary tree.
- Diameter.
- Same tree.
- Symmetric tree.
- Validate BST.
- Lowest Common Ancestor.
- Level-order traversal.
- Construct tree from traversals.
- Maximum path sum.
- Kth smallest element in BST.

## AVL tree

An AVL tree is a self-balancing BST.

Balance factor:

`height(left subtree) - height(right subtree)`

Allowed values:

- -1
- 0
- 1

Rotations restore balance.

Recent campus reports have included AVL-tree discussion.

## Resource

GeeksforGeeks maintains a current tree interview collection covering concepts and problems from easy through hard.

[Tree interview preparation — GeeksforGeeks](https://www.geeksforgeeks.org/dsa/commonly-asked-interview-questions-on-tree/?utm_source=chatgpt.com)

---

# Heaps and Priority Queues

## Heap

A complete binary tree satisfying a heap property.

### Min heap

Parent ≤ children.

### Max heap

Parent ≥ children.

## Complexity

- Peek: O(1)
- Insert: O(log n)
- Delete root: O(log n)
- Build heap: O(n)

## Use when

You repeatedly need:

- Minimum.
- Maximum.
- Top K elements.
- Highest-priority task.

## Essential problems

- Kth largest element.
- Top K frequent elements.
- Merge K sorted lists.
- Find median from stream.
- K closest points.

---

# Recursion

## Core model

A recursive function requires:

- Base case.
- Recursive transition.
- Progress toward the base case.

## Interview concern

Understand the call stack.

Recursive DFS may require:

- O(h) stack for a tree of height `h`.
- O(n) in a worst-case skewed tree.

## Recursion vs iteration

Recursion:

- Often clearer for trees, DFS and backtracking.
- Uses call-stack memory.
- May encounter stack-depth limits.

Iteration:

- Provides explicit stack/queue control.
- Often avoids recursive stack overflow.
- Can be more verbose.

---

# Backtracking

## Core idea

Explore a decision.

If it cannot produce a valid solution:

- Undo the decision.
- Try another option.

Typical structure:

- Choose.
- Explore.
- Undo.

## Essential problems

- Subsets.
- Permutations.
- Combination Sum.
- N-Queens.
- Sudoku.
- Word Search.
- Generate Parentheses.
- Palindrome Partitioning.

## Backtracking vs dynamic programming

Backtracking:

- Explores possibilities.
- Often exponential.
- Useful for enumeration and constraint satisfaction.

Dynamic programming:

- Reuses solutions to overlapping states.
- Appropriate when repeated subproblems exist.

---

# Greedy Algorithms

## Core idea

Make the locally best decision and never reconsider it.

## Requirement

A greedy algorithm is valid only if the problem has the required mathematical structure.

Do not say:

> “This looks greedy.”

Explain why the local choice cannot make the global solution worse.

## Essential examples

- Activity Selection.
- Fractional Knapsack.
- Job Sequencing.
- Minimum Platforms.
- Huffman Coding.
- Kruskal's algorithm.
- Prim's algorithm.

## Greedy vs DP

Greedy:

- Faster and simpler when valid.
- Makes irreversible choices.

DP:

- Evaluates multiple states.
- More general.
- Usually costs more time and memory.

---

# Graphs

Graphs deserve **high priority** because they appear explicitly in your preparation instructions.

## Representations

### Adjacency list

Space:

- O(V + E)

Best for:

- Sparse graphs.

### Adjacency matrix

Space:

- O(V²)

Advantages:

- O(1) edge existence lookup.

Best for:

- Dense graphs or small V.

## BFS

Uses a queue.

Good for:

- Level traversal.
- Unweighted shortest path.
- Minimum number of moves.

Complexity with adjacency list:

- O(V + E)

## DFS

Uses recursion or explicit stack.

Good for:

- Connected components.
- Cycle detection.
- Topological processing.
- Backtracking.
- Tree/graph DP.

Complexity:

- O(V + E)

## Essential graph problems

- BFS.
- DFS.
- Number of Islands.
- Flood Fill.
- Rotten Oranges.
- Detect Cycle.
- Bipartite Graph.
- Course Schedule.
- Topological Sort.
- Number of Provinces.
- Dijkstra.
- Minimum Spanning Tree.
- Union-Find.

GeeksforGeeks' current graph interview guide covers BFS, DFS, cycle detection, Dijkstra, Bellman-Ford, topological sorting, MST and related problems.

[Graph interview guide — GeeksforGeeks](https://www.geeksforgeeks.org/dsa/commonly-asked-data-structure-interview-questions-on-graph/?utm_source=chatgpt.com)

---

# Shortest Path Algorithms

## BFS

Use for:

- Unweighted graph.
- Equal edge weights.

Complexity:

- O(V + E).

## Dijkstra

Use when:

- Edge weights are non-negative.

Typical implementation:

- Adjacency list.
- Min-priority queue.

Complexity:

- Approximately O((V + E) log V).

Do not use standard Dijkstra with negative edges.

## Bellman-Ford

Advantages:

- Supports negative edge weights.
- Can detect reachable negative cycles.

Disadvantages:

- O(VE), significantly slower than Dijkstra.

## Floyd-Warshall

Use when:

- Need shortest paths between all pairs.
- Graph is relatively small.

Complexity:

- O(V³).

---

# Topological Sorting

Applicable only to a **Directed Acyclic Graph**.

Methods:

- DFS finishing order.
- Kahn's algorithm using indegrees and BFS.

Typical problems:

- Course prerequisites.
- Build dependencies.
- Task ordering.

---

# Union-Find / Disjoint Set Union

Supports:

- `find`
- `union`

Optimizations:

- Path compression.
- Union by rank or size.

With both optimizations operations are effectively near constant time for practical input sizes.

Uses:

- Connectivity.
- Cycle detection.
- Kruskal's MST.
- Group merging.

---

# Dynamic Programming

This should receive significant preparation time because the official scope specifically lists:

- Knapsack.
- LCS.
- Palindromic subsequence.
- DP on trees.
- DP on graphs.

Recent interviews have also included climbing-stairs and partition-DP questions.

## How to derive DP

Do not memorize only code.

For every DP problem determine:

- State.
- Choices.
- Transition.
- Base cases.
- Evaluation order.
- Final answer.
- Possible space optimization.

## Memoization

Top-down recursion + cache.

Advantages:

- Natural transition from recursion.
- Computes only required states.

Disadvantages:

- Recursion overhead.
- Stack-depth limits.

## Tabulation

Bottom-up table.

Advantages:

- No recursion overhead.
- Often easier to optimize memory.

Disadvantages:

- May compute states never required.
- State ordering can be harder to derive.

## Essential DP families

### One-dimensional DP

Examples:

- Fibonacci.
- Climbing Stairs.
- House Robber.
- Maximum non-adjacent sum.

### Grid DP

Examples:

- Unique Paths.
- Minimum Path Sum.
- Triangle.

### Knapsack family

Know:

- 0/1 Knapsack.
- Unbounded Knapsack.
- Subset Sum.
- Partition Equal Subset Sum.
- Coin Change.

### String DP

Know:

- Longest Common Subsequence.
- Longest Common Substring.
- Edit Distance.
- Longest Palindromic Subsequence.
- Palindrome Partitioning.

### LIS

Longest Increasing Subsequence.

Know:

- O(n²) DP.
- O(n log n) optimization concept.

### Stock DP

State may include:

- Day.
- Holding/not holding.
- Transactions remaining.

### Interval / partition DP

Examples:

- Matrix Chain Multiplication.
- Burst Balloons.
- Palindrome partitioning.

### Tree DP

Use DFS to compute information from child subtrees.

Examples:

- Maximum path.
- Tree independent-set style problems.
- Diameter-like states.

### Graph DP

Most straightforward on DAGs after topological ordering.

## Resources

MIT's Introduction to Algorithms notes include BFS, DFS, Dijkstra, Bellman-Ford and multiple dynamic-programming lectures.

[MIT OpenCourseWare — Introduction to Algorithms lecture notes](https://ocw.mit.edu/courses/6-006-introduction-to-algorithms-fall-2011/pages/lecture-notes/?utm_source=chatgpt.com)

Stanford CS161 provides algorithm material covering graphs, greedy algorithms, dynamic programming, LCS and knapsack.

[Stanford CS161 lectures](https://cs161-stanford.github.io/lectures/?utm_source=chatgpt.com)

LeetCode maintains a dedicated dynamic-programming study plan focused on essential DP patterns.

[LeetCode Dynamic Programming Study Plan](https://leetcode.com/studyplan/dynamic-programming/?utm_source=chatgpt.com)

GeeksforGeeks maintains a current collection covering LCS, LIS, knapsack, edit distance, subset sum, coin change and other DP interview problems.

[Dynamic Programming interview problems — GeeksforGeeks](https://www.geeksforgeeks.org/dsa/top-20-dynamic-programming-interview-questions/?utm_source=chatgpt.com)

---

# DSA Practice Curriculum

## Foundation set

Be able to solve these comfortably:

- Two Sum.
- Valid Anagram.
- Contains Duplicate.
- Maximum Subarray.
- Best Time to Buy and Sell Stock.
- Binary Search.
- Valid Parentheses.
- Reverse Linked List.
- Linked List Cycle.
- Merge Two Sorted Lists.
- Maximum Depth of Binary Tree.
- BFS traversal.
- DFS traversal.
- Climbing Stairs.

## Intermediate set

- Longest Substring Without Repeating Characters.
- Three Sum.
- Product of Array Except Self.
- Merge Intervals.
- Search in Rotated Sorted Array.
- Group Anagrams.
- Top K Frequent Elements.
- Kth Largest Element.
- Lowest Common Ancestor.
- Validate BST.
- Number of Islands.
- Course Schedule.
- Dijkstra.
- Combination Sum.
- Generate Parentheses.
- House Robber.
- Coin Change.
- Longest Common Subsequence.
- Longest Palindromic Subsequence.

## SP-depth set

- Word Break.
- Edit Distance.
- Partition Equal Subset Sum.
- Matrix Chain Multiplication.
- Palindrome Partitioning.
- Tree DP problem.
- DAG DP problem.
- Strongly Connected Components.
- Union-Find problems.
- Minimum Spanning Tree.
- Advanced stock DP.
- Partition DP.

## Curated practice resources

LeetCode's Top Interview 150 provides 150 classic interview problems and is designed as a broad interview-preparation curriculum.

[LeetCode Top Interview 150](https://leetcode.com/studyplan/top-interview-150/?utm_source=chatgpt.com)

TakeUForward provides A2Z, SDE, Blind 75 and last-minute DSA sheets alongside core-CS material.

[TakeUForward DSA and Core CS resources](https://takeuforward.org/home?utm_source=chatgpt.com)

HackerRank offers structured interview preparation kits and timed practice.

[HackerRank Preparation Kits](https://www.hackerrank.com/interview/preparation-kits?utm_source=chatgpt.com)

---

# Live Coding Strategy

Recent campus reports make this part particularly important. Candidates have reported being shown two problems and being required to solve one within approximately 30 minutes.

## Before coding

State:

- What you understood.
- Input format.
- Output format.
- Constraints.
- Important edge cases.

## Explain a baseline

Briefly describe the straightforward solution.

Example:

> “A nested-loop solution would take O(n²). Since we need faster lookup, I can store previously seen values in a hash map and reduce expected complexity to O(n).”

## State the optimized approach

Explain:

- Data structure.
- Invariant.
- Why it works.
- Time complexity.
- Space complexity.

## Then code

Maintain:

- Meaningful variable names.
- Small logical blocks.
- Correct boundary handling.
- No unnecessary abstractions.

## Dry-run

Use at least:

- Normal case.
- Smallest case.
- Duplicate-heavy case.
- Boundary case.

## Debug systematically

Inspect:

- Initialization.
- Loop boundaries.
- Pointer updates.
- Duplicate handling.
- Null/empty inputs.
- Integer overflow.
- Recursion base cases.
- Visited structures.
- DP initialization.

## What the interviewer evaluates

Not only:

- Whether the code runs.

Also:

- Problem decomposition.
- Algorithm selection.
- Complexity awareness.
- Ability to respond to hints.
- Ability to optimize.
- Communication while solving.

---

# Object-Oriented Programming

# Core OOP Concepts

## Encapsulation

Bundle data and behavior together while controlling access to internal state.

Benefits:

- Protect invariants.
- Reduce accidental modification.
- Hide implementation details.

## Abstraction

Expose essential behavior while hiding unnecessary implementation details.

Common mechanisms:

- Interfaces.
- Abstract classes.

## Inheritance

A subclass obtains behavior/state from a parent class.

Good for genuine **is-a** relationships.

Potential problem:

- Tight coupling.
- Fragile inheritance hierarchies.

## Polymorphism

The same interface can represent different implementations.

Example:

`PaymentProcessor processor`

could reference:

- `CardProcessor`
- `UPIProcessor`
- `NetBankingProcessor`

Oracle's modern Java learning site provides concise material on objects, classes, interfaces, packages and inheritance.

[Java OOP — Dev.java](https://dev.java/learn/oop/?utm_source=chatgpt.com)

---

# Composition vs Inheritance

## Inheritance

Advantages:

- Reuse common implementation.
- Natural modeling for true hierarchical relationships.

Disadvantages:

- Tight coupling.
- Changes in parent classes can affect subclasses.
- Deep hierarchies become difficult to reason about.

## Composition

An object contains another object and delegates work to it.

Advantages:

- Flexible.
- Easier testing.
- Lower coupling.
- Runtime substitution is easier.

Interview preference:

> Prefer composition when the relationship is “has-a”; use inheritance when a stable “is-a” relationship genuinely exists.

---

# Interface vs Abstract Class

## Interface

Use when defining a capability or contract.

Advantages:

- Allows multiple interfaces.
- Decouples implementation.

## Abstract class

Use when related subclasses should share:

- State.
- Constructors.
- Common implementation.

Interview question:

**Can an abstract class have a constructor?**

Yes.

Its constructor initializes the inherited portion of subclass objects.

---

# Overloading vs Overriding

## Overloading

Same method name, different parameters.

Resolved primarily at compile time.

## Overriding

Subclass supplies a new implementation with compatible signature.

Enables runtime polymorphism.

---

# SOLID Principles

## Single Responsibility Principle

A class should have one focused reason to change.

Bad design:

`UserService`

handling:

- Authentication.
- Email.
- PDF generation.
- Database access.
- Logging.

Better design separates these responsibilities.

## Open/Closed Principle

Software entities should allow extension without repeatedly modifying stable code.

Typical support:

- Interfaces.
- Polymorphism.
- Strategy pattern.

## Liskov Substitution Principle

A subtype should work wherever its parent abstraction is expected without violating expected behavior.

## Interface Segregation Principle

Prefer small focused interfaces over large interfaces that force implementations to support irrelevant methods.

## Dependency Inversion Principle

High-level modules should depend on abstractions rather than concrete low-level implementations.

---

# Factory Pattern

## Purpose

Centralize object creation and hide concrete implementation selection.

Example:

`NotificationFactory.create("EMAIL")`

might return:

- `EmailNotification`
- `SMSNotification`
- `PushNotification`

## Advantages

- Reduces coupling to constructors.
- Centralizes creation rules.
- Supports polymorphism.

## Disadvantages

- Adds classes and abstraction.
- Can be unnecessary for very simple object creation.

## Alternatives

- Direct constructor.
- Dependency injection.
- Builder pattern.

Refactoring.Guru provides diagrams, implementation examples and comparisons for creational patterns.

[Factory and creational design patterns](https://refactoring.guru/design-patterns/creational-patterns?utm_source=chatgpt.com)

---

# Singleton Pattern

## Purpose

Ensure only one instance of a class and provide controlled access to it.

## Possible use cases

- Shared application configuration.
- Coordinated service instance.
- Certain resource managers.

## Advantages

- Controlled single instance.
- Lazy initialization is possible.

## Disadvantages

- Global shared state.
- Harder unit testing.
- Concurrency complications.
- Can hide poor dependency structure.

Refactoring.Guru specifically identifies testing, global-state and multithreading concerns around Singleton.

[Singleton pattern — Refactoring.Guru](https://refactoring.guru/design-patterns/singleton?utm_source=chatgpt.com)

## Alternatives

- Dependency injection.
- Application-managed singleton scope.
- Explicit object ownership.

Interview-quality answer:

> “I know how Singleton works, but I would not automatically use it simply because a resource should be shared. Dependency injection with application-level lifecycle management often provides the same single-instance behavior while improving testability.”

---

# Java Interview Preparation

Current Infosys interviews have included Java internals such as `final`, static variables, static blocks, strings and memory concepts.

## Core language

Know:

- Primitive vs reference types.
- Pass-by-value.
- Classes and objects.
- Constructors.
- `this`.
- `super`.
- Access modifiers.
- `static`.
- `final`.
- Abstract class.
- Interface.
- Exceptions.
- Generics.
- Collections.

## `static`

A static member belongs to the class rather than an individual instance.

Know:

- Static field.
- Static method.
- Static block.
- Initialization timing.

## `final`

### Final variable

Reference/value cannot be reassigned after initialization.

Important:

```java
final ArrayList<Integer> list = new ArrayList<>();
list.add(10);
```

This is valid.

`final` prevents `list` from referencing another object.

It does **not** make the `ArrayList` immutable.

## String vs StringBuilder vs StringBuffer

### String

- Immutable.

### StringBuilder

- Mutable.
- Efficient repeated modification.
- Not synchronized.

### StringBuffer

- Mutable.
- Synchronized.
- Usually slower than `StringBuilder`.

## `==` vs `.equals()`

For objects:

- `==` checks whether references point to the same object.
- `.equals()` can compare logical equality when properly implemented.

## `hashCode()`

If two objects are equal according to `equals`, they must have the same hash code.

Essential when using:

- `HashMap`.
- `HashSet`.

## ArrayList vs LinkedList

### ArrayList

- Fast random access.
- Good cache locality.
- Usually preferred for general lists.

### LinkedList

- O(1) insertion/removal when the node position is already known.
- O(n) positional access.
- Additional node memory.

## HashMap

Know conceptually:

- Hashing.
- Buckets.
- Collision handling.
- `equals`.
- `hashCode`.
- Null handling.
- Average lookup behavior.

## Stack vs heap

### Stack

Commonly contains:

- Method frames.
- Local execution state.
- Local primitive values.
- References.

### Heap

Contains dynamically created objects.

Recent campus candidates have explicitly reported stack/heap and memory-leak questions.

## Garbage collection

Java automatically reclaims heap objects that are no longer reachable.

Do not say:

> “Java cannot have memory leaks.”

A Java application can retain references to objects it no longer needs, preventing reclamation.

## Current Java resource

Oracle's modern Java learning portal covers language basics, OOP, classes, interfaces, generics, strings and other fundamentals.

[Learn Java — Dev.java](https://dev.java/learn/?utm_source=chatgpt.com)

---

# DBMS and SQL

Current candidate reports and your preparation instructions both indicate that this is one of the highest-priority non-DSA areas. Recent candidates have reported multiple SQL queries in a single interview.

# Relational Database Fundamentals

## Table

Rows represent records.

Columns represent attributes.

## Primary key

Uniquely identifies a row.

Properties:

- Unique.
- Non-null.

## Foreign key

References a key in another table and represents a relationship.

## Candidate key

A minimal attribute set capable of uniquely identifying a row.

## Super key

Any attribute set capable of uniquely identifying a row, including non-minimal sets.

---

# Joins

## INNER JOIN

Returns matching rows from both tables.

## LEFT JOIN

Returns:

- Every row from left table.
- Matching right rows.
- NULL where no match exists.

## RIGHT JOIN

Opposite orientation of LEFT JOIN.

## FULL OUTER JOIN

Returns matching and unmatched rows from both sides.

## CROSS JOIN

Cartesian product.

## Self join

Joins a table with itself.

Typical example:

- Employee → manager relationships.

---

# GROUP BY and HAVING

`GROUP BY` creates groups.

Aggregate functions include:

- `COUNT`
- `SUM`
- `AVG`
- `MIN`
- `MAX`

`WHERE` filters rows before grouping.

`HAVING` filters groups after aggregation.

---

# Logical SQL Execution Order

Know approximately:

`FROM / JOIN`

→ `WHERE`

→ `GROUP BY`

→ `HAVING`

→ `SELECT`

→ `DISTINCT`

→ `ORDER BY`

→ `LIMIT / OFFSET`

This explains many SQL behavior questions.

---

# Subqueries and CTEs

## Subquery

A query nested inside another query.

## CTE

Defined using `WITH`.

Advantages:

- Readability.
- Logical decomposition.
- Recursive CTE support where applicable.

Trade-off:

A CTE is not automatically faster than a subquery; optimizer behavior and database implementation matter.

---

# Window Functions

Your preparation mail specifically calls out window functions and `DENSE_RANK`.

Window functions compute values across related rows without collapsing rows into one result like ordinary aggregation. PostgreSQL's documentation explains this distinction directly.

## Essential functions

- `ROW_NUMBER()`
- `RANK()`
- `DENSE_RANK()`
- `LAG()`
- `LEAD()`
- `SUM() OVER(...)`
- `AVG() OVER(...)`

## ROW_NUMBER

Every row receives a unique sequential number.

## RANK

Ties receive the same rank, with gaps afterward.

Example ranks:

`1, 2, 2, 4`

## DENSE_RANK

Ties receive the same rank without gaps.

Example:

`1, 2, 2, 3`

## Second-highest salary

A robust conceptual approach:

```sql
SELECT salary
FROM (
    SELECT salary,
           DENSE_RANK() OVER (ORDER BY salary DESC) AS rnk
    FROM employees
) x
WHERE rnk = 2;
```

If employee rows rather than salary values are required, return the relevant employee columns while ranking salaries.

## Resource

[PostgreSQL Window Functions documentation](https://www.postgresql.org/docs/current/functions-window.html?utm_source=chatgpt.com)

---

# Normalization

## Purpose

Reduce:

- Redundancy.
- Update anomalies.
- Insertion anomalies.
- Deletion anomalies.

## First Normal Form

Values should be atomic.

## Second Normal Form

Must satisfy 1NF and remove partial dependency on part of a composite key.

## Third Normal Form

Must satisfy 2NF and remove transitive dependency of non-key attributes on other non-key attributes.

## BCNF

Every determinant should be a candidate key.

## Normalization trade-off

Advantages:

- Better integrity.
- Less duplication.

Disadvantages:

- More joins.
- Sometimes increased query complexity.

For read-heavy analytical systems, selective denormalization may improve performance.

---

# ACID Properties

## Atomicity

Transaction completes fully or not at all.

## Consistency

Transaction preserves database rules and constraints.

## Isolation

Concurrent transactions behave according to the selected isolation guarantees.

## Durability

Committed changes survive system failures according to the database's persistence guarantees.

## Interview example: bank transfer

A transfer:

- Deducts from A.
- Adds to B.

Atomicity ensures that only one side cannot commit.

---

# Isolation Problems

Understand:

- Dirty read.
- Non-repeatable read.
- Phantom read.
- Lost update.

Know the common isolation levels conceptually:

- Read Uncommitted.
- Read Committed.
- Repeatable Read.
- Serializable.

Higher isolation:

- Stronger consistency.
- Potentially less concurrency or greater implementation cost.

---

# Indexes

An index is an auxiliary data structure that speeds specific lookups.

Common database indexes use tree structures such as B+ trees.

## Benefits

- Faster reads.
- Faster filtering.
- Faster joins.
- Potentially faster ordering.

## Costs

- Extra disk/storage.
- More work on INSERT.
- More work on UPDATE.
- More work on DELETE.
- Poorly chosen indexes may not be used.

## Good index candidates

Columns frequently used in:

- `WHERE`.
- `JOIN`.
- `ORDER BY`.
- Certain grouping queries.

## Index trade-off

Do not answer:

> “Index every column.”

Index design should follow actual query patterns.

---

# Query Optimization

If asked why a query is slow:

- Inspect the execution plan.
- Check full scans.
- Check available indexes.
- Check selectivity.
- Avoid unnecessary columns.
- Verify joins.
- Filter unnecessary rows.
- Avoid unnecessary repeated subqueries.
- Check sort operations.
- Check statistics.
- Measure again after optimization.

PostgreSQL's current SQL documentation includes indexing, concurrency control and `EXPLAIN`/performance sections.

[PostgreSQL SQL and performance documentation](https://www.postgresql.org/docs/current/sql.html?utm_source=chatgpt.com)

---

# SQL Practice Problems

Master queries involving:

- Second highest salary.
- Nth highest salary.
- Duplicate salaries.
- Duplicate rows.
- Employees earning above department average.
- Department with highest salary.
- Employee count per department.
- Departments having more than N employees.
- Employees without departments.
- Customers without orders.
- Consecutive values.
- Running total.
- Rank by department.
- Top three salaries per department.
- Delete duplicates.
- Latest record per user.
- Join three tables.

## Practice resources

SQLBolt provides interactive lessons covering SELECT, constraints, joins, NULLs, aggregates and SQL query execution order.

[SQLBolt interactive SQL lessons](https://sqlbolt.com/?utm_source=chatgpt.com)

LeetCode's SQL 50 contains 50 basic-to-intermediate interview-focused SQL questions.

[LeetCode SQL 50](https://leetcode.com/studyplan/top-sql-50/?utm_source=chatgpt.com)

For deeper database understanding, Carnegie Mellon's database-systems material covers SQL, storage, indexes, transactions, concurrency, recovery and query optimization.

[CMU 15-445 Database Systems](https://15445.courses.cs.cmu.edu/spring2026/?utm_source=chatgpt.com)

---

# Operating Systems

# Process vs Program

## Program

Passive executable instructions.

## Process

A running instance of a program with execution state and resources.

---

# Process vs Thread

## Process

Typically has its own:

- Address space.
- Resources.
- Execution context.

## Threads

Threads in the same process typically share:

- Heap/address space.
- Files and process resources.

Each thread has its own execution state such as:

- Stack.
- Registers.

MIT operating-systems material explicitly covers processes, threads, synchronization, deadlock, paging, virtual memory and file systems.

---

# Context Switch

The CPU stops executing one process/thread and resumes another.

Requires saving and restoring execution state.

Context switching has overhead because it performs management work rather than application work.

---

# CPU Scheduling

Know conceptually:

- FCFS.
- SJF.
- SRTF.
- Round Robin.
- Priority scheduling.

## FCFS

Simple.

Problem:

- Convoy effect.

## SJF

Minimizes average waiting time when burst durations are known accurately.

Problem:

- Future execution time is difficult to know.

## Round Robin

Good responsiveness for time-sharing systems.

Trade-off:

- Very small quantum → excessive context switching.
- Very large quantum → approaches FCFS.

---

# Concurrency and Race Conditions

A race condition occurs when program correctness depends on uncontrolled timing between concurrent operations.

Example:

Two threads execute:

`counter++`

This is not necessarily an atomic operation.

---

# Critical Section

Code that accesses shared mutable data and must obey synchronization requirements.

---

# Mutex

Provides mutual exclusion.

Typically only one thread can hold the mutex at a time.

---

# Semaphore

Maintains a counter controlling access to resources.

## Binary semaphore

Values conceptually limited to 0/1.

## Counting semaphore

Allows a specified number of concurrent users of a resource.

---

# Deadlock

A deadlock occurs when participants wait indefinitely for resources held by each other.

Classic necessary conditions:

- Mutual exclusion.
- Hold and wait.
- No preemption.
- Circular wait.

Preventing one condition can prevent classical deadlock.

---

# Paging

Virtual memory is divided into pages.

Physical memory is divided into frames.

The page table maps:

- Virtual page → physical frame.

Advantages:

- Avoids external fragmentation associated with contiguous allocation.

Costs:

- Page-table overhead.
- Translation overhead.
- Possible internal fragmentation.

---

# Virtual Memory

Provides each process with a virtual address space independent of direct physical-memory layout.

Benefits include:

- Isolation.
- Protection.
- Ability to use address spaces larger than immediately available physical RAM through paging mechanisms.

---

# Page Fault

Occurs when a referenced virtual page is not currently mapped in the required way, often requiring operating-system handling.

If the page must be loaded from secondary storage, the operation can be expensive.

---

# Thrashing

Occurs when excessive page faults cause the system to spend much of its time moving pages rather than performing productive computation.

---

# OS Resources

**Operating Systems: Three Easy Pieces** is a free university textbook organized around virtualization, concurrency and persistence.

[Operating Systems: Three Easy Pieces — Free Book](https://pages.cs.wisc.edu/~remzi/OSTEP/?utm_source=chatgpt.com)

MIT's Operating System Engineering course covers virtual memory, file systems, threads, context switching, kernels, interrupts, system calls and IPC.

[MIT Operating System Engineering](https://ocw.mit.edu/courses/6-1810-operating-system-engineering-fall-2023/?utm_source=chatgpt.com)

---

# Computer Networks

# OSI and TCP/IP Models

For interview purposes, understand the layers rather than memorizing names alone.

## Application

Examples:

- HTTP.
- DNS.
- SMTP.

## Transport

- TCP.
- UDP.

## Network

- IP.
- Routing.

## Data Link

- Ethernet.
- MAC addressing.

## Physical

- Transmission of bits through the physical medium.

---

# TCP vs UDP

## TCP

Characteristics:

- Connection-oriented.
- Reliable delivery.
- Ordered byte stream.
- Retransmission.
- Congestion control.

Suitable for:

- Web traffic.
- File transfer.
- Many transactional protocols.

## UDP

Characteristics:

- Connectionless.
- No built-in delivery guarantee.
- No built-in ordering.
- Lower protocol overhead.

Suitable for cases where:

- Low latency matters.
- The application handles loss/recovery.
- Occasional loss is acceptable.

Examples include some:

- Real-time media.
- DNS communication.
- Gaming protocols.

---

# TCP Handshake

Conceptually:

- SYN.
- SYN-ACK.
- ACK.

Purpose:

- Establish connection state.
- Synchronize sequence-number information.

---

# DNS

DNS translates domain names to network addressing information and stores several resource-record types.

Know:

- A.
- AAAA.
- CNAME.
- MX.
- NS.

DNS commonly uses UDP for ordinary queries but also uses TCP in specific situations. Kurose and Ross provide interactive DNS exercises covering this behavior.

---

# HTTP

HTTP is an application-layer request-response protocol.

Common methods:

- GET.
- POST.
- PUT.
- PATCH.
- DELETE.

## GET

Retrieve representation/data.

Should not normally modify server state as its intended semantics.

## POST

Create/process a subordinate resource or submit data depending on API semantics.

## PUT

Typically replaces the target resource representation.

Expected to be idempotent.

## PATCH

Partially updates a resource.

## DELETE

Requests resource removal.

Expected to be idempotent in HTTP semantics: repeated identical requests should have the same intended effect on server state.

---

# HTTP Status Codes

Know:

- `200 OK`
- `201 Created`
- `204 No Content`
- `400 Bad Request`
- `401 Unauthorized`
- `403 Forbidden`
- `404 Not Found`
- `409 Conflict`
- `500 Internal Server Error`
- `503 Service Unavailable`

---

# HTTPS and TLS

HTTPS means HTTP protected using TLS.

Provides:

- Encryption.
- Integrity protection.
- Server authentication using certificates.

---

# What Happens When You Enter a URL?

Be able to explain:

- Browser parses URL.
- DNS resolves the hostname.
- Connection is established.
- TLS handshake occurs for HTTPS.
- HTTP request is sent.
- Load balancer/reverse proxy may receive request.
- Application processes request.
- Application may access cache/database.
- Response is generated.
- Browser processes and renders content.

---

# REST APIs

Recent Infosys interviews have included REST API endpoint and parameter questions.

Understand:

- Resources.
- HTTP methods.
- Status codes.
- Path parameters.
- Query parameters.
- Request body.
- Headers.
- Authentication.
- Idempotency.

## Path parameter

Example:

`GET /users/42`

`42` identifies a resource.

## Query parameter

Example:

`GET /users?department=MCA`

Useful for:

- Filtering.
- Sorting.
- Pagination.

## Request body

Often contains structured input for POST, PUT or PATCH.

---

# Networking Resource

Kurose and Ross provide freely accessible online presentations and review material covering application, transport, network and link layers.

[Computer Networking: A Top-Down Approach — Online Lectures](https://gaia.cs.umass.edu/kurose_ross/online_lectures.htm?utm_source=chatgpt.com)

---

# Generative AI and Machine Learning

Infosys states that generative AI and prompt engineering are now part of its graduate Foundation Program, and current campus candidates have reported interview questions on RAG, embeddings, precision, recall, prompt engineering and fine-tuning.

# AI vs ML vs Deep Learning vs Generative AI

## Artificial Intelligence

Broad field concerned with systems performing tasks associated with intelligent behavior.

## Machine Learning

Systems learn patterns from data instead of relying entirely on manually specified rules.

## Deep Learning

Machine learning based on multi-layer neural networks.

## Generative AI

Models capable of producing new content such as:

- Text.
- Images.
- Code.
- Audio.

---

# Supervised Learning

Training data contains labeled input-output pairs.

Examples:

- Spam classification.
- House-price prediction.

---

# Unsupervised Learning

Training data does not provide explicit target labels.

Examples:

- Clustering.
- Dimensionality reduction.

---

# Classification vs Regression

## Classification

Predict categories.

Examples:

- Fraud/not fraud.
- Spam/not spam.

## Regression

Predict numerical values.

Examples:

- Price.
- Temperature.

---

# Training, Validation and Test Sets

## Training set

Used to fit model parameters.

## Validation set

Used to choose:

- Hyperparameters.
- Thresholds.
- Model variations.

## Test set

Used for final unbiased evaluation after model selection.

---

# Overfitting

Model learns training data too specifically and performs poorly on unseen data.

Possible remedies:

- More data.
- Regularization.
- Simpler model.
- Early stopping.
- Data augmentation where appropriate.

---

# Underfitting

Model is too simple or insufficiently trained to capture useful patterns.

---

# Confusion Matrix

Binary classification contains:

- True Positive.
- True Negative.
- False Positive.
- False Negative.

---

# Accuracy

`correct predictions / total predictions`

Can be misleading with heavily imbalanced classes.

---

# Precision

`TP / (TP + FP)`

Question answered:

> Of the examples predicted positive, how many were actually positive?

Use when false positives are particularly costly.

---

# Recall

`TP / (TP + FN)`

Question answered:

> Of all actual positive examples, how many were detected?

Use when false negatives are particularly costly.

Google's ML Crash Course discusses precision, recall, accuracy and their trade-offs, including why accuracy can fail for imbalanced datasets.

[Google ML Crash Course — Precision and Recall](https://developers.google.com/machine-learning/crash-course/classification/accuracy-precision-recall?utm_source=chatgpt.com)

---

# F1 Score

Harmonic mean of precision and recall.

Useful when both matter and class distribution makes accuracy inadequate.

---

# Neural Network Basics

Understand at interview level:

- Input layer.
- Hidden layers.
- Output layer.
- Weights.
- Bias.
- Activation function.
- Loss.
- Gradient descent.
- Backpropagation.

Detailed mathematical derivation is usually unnecessary unless your resume highlights ML research.

---

# Large Language Models

Know:

- Tokens.
- Context.
- Transformer.
- Attention.
- Pretraining.
- Inference.
- Temperature concept.
- Prompt.
- Embeddings.
- Hallucination.

---

# Tokens

Models process text as tokens rather than directly as human words.

A token can represent:

- Whole word.
- Part of a word.
- Punctuation.
- Other textual units.

---

# Embeddings

An embedding is a numerical vector representation of information.

Semantically related content tends to receive vectors that are closer according to the embedding model's representation.

Uses:

- Semantic search.
- Recommendation.
- Clustering.
- RAG.

Azure's current vector-search documentation describes vector search as matching numeric representations according to similarity and supports semantic and hybrid retrieval.

---

# Cosine Similarity

Measures similarity based on the angle between vectors.

Often used for comparing embeddings.

High cosine similarity generally indicates stronger directional similarity in the embedding space.

---

# Vector Database / Vector Index

Stores vectors and supports nearest-neighbor search.

Examples of systems/features commonly used for vector retrieval include:

- FAISS.
- Chroma.
- Pinecone.
- pgvector.
- Azure AI Search.
- Elasticsearch vector search.

Interview focus should be the architecture rather than memorizing vendor names.

---

# Retrieval-Augmented Generation

RAG grounds model generation using retrieved information.

Typical pipeline:

- Documents.
- Preprocessing.
- Chunking.
- Embeddings.
- Vector/search index.
- User query.
- Query embedding/search.
- Retrieve relevant chunks.
- Add retrieved information to model context.
- Generate answer.

Microsoft's description of RAG similarly includes converting documents into embeddings, storing them in searchable infrastructure, retrieving relevant chunks and supplying those chunks to an LLM.

## Advantages

- Knowledge can be updated without retraining the base model.
- Supports private/domain information.
- Can provide source grounding.
- Retrieval can reduce unsupported answers when designed well.

## Limitations

- Poor retrieval causes poor answers.
- Chunking affects quality.
- Embedding model affects retrieval.
- Context limits still matter.
- Additional latency and infrastructure.

## RAG vs fine-tuning

### RAG

Best when:

- Information changes frequently.
- Need access to private knowledge.
- Need grounding in documents.

### Fine-tuning

Best when:

- Need behavioral adaptation.
- Need domain-specific output style.
- Need stronger task-specific model behavior.

Fine-tuning should not normally be treated as a replacement for retrieving frequently changing factual information.

---

# Prompt Engineering

Focus on:

- Clear instructions.
- Context.
- Output constraints.
- Examples where useful.
- Separating instructions from reference data.
- Explicit success criteria.

OpenAI's current prompt-engineering guidance emphasizes clear instructions and appropriate prompt structure.

[OpenAI Prompt Engineering Best Practices](https://help.openai.com/en/articles/6654000-playground-and-prompt-engineering?utm_source=chatgpt.com)

---

# RAG Learning Resources

Microsoft's current RAG architecture guidance covers ingestion, embeddings, retrieval, indexing, vector/keyword/hybrid search and reranking.

[Microsoft Advanced RAG Architecture Guide](https://learn.microsoft.com/en-us/azure/developer/ai/advanced-retrieval-augmented-generation?utm_source=chatgpt.com)

Hugging Face provides practical RAG cookbooks covering document ingestion, embeddings, vector stores, retrieval and advanced RAG improvements.

[Hugging Face Advanced RAG Cookbook](https://huggingface.co/learn/cookbook/advanced_rag?utm_source=chatgpt.com)

---

# System Design for Specialist Programmer

For strong SP evaluations, prepare system design beyond definitions. Current interview reports indicate deeper architecture discussion for stronger candidates.

# System Design Interview Framework

When asked to design a system, cover:

- Functional requirements.
- Non-functional requirements.
- Core entities.
- APIs.
- High-level components.
- Database choice.
- Request/data flow.
- Scaling.
- Reliability.
- Security.
- Bottlenecks.
- Trade-offs.

---

# Functional vs Non-Functional Requirements

## Functional

What the system does.

For chat:

- Send message.
- Receive message.
- Group conversations.
- Message history.

## Non-functional

How well it must operate.

Examples:

- Availability.
- Latency.
- Scalability.
- Durability.
- Security.

---

# Vertical vs Horizontal Scaling

## Vertical

Increase resources of one machine.

Advantages:

- Simple.

Disadvantages:

- Hardware limit.
- Larger failure domain.
- Expensive at high scale.

## Horizontal

Add more machines.

Advantages:

- Greater scalability.
- Better fault distribution.

Disadvantages:

- Distributed-system complexity.
- Coordination.
- Load distribution.

---

# Load Balancer

Distributes traffic across multiple servers.

Benefits:

- Scalability.
- Availability.
- Failure isolation.

Common categories:

- Layer 4.
- Layer 7.

---

# Stateless Application Servers

A stateless server does not depend on process-local user session state between requests.

Benefits:

- Easier load balancing.
- Easier horizontal scaling.
- Easier replacement after failure.

Session data can be stored in:

- Shared database.
- Distributed cache.
- Token-based client/server mechanism depending on requirements.

---

# Cache

Stores frequently accessed data closer to the application.

Advantages:

- Lower latency.
- Reduced database load.

Problems:

- Stale data.
- Cache invalidation.
- Memory cost.
- Consistency complexity.

## Common strategies

### Cache-aside

Application:

- Checks cache.
- On miss, reads database.
- Stores result in cache.

### Write-through

Writes cache and backing store as part of the write path.

### Write-behind

Writes cache first and persists asynchronously.

Higher performance but increased durability/consistency complexity.

ByteByteGo provides a visual caching guide covering distributed cache, invalidation and cache strategies.

[ByteByteGo Cache Guide](https://bytebytego.com/guides/learn-cache/?utm_source=chatgpt.com)

---

# SQL vs NoSQL

## Relational database

Prefer when:

- Relationships matter.
- Transactions matter.
- Structured schema is useful.
- Complex joins are needed.

## NoSQL

Can be useful for:

- Flexible schemas.
- Specific access patterns.
- Very high horizontal scale.
- Key-value/document workloads.

Do not answer:

> “NoSQL is faster.”

Performance depends on:

- Workload.
- Schema.
- indexes.
- queries.
- consistency requirements.
- implementation.

---

# Replication

Copies data across nodes.

Benefits:

- Availability.
- Read scaling.
- Disaster recovery.

Costs:

- Replication lag.
- Consistency challenges.
- Failover complexity.

---

# Sharding

Partitions data across multiple database nodes.

Benefits:

- Horizontal storage growth.
- Increased aggregate throughput.

Costs:

- Complex joins.
- Rebalancing.
- Hot shards.
- Routing complexity.
- Cross-shard transactions.

---

# Message Queue

Allows asynchronous communication.

Uses:

- Email sending.
- Image processing.
- Notification processing.
- Background jobs.

Benefits:

- Decoupling.
- Traffic smoothing.
- Retry capabilities.

Costs:

- More infrastructure.
- Eventual processing.
- Duplicate delivery concerns.
- Ordering concerns.

---

# CDN

Caches content geographically closer to users.

Useful for:

- Images.
- CSS/JS.
- Video.
- Static content.

Reduces:

- Origin load.
- User latency.

---

# WebSocket vs HTTP

## HTTP request-response

Good for:

- Standard APIs.
- CRUD applications.

## WebSocket

Maintains a bidirectional connection.

Good for:

- Chat.
- Live updates.
- Collaborative editing.

Trade-off:

- Persistent connections increase connection-management complexity.

---

# Monolith vs Microservices

## Monolith

Advantages:

- Simple deployment.
- Easier transactions.
- Easier development for small teams.

Disadvantages:

- Large codebase may become difficult to manage.
- Independent scaling is harder.

## Microservices

Advantages:

- Independent deployment.
- Independent scaling.
- Team/service boundaries.

Disadvantages:

- Network failures.
- Distributed transactions.
- Observability complexity.
- Deployment complexity.
- Data consistency concerns.

Interview-quality position:

> Start with the simplest architecture satisfying requirements. Do not introduce microservices only because the system may become large someday.

---

# CAP Theorem

In the presence of a network partition, a distributed data system must make trade-offs between:

- Consistency.
- Availability.

Partition tolerance is generally unavoidable in distributed environments where partitions can occur.

Do not misuse CAP to claim that every database simply chooses two properties permanently.

---

# System Design Practice Problems

Prepare:

- URL shortener.
- Chat application.
- Notes application.
- File upload/storage service.
- Notification service.
- Social-media feed.
- Ride-booking service.
- College attendance system.
- Library management system.

For fresher interviews, emphasize:

- Clean requirements.
- Correct components.
- Data model.
- APIs.
- Scaling reasoning.
- Trade-offs.

## Resource

The open-source System Design Primer covers load balancing, caching, databases, replication, sharding, queues, communication protocols and common design trade-offs.

[System Design Primer — GitHub](https://github.com/donnemartin/system-design-primer?utm_source=chatgpt.com)

ByteByteGo's system-design blueprint covers major components including load balancing, API gateways, databases, caching, queues, scalability, availability and security.

[ByteByteGo System Design Blueprint](https://bytebytego.com/guides/system-design-blueprint-the-ultimate-guide/?utm_source=chatgpt.com)

---

# Project Preparation

Project discussion can become one of the longest sections of the interview.

Do not prepare only:

> “My project uses React, Node.js and MongoDB.”

Prepare the **complete engineering story**.

# Project Explanation Structure

## Problem

Explain:

- What problem exists.
- Who experiences it.
- Why solving it matters.

## Requirements

Separate:

- Functional requirements.
- Non-functional requirements.

## Architecture

Be able to draw:

`Client → API → Business Logic → Database → External Services`

Add relevant components such as:

- Authentication.
- Cache.
- Queue.
- Object storage.
- AI service.

## Data model

Know:

- Main entities.
- Primary keys.
- Foreign keys.
- Relationships.
- Indexes.

## API design

For each important feature know:

- Endpoint.
- Method.
- Request.
- Response.
- Authentication.
- Validation.

## Technology decisions

For every major technology answer:

- Why did you choose it?
- What alternative did you consider?
- What benefit did this choice provide?
- What drawback did it introduce?

---

# Project Technology Decision Matrix

Prepare a table like this for your project:

| Decision | Selected | Alternative | Why selected | Limitation |
|---|---|---|---|---|
| Database | PostgreSQL | MongoDB | Relational integrity | Schema less flexible |
| API | REST | GraphQL | Simpler client/API model | Multiple requests possible |
| Auth | JWT | Session | Stateless API use | Token revocation complexity |
| Deployment | Cloud VM | Serverless | Greater runtime control | More operations work |

---

# Project Security Questions

Expect:

- How do you authenticate users?
- Where are passwords stored?
- Why hash passwords?
- What is JWT?
- How do you prevent unauthorized access?
- How do you validate user input?
- How do you protect secrets?
- What is SQL injection?
- What is XSS?
- What is CORS?
- Why HTTPS?

---

# Project Scalability Questions

Prepare:

- What fails first at 10× traffic?
- What fails at 100× traffic?
- Can application servers scale horizontally?
- Where are sessions stored?
- Which queries are expensive?
- What can be cached?
- What work can become asynchronous?
- How would files be stored?
- How would the database scale?

---

# Project Failure Questions

Prepare real examples of:

- Difficult bug.
- Incorrect architectural choice.
- Performance issue.
- Integration problem.
- Deployment failure.
- Team disagreement.

For each explain:

- Symptom.
- Root cause.
- Investigation.
- Fix.
- Validation.
- Lesson.

---

# Project Questions to Rehearse

- Explain the project in two minutes.
- Explain the architecture.
- Draw the database schema.
- Why this database?
- Why this framework?
- Why REST?
- What did you personally implement?
- What was the hardest part?
- What was one bug you solved?
- What would you redesign?
- How do users authenticate?
- How do you handle invalid input?
- How is the project deployed?
- How would you support one million users?
- How do you test it?
- What security threats exist?
- How would you monitor production?
- What happens when the database is unavailable?

---

# Behavioral Interview Preparation

Behavioral evaluation is explicitly part of your interview process.

# Answer Structure

Use:

- Situation.
- Responsibility.
- Action.
- Result.
- Reflection.

Focus on **your contribution**.

Avoid answers where every sentence begins with:

> “We…”

The interviewer needs to understand what you personally did.

---

# Self-Introduction

Target approximately one minute.

Cover:

- Current education.
- Strongest technical interests.
- Relevant development skills.
- One or two strong projects.
- Problem-solving interest.
- Why this opportunity fits.

Avoid:

- Family biography.
- Reading every resume line.
- Generic adjectives without evidence.

---

# Why Infosys?

A technically grounded answer can refer to:

- Specialist programming career path.
- Live technical work.
- Structured graduate training.
- Exposure to enterprise technologies.
- Current emphasis on AI and modern engineering.

Infosys states that its campus Foundation Program spans more than 45 technology streams and includes recent additions such as generative AI and prompt engineering.

---

# Why Specialist Programmer?

A strong answer should connect the role to:

- Coding.
- Problem solving.
- Software engineering.
- Technical depth.
- Architecture.
- Continuous technical development.

Avoid basing the answer mainly on compensation.

---

# Strengths

Choose evidence-backed strengths.

Examples:

- Problem decomposition.
- Debugging.
- Learning unfamiliar technologies.
- Database design.
- Coding consistency.

Then provide one example.

---

# Weakness

Choose something genuine but manageable.

Good structure:

- Specific weakness.
- Its effect.
- Action being taken.
- Evidence of improvement.

Avoid disguised strengths such as:

> “I work too hard.”

---

# Common Behavioral Questions

- Tell me about yourself.
- Why Infosys?
- Why SP/DSE?
- Tell me about a difficult technical problem.
- Tell me about a disagreement.
- Tell me about a failure.
- Tell me about a deadline you struggled with.
- Describe a leadership experience.
- How do you learn a new technology?
- How do you handle pressure?
- Are you willing to relocate?
- Are you comfortable learning technologies outside your current stack?
- Where do you see your career developing?
- Why should we select you?

---

# Resume Preparation

Assume **every word is examinable**.

For every skill listed, prepare:

- Definition.
- Practical use.
- One example.
- Trade-off.
- Alternative.

If your resume contains:

`Docker`

Expect:

- Container vs VM.
- Image vs container.
- Dockerfile.
- Port mapping.

If it contains:

`MongoDB`

Expect:

- Document database.
- Collection/document.
- Index.
- MongoDB vs SQL.

If it contains:

`React`

Expect:

- Component.
- Props/state.
- Hooks.
- Virtual DOM.
- Client/server rendering depending on your project.

If it contains:

`AI/RAG`

Expect:

- Embeddings.
- Vector retrieval.
- Chunking.
- Similarity.
- Prompting.
- Hallucination.
- Evaluation.

Delete technologies that you cannot defend.

---

# Core REST and Backend Engineering Questions

Be ready to answer:

- What is REST?
- REST vs SOAP.
- GET vs POST.
- PUT vs PATCH.
- Authentication vs authorization.
- What is JWT?
- Cookie vs token.
- What is middleware?
- What is CORS?
- What is an API gateway?
- What happens when an API returns 500?
- How would you design pagination?
- How do you handle duplicate requests?
- What is idempotency?
- Why validate data server-side?

---

# High-Value Trade-Off Questions

Strong SP candidates should be able to discuss decisions, not just definitions.

## Array vs Linked List

Use array when:

- Random access matters.
- Memory locality matters.

Use linked list when:

- Frequent node-level insert/remove operations dominate.
- Random access is unnecessary.

## HashMap vs TreeMap

HashMap:

- Faster average lookup.
- No natural sorting.

TreeMap:

- Sorted keys.
- O(log n) operations.

## BFS vs DFS

BFS:

- Unweighted shortest path.
- Level traversal.

DFS:

- Deep traversal.
- Components.
- Cycle/topological patterns.

## Recursion vs Iteration

Recursion:

- Simpler hierarchical logic.

Iteration:

- Greater explicit control.
- Avoids recursion-depth issues.

## Greedy vs DP

Greedy:

- Simpler/faster when mathematically valid.

DP:

- Handles overlapping state choices where local decisions cannot safely commit.

## SQL vs NoSQL

SQL:

- Relations and transactions.

NoSQL:

- Flexible/access-pattern-specific distributed workloads.

## Monolith vs Microservices

Monolith:

- Simpler operationally.

Microservices:

- Independent scaling/deployment at substantial complexity cost.

## REST vs WebSocket

REST:

- Request-response APIs.

WebSocket:

- Real-time bidirectional interaction.

## RAG vs Fine-Tuning

RAG:

- Dynamic knowledge.

Fine-tuning:

- Behavioral adaptation.

## Cache vs Database

Cache:

- Fast but not normally the authoritative source.

Database:

- Persistent source of truth.

---

# Interview Question Bank

## DSA

- Explain the difference between an array and linked list.
- Implement longest substring without repeated characters.
- Detect a linked-list cycle.
- Reverse a linked list.
- Find the second largest element.
- Implement binary search.
- Search rotated sorted array.
- Explain merge sort.
- Explain quick sort.
- Validate parentheses.
- Find top K frequent elements.
- Traverse a binary tree.
- Validate BST.
- Find tree diameter.
- Explain AVL tree.
- BFS vs DFS.
- Detect graph cycle.
- Find shortest path.
- Explain Dijkstra.
- Explain topological sort.
- Solve 0/1 Knapsack.
- Explain LCS.
- Explain longest palindromic subsequence.
- Solve coin change.
- Explain memoization vs tabulation.
- Explain DP on trees.

## DBMS/SQL

- Primary key vs foreign key.
- Candidate key vs super key.
- Explain normalization.
- Explain ACID.
- What is an index?
- When does an index hurt performance?
- Clustered vs non-clustered index concept.
- SQL query execution order.
- `WHERE` vs `HAVING`.
- `DELETE` vs `TRUNCATE` vs `DROP`.
- `UNION` vs `UNION ALL`.
- Subquery vs join.
- CTE.
- Window function.
- `RANK` vs `DENSE_RANK`.
- Find second highest salary.
- Find duplicates.
- Highest salary per department.
- Employees earning more than department average.
- Explain transaction isolation.

## OOP/Java

- Four pillars of OOP.
- Interface vs abstract class.
- Overloading vs overriding.
- Composition vs inheritance.
- SOLID.
- Factory.
- Singleton.
- Why Singleton can be problematic.
- `final`.
- `static`.
- Static block.
- String immutability.
- StringBuilder vs StringBuffer.
- `==` vs `equals`.
- `hashCode`.
- ArrayList vs LinkedList.
- HashMap internals conceptually.
- Stack vs heap.
- Garbage collection.
- Memory leak in Java.

## OS

- Program vs process.
- Process vs thread.
- Context switch.
- Race condition.
- Critical section.
- Mutex vs semaphore.
- Deadlock.
- Deadlock conditions.
- CPU scheduling.
- Paging.
- Virtual memory.
- Page fault.
- Thrashing.
- Fragmentation.

## Networks

- OSI layers.
- TCP vs UDP.
- TCP handshake.
- DNS.
- HTTP vs HTTPS.
- TLS.
- Cookies.
- HTTP methods.
- Status codes.
- What happens after entering a URL?
- REST.
- Path vs query parameters.
- PUT vs PATCH.
- Proxy vs reverse proxy.
- Load balancer.

## AI/ML

- AI vs ML vs DL.
- Classification vs regression.
- Supervised vs unsupervised.
- Overfitting.
- Training vs inference.
- Accuracy.
- Precision.
- Recall.
- F1.
- LLM.
- Token.
- Transformer.
- Embedding.
- Vector database.
- Cosine similarity.
- RAG.
- RAG vs fine-tuning.
- Prompt engineering.
- Hallucination.
- How would you evaluate a RAG system?

---

# Recommended Books and Study Material

## Algorithms

### Introduction to Algorithms — CLRS

Use for:

- Algorithm fundamentals.
- Trees.
- Graphs.
- Greedy.
- DP.
- Complexity.

For interview preparation, use it as a reference rather than reading cover-to-cover.

### MIT 6.006

Use for concise academic treatment of:

- Data structures.
- BFS.
- DFS.
- shortest paths.
- DP.

[MIT 6.006 Lecture Notes](https://ocw.mit.edu/courses/6-006-introduction-to-algorithms-fall-2011/pages/lecture-notes/?utm_source=chatgpt.com)

### Stanford CS161

Useful slides and algorithm material.

[Stanford CS161](https://cs161-stanford.github.io/?utm_source=chatgpt.com)

---

# Database Material

### Database System Concepts — Silberschatz, Korth, Sudarshan

Use for:

- Relational model.
- SQL.
- transactions.
- concurrency.
- indexing.

### CMU 15-445

Use selectively for:

- Indexes.
- transactions.
- joins.
- query optimization.

[CMU Database Systems](https://15445.courses.cs.cmu.edu/spring2026/?utm_source=chatgpt.com)

### SQLBolt

Best for quickly rebuilding SQL fundamentals.

[SQLBolt](https://sqlbolt.com/?utm_source=chatgpt.com)

### LeetCode SQL 50

Best for interview query practice.

[LeetCode SQL 50](https://leetcode.com/studyplan/top-sql-50/?utm_source=chatgpt.com)

---

# Operating Systems Material

### Operating Systems: Three Easy Pieces

High-value chapters:

- Processes.
- Scheduling.
- Threads.
- Locks.
- Semaphores.
- Paging.
- Virtual memory.
- Files.

[OSTEP Free Book](https://pages.cs.wisc.edu/~remzi/OSTEP/?utm_source=chatgpt.com)

### MIT Operating System Engineering

Use only if you need deeper conceptual understanding.

[MIT OS Engineering](https://ocw.mit.edu/courses/6-1810-operating-system-engineering-fall-2023/?utm_source=chatgpt.com)

---

# Networking Material

### Computer Networking: A Top-Down Approach — Kurose & Ross

Prioritize:

- Application layer.
- HTTP.
- DNS.
- Transport layer.
- TCP/UDP.
- IP basics.

The authors provide online lectures and interactive questions.

[Kurose & Ross Online Networking Material](https://gaia.cs.umass.edu/kurose_ross/online_lectures.htm?utm_source=chatgpt.com)

---

# OOP and Design Patterns Material

### Dev.java

For current Java fundamentals:

[Java Learning Portal](https://dev.java/learn/?utm_source=chatgpt.com)

### Refactoring.Guru

Use for:

- Factory.
- Singleton.
- Strategy.
- Observer.
- Adapter.
- design-pattern trade-offs.

[Design Patterns Catalog](https://refactoring.guru/design-patterns/catalog?utm_source=chatgpt.com)

---

# System Design Material

### System Design Primer

Strong free introduction.

[System Design Primer](https://github.com/donnemartin/system-design-primer?utm_source=chatgpt.com)

### ByteByteGo

Use diagrams for:

- Cache.
- Load balancing.
- databases.
- queues.
- scaling.

[System Design Blueprint](https://bytebytego.com/guides/system-design-blueprint-the-ultimate-guide/?utm_source=chatgpt.com)

---

# AI and ML Material

### Google Machine Learning Crash Course

Focus on:

- Classification.
- loss.
- overfitting.
- precision.
- recall.
- evaluation.

[Google ML Crash Course](https://developers.google.com/machine-learning/crash-course?utm_source=chatgpt.com)

### Hugging Face RAG Cookbooks

Practical RAG implementation and evaluation.

[Hugging Face Advanced RAG](https://huggingface.co/learn/cookbook/advanced_rag?utm_source=chatgpt.com)

### Microsoft RAG Architecture

Good architecture-level reference.

[Microsoft Advanced RAG Guide](https://learn.microsoft.com/en-us/azure/developer/ai/advanced-retrieval-augmented-generation?utm_source=chatgpt.com)

---

# Complete Preparation Schedule

## Foundation Block

Focus:

- Complexity.
- Arrays.
- Strings.
- Hashing.
- Sorting.
- Binary search.
- OOP fundamentals.
- SQL fundamentals.

Daily work:

- Concept revision.
- Several coding problems.
- SQL practice.
- One verbal technical-answer session.

---

## Pattern Block

Focus:

- Two pointers.
- Sliding window.
- Linked lists.
- Stack/queue.
- Trees.
- Recursion.
- Backtracking.

Target:

- Recognize the appropriate pattern before coding.
- Explain brute force and optimized approaches.

---

## Advanced DSA Block

Focus:

- Graphs.
- Heaps.
- Greedy.
- Dynamic programming.

DP sequence:

- Basic recursion.
- Memoization.
- Tabulation.
- Space optimization.
- Knapsack.
- LCS.
- subsequence DP.
- partition DP.
- tree DP.

---

## Core CS Block

Focus:

- DBMS.
- Advanced SQL.
- OS.
- Networks.
- REST.
- Java internals.

Practice technical answers aloud.

Target each answer at:

- 30 seconds for definition.
- 90 seconds for mechanism.
- Several minutes for deeper follow-up.

---

## Architecture and AI Block

Focus:

- Project architecture.
- API design.
- scaling.
- caching.
- databases.
- load balancing.
- queues.
- GenAI.
- ML.
- RAG.
- embeddings.

Draw architectures on paper.

---

## Mock Interview Block

Simulate:

- 30-minute live coding.
- SQL.
- DSA follow-ups.
- OOP.
- DBMS.
- OS/CN.
- project.
- AI.
- behavioral questions.

Do not use:

- AI assistants.
- copied templates.
- IDE autocomplete that hides basic syntax errors.

---

# Compressed Final-Week Revision

## DSA

Complete at least one problem from each:

- Hashing.
- Sliding window.
- Two pointers.
- Binary search.
- Stack.
- Linked list.
- Tree.
- Graph.
- Backtracking.
- Greedy.
- DP.

## SQL

Write without reference:

- Second-highest salary.
- Top salary by department.
- `DENSE_RANK`.
- Join.
- Group/Having.
- duplicate detection.
- correlated/subquery problem.

## CS fundamentals

Explain from memory:

- SOLID.
- Factory.
- Singleton.
- ACID.
- normalization.
- index.
- process vs thread.
- deadlock.
- paging.
- TCP vs UDP.
- DNS.
- HTTP/HTTPS.
- REST.

## AI

Explain:

- precision/recall.
- overfitting.
- embedding.
- vector database.
- RAG.
- fine-tuning.
- prompt engineering.

## Project

Perform:

- Two-minute explanation.
- Ten-minute deep explanation.
- Architecture drawing.
- Database explanation.
- API explanation.
- scalability discussion.
- failure/challenge discussion.

---

# Final Interview Readiness Checklist

## Coding

- I can derive complexity correctly.
- I can explain brute force before optimization.
- I can code without autocomplete.
- I can debug manually.
- I can dry-run code.
- I understand common DSA patterns.
- I can implement BFS and DFS.
- I can solve medium DP problems.
- I understand trees and graphs.

## SQL/DBMS

- I can write joins.
- I can use aggregation.
- I understand window functions.
- I can write second-highest salary in multiple ways.
- I understand ACID.
- I understand normalization.
- I understand indexes.
- I understand transactions.

## OOP/Language

- I understand all OOP pillars.
- I can explain SOLID.
- I understand Factory and Singleton.
- I can discuss their disadvantages.
- I know my primary language deeply enough to defend resume claims.
- I understand collections.
- I understand memory basics.

## OS/CN

- I understand process/thread.
- I understand concurrency.
- I understand deadlocks.
- I understand paging/virtual memory.
- I understand TCP/UDP.
- I understand DNS.
- I can explain HTTPS.
- I can explain what happens after entering a URL.

## AI

- I understand ML fundamentals.
- I can calculate precision and recall.
- I understand embeddings.
- I understand RAG.
- I understand RAG vs fine-tuning.
- I understand prompt engineering.

## Project

- I know every technology listed.
- I know why each technology was selected.
- I can explain alternatives.
- I can draw the architecture.
- I know my database schema.
- I know my APIs.
- I can discuss security.
- I can discuss scalability.
- I have a genuine challenge/failure story.

## Behavioral

- Self-introduction is prepared.
- Why Infosys is prepared.
- Why SP/DSE is prepared.
- Strength and weakness answers have evidence.
- Team-conflict story is prepared.
- Failure story is prepared.
- Leadership story is prepared.

## Physical Interview

- Original college ID.
- Government-issued photo ID.
- Two updated printed resumes.
- Resume file/folder.
- Formal attire.
- Pens.
- Basic stationery.

---

# Highest-Priority Revision Sheet

If preparation time becomes limited, prioritize these topics above everything else:

- Sliding window.
- Two pointers.
- HashMap/HashSet.
- Binary search.
- Trees/BST.
- BFS/DFS.
- Graph shortest paths.
- Recursion/backtracking.
- Knapsack.
- LCS.
- Longest Palindromic Subsequence.
- Core DP patterns.
- Merge sort.
- SQL joins.
- SQL aggregation.
- `RANK` / `DENSE_RANK`.
- Second-highest salary.
- Query execution order.
- Indexes.
- ACID.
- normalization.
- SOLID.
- Factory.
- Singleton.
- Java collections.
- String/StringBuilder/StringBuffer.
- stack vs heap.
- process vs thread.
- deadlock.
- paging.
- TCP vs UDP.
- DNS.
- HTTP/HTTPS.
- REST.
- precision/recall/F1.
- embeddings.
- RAG.
- prompt engineering.
- project architecture.
- project scalability.
- behavioral evidence.

---

# Primary Resource Stack

Use a limited resource set rather than repeatedly switching platforms.

- **DSA concepts:** MIT 6.006 + TakeUForward.
- **DSA practice:** LeetCode Top Interview 150.
- **DP:** LeetCode DP Study Plan + MIT/Stanford.
- **SQL:** SQLBolt + LeetCode SQL 50.
- **DBMS:** CMU 15-445 for selected deeper concepts.
- **OOP/Java:** Dev.java + Refactoring.Guru.
- **OS:** OSTEP.
- **Networks:** Kurose & Ross.
- **System Design:** System Design Primer + ByteByteGo.
- **ML:** Google ML Crash Course.
- **GenAI/RAG:** Microsoft Architecture + Hugging Face.
- **Infosys role calibration:** official Infosys Power Programmer/Careers pages plus recent campus interview reports.

---

# Interview Standard to Aim For

For every important concept, reach the point where you can answer all of these without searching:

- **What is it?**
- **How does it work?**
- **What is its complexity or cost?**
- **When would I use it?**
- **When should I not use it?**
- **What is the main alternative?**
- **What trade-off exists between them?**
- **Where did I use this concept in a project?**

For every coding problem, be able to:

- Understand the constraints.
- Identify the pattern.
- Explain a straightforward approach.
- Derive a better approach.
- Prove why it works informally.
- State complexity.
- Implement correctly.
- Test edge cases.
- Respond to an optimization follow-up.

For every project, be able to:

- Explain the problem.
- Draw the architecture.
- Explain the data model.
- Explain request flow.
- Defend technology choices.
- Explain security.
- Explain deployment.
- Explain one difficult technical problem.
- Explain limitations.
- Redesign it for significantly greater scale.

That combination matches the technical breadth expected by the preparation instructions you received and the strongest patterns visible in current Infosys SP/DSE campus interviews.