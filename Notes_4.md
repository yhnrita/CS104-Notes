#### 9/5/19


#### Security Levels
```c++
	class A : public B
```
`public` is the type of inheritance (`public`, `protected`, `private`)

**`public` inheritance**
`B public A`
`public` -> `public`
`protected` -> `protected`
`private` -> `inaccessible`

**`protected` inheritance**
`B protected A`
`public` -> `protected`
`protected` -> `protected`
`private` -> `inaccessible`

**`private` inheritance**
`B private A`
`public` -> `private`
`protected` -> `private`
`private` -> `inaccessible`

**What inheritance**
When using "is-a", use public inheritance  
	e.g. A cat _is a_ mammal -> `Cat : public Mammal`

When using "as-a", use protected/private inheritance  
	e.g. A couch is **not** a bed, but it can serve _as a_ bed -> `Couch : protected Bed`

When using "has-a", do NOT use inheritance, use composition
	e.g. A car _has a_ radio ->
```c++
		class Car {
			private:
			Radio* r;
		}
```


#### Multiple Inheritance
**_Diamond of Dread_**
```c++
	class Couch : protected Bed, protected Chair {...};

	class Furniture {
	public:
		int price;
	};

	class Bed : public Furniture {...};

	class Chair : public Furniture {...};
```
```c++
	Couch C;
	cout << c.Bed::price;
	cout << c.Chair::price;
```
The outputs will be different
**Avoid multiple inheritance**


#### Polymorphism
```c++
	DeluxeLinkedList *dll = new IntLinkedList; //Line 1
	IntLinkedList *ll = new DeluxeLinkedList; //Line 2
```
** `DeluxeLinkedList` inherit from `IntLinkedList`
Line 1 will NOT work, but Line 2 WILL work: `DeluxeLinkedList` can do everything an `IntLinkedList` needs to do; but an `IntLinkedList` canNOT do everything a `DeluxeLinkedList` can do
** Only for `public` inheritance


```c++
	class IntLL {
	public:
		void print();
	}

	class DeluxeLL : public IntLL {
	public:
		void print();
	}

	IntLL *ll = new DeluxeLL;
	ll->print();
```
The `print()` from `IntLL` will be called by default


```c++
	class IntLL {
	public:
		virtual void print();
	}

	class DeluxeLL : public IntLL {
	public:
		void print();
	}

	IntLL *ll = new DeluxeLL;
	ll->print();
```
The `print()` from `DeluxeLL` will be called by default


###### In the case where no `virtual` was added
```c++
	IntLL *ll;
	if(blah) {
		ll = new IntLL;
	}
	else {
		ll = new DeluxeLL;
	}

	((DeluxeLL*)ll) -> print();
```








