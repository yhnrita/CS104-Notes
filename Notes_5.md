#### 9/10/19


#### Polymorphism Cont.
```c++
	class Shape {
		public:
			Shape();
			~Shape();
			virtual void draw();
		protected:
			int color;
			int sides;
	};
```
```c++
	Shape *s;
	if(...)
		s = new Triangle();
	else
		s = new Rectangle();
	s->draw();
```
** No `virtual` -> static binding
** Has `virtual` -> dynamic binding
_Polymorphism_ = many forms (ex. the `draw` could be different based on the type of `s`)

**What to do with the base function? How to draw a "Shape"?**
```c++
	virtual void draw() = 0;
```
** A way to provide a function in the base class but not actually having to implement it
** An abstract (completely virtual) function

** A _pure virtual_ function means a virtual function that is not implemented
** A _pure virtual_ function, causes the class to be _abstract_ (can never instantiate it)


###### Interface
** consists only of _pure_ virtual functions
```c++
	class setADT {
	public:
		virtual void add(int item) = 0;
		virtual void remove(int item) = 0;
		virtual bool contains(int item) = 0;
	};
```
** Multiple inheritance is fine as long as only one of the classes inheriting from is an actual class, all other classes inheriting from are Interfaces

**Example**
```c++
	class IncompleteList {
	public:
		void prepend(int item);
		virtual void insert(int n, int item) = 0;
	};
```
```c++
	void IncompleteLise::prepent(int item) {
		insert(0, item);
	}
```

**Design Example**
```c++
	class Hero
	class Instructor 
	class TAs
	class CPs

	while(1) {
		for(...)
			instructors[i].move();
		for(...)
			TAs[i].move();
		for(...)
			CPs[i].move();
	}
```
_Bad design_ ^
** Create a `Monster` base class, dynamically allocate an array of `Monster` pointers each point to a different type of `Monster`

*__** Always make your destructor _virtual_ in your base case__*


#### Recursion
Recursive: defined in terms of itself

**Example**
calculate: n! = n * (n-1) * (n-2) * ... * 1;
```c++
	int factorial(int n) {
		int p = 1;
		for(int i = 1; i <= n; i++)
			p *= i;
		return p;
	}
```
```c++
	int factorial(int n) {
		if(n ==1) return 1;
		else return n * factorial(n-1);
	}
```

**Tail Recursion**
```
	does stuff
	makes a recursive call
	and returns the result of that call

	Recurse(...) {
		...
		...
		return Recurse(...);
	}
```

**Head Recursion**
```c++
	Recurse(...) {
		Recurse(...);
		...
		...
	}
```
OR
```c++
	Recurse(...) {
		return 1 + Recurse(...);
	}
```

** Tail Recursion is easier to get rid of the recursion than Head Recursion (sometimes compiler even does it for you)











