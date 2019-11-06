#### 9/17/19

#### Operator Overload
```c++
	class IntArray {
		int *data; //if no category is given, it's private by default
		int mem;
		int size;
	public:
		IntArray(int s);
		IntArray& operator++();
		IntArray operator*(int m) const;
		//"friend" allows the specific function access to private class variables
		friend IntArray operator*(int m, IntArray o);
		//friend class X; //do NOT use unless really REALLY needs it, BAD DESIGN
		friend ostream& operator<<(ostream &o, const IntArray &a);
		IntArray& operator=(const IntArray &o);
	};

	IntArray::IntArray(int s) {
		data = new int[s];
		mem = s;
		size = 0;
	}

	IntArray ia1, ia2;
	if(ia1 == ia2)
		ia1[5] = 7;
	(++ia1)[5] = 7;
	(ia1++)[5] = 7; //does NOT modify the original IntArray
	ia1++;

	ia2 = ia1 * 7; //calls on ia2 = ia1.operator*();
	ia2 = 7 * ia1; //calls on a different function -> ia2 = operator*(7, ia1); <- a global function

	cout << ia; //calls on cout.operator<<(ia); <- needs a global functions since "cout" is not in the class
```

**Operator ++**
```c++
	IntArray& IntArray::operator++() { //prefix ++ (ex. ++array)
	//return an IntArray just in case you want to store it in main
		for(int i = 0; i < size; i++)
			data[i]++;
		return *this; //dereference before returning the pointer
	}

	IntArray IntArray::operator++(int dummy) { //postfix ++ (ex. array++)
	//DO NOT RETURN BY REFERENCE
		IntArray copy = *this;
		++(*this);
		return copy;
	}
```
** Do _*NOT*_ use Postfix ++ unless it is exactly what you want (return a copy of the original)

__Operator *__
```c++
	IntArray IntArray::operator*(int m) const { //the class data will not be changed
		IntArray res(size);
		for(int i = 0; i < size; i++) 
			res[i] = data[i] * m;
		res.size = size;
		return res;
	}

	IntArray operator*(int m, IntArray o) {
		IntArray res(o.size);
		...
		for(int i = 0; i < size; i++)
			res[i] = o.data[i] * m;
		...
	}
```

**Operator <<**
```c++
	ostream& operator<<(ostream &o, const IntArray &a) { //const so the value won't change, reference to save memory
	//return a reference so a series chain of things can be passed in
		for(int i = 0; i < a.size; i++)
			o << a.data[i] << " ";
		return o;
	}
```

**Operator =**
```c++
	IntArray& IntArray::operator=(const IntArray &o) {
		size = o.size;
		delete [] data;
		data = new int[size];
		mem = size;
		for(int i = 0; i < siez; i++) 
			data[i] = o[i];
		return *this;
	}
```







