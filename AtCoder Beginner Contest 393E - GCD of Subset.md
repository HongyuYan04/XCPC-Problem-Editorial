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

### Hint
对于每一个 $A_i$, 它的答案一定是 $A_i$ 的某个因子。

考虑记录每一个数字 $x$, $A$ 中有多少数字是它的倍数, 从大到小枚举 $A_i$ 的因子 $x$, 若 $cnt_x \ge K$, 那么 $x$ 就是所要求的答案。

记值域为 $V$, 时间复杂度为 $\mathcal{O}(VlogV + NlogV)$。

```
c++

#include <bits/stdc++.h>

using i64 = long long;

constexpr int V = 1E6;
int f[V + 1][240], ind[V + 1], cntm[V + 1];

inline int read() {
	bool sym = false; int res = 0; char ch = getchar();
	while (ch < '0' || ch > '9') sym |= ch == '-', ch = getchar();
	while (ch >= '0' && ch <= '9') res = (res << 3) + (res << 1) + (ch & 15), ch = getchar();
	return sym ? -res : res;
}

int main() {
	for (int i = V; i >= 1; i--) {
		for (int j = i; j <= V; j += i) {
			f[j][ind[j]++] = i;
		}
	}
	
	int N = read(), K = read();
	
	std::vector<int> A(N);
	for (int i = 0; i < N; i++) {
		A[i] = read();
		for (int j = 0; j < ind[A[i]]; j++) {
			cntm[f[A[i]][j]]++;
		}
	}
	
	for (int i = 0; i < N; i++) {
		for (int j = 0; j < ind[A[i]]; j++) {
			if (cntm[f[A[i]][j]] >= K) {
				printf("%d\n", f[A[i]][j]);
				break;
			}
		}
	}
	return 0;
}
```
