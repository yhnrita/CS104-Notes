#### 10/22/19

#### Quick Sort
- Divide & Conquer
```c++
	void quickSort(T *a, int l, int r) {
		if(l < r) {
			int m = partition(a, l, r);
			quickSort(a, l, m - 1);
			quickSort(a, m + 1, r);
		}
	}

	int partition(T *a, int l, int r) {
		int i = l;
		T p = a[r];
		for(int j = l; j < r; ++j) {
			if(a[j] <= p) {
				swap(a[i], a[j]);
				++i;
			}
		}
		swap(a[i], a[r]);
		return i;
	}
```
- input is _NOT_ random
- Any efficient Quick Sort algorithm _will_ have a worst case of Theta(n^2)
- __*Runtime Analysis Refer Handout 16*__
- How to choose a pivot?
	1. Choose the middle element (median position for all sorted data)
	2. Median-of-3
		- `a[l]`, `a[(l+r)/2]`, `a[r]`
		- find the median of the 3, choose that as pivot
	3. Median-of-5
		- 0%, 25%, 50%, 75%, 100% mark values
		- choose the median of these 5 as pivot
- Average Case O(n log n)
```c++
	//This is worse algorithm design, only used to show O(n log n)
	int m;
	while(...) {
		m = partition(a, l, r);
	} //Repeat until the pivot is in the middle 50% of the data (50% chance, takes 2 times on average)

	/*  Worst case recurrent relation
	 *	f(n) = f(3n/4) + f(n/4) + Theta(n)
	 *	See analysis by tree on Handout 16
	 */
```
- Quick Sort is _NOT_ stable
```c++
	int partition(T *a, int l, int r) {
		int i = l;
		int pivot = pivotSelectionProcedure();
		swap(a[pivot], a[r]);
		T p = a[r];
		for(int j = l; j < r; ++j) {
			if(a[j] <= p) {
				swap(a[i], a[j]);
				++i;
			}
		}
		swap(a[i], a[r]);
		return i;
	}
```


#### Templates
```c++
	template <class T> //put this before any templated item
	struct Item {
		T value;
		Item<T> *n, *p;
	};
	Item<int> i1;
	Item<string> i2;
	Item<Item<double>> i3;
```
```c++
	template <class T>
	class LinkedList {
	public:
		LinkedList(T n);
		void prepend(T n);
	private:
		Item<T> *head;
		void printReverseHelper(Item<T> *c);
	};

	template <class T>
	void LinkedList<T>::prepend(T n) {
		...
	}
```
**Multi-templated Types**
```c++
	template <class kT, class vT>
	class map{
		...
	};
```
**Templated Function**
```c++
	template <class T>
	int partition(T *a, int l, int r) {
		...
	}
```
- `template <class T>` only covers until the most recent `}`
- If a class is templated, every single function need to be implemented with `template <class T>`
- Disadvatanges of templates:
```c++
	#include "linkedlist.h"

	int main() {
		LinkedList<string> ll;
		LinkedList<int> lli;
	}
```
	- **Cannot** compile `linkedlist.cpp` because there is _NO_ real code
	- Only write a `linkedlist.h` with all the initialization and implementation


#### Graphs
- G(V, E)
	- V = {vertices}; |V| = n
	- E = {edges}; |E| = m
- Computer Network: undirected
- Internet: directed (pages)
- Social Networks
	- FaceBook: undirected (mutually friends)
	- Twitter: directed (one can just follows the other)
- Disadvantage: Graphs can only capture _pairwise relationships_
- Hypergraphs: captures more than pairwise relationships








