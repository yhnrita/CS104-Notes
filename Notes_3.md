#### 9/3/19
#
#

#### What to do when there's an error:
1. terminate, error message
2. ```
	#include <cassert>
	assert (pos <size()>)
	```
3. `return -1`
4. pass in a `bool& r`

#
#
#### Exceptions
**Programmer**
```c++
	#include <exception>
	int LL::get(int pos) {
		if(pos >= sizer()) 
			throw exception(); //construct an exception object on the spot
	}
	...
	return;
```
#
**User**
```c++
	try {
		cout << ll->get(15) << endl;
		cout << ll->get(5) << endl;
	}
	catch(exception &e) {
		cout << e.what() << endl;
	}
```
#
**More Functions**
`#include <stdexcept>`
```c++
	int LL::get(int pos) {
		if(pos >= size())
			throw out_of_range("blah...blah...");
	}
	...
	return;
```
```c++
	try {
		cout << ll->get(15) << endl;
		cout << ll->get(5) << endl;
	}
	catch(out_of_range &e) {
		cout << e.what() << endl;
	}
```
Every type of exception (`out_of_range()`, `basic_error()`, etc.) is just a special type of `exception()`

#
#
#### Inheritance
```c++
	class DeluxeLinkedList : public IntLinkedList {
	public:
		void print();
		bool isEmpty();
	};
```
`DeluxelinkedList` is the subclass for `IntLinkedList`

#
**If both base class and subclass has `print()`**
```c++
	DeluxeLinkedList *dll = new DeluxelinkedList;
	dll->print(); //call on the print() within DeluxeLinkedList
	dll->IntLinkedList::print(); //call on the print() within IntLinkedList
```

#
**function types**
A subclass cannot access the private functions in the base class
```c++
	class IntLinkedList {
	public:
	protected: //both the base class and subclass can access, users cannot
	private: //only base class
	};
```

#
**base class**
```c++
	class IntLinkedList {
	public:
		IntLinkedList(int n);
		IntLinkedList();
		~IntLinkedList();
		void prepend(int x);
		void print();
	private:
		Item* head;
	}
```
**subclass**
```c++
	class DeluxeLinkedList : public IntLinkedList {
	public:
		void print();
		bool isEmpty();
		DeluxeLinkedList(); //default constructor
		DeluxeLinkedList() : IntLinkedList(5) {}; //call the specific base ckass constructor
		~DeluxeLinkedList();
	}
```
**execution**
```c++
	int main() {
		DeluxeLinkedList *dll = new DeluxeLinkedList;
		dll->print();
		delete dll;
		return 0;
	}
```
When a `DeluxeLinkedList` constructor is called, a `IntLinkedList` constructor will be automatically called
When a `~DeluxeLinkedList` destructor is called, a `~IntLinkedList` destructor will be automatically called (at the end of the subclass destructor)











