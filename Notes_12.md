#### 10/3/19

#### Midterm Review

#### Runtime Analysis
__*REFER TO THE LECTURE 12 HANDOUT FOR SUMMATIONS*__
f(n) = O(q(n)) means:
	f(n) <= c * q(n), for all n >= n0, for some constants c, n0
- only use Big-O notation when you have limited knowledge
- Big-Omega notation is also limited
- Bit-Theta notation is perfect knowledge: knows exactly what the runtime is
- __*Every runtime analysis in this class is a Big-Theta analysis*__
- runtime analysis should be the analysis of the worst case

**How to do runtime analysis for the worst case**
1. Don't assume specific input
2. If branches, then analyze the worst branch

```c++
	a[i]++; //Big-Theta of 1
```
- If two code blocks T(n) + P(n) run in sequnce, the runtime is the sum

```c++
	for(int i = 0; i < n; i++) { 
		if(a[i][0] == o) { //ϴ(i), goes from 0 to n-1
			for(int j = 0; j < i; j++) { //ϴ(i)
				a[i][j] = i * j; //ϴ(1)
			}
		}
	}
```
The runtime for this block is SUM(i=0 : n-1)[ϴ(i)] = ϴ(n^2);

```c++
	for(int i = 1; i < n; i *= 2) {
		for(int j = 0; j < i; j++) { //ϴ(i)
			a[i][j] = i * j; //ϴ(1)
		}
	}
```
The runtime for this block is SUM(i=0 : log(n-1))[2^i] = ϴ(n);

```c++
	for(int i = 0; i < n; i++) {
		if(i == 0) {
			for(int j = 0; j < n; j++) //ϴ(n)
				a[i][j] = i * j; //ϴ(1)
		}
	}
```
The runtime for this block is ϴ(n) since the `if` condition can only be triggered once

```c++
	int ibs(int t, int *b, int len) {
		int l = 0, h = len - 1, mid; //ϴ(1)
		while(l <= h) { //ϴ(number of iterations)
			mid = (h + l) / 2; //everything in the loop is ϴ(1)
			if(b[mid] == t)
				return mid;
			if(t < b[mid])
				h = mid - 1;
			else
				l = mid + 1;
		}
		return -1; //ϴ(1)
	}
```
The number of iterations is log(h-l), so run time is ϴ(log n)

```c++
	for(int i = 0; i < n; i++) {
		if((i % 2) == 0) {
			for(int j = 0; j < n; j++)
				a[i][j] = i * j;
		}
		else 
			a[i][0] = i;
	}
```
Runtime is ϴ(n^2)

```c++
	for(int i = 1; i < n; i++) {
		for(int j = 0; j < n; j += i) //ϴ(n/i)
			a[i][j] = i * j;
	}
```
Runtime is ϴ(nlog n)

```c++
	for (int i = 0; i < n; i++) {
		for(int j = i; j < n; j++) {
			for(int k = i; k < j; k++) //ϴ(j-i)
				a[i][j][k] = i * j * k; //ϴ(1)
		}
	}
```
For the second loop, runtime is SUM(j=i : n-1)[j-i] == SUM(j=0 : n-1-i)[j] = ϴ((n-i)^2)
For the third loop, runtime is SUM(i=0 : n-1)[(n-i)^2] = n^2 + (n-1)^2 + ... + 2^2 + 1^2
		== SUM(i=1 : n)[i^2] = ϴ(n^3)

**List**
1. set(int pos, T val);
2. get(int pos);
3. insert(int pos, T val);
4. remove(int pos);
** Implemented with a Linked List
1. ϴ(pos)
2. ϴ(pos)
3. ϴ(pos)
4. ϴ(pos)
** Implemented with an ArrayList
1. ϴ(1)
2. ϴ(1)
3. ϴ(n) since if you are out of room, a new array will be allocated and everything is copied over
4. ϴ(n - pos)

average case & amortized analysis will be more fair for some specific 









