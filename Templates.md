# Templates
We can create generic functions and classes using templates. Meaning we don't have to specify what the types of the variables are. 

General form of a template is:
```C++
template <class var> return_type func_name(){
//code
}
```
instead of `class var` we can use `typename var`. Here var is a variable that has unknown type that will be specified by the compiler.
Example:
```C++
#include <iostream> 
using namespace std;

// This is a function template. 
template <class X>           //whether these are in the same line or not
void swapargs(X &a, X &b) {  //doesn't matter (thanks python) 
							   
void swapargs(X &a, X &b) {
	X temp;
	temp = a; a = b;
	b = temp; 
}

int main() {
	int i=10, j=20;
	double x=10.1, y=23.3; char a='x', b='z';
	cout << "Original i, j: " << i << ' ' << j << '\n'; 
	cout << "Original x, y: " << x << ' ' << y << '\n'; 
	cout << "Original a, b: " << a << ' ' << b << '\n';
	swapargs(i, j); // swap integers 
	swapargs(x, y); // swap floats 
	swapargs(a, b); // swap chars
	cout << "Swapped i, j: " << i << ' ' << j << '\n'; 
	cout << "Swapped x, y: " << x << ' ' << y << '\n'; 
	cout << "Swapped a, b: " << a << ' ' << b << '\n';
	return 0;
}
```

We can of course define more than one generic data type:
```C++
template <class X, class Y> // X and Y can be int float string char or 
							// anything independently 
```

We can explicitly overload a generic function:
```C++
template<class X> 
void add_val(X a, X b){ // here a and b are of type X 
	std::cout << a+b << endl;
}

void add_val(std::string a, std::string b){ // this function will be called when
											// a and b are both strings
	std::cout << a + " " + b << endl;
}
```
This is overloading function add_val for string types. For more see [[Function Overloading]]

We also overload a generic function definition itself:
```c++
template <class X> void func(X a){ //when only one argument is passed 
	//code
}

template <class X, class Y> void func(X a, Y b){ //when two arguments are passed
	//code
}
```

We can also define generic classes using templates:
```c++
#define SIZE 10

template <class ClassType> class myclass{
private:
	ClassType array[size]; //example array of an object of myclass 
						   //having ClassType type 
public:
	myclass(){
		//constructor code
	}
	
};
```

once the class is defined we can create an object of this class using:
```c++
myclass<type> obj1; //type is the type of the object (int, double, etc.)
//or
myclass<type *> obj2 //we can also create object pointers cool ya?
```

we can even have classes of custom structs that we have defined:
```c++
struct contact{
	std::string name;
	std::string surname;
	int number;
};

int main(){
	/*
	 * Some code
	*/
	myclass <contact> obj; //this will be useful with data 
						   //structures as we will see
}

```

### *Will be continued with more content regarding classes*

