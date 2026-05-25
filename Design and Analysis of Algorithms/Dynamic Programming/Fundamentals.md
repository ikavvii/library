
for Fibonacci()
Recursive - Explosive Time
Memoization - Linear time, Linear space,
Bottom-up - Linear time, constant space

Divide and conquer deals with non-overlapping subproblems.
- Dynamic programming deals with highly-overlapping subproblems.
- Dynamic programming makes sure each subproblem is solved exactly once
- All Directed Acyclic Graphs are linearizable, making it possible to solve the subproblems in order of dependency.

What is the downside of using memoization?
- It potentially increases memory usage.
- Answers to subproblems are kept around even after they are not needed.

