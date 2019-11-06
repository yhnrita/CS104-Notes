#### 10/8/19

#### Runtime Analysis for Recursion
__*Refers to the paper handout*__

#### Array Lists
**Runtime Analysis**
__*Refers to the paper handout*__

```c++
	ArrayList a(1);
	for(int i = 0; i < n; i++) {
		a.push_back(i);
	} //naive O(n^2)
```
Analysis:
1. 1 time //1 thing, 1 slot
2. 2 times (create new array, copy over) //2 things, 2 slots
3. 4 times (create new array, copy over) //3 things, 4 slots
4. 1 time //4 things, 4 slots
5. 8 times //5 things, 8 slots
6. 1 time //6 things, 8 slots
7. 1 time //7 things. 8 slots
...
** The ArrayList will grow log(n) times so: SUM[1 : logn](2^i) + SUM[1 : n-logn](1)

**Amortized Runtime**
- Divide a runtime by the number of calls
- _Different_ from Average Case Analysis

#### Sorted List
- Do _NOT_ need a set() function
- Modify insert() function
1. insert(T val)
2. remove(int pos)
3. T get(int pos)

#### Interpolation Search
- Make a logical guess about where the thing is going to be and continues with binary search
