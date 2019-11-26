#### 11/26/19

#### Collision Resolution
**Linear Probing**
- if collision happens, move one down until finding an empty slot
- will create primary clumping
- very long chain to search
- _BAD_ probing, never use it

**Quadratic Probing**
- `h(k, i) = (h(k) + (i^2)) % n`
	- if collision, increment `i` and try again
	- `k` is the key and `i` is the value added
- ~50% of the hash table _**has**_ to be empty so collision happens less
- Example:
	- `h(k) = k % 10`
	- too full, not prime sized, bad hash function
	- insert 1, 11, 2, 21, 12, 31, 41
			----------
		0	|	31
			----------
		1	|	1
			----------
		2	|	11
			----------
		3	|	2
			----------
		4	|
			----------
		5	|	21
			----------
		6	|	12
			----------
		7	|	41
			----------
		8	|
			----------
		9	|
			----------
- For _**any**_ hash table that will be using probing to have:
	- #items/#indices <= 0.5
- For hash tables using chaining
	- about the same size as the amount of data you will have
- Example:
	- `h(k) = k % 9`
	- insert 36, 27, 18, 9, 0
			----------
		0	|	36
			----------
		1	|	27
			----------
		2	|	
			----------
		3	|	
			----------
		4	|	18
			----------
		5	|	
			----------
		6	|	
			----------
		7	|	9	
			----------
		8	|
			----------
	- no spot to place 0
	- because it's not a prime size
- _**Quadratic probing has to have a prime hash table size AND 50% full property**_
- Secondary Clumps
	- A clump of all things mapping to the same index
- Example
	- Key = k
	- at i-th attempt, check (h(k) + i^2) % n
	- at j-th attempt, check (h(k) + j^2) % n
	- if i != j && 0 <= i,j <= n/2, they won't equal
	- Assume: (h(k) + i^2) % n = (h(k) + j^2) % n
			i^2 % n = j^2 % n
			(i^2 - j^2) % n = 0
			(i+j)(i-j) % n = 0       <--- n is prime, so it is a full divisor of _one_ of them
			0 < i+j < n
			-n < i-j < n
			contradiction

**Double Hashing**
- Having a second hash function `h'(k)` in addition to `h(k)`
- `h(k, i) = (h(k) + i * h'(k)) % n`
- linear probing but with different (random) factors
- linear probing is a specific double hashing where `h'(k) = 1`
- `h(k)` can*NOT* equal to `h'(k)`
- double hashing does _NOT_ have secondary clumping
- double hashing _does_ have tertiary clumping
- A good second hash function is:
	- `h'(k) = p - (k % p)`
	- `p` is a prime slightly smaller than n
	- can*NOT* every return 0
- Still needs a prime hash table size and _preferred_ 50% full


#### Removal
- In a probing hash table, there are two types of empty
	- every slot start with empty empty
	- after something is removed, they are marked as removed, but not marked as empty empty
	- if insert, treat remove as empty
- Remove count _against_ load factor
	- `a = (#items + #removals) / #indices`
	- if a > 0.5
		- if primarily #items, double the size of the hash table
		- if primarily #removals, re-hash the entire table



#### Bloom Filters
- A hash table is usually implementing a map (putting in a key and get hashed value out)
- Set implementation: was it inside the hash table or not
- Blook Filter is a hash table that implements a set and condense memory
- Simple implementation
	- have a hash table of bits, either 0 or 1
	- problem with collision
- A bloom filter is probabilistic
	- more compact at cost: sometimes return the wrong answer
- False Positive
	- we say "yes" but answer is "no"
	- will always be there in bloom filters, but we try to minimize it
- False Negative
	- we say "no" but answer is "yes"
	- bloom filter will _neve_ return a false negative as long as **no removal**
- Do _NOT_ use bloom filters if ever worried about removing something
- Reduce collision
	- use multiple hash functions
	- `h1(k) = (7x + 4) % 10`
	- `h2(k) = (2x + 1) % 10`
	- `h3(k) = (5x + 3) % 10`
	- only if all three of them are 1 then saying yes it is there
	- choose hash table size 
