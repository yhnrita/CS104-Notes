#### 10/10/19

#### Interpolation Search
- Binary Search requires the array to be sorted
- Interpolation Search _also_ requires data to be sorted
	* It would be also great if the data is equally spread out
	* Interpolation Search outperforms Binary Search if data is equally spread out

```c++
	int *a;

	int interpolationSearch(T x, int l, int r) {
		if(r < l)
			return -1;

		// Needs to have a well-definied subtraction
		int m = (int)((double)(x - a[l])/(a[r] - a[l])*(r - l)) + l; //The line that distinguish from Binary Search

		if(a[m] == x) 
			return m;
		if(a[m] < x)
			return interpolationSearch(x, m + 1, r);
		return interpolationSearch(x, l, m - 1);
	}
```
** If data is sorted, but not equally spread out, it can produce as worse as Linear Search
** Under the asummption that the data is sorted _AND_ equally spread out, it runs at **O(log log n)**

#### Sorting
1. Bubble Sort (BAD)
2. Merge Sort (GOOD)
3. Selection Sort (BAD)
4. Insertion Sort (BAD)
5. Quick Sort (GOOD)
6. Heap Sort

**Stability**
- a sorting algorithm is _stable_ if all elements of the same value maintain their relative order

**Bubble Sort**
** TRY NOT TO USE, OBJECTIVELY BAD
- Swap the two adjacent elements
- Starting from the first element and move all the way to the right (the largest element is at the right)
- Start from the first element and then stop and the second to last element (last 2 are the largest)
- Runtime of Theta(n^2)
```c++
	for(int i = n-1; i > 0; --i) { //SUM[1:n-1]{i} = O(n^2)
		for(int j = 0; j < i; j++) { //O(i)
			if(a[j] > a[j+1]) //O(1)
				swap(a[j], a[j+1]);
		}
	}
```
- _Stable_
- Loop Invariants
- should say that after i iterations, this is the state of the data
- __*Refers to paper handout*__

**Insertion Sort**
- loop through the data and insert each element at the appropriate spot
```c++
	for(int i = 1; i < n; i++) {
		int j = i;
		while(j > 0 && a[i] < a[j-1]) {
			swap(a[i], a[j - 1]);
			--j;
		}
	}
```
- Runtime Theta(n^2)
- Works better than Bubble Sort because it doesn't always loop through everything (there's a stopping condition)
- Stable
- Loop Invariant
	After i iterations, the first i+1 elements are sorted.
	B.C. After 0 iterations, the first 1 element is sorted (1 single element is always sorted)

**Selection Sort**
- Scan through the entire list, find the smallest, move it to the front, shrink your array size, do it again
```c++
	for(int i = 0; i < n - 1; ++i) {
		int smallest = i;
		for(int j = i + 1; j < n - 1; ++j) {
			if(a[j] < a[smallest])
				smallest = j;
		}
		swap(a[i], a[smallest]);
	}
```
- Runtime Theta(n^2)
- Key difference from Bubble Sort: it only swaps once, so it's better than Bubble Sort
- _NOT_ stable
- Loop Invariant
	After i iterations, the first i elements are the smallest i elements and are sorted.
	B.C. After 0 iterations, the first 0 element is sorted.







