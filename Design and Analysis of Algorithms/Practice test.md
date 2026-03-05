AVL
- time and height log2n
- max height 1.44 log2n
- single or double rotation
- self balancing bst

B Tree
- self balancing m-way st

## Interesting Facts about B-Tree

1. Height when the B-tree is ****completely full**** (i.e., all nodes have the maximum `m` children):

> $hmin=⌈log⁡m(n+1)⌉−1$

2. Height when the B-tree is ****least filled**** (each node has the minimum `t` children):

> $hmax=⌊log⁡t(n+12)⌋$