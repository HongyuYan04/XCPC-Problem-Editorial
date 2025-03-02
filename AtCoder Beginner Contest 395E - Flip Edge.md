### Problem Statement

有一个 $N$ 个结点, $M$ 条边构成的有向图. 第 $i$\ 条边 $(1 \leq i \leq M)$ is a directed edge from vertex $u _ i$ to vertex $v _ i$.

Initially, you are at vertex $1$. You want to repeat the following operations until you reach vertex $N$:

-   Perform one of the two operations below:
    -   Move along a directed edge from your current vertex. This incurs a cost of $1$. More precisely, if you are at vertex $v$, choose a vertex $u$ such that there is a directed edge from $v$ to $u$, and move to vertex $u$.
    -   Reverse the direction of all edges. This incurs a cost of $X$. More precisely, if and only if there was a directed edge from $v$ to $u$ immediately before this operation, there is a directed edge from $u$ to $v$ immediately after this operation.

It is guaranteed that, for the given graph, you can reach vertex $N$ from vertex $1$ by repeating these operations.

Find the minimum total cost required to reach vertex $N$.
