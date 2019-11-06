#### 9/26/19

#### ADTs Cont.

**Stack Cont.**
Ex. Given a string of lowercase letters, parentheses, brackets, braces.
	Is it properly parenthesized?
1. start w/ an empty stack
2. if there are no more characters, stack is empty, accept
3. if there are no more characters, stack not empty, reject
4. scan the next character
5. If the character is (, [, {, add it to stack
6. If the character is ), ], }, pop the top item from stack, and reject if they don't match
7. loop to step 2
	Example input: ([ab{c}]de())

**Queues**
A queue is either:
1. an empty queue
	OR
2. `Q.enqueue(data)`, where `Q` is a queue, and `data` is a data item

**Deques**
aka "Double Ended Queue"
** Can add to either side and pop from each size
** Constant runtimes for everything
** Memory cost: similar to a Doubly Linked List


#### STL
aka "Standard Template Library"
Ex. `vector<int> v;`, `vector<string> vs`;
**Contains**:
* list
* set
* map
* unordered_set
* unordered_map
* stack
* queue
* priority_queue

**map**
_**MIGHT WANT TO USE FOR HW4**_
** **The first type need to be sortable, the second type does not have to**
** __"Sortable"__ means there is `operator<` defined for the type
** _Can_ be fixed by doing operator overload
```c++
	#include <map>
	#include "student.h"
	int main() {
		map<string, Student> m;
		Student s1("Tommy", 86328):
		Student s2("Tina", 54982);

		//the map is overloading the operator[]
		m["Tommy"] = s1; //insert Tommy into the map pairing "Tommy" with s1
		m["Tina"] = s2;

		m.erase("Tommy");
		m.erase("Tina");

		//behave the same way as using m[]
		pair<string, Student> p("Tina", s2); //see notes below
		m.insert(p);
```

**Pairs**
** Take 2 objects and paste them into a single discrete object
```c++
	std::pair<string, int> mypair("Bill", 1);
	std::cout << mypair.first << mypair.second;

	std::pair<int, pair<int, int>> p(1, pair<int, int> (2, 3));
	std::cout << p.second.first;
```
** A Map uses Pairs
* a map is a collection of objects
* maps store pairs of Type1, Type2
* `insert(pairs)` can only be used with pairs

**Iterator**
** Purpose is to walk through the data of a data structure one at a time
```c++
	map<int, string> m;
	...

	map<int, string>::iterator it; //type of the iterator object
	vector<int>::iterator vint;
	list<string>::iterator list;

	//decalred an interator class inside another class
	class Map {
	public:
		class Iterator {
			...
		};
	};
```
** An iterator is _NOT_ a pointer, but it behaves like a pointer
```c++
	//how to use iterators
	map<int, string>::iterator it;
	map<int, string> m;
	for(it = m.begin(); it != m.end(); it++) {
		//the iterator dereferenced will return the pair in the map at that location
		cout << it->first << it->second << endl;
	}
	//takes in a value and finds the first data that has that value
	//in this case, the "42" is the key
	it = m.find(42);
	if(it != m.end()) //end() is pointing at the place AFTER the last data
		cout << "life=" << it->second;
```










