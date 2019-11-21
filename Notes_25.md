#### 11/21/19

#### Hash Tables
- Try to generalize the idea of array access for other keys (not just 0:(n-1) indices)
- A dictionary
	- to store "discrete" in the dictionary, store the first five letters `m["discr"]`
	- 26^5 > 1,000,000 English words <- but collisions
- **Hash Function**
	- takes in a key and spits out a number
	- depends on how you implement your has function, the number output will be different
	- Good/Universal Hash Function properties:
		1. efficient to calculate ( O(length of key) )
		2. values should be well distributed (how well?)
			- distribute as well as a random number generator does
			- probability of 2 specific keys collide: <= 1/n 
		3. consistent (the same key should generate the same output)
		- Pseudo-Random: it is consistent but also probability of collision is <- 1/n
	- _**WILL**_ end up with collisions
	- `h(k) = k % n` n is the size of the array
		- breaks the well-distributed rule
		- data is not random
	- `h(k) = random number between 0 : n - 1`
		- the holy grail in terms of distribution
		- but breaks the consistency property
	- _How to solve collision_
		- A hash table is an array of linked lists
		- all keys mapped to the same number will be in the linked list
		- AKA Handling collissions via chaining
		- Typically of size of the chain array is the total expected input
	- Collision happens quickly, typically around **Theta(sqrt(n))**
	- a Hash Function could be considered a One-Way Function
- Good at: Storing Passwords
	- hash the passwords
	- the hashed password will be stored, the real password will be discarded
	- No actual hash table, just hashing the passwords and store the hashed version in the profile
- Worst Case
	- `find()` : Theta(n)
	- `remove()` : Theta(n)
	- `insert()` : Theta(n)
- Average Case
	- Theta(1) for everything
	- technically Theta(key length) for everything
- **Universal Hash Function**
	- x is the largest word's length (in the dictionary example)
	- Assume your input is base-p, where p is a prime slightly larger than the expected number of things
	- w1, w2, w3, ...., wx, each w between 0 to p-1
```c++
	HashTable::HashTable() {
		generate a length-x base-p number uniformly at random
		a1, a2, ...., ax <- SAVE that
	}

	h(w) = (SUM [i : x] : a_i * w_i) % p;
```
- **Probing Hash Table**
	- no linked list
	- an array with 0 or 1 thing
	- if collision happens, go find another place in the table where there's nothing in it
	- Linear Probing
		- bad idea, teaching example only
	- allocate 2 times as many things you expect to get
	- modify the hash function to take in the number of failed attempts
		- `h(k, i) = (h(k) + i) % n`



