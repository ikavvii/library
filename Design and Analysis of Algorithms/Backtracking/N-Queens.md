 The **$n$-Queens problem** is a classic combinatorial problem that serves as a primary example of the **backtracking** algorithm design paradigm. The goal is to place $n$ queens on an $n \times n$ chessboard such that no two queens "attack" each other, meaning no two queens share the same row, column, or diagonal.

### 1. Problem Formulation

To solve this efficiently, the problem is formulated with specific constraints:

- **Representation:** Solutions are represented as an **$n$-tuple $(x_1, \dots, x_n)$**, where $x_i$ is the column index on which the $i$th queen is placed. This assumes that each queen is placed on a different row (queen $i$ on row $i$), which is a necessary condition for a solution.
- **Explicit Constraints:** Each $x_i$ must be an integer in the set $S_i = {1, 2, \dots, n}$.
- **Implicit Constraints:** No two $x_i$ can be the same (all queens must be in different columns), and no two queens can reside on the same diagonal.

### 2. Backtracking Algorithm

The sources provide a specific recursive algorithm to find all non-attacking placements:

- **The `Place(k, i)` Function:** This helper function checks if a queen can be safely placed in row $k$ and column $i$. It iterates through all previously placed queens (rows $1$ to $k-1$) to ensure no two are in the same column ($x[j] = i$) and no two are on the same diagonal ($|x[j] - i| = |j - k|$).
- **The `NQueens(k, n)` Procedure:** This is the core backtracking routine. It attempts to place a queen in row $k$ by iterating through columns $i = 1$ to $n$. If `Place(k, i)` returns true, the column is recorded, and the algorithm recursively calls itself for row $k+1$. If $k=n$, a full solution is printed.

### 3. Efficiency and Pruning

Backtracking is significantly more efficient than a brute-force approach:

- **Search Space Reduction:** A pure brute-force approach for an $8 \times 8$ board would involve checking approximately **4.4 billion** tuples. By ensuring queens are on distinct rows and columns, the space is reduced to $8!$, or **40,320** tuples.
- **Pruning:** Backtracking uses **bounding functions** to "kill" live nodes in the state space tree that cannot lead to a solution. For the 8-queens problem, while the full state space tree contains 69,281 nodes, the backtracking algorithm typically only generates about **2.34%** of them (approximately 1,625 nodes on average).

### 4. Symmetry Considerations

The sources note that many solutions are simply **reflections or rotations** of each other. For example, in the 4-queens problem, certain solutions are equivalent under reflection. To improve efficiency and find only inequivalent solutions, the algorithm can be modified to limit the first queen's placement to the first $\lceil n/2 \rceil$ columns.

To solve the **$n$-Queens problem** using the backtracking approach described in the Ellis Horowitz textbook, you need two primary algorithms: a helper function to check for valid placements and the main recursive procedure to explore the state space tree.

### 1. The `Place` Algorithm

This function determines if a queen can be safely placed in the $k$-th row and $i$-th column. it checks two conditions based on previously placed queens in rows $1$ to $k-1$:

- **Column Constraint:** No two queens can be in the same column ($x[j] = i$).
- **Diagonal Constraint:** No two queens can be on the same diagonal ($|x[j] - i| = |j - k|$).

```
Algorithm Place(k, i)
// Returns true if a queen can be placed in kth row and
// ith column. Otherwise it returns false. x[ ] is a
// global array whose first (k - 1) values have been set.
// Abs(r) returns the absolute value of r.
{
    for j := 1 to k - 1 do
        if ((x[j] = i) // Two in the same column
        or (Abs(x[j] - i) = Abs(j - k))) // or in the same diagonal
            then return false;
    return true;
}
```

### 2. The `NQueens` Algorithm

This is the core backtracking routine. It iterates through all possible columns ($i$) for the current row ($k$). if `Place(k, i)` is successful, it records the column in the solution vector $x$ and either prints the solution (if all $n$ queens are placed) or moves to the next row.

```
Algorithm NQueens(k, n)
// Using backtracking, this procedure prints all
// possible placements of n queens on an n x n
// chessboard so that they are nonattacking.
{
    for i := 1 to n do
    {
        if Place(k, i) then
        {
            x[k] := i;
            if (k = n) then write (x[1:n]);
            else NQueens(k + 1, n);
        }
    }
}
```


### Implementation Notes:

- **Initial Call:** To find all solutions for an $n \times n$ board, the algorithm is initially invoked as **`NQueens(1, n)`**.
- **Solution Representation:** The solution is output as an $n$-tuple $(x_1, \dots, x_n)$, where each $x_i$ represents the column index for the queen in row $i$.
- **Efficiency:** For an $8 \times 8$ board, this algorithm reduces the search space from $8^8$ (over 16 million) or $8!$ (40,320) possible tuples down to an average of only **1,625 nodes** generated in the state space tree.

Would you like me to create a tailored report that provides a visual trace of these algorithms for a **4-Queens** board to illustrate how the backtracking happens?