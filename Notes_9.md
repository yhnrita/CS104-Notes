#### 9/24/19

#### ADTs (Abstract Data Types)
What public functions are available? 
Those are the ADTs: 
1. Add `int` to the list
2. Remove `int` from the list
3. Print the list in order
...

**List**
1. `insert(int pos, T val)` (0 : size) <- 0 to size
2. `remove(int pos)` (0 : size - 1)
3. `set(int pos, T val)` (0 : size - 1)
4. `T get(int pos) const` (0 : size - 1)
** A List ADT is a lot like an array
** If a List ADT is implemented with an array, it is called an ArrayLists
** What is the 7th thing in the list
** Ordered

**Set (Bag)**
1. `add(T item)`
2. `remove(T item)`
3. `bool contains(T item)`
** Basically the idea of a mathematical set
** Is there a thing or not
** Usually implemented using a Hash Table, Red Black Tree, or AVL Tree, or Bloom
** Not ordered

**Map (Dictionary)**
1. `add(kT key, vT val)`
2. `remove(kT key)`
3. `vT get(kT key)`
** `key` is the key info used to search for the item, can be anything
** Every key is unique, but not necessarily the values associated with the keys
** Where is that thing
** Usually implemented using a Hash Table, Red Black Tree, or AVL Tree
** Not ordered

**Queues**
```c++
	class QueueADT {	
	public:
		void enqueue(const T& data);
		const T& peekfront() const; //ensures the returned value will not be changed, and no copy will be made
		void dequeue();
	};
```
** More limited
** FIFO (First In, First Out)
** A Singly Linked List will work great: dequeue from the Head, append to the Tail (needs both head & tail pointers)
** A circularly wrapped array with an int tracking the current "head" index and one tracking the current "tail"

**Stacks**
```c++
	class StackADT {
	public:
		void push(const T&  data);
		const T& top() const;
		void pop();
	};
```
** LIFO (Last In, First Out)
** A Singly Linked List will work great: pop from Head, append to Head (needs only head pointer)
** A regular array
** Recursive in nature: anything you can do with recursion, you can do with a stack; anything you can do with a stack, you can do with recursion
** A stack is
1. The empty stack
	OR
2. `s.push(data)` where `s` is a stack, and `data` is any one data item

** _Stack Exioms_
1. For all stack `S`, `S.push(data).top() = data;`
2. For all stack `S`, `S.push(data).pop() = S;`
** `s.push(5).top().pop()` is NOT a valid operation, since `s.push(5).top()` is an int not a stack

```c++
	stringstream word;
	stack s;
	cin >> word;
	for(int i = 0; i < word.str().size(); i++) {
		char c;
		c << word;
		s.push(c);
	}
```

Ex. Given a string of lowercase letters, parentheses, brackets, braces.
	Is it properly parenthesized?
	Answer in Notes_10









