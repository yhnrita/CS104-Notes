#### 11/7/19

#### Backtracking
**Subset Sum**
Is there a subset of `vector<int> vals` that adds up to `int target`?
```c++
	bool subsets(const vector<int> & vals, int target) {
		return helper(vals, target, 0);
	}

	bool helper(const vector<int> & vals, int target, int index) {
		if(i == vals.size()) {
			if(target == 0)
				return true;
			else
				return false;
		}

		if(helper(vals, target, i + 1))
			return true;
		return helper(vals, target - vals[i], i + 1);
	}
```
- always involves recursion (backtracking _is_ recursion)

#### QuickSort
- Average-case : Theta(n log n)
	- average - input
	- average - luck
- Worst-case : Theta(n^2)
* If you use average runtime for analysis, you will get an average runtime

#### A*
- Like Dijkstra's but inus the distance so far
	- distance-so-far g(v)
	- heuristic estimate h(v)
	- add them
- Manhattan distance
	- x-diff + y-diff
- Euclidean distance
- Letters-out-of-place

#### Heaps
```c++
	void maxHeap::remove() {
		swap(a[0], a[size-1]);
		swap(m[a[0].idx], m[a[size-1].idx]);
		--size;
		trickleDown(0);
	}
	void maxHeal::trickleDown(int parent) {
		...
		swap(a[parent], a[child]);
		swap(m[a[parent].idx], m[a[child].idx]);
		...
	}
```
- If you are using a map within a heap, you are doing it wrong

#### Adjacency Lists/Matrices

#### Interpolation Search
- needs array to be sorted & relatively spread out
- Binary Search: m = (l+r)/2
- Interpolation Search: look for value x
	- m = (x - a[l]) / (a[r] - a[l]) * (r-l) + l

#### Loop Invariant
```c++
	for(int i = 0; i < n/2; ++i) {
		for(int j = i; j < n-1-i; ++j) {
			if(a[j] > a[j+1])
				swap(a[j], a[j+1]);
		}
		for(int j = n-2-i; j > i; --j) {
			if(a[j] < a[j-1])
				swap(a[j], a[j-1]);
		}
	}
```

#### BFS





