#### 10/1/19

#### Midterm Review

**Recursion**
Ex. Merging two separate Linked Lists together, they need to be in correct order when you take out all elements from the other Linked List
```c++
	struct Node 
	{
		int val;
		Node *next;
	};

	bool merge(Node *s, Node *t, Node *m) 
	{
		if(!m && s && t)
			return false;
		if(!s && !t && !m)
			return true;

		if(s && !t && m)
			continue;
		else
			return false;
		if(!s && t && m)
			continue;
		else
			return false;

		if(s->val == m->val)
		{
			return merge(s->next, t, m->next);
		}
		if(t->val == m->val)
		{
			return merge(s, t->next, m->next);
		}
		return false;
	}
```

**Search**
Binary Search
```c++
	int binarySearch(int val, int *a, int start, int end)
	{
		if(r < l)
			return -1;

		int m = (start + end) / 2;
		if(a[m] == val)
			return m;
		if(a[m] < val)
			return binarySearch(val, a, m + 1, end);
		if(a[m] > val)
			return binarySearch(val, a, start, m - 1);
	}
```

**ADTs**
1. Lists
	* ordered
	* get, set, insert, remove
	* provide the position (index) of the thing you want
2. Maps
	* not inheritantly ordered
	* a set of pairs
	* mapping from a key to a value
	* add, remove, find
3. Sets
	* not inheritantly ordered
	* keeps track of things inside it
	* set, add, remove, contains
4. Stacks
	* list-like but can only access the last thing that was added
	* pop, push, top
5. Queue
	* list-like but can only access the first thing that was added
	* dequeue, enqueue, peekfront

**const**
```c++
	const T& myClass::func(const T& data, const T& odata) const {
		//this->stuff = blah;
		//stuff = blah;
		//this->nonconstfunc();
		this->constfunc();
		//data = blah;
		//data.nonconstfunc();
		data.constfunc();
	}

	int main() {
		myClass c;
		//c,func()++;
		Tx = c.func();
		x++;
	}
```

**Inheritance & Polymorphism**
```c++
	class BaseCalss {
	public: 
		BaseCalss() {
			cout << "BC";
		}
		virtual ~BaseCalss() {
			cout << "BD";
		}
		void print() {
			cout << "BP";
		}
	};

	class MidClass : public BaseCalss {
	public:
		MidClass() {
			cout << "MC";
		}
		virtual ~MidClass() {
			cout << "MD";
		}
		virtual void print() {
			cout << "MP";
		}
	};

	class SubClass : public MidClass {
	public:
		SubClass() {
			cout << "SC";
		}
		virtual ~SubClass() {
			cout << "SD";
		}
		virtual void print() {
			BaseCalss::print();
		}
	};


	int main() {
		MidClass m1; //BCMC
		BaseCalss *b = new MidClass(); //BCMC
		b->print(); //BP
		MidClass *m2 = new SubClass(); //BCMCSC
		m2->print(); //BP
		delete b; //MDBD
		SubClass *s; //prints nothing
		delete m2; //SDMDBD
		return; //MDBD
	}
```

**Operator Overload**
```c++
	class IntArray {
	public:
		IntArray& operator++(); //prefix ++
	private:
		int size;
		int alloc;
		int *data;
	};

	IntArray& IntArray::operator++() {
		for(int i = 0; i < size; i++) {
			data[i]++;
		}
		return *this;
	}
```








