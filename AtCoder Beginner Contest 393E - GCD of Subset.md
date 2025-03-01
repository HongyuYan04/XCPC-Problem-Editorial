### Problem Statement

You are given a sequence $A = (A_1, A_2, \dots, A_N)$ of length $N$ and a positive integer $K$ (at most $N$).  
For each $i = 1, 2, \dots, N$, solve the following problem:

-   When you choose $K$ elements from $A$ that include $A_i$, find the maximum possible GCD (greatest common divisor) of those chosen elements.

### Constraints

-   $1 \leq K \leq N \leq 1.2 \times 10^6$
-   $1 \leq A_i \leq 10^6$
-   All input values are integers.

### Input

The input is given from Standard Input in the following format:

$N$ $K$

$A_1$ $A_2$ $\dots$ $A_N$


### Output

Print $N$ lines. The $j$\-th line should contain the answer for $i=j$.

### Sample Input 1

```
5 2
3 4 6 7 12
```

### Sample Output 1

```
3
4
6
1
6
```

For $i=1$, choosing $A_1$ and $A_3$ yields $\gcd(\lbrace 3,6 \rbrace) = 3$, which is the maximum.  
For $i=2$, choosing $A_2$ and $A_5$ yields $\gcd(\lbrace 4,12 \rbrace) = 4$, which is the maximum.  
For $i=3$, choosing $A_3$ and $A_5$ yields $\gcd(\lbrace 6,12 \rbrace) = 6$, which is the maximum.  
For $i=4$, choosing $A_4$ and $A_2$ yields $\gcd(\lbrace 7,4 \rbrace) = 1$, which is the maximum.  
For $i=5$, choosing $A_5$ and $A_3$ yields $\gcd(\lbrace 12,6 \rbrace) = 6$, which is the maximum.

--------------

对于每一个 $A_i$, 
