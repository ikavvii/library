## Longest Common Subsequence

**Recurrence Rule:**
If $X[i] == Y[j]$: $L[i, j] = 1 + L[i-1, j-1]$
If $X[i] \neq Y[j]$: $L[i, j] = \max(L[i-1, j], L[i, j-1])$

