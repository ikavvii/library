
### 🧠 Data Structures & Algorithms (DSA)

**1. Array & Memory**: An array stores elements of the same data type in contiguous memory locations. The exact memory address of an element is calculated via a base address plus an offset: `Base_Address + (Index * Element_Size)`. This mathematical mapping provides $O(1)$ random access.

**2. Array vs Linked List**: Arrays allocate contiguous static memory, granting excellent CPU cache locality and $O(1)$ access, but $O(n)$ insertions. Linked Lists allocate dynamic, scattered memory nodes connected by pointers. They offer $O(1)$ insertions/deletions (if the pointer is known) but suffer from $O(n)$ access time and poor cache locality.

**3. Big‑O Notation**: It defines the asymptotic upper bound of an algorithm's time or space requirements as the input size $n$ approaches infinity. It intentionally drops constants and lower-order terms to focus purely on the growth rate (e.g., scaling from $O(n)$ to $O(n^2)$).

**4. Stack via Array**: Allocate a fixed-size array and track an integer index, `top`, initialized to `-1`. A `push()` increments `top` and stores the value; a `pop()` retrieves the element at `top` and decrements the index. Both operations are strictly $O(1)$.

**5. Queue via Array**: To avoid the $O(n)$ penalty of shifting elements after a dequeue, queues are implemented using a circular array. Maintain `front` and `rear` pointers, advancing them using modulo arithmetic: `(pointer + 1) % array_capacity`.

**6. Hash Table**: It maps keys to values. A hash function converts a key into a numerical hash code, which is then mapped to an array index (often using modulo). It provides amortized $O(1)$ lookups, insertions, and deletions.

**7. Collisions**: Handled primarily via **Chaining** (storing a linked list or, in modern Java, upgrading to a balanced tree at each bucket index) or **Open Addressing** (probing linearly or quadratically for the next available empty slot in the array).

**8. BT vs BST**: A Binary Tree allows up to two children per node with no ordering rules. A Binary Search Tree (BST) enforces a strict property: all left descendants are smaller than the node, and all right descendants are larger. This structure enables $O(\log n)$ search times.

**9. Tree Traversals**: DFS approaches include **Inorder** (Left, Root, Right—which visits a BST in sorted order), **Preorder** (Root, Left, Right—ideal for copying trees), and **Postorder** (Left, Right, Root—ideal for safely deleting a tree from the leaves up).

**10. Recursion**: A function calling itself to break a larger problem into identical sub-problems. It requires a rigid base case to prevent stack overflow. It naturally uses the execution call stack and is standard for tree traversals and dynamic programming.

---

### 🌱 Arrays, Strings, Two‑Pointers

**11. Remove Duplicates**: Use an $O(1)$ space two-pointer approach. Maintain a `slow` pointer for the boundary of unique elements. Scan with a `fast` pointer; when a new distinct element is found, increment `slow` and overwrite the array at `slow` with the `fast` value.

**12. Two Sum**: For unsorted arrays, hash maps provide $O(n)$ time and space by tracking `target - current_val`. If the array is sorted, place two pointers at opposite ends and move them inward based on the sum, achieving $O(n)$ time and an optimal $O(1)$ space.

**13. Reverse String/Array**: Place pointers at the `start` (0) and `end` ($n-1$). Swap the elements and converge the pointers toward the middle. This executes in $O(n)$ time with $O(1)$ space complexity.

**14. Kadane’s Algorithm**: Track `current_sum` and `max_sum`. Iterate the array, adding elements to `current_sum`. If `current_sum` drops below zero, reset it to zero (a negative prefix sum mathematically cannot improve a future subarray).

**15. Rotate Array**: To rotate $k$ steps with $O(1)$ space optimization: reverse the entire array, reverse the first $k$ elements, and finally reverse the remaining $n-k$ elements.

**16. Missing Positive**: Utilize cyclic sort for an $O(1)$ space solution. Iterate through the array, swapping every valid number $x$ to its correct index $x-1$. Scan the array again; the first index $i$ where `arr[i] != i + 1` is the missing positive.

**17. Sliding Window**: Maintain a window using `left` and `right` indices. Expand `right` to ingest elements until a condition is broken, then shrink `left` until the condition is valid again. This reduces nested loops ($O(n^2)$) to linear time ($O(n)$).

**18. Merge Sorted Arrays**: If one array acts as a buffer with empty space at the end, set pointers at the end of the populated elements in both arrays. Compare backwards, placing the largest elements at the absolute end of the buffer to avoid $O(n)$ shifting.

**19. Longest Substring Without Repeats**: Use a sliding window alongside a boolean array or HashSet to track character presence. When a duplicate is hit, slide the `left` pointer forward, removing characters from the set until the duplicate is evicted.

**20. Circular Buffer**: Uses a fixed-size array where the `head` and `tail` pointers wrap around to index 0 when they reach the end, managed via modulo arithmetic `(index + 1) % capacity`. Old data is continuously overwritten.

---

### 🔗 Linked Lists

**21. Reverse List**: Maintain three pointers: `prev` (initialized to null), `curr` (head), and `next`. Inside a loop, store `curr.next`, redirect `curr.next = prev`, then shift both `prev` and `curr` forward one step.

**22. Detect Cycle**: Employ Floyd’s Tortoise and Hare. Move a `slow` pointer by one node and a `fast` pointer by two nodes. If the pointers intersect at the same memory reference, a cycle exists.

**23. Middle Node**: Use the fast/slow pointer technique. By the time the `fast` pointer reaches the end of the list, the `slow` pointer will have traversed exactly half the distance, landing on the middle node.

**24. Merge Sorted Lists**: Instantiate a "dummy head" node. Compare the current nodes of both lists, append the smaller node to the dummy's tail, and advance the respective pointer. Return `dummy.next`.

**25. Remove Duplicates**: In a sorted list, traverse and check if `curr.val == curr.next.val`. If so, bypass the next node: `curr.next = curr.next.next`. In an unsorted list, track seen values using a HashSet.

**26. Dummy Head**: A placeholder node instantiated before the actual head of a list. It acts as an anchor, radically simplifying edge cases where the true head of the list might need to be deleted or reassigned.

**27. Delete Node (No Head)**: Since you cannot access the previous node to alter its pointer, copy the data from the `next` node into the current node, then bypass the next node by setting `curr.next = curr.next.next`.

**28. Circular Linked List**: A list where the `next` pointer of the final tail node does not point to null, but instead points back to the head node, creating a closed loop.

**29. Split List**: Find the middle using fast/slow pointers. Store the node immediately following the middle, set the middle node's `next` to null to terminate the first half, and use the stored node as the head of the second half.

**30. Doubly Linked List**: Each node contains references to both `next` and `prev` nodes. This slightly increases memory overhead but allows bidirectional traversal and $O(1)$ node deletion if the node reference is known.

---

### 🗂️ Stacks, Queues, and Heaps

**31. Max-Stack**: Maintain two parallel stacks: a primary stack for values and a secondary stack tracking the maximum. On `push(x)`, push to the main stack, and push `Math.max(x, max_stack.peek())` to the max-stack.

**32. Queue via Stacks**: Maintain two stacks: `in` and `out`. Push all elements to `in`. For a pop/peek, if `out` is empty, pop all elements from `in` and push them to `out` (reversing their order to FIFO), then pop from `out`.

**33. Min-Stack**: Conceptually identical to the max-stack, but the secondary stack continuously tracks the minimum value seen at the time each element was pushed.

**34. Monotonic Stack**: A stack whose elements are strictly increasing or decreasing. It is used for "Next Greater Element" logic, where elements that violate the monotonic property are popped off and resolved.

**35. Priority Queue / Heap**: A binary tree conceptually mapped to an array. For a node at index $i$, children are at $2i+1$ and $2i+2$. Operations like `insert` and `extract` bubble elements up or down, taking $O(\log n)$ time.

**36. Top K Elements**: Count element frequencies. Push the frequencies into a Min-Heap capped at size $k$. If the heap size exceeds $k$, pop the minimum. The heap naturally retains the $k$ largest elements.

**37. Merge K Sorted Lists**: Insert the head of every list into a Min-Heap based on node values. Pop the minimum node, append it to the result list, and push that node's `next` element back into the heap.

**38. LRU Cache**: Combine a HashMap (for $O(1)$ key lookups) and a Doubly Linked List (for $O(1)$ reordering). When an item is accessed, detach it from the list and move it to the head. When capacity is reached, evict the tail node.

**39. Balanced Parentheses**: Iterate through the string. Push opening brackets `(`, `{`, `[` onto a stack. When encountering a closing bracket, pop the stack and verify it forms a valid pair. The stack must be empty at the end.

**40. Circular Queue**: An array where the logical end wraps back to index 0. Handled mathematically via `(index + 1) % size`. It prevents memory waste that occurs in standard array queues when elements are dequeued.

---

### 🌳 Trees & Graphs

**41. BFS & DFS**: BFS utilizes a Queue to process nodes level-by-level (guaranteeing the shortest path in unweighted graphs). DFS utilizes a Stack (or the call stack via recursion) to plunge down a branch until hitting a leaf before backtracking.

**42. Tree Height**: Solved recursively: `1 + Math.max(height(node.left), height(node.right))`. The base case returns 0 (or -1) when the node is null.

**43. Level-Order Traversal**: Standard BFS. Push the root to a queue. Loop while the queue has elements: record the queue's size, dequeue that many elements (processing one level), and enqueue all their valid children.

**44. Validate BST**: Pass strict `min` and `max` boundaries down the recursive tree. A node is only valid if `min < node.val < max`. When recursing left, update `max` to `node.val`; when recursing right, update `min` to `node.val`.

**45. Preorder Iterative**: Initialize a stack and push the root. Loop: pop a node, process it, push its RIGHT child, then push its LEFT child. Pushing the left child last ensures it is popped and processed first.

**46. Postorder Iterative**: Use a stack to execute a pseudo-preorder (Root, Right, Left). Instead of printing the values, push them to a second stack. Finally, pop everything from the second stack to yield Left, Right, Root.

**47. Lowest Common Ancestor (LCA)**: In a BST, traverse down; the LCA is the exact node where the two target values numerically split (one is smaller, one is larger). In a standard BT, recurse up; the node that receives non-null returns from both left and right branches is the LCA.

**48. Serialize & Deserialize**: Serialize by running a preorder traversal, appending values to a string and using a marker (like `#`) for null leaves. Deserialize by parsing the string sequentially via an iterator to perfectly rebuild the tree structure.

**49. Detect Graph Cycle**: Run DFS. Pass the `parent` node along with the `current` node. If the DFS encounters a node that is already in the `visited` set, and that node is _not_ the `parent`, a back-edge cycle exists.

**50. Dijkstra’s Algorithm**: Finds the shortest path from a source node. Maintain a Min-Heap of distances. Continuously pop the node with the smallest known distance, and "relax" (update) the path costs to its adjacent neighbors.

---

### 📊 Sorting, Searching & DP

**51. Quicksort vs Mergesort**: Quicksort selects a pivot and partitions the array in-place, offering $O(n \log n)$ average time but $O(n^2)$ worst-case. Mergesort recursively divides the array and merges halves, guaranteeing $O(n \log n)$ time but requiring $O(n)$ space overhead.

**52. Rotated Binary Search**: Find the mid-point. At least one half of the array will always be strictly sorted. Check if your target falls within the boundary of the sorted half; if it does, binary search that half, otherwise search the chaotic half.

**53. Insertion Sort**: Builds the final sorted array one item at a time by shifting elements to the right to make room. Highly efficient for very small datasets or arrays that are already nearly sorted.

**54. K-th Largest Element**: Can be solved with a Min-Heap of size $k$ in $O(n \log k)$ time. The optimal $O(n)$ average time solution uses Quickselect, utilizing the partitioning logic from Quicksort to discard halves of the array.

**55. DFS vs Backtracking**: DFS comprehensively explores all paths in a state space. Backtracking is an optimized DFS strategy that evaluates paths incrementally and "prunes" (abandons) a branch the moment it violates a constraint.

**56. N-Queens**: A classic backtracking problem. Place queens row by row. Use HashSets to track attacked columns, positive diagonals `(row + col)`, and negative diagonals `(row - col)` for instant $O(1)$ validation.

**57. Subsets & Permutations**: Backtracking. To generate subsets, branch twice at every element: once including it, once excluding it. For permutations, swap elements in-place recursively to generate all factorial combinations.

**58. Coin-Change**: Dynamic Programming. Initialize an array `dp` where `dp[i]` represents the minimum coins for amount `i`. Iterate through the amounts, calculating `dp[i] = Math.min(dp[i], dp[i - coin] + 1)`.

**59. Fibonacci**: Standard recursion takes $O(2^n)$. DP (memoization) reduces this to $O(n)$ time. Space can be optimized to $O(1)$ using just two variables. For extreme scale, matrix exponentiation computes it in $O(\log n)$ time.

**60. LIS (Longest Increasing Subsequence)**: The DP approach takes $O(n^2)$ time. The optimized approach maintains a `tails` array and uses binary search to overwrite elements, achieving $O(n \log n)$ time while maintaining the smallest possible tail for any subsequence length.

---

### 🌐 Full‑Stack / System‑Design (General)

**61. Web Request Lifecycle**: The browser checks the DNS cache $\rightarrow$ queries a DNS server $\rightarrow$ establishes a TCP connection (via three-way handshake) $\rightarrow$ initiates TLS encryption $\rightarrow$ sends the HTTP request $\rightarrow$ the server processes it $\rightarrow$ returns an HTTP response $\rightarrow$ the browser renders the DOM.

**62. HTTP vs HTTPS**: HTTPS uses TLS (Transport Layer Security) to encrypt the HTTP payload. It provides data confidentiality (preventing packet sniffing), integrity (preventing tampering), and authentication (verifying server identity).

**63. DNS**: The Domain Name System is a hierarchical, decentralized system that translates human-readable domain names (like `example.com`) into machine-routable IP addresses.

**64. CDN**: A Content Delivery Network is a geographically distributed group of proxy servers. It caches static assets (images, CSS, JS) close to the user's physical location, drastically reducing network latency and origin server load.

**65. Reduce Latency**: Implement CDNs, aggressively cache data (Redis/Memcached), optimize DB queries, paginate API payloads, compress data (Gzip/Brotli), and handle heavy processing via asynchronous background workers.

**66. Caching Layers**: Data can be cached at the client (browser cache), the edge (CDN), the API gateway, the application layer (in-memory data grids like Redis for hot data), and within the database (query plan caching).

**67. Scaling**: Vertical scaling (scaling up) means adding more CPU/RAM to an existing node. Horizontal scaling (scaling out) means adding more standalone nodes to a cluster, which necessitates a load balancer.

**68. Load Balancing**: Acts as a reverse proxy, distributing incoming network traffic across a cluster of backend servers. Common routing algorithms include Round Robin, Least Connections, and IP Hash.

**69. Rate Limiting**: Throttles API requests to prevent abuse or DDoS attacks. Commonly implemented via Token Bucket, Leaky Bucket, or Fixed Window algorithms, typically using Redis to track client IP request counts.

**70. URL Shortener Design**: Generate a unique short string via Base62 encoding of an auto-incrementing database ID. Store the mapping in a high-throughput database. Implement an HTTP 301/302 redirect on the backend, and heavily cache popular links.

---

### 📂 Databases & Backend Theory

**71. SQL vs NoSQL**: SQL databases are relational, using strict schemas and tables; they excel at complex joins. NoSQL (Document, Key-Value, Graph) databases are non-relational, schema-less, and scale horizontally with ease for unstructured data.

**72. ACID**: Atomicity (all operations succeed or fail together), Consistency (data validates against schemas), Isolation (concurrent transactions act sequentially), and Durability (committed data survives crashes). Vital for financial ledgers.

**73. Normalization**: The process of structuring relational tables to eliminate data redundancy (creating strict foreign key relationships). Denormalization intentionally re-introduces redundancy to speed up heavy read workloads by avoiding complex `JOIN` statements.

**74. Indexing**: Creating auxiliary data structures (typically B-Trees) that allow the database to locate rows in $O(\log n)$ time rather than performing full table scans. Indexes drastically speed up `WHERE` clauses but slow down `INSERT` operations.

**75. Sharding vs Replication**: Sharding partitions data horizontally, distributing rows across multiple separate database servers to spread write/read load. Replication creates exact copies of the entire database to ensure high availability and scale read operations.

**76. Consistency Models**: Strong consistency guarantees that a read will instantly return the most recent write. Eventual consistency allows nodes to temporarily hold stale data, guaranteeing that all nodes will eventually sync up (highly utilized in distributed NoSQL).

**77. Transactions**: A logical block of database operations executed as a single unit. If the application crashes, a constraint is violated, or a deadlock occurs mid-execution, a rollback is triggered, reverting the database to its state before the transaction began.

**78. Connection Pooling**: Establishing a TCP/DB connection is highly resource-intensive. A connection pool maintains a cache of active, open database connections that applications can borrow, execute queries on, and return without the handshake overhead.

**79. CAP Theorem**: A distributed system can only provide two of three guarantees: Consistency, Availability, and Partition Tolerance. Because network partitions are inevitable, architects must design systems to favor either Consistency or Availability during a failure.

**80. UGC Schema Design**: User-Generated Content requires highly scalable schemas. Metadata (timestamps, authors) is stored in SQL or document databases, while the heavy binary data (images, videos) is uploaded directly to object storage (like AWS S3) to keep the database lean.

---

### 💡 Coding & Problem‑Pattern Practice

**81. Sum Array**: For quick execution during timed assessments, utilizing the native `Arrays.stream(arr).sum()` in Java is concise. When dealing with standard input logic, using `Scanner` provides rapid, clean parsing compared to buffered readers.

**82. Reverse String**: In Java, utilize `new StringBuilder(str).reverse().toString()` for clean code, or a standard two-pointer array swap for absolute $O(1)$ memory allocation.

**83. Longest Palindrome**: Use the "expand around center" technique. Iterate through the string, treating each character (and the space between characters) as the center, expanding outward as long as the left and right characters match.

**84. Debounce**: An architectural pattern that ensures a function is not called again until a specified amount of time has passed without it being triggered (e.g., waiting for the user to stop typing before sending a search API request).

**85. Throttle**: Ensures that a function is executed at most once every specified time interval, regardless of how frequently the trigger event fires (e.g., executing logic every 100ms during continuous window scrolling).

**86. Flatten Array**: Iterate through the nested structure. If an element is a primitive, append it. If it is an array, recursively call the flatten function on it and merge the results.

**87. Pub/Sub**: The Publisher-Subscriber pattern decouples system components. Maintain a map linking an event string to a list of callback functions. Publishers emit events, triggering the loop that executes all subscribed callbacks.

**88. Promise.all (Concept)**: Given an array of asynchronous tasks, iterate and execute them. Maintain a counter and an output array. As each task resolves, store the result and decrement the counter. Only return the final promise when the counter hits zero.

**89. Group Anagrams**: Iterate over the array of strings. Sort the characters of each string to use as a standardized key in a HashMap. The value mapped to that key is a list of the original strings that share that sorted configuration.

**90. LRU Implementation**: Create a custom class holding a capacity limit, a HashMap (mapping keys to Node objects), and a Doubly Linked List. `get()` moves accessed nodes to the head. `put()` adds to the head, and if size > capacity, removes the node at the tail.

---

### 🧠 Behavioral & System‑Design (Full‑Stack / SWE)

**91. End‑to‑End Project**: Structure your answer using the STAR method (Situation, Task, Action, Result). Emphasize architectural decisions, API design, database schemas, and how you handled deployment/hosting.

**92. Exceeded Performance**: Focus on quantitative metrics. Discuss utilizing algorithmic space optimization (refactoring logic to run in $O(1)$ space), adding indexes to bottlenecked queries, or shifting heavy I/O tasks to background queues.

**93. Debugging Production**: Detail your isolation process: checking application logs, replicating the state locally, isolating the breaking commit via binary search, deploying the patch, and finally, writing a regression test to prevent recurrence.

**94. Technical Debt**: Explain how you identify monolithic or tightly coupled code. Discuss strategies like writing unit tests to lock in behavior before refactoring, breaking down large files, and updating deprecated dependencies systematically.

**95. Simple Chat System**: Design around WebSockets for persistent, real-time bidirectional data flow. Use a message broker like Kafka to handle high throughput, and dump chat logs into a highly write-optimized NoSQL database like Cassandra.

**96. File-Uploading Service**: Do not route massive binary files through your primary application server. Have the server generate a secure, pre-signed URL. The client uploads the file directly to cloud object storage (S3) using that URL, keeping backend I/O free.

**97. Task Management App**: Design a relational database with normalized tables (Users, Workspaces, Tasks). Implement optimistic locking or WebSockets to handle concurrent state changes without overwriting a teammate's edits.

**98. Team Collaboration**: Emphasize API contracts. The backend and frontend teams agree on a Swagger/OpenAPI spec first. The frontend uses mock data to build UI while the backend implements the actual logic, converging for integration testing.

**99. Conflicting Requirements**: Prioritize data and constraints. If product wants a heavy feature but infrastructure demands low latency, clearly communicate the technical trade-offs. Negotiate an MVP that satisfies core business logic without tanking performance.

**100. System-Design Prep**: Master back-of-the-envelope capacity estimations. Understand the distinct trade-offs between SQL and NoSQL, Microservices vs Monoliths, and know when to leverage caching vs message queues. Read "Designing Data-Intensive Applications".