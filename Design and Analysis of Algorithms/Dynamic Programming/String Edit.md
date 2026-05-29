## Minimum-Cost Edit Sequence
"The cost of a change operation is normally taken to be the sum of the costs of a delete and an insert operation."

Since the standard costs for deletion ($D$) and insertion ($I$) are 1, the cost for a replacement/change ($R$) is typically 2. This effectively means a replacement is treated as a deletion followed by an insertion.

$D=1, I=1, R=2$

$cost(i, j) = \min \{ cost(i-1, j-1) + replace\_cost, cost(i-1, j) + delete, cost(i, j-1) + insert \}$
     
### Backtracking Procedure

The backtracking begins at the bottom-right corner of the matrix, $C[n, m]$, where $n$ is the length of string $X$ and $m$ is the length of string $Y$. You move backward toward $C[0, 0]$ by determining which operation produced the value in the current cell.

#### Identify the Operation at Cell $(i, j)$

Compare the value of the current cell $C[i, j]$ with its three neighbors to find which one satisfies the recurrence relation:

- **Match / No Operation** (Diagonal Move):
    - **Condition:** $X[i] = Y[j]$ AND $C[i, j] = C[i-1, j-1]$.
    - **Action:** No edit cost was incurred. Move to $C[i-1, j-1]$.
- **Replacement / Change** (Diagonal Move):
    - **Condition:** $X[i] \neq Y[j]$ AND $C[i, j] = C[i-1, j-1] + R$ (where $R=2$).
    - **Action:** $X[i]$ was replaced by $Y[j]$. Move to $C[i-1, j-1]$.
- **Deletion** (Vertical Move Up):
    - **Condition:** $C[i, j] = C[i-1, j] + D$ (where $D=1$).
    - **Action:** The character $X[i]$ was deleted from string $X$. Move to $C[i-1, j]$.
- **Insertion** (Horizontal Move Left):
    - **Condition:** $C[i, j] = C[i, j-1] + I$ (where $I=1$).
    - **Action:** The character $Y[j]$ was inserted into string $X$. Move to $C[i, j-1]$.

