#### 12/3/19

#### Bloom Filters
- Hash table : map
- Bloom filter : set <- a hash table trying to implement a set
- collision: false positive
- Monte Carlo randomized
	- gambles with the answers
	- sometimes it might give wrong answer
	- e.g. Bloom Filters
- Las Vegas randomized
	- gambles with the runtime
	- sometimes it might be significantly longer
	- e.g. QuickSort, Hash Tables
- a set allows for:
	1. add
	2. contain
	3. remove <- usually _NOT_ allowed in a bloom filter
- hash functions
	- m = # indices
	- n = # things
	- k = # hash functions
	- k = (m/n) * ln 2
	- For an error rate <= 1%
		- m / n = 9.2
		- k = 7
	- For an error rate <= 0.1%
		- m / n = 14
		- k = 10
	- In general, most bloom filters use 2-20 hash functions
- Any situation where a false positive is not the end of the world is a good place to use bloom filters
- If willing to spend slight extra time to check on the positives and majority of the answers are no, bloom filters are good choice
- A Bloom Filter is not actually a table of booleans, it's actually a table of ints
	- A `bool` is 4 bytes, not memory efficient
	- Each `int` is 32 bits, bits 0-31 will be in the first int, bits 32-63 will be in the second int, etc.
	- Find the value of the specific bit (represent one "index") is called _Masking_
	- to find the x-th bit:
		- it's in the `floor(x / 32)` -th int
		- then mask with `arr[x / 32] & (1 << (x % 32))`
		- if the result is 0, then the bit is 0; else, the bit is 1

#### Tries
- For very longkey length
- effectively gets Theta(L) to find a key (L = length of key)
- comparing the key but doing it one step (character) at a time
- Application: auto-complete
- Main problem: 
	- uses lots and _lots_ of space
	- there's no try that is both time and space effective
- **Compressed Tries**
	- get rid of an unnecessary node and merge the edges
	- every node is either
		- a word node
		- the root node
		- has at least 2 children
	- typically the root node would be the empty string
	- Network Routing

#### Suffix Trees
- a compressed try of one string S and all its suffixes
- _NOT on the final_