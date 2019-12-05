#### 12/5/19

#### Final Exam Review
- cumulative but strong emphasis on the last parts
- one hand-written front & back notes

#### Hash Functions
- Efficient (Theta(L))
- Distribute well (Pr(collision) <= 1/m)
- Consistent
- Collision solutions
	○ Chaining
	○ Quadratic probing
	○ Double hashing
- M = # indices
- L = length of the key
- If doing any type of probing, want the hash table to be half empty with a prime size
- If doing chaining, load factor can be close to 1 instead of 0.5

#### Bloom Filters
- Hash table implementing a set instead of a map
- False positive - say yes, answer is no
- False negative - will never happen as long as no remove from the bloom filter
- To control the false positives, use multiple hash functions
	○ Puts keys to all hash functions and set all result to 1
	○ Only if all of them are 1 should you return a `true` when `find()`

#### Tries
- So a key is not read multiple times
- Uses lots of memory
- Great runtime: Theta(L)
- Excels at super long keys
- **Compressed Trie**
	○ Same runtimes
	○ Saves lots of memory

#### Splay Trees
- Remember the rotations
	○ Single rotation (2-level single rotation)
	○ Double rotation (same as AVL double rotation)
	○ Special single rotation (target is one level below the root)
- Not guaranteed to be balanced
- Utilizing the 90/10 rule
- Whenever going down a path, leave it in a better state than before (so the average runtime will be met, Theta(log n))

#### AVL Trees
- When doing `insert()`, the tree is guaranteed to be balanced after 1 rotation (if necessary)

#### Runtime Analysis
```c++
	for(each node i) {
		peek();
		remove();
		for(each edge(i, x)) {
			if(blah)
				add();
			else
				update();
		}
	}
```

#### Interpolation Search
```c++
	InterpolationSearch(int x) {
		while(l <= r) {
			int m = (x - a[l])/(a[r] - a[l]) * (r-l) + l;
			if(a[m] == x)
				return m;
			if(a[m] < x) 
				l = m+1;
			if(a[m] > x)
				r = m-1;
		}
		return -1;
	}
```
- when it _works_, Theta(log log n)
- when it doesn't, Theta(n)

#### Backtracking
- K-color problem
```c++
	Graph G;
	int n;
	int colors[n];
	bool 3Color() {
		initialize colors = 0;
		return helper(0);
	}

	bool helper(int i) {
		if(i == n)
			return true; //colored all the nodes and found no problem

		for(int j = 1; j <= 3; ++j) {
			colors[i] = j;
			bool b = true;
			for(each edge (i, x) in G) {
				if(colors[x] == j) {
					b = false;
					break;
				}
			}

			if(!b) {
				continue
			}
			if(helper(i + 1)) {
				return true;
			}
		}

		colors[i] = 0;
		return false;
	}
```

#### Heap
- Complete tree
- Adding left to right
- Only one place to insert/delete
- bubbleUp/trickleDown accordingly

