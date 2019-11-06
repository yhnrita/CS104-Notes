#### 9/19/19


#### Operator Overload Cont.
**Operator =**
```c++
	IntArray& IntArry::operator=(const IntArray &o) {
		if(data) delete [] data;
		size = o.size;
		mem = size;
		data = new int[size];
		for(int i = 0; i < size; i++)
			data[i] = o[i];
		return *this;
	}
```
** But what if someone wrote `ia1 = ia1`? *_DISASTER_*
How to fix it?
```c++
	IntArray& IntArry::operator=(const IntArray &o) {
		if(this == &o) return *this;
		if(data) delete [] data;
		size = o.size;
		mem = size;
		data = new int[size];
		for(int i = 0; i < size; i++)
			data[i] = o[i];
		return *this;
	}
```


**Copy Constructors**
** If you do not write one, the compiler will write one for you (a shallow copy)
```c++
	IntArray ia;
	IntArray *ia2 = new IntArray(ia);
	IntArray ia3(ia);
```
** If deleting memory without writing a copy constructor, __*BAD*__ things happen
*** The data for `ia` will be deleted when deleting `ia2`
```c++
	IntArray ia;
	func(ia);

	void func(IntArray ia) {
		return;
	}
```
** the Copy Constructor is automatically called to make a shallow copy of `ia` as a local variable
** when exiting the function, the shallow copy is deleted, hence deleting `ia`'s data

##### _Rule of 3_
* operator =
* copy constructor
* destructor
** Do *__NOT__* write any of them, or write __*ALL*__ of them

```c++
	IntArray::IntArray(const IntArray &o) {
		size = o.size;
		mem = size;
		data = new int[size];
		for(int i = 0; i < size; i++)
			data[i] = o[i];
	}
```


#### Linked Lists
* easy to grow, easy to shrink
* modular
* hard to search
```c++
	struct Item {
		int val;
		Item *next, *prev;
		Item(int v, Item* n, Item* p) : val(v), next(n), prev(p);
	};

	void LinkedList::prepend(int n) {}
	
	//global function
	void prepend(Item* &head, int n) {
		Item *newE = new Item(n, head, NULL);
		if(head != NULL)
			head->prev = newE;
		head = newE;
	}

	void LinkedList::append(int n) {
		helper(head, n);
	}
	void LinkedList::helper(Item *curr, int n) {
		if(!curr) {
			head = new Item(n, NULL, NULL);
			return;
		}
		if(curr->next) {
			helper(curr->next, n);
			return;
		}
		curr->next = new Item(n, NULL, curr);
	}
```







