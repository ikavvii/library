

### Problem Description

A plumber needs to install pipelines on a brick wall. To do this, some bricks must be broken to fit the pipes.

There are two types of bricks in the wall:

- **Red Bricks (R):** Hard to break.
- **Green Bricks (G):** Easy to break.

The plumber will only break Green Bricks to make the job easier. The wall is represented as a square grid, with each brick type and its length specified (e.g., "3R" means a Red Brick of length equal to three unit Bricks). The wall also includes a **Source (S)** where the pipe starts and a **Destination (D)** where it ends.

Pipes can be laid either vertically or horizontally, moving from the current brick to any adjacent Green Brick (up, down, left, or right). The goal is to find the minimum number of Green Bricks that must be broken to connect the source to the destination. Red Bricks cannot be used.

Assume the layout of the brick wall is shown below.

![](attachments/Pasted%20image%2020260925221953.png)

The input notation to represent the above brick wall is shown below:

3R1D  
1R1R1R1G  
2G1G1G  
2S2R

### Constraints

3<=N<=25

### Input

The first line contains N, the size of the wall (N x N).  
The next N lines describe the wall layout using the notation above.

### Output

Print a single integer: the least number of Green Bricks that need to be broken.

### Time Limit (secs)

1

### Examples

Example 1

4

3R1D

1R1R1R1G

2G1G1G

2S2R

Output

4

Explanation

The input and image already shown in description.

From the image we can see that 4 bricks need to be destroyed to lay pipes between source and destination.

Example 2

Input

5

3G1R1G

1G1R1G2R

1S1R1G1R1D

2R1G1R1G

5G

Output

7

Explanation

The image below represents the above input.


![](attachments/Pasted%20image%2020260925221930.png)

From this you can see that 7 bricks must be broken to lay pipelines between source and destination.