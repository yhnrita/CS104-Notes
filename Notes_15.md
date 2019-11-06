#### 10/15/19

#### Merge Sort
- Runtime: Theta(n log n)
- Uses:
	1. Recursion
	2. Divide & Conquer
```c++
	void mergeSort(T *a, int left, int right) {
		if(l < r) {
			int m = (l + r) / 2;
			mergeSort(a, left, m);
			mergeSort(a, m + 1, right);
			merge(a, l, r, m);
		}
	}

	void merge(T *a, int left, int right, int middle) {
		int i = left, j = middle + 1, k = 0;
		T temp[right - left + 1];
		while(i <= m || j <= r) {
			if(j > r || (i <= m && a[i] <= a[j])) {
				temp[k] = a[i];
				++i;
			}
			else {
				temp[k] = a[j];
				++j;
			}
			++k;
		}

		for(k = 0; k < right - left + 1; ++k)
			a[k + left] = temp[k];
	}
```
- Stable
- **Best sorting algorithm that works on anything and is stable**

#### How to solve an Recurrence Relation
1. Induction
2. Solve by tree
__*Refer to handout 15*__

#### Quick Sort
- Divide & Conqure algorithm
- Generally the most effective sort
- Generally Runtime Theta(n log n)
- Steps:
	1. Choose a "Pivot"
	2. Everything smaller than the "Pivot" is shoveled to the left, everything else is shoveled to the right
	3. Repeat for each portion, until reaches down to one single element (base case)
```c++
	void QuickSort(T *a, int left, int right) {
		if(left < right) {
			int m = partition(a, left, right); //m is in the correct place
			QuickSort(a, left, m - 1);
			QuickSort(a, m + 1, right);
		}
	}
```
- Choose your "Pivot" **Wisely**











