trace BFS and DFS algorithms, write the traversal sequence for the given graph
   0: {1, 3}
   1: {0, 2, 3, 5, 6}
   2: {1, 3, 4, 5}
   3: {0, 1, 2, 4}
   4: {2, 3, 6}
   5: {1, 2}
   6: {1, 4}

 Assuming we always visit neighbors in ascending vertex order, here are the traversals.

   Breadth-First Search (BFS) from 0

   Adjacency (sorted):
   0: 1,3
   1: 0,2,3,5,6
   2: 1,3,4,5
   3: 0,1,2,4
   4: 2,3,6
   5: 1,2
   6: 1,4

   BFS steps:

     - Start at 0: visited = {0}, Q = [0]
     - Dequeue 0 → visit neighbors 1,3 → visited={0,1,3}, Q=[1,3]
     - Dequeue 1 → neighbors: 0(visited),2,3(visited),5,6 → add 2,5,6 → visited={0,1,3,2,5,6}, Q=[3,2,5,6]
     - Dequeue 3 → neighbors: 0,1,2,4; only 4 unvisited → add 4 → visited={0,1,2,3,4,5,6}, Q=[2,5,6,4]
     - Dequeue 2,5,6,4 → all neighbors already visited, queue empties.

   BFS order (from 0):
   0, 1, 3, 2, 5, 6, 4

   -----------------------------------------------------------------------------------------------------------------------------------------------

   Depth-First Search (DFS) from 0 (recursive, ascending neighbors)

   DFS(0):

     - Visit 0
       - Go to 1
         - Visit 1
           - 0 already, go to 2
             - Visit 2
               - 1 visited; go to 3
                 - Visit 3
                   - 0,1,2 visited; go to 4
                     - Visit 4
                       - 2,3 visited; go to 6
                         - Visit 6
                           - 1,4 visited → backtrack
                     - backtrack from 4 → 3 done
               - then neighbor 4 already visited, then 5
                 - Visit 5
                   - 1,2 visited → backtrack
           - then neighbors 3,5,6 all visited → backtrack
       - then neighbor 3 already visited → DFS finishes.

   DFS order (from 0):
   0, 1, 2, 3, 4, 6, 5
