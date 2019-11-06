#### 9/12/19

#### Recursion cont.
**Binary Search**
```c++
	int binarySearch(int n, int* array, int low, int high) {
		if(high < low)
			return -1;
		int mid = (high + low) / 2;
		if(n == b[mid])
			return mid;
		if(n < b[mid])
			return binarySearch(n, b, low, mid - 1);
		else if(n > b[mid])
			return binarySearch(n, b, mid + 1, high);
	}
```

**Other recursive definitions examples**
* A string of lower-case letter is:
	1. the empty string
	or
	2. a single letter 'a' to 'z' followed by a string of lower-case letters
* A non-negative integer is:
	1. 0
	or
	2. (n + 1) where n is a non-negative integer
* A palindrome is:
	1. the empty string
	or
	2. a single letter
	or
	3. xPx where x is a single letter 'a' - 'z' and P is a palindrome
* A simple algebraic expression is
	1. a number
	or
	2. a variable
	or 
	3. (A + B) or (A * B) where A, B are simple algebraic expressions


#### Operator Overloading
```c++
	int min(intx, int y);
	double min(double x, double y);
```
Allowed since difference can be determined by the different parameters the user passed in
```c++
	bool foo();
	void foo();
```
NOT allowed since only return types are different

`x + y`
* `+` is a function
* `operator+(x, y);`
* `x.operator+(y);`

You can overload functions, therefore you can overload `+` with your own definition

```c++
	class IntArray {
	private:
		int size; //num of things in array
		int mem; //allocated slots
		int *data;
	public:
		int& operator[](int index);
		bool operator==(IntArray other); //the first object is the class calling the function
	};

	int& IntArray::operator[](int index) { //return a reference so user can overwrite the value
		return data[index];
	}

	bool IntArray::operator==(IntArray other) {
		if(size != other.size)
			return false;
		for(int i = 0; i < size; i++) {
			if(this->data[i] != other.data[i]) //equivalent to this->data[i] != other[i]
				return false;
		}
		return true;
	}

	IntArray n, n1, n2;
	...
	n[5] = 7;
	if(n1 == n2) {} // equivalent to n1.operator==(n2)

```







