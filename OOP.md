# Classes
## Basic concepts

Constructors are basically functions that are called when an object of a class is initialized.
We can have multiple constructors having one or no argument:
```c++
//header file
Class myclass{
	public:
		myclass(){ // default behaviour
		// code
		}
		myclass(int a){ // second constructor
		// code with a
		}
}
```

In class constructors we can initialize a variable that is const or not:
```c++  
//header file
Class myclass{
	public:
		myclass(){ // default behaviour
		// code
		}
		myclass(int a) : value {a} // assigning a to value even though it's const
		{ 
		// code with a
		}
	private:
		const int value 
}
```

We can add preprocessor commands to include header files only once per program:
```c++
//header file
#ifndef header_H
#define header_H

Class myclass{
	public:
		myclass(){ // default behaviour
		// code
		}
		myclass(int a) : value {a} // assigning a to value even though it's const
		{ 
		// code with a
		}
	private:
		const int value 
}

#endif
```

Alternatively pragma once can also be used to reduce lines of code in supported linkers:
```c++
//header file
#pragma once

Class myclass{
	public:
		myclass(){ // default behaviour
		// code
		}
		myclass(int a) : value {a} // assigning a to value even though it's const
		{ 
		// code with a
		}
	private:
		const int value 
}
```

We should have different files containing function and class definition and initializations:
```c++
//header file
Class myclass{
	public:
		myclass(){ // default behaviour
		// code
		}
		myclass(int a) : value {a} // assigning a to value even though it's const
		{ 
		// code with a
		}
		int read() const // const keyword to indicate that this is a 
						 // function that is not supposed to change 
						 // any member of class aka accessor
	private:
		const int value 
}
```

```c++
// .cpp file
#include "header.h"

myclass::read() const{ // :: is called **scope resolution operator**
// code
}
```

**Function  signitures must match exactly with cpp and header files!!!**

We can declare objects in several ways in classic and modern c++:
```c++
#include "header.h"

int main(){

	myclass obj1; // zero parametr for constructor, default behaviour
	myclass obj2(10); // use of second constructor with custom parametr
	
	// in c++11 we can also write 
	myclass obj3 { }; // zero parametr, same as obj1, obj1 is still legal in c++11
					  // but using this style gives uniformity
	myclass obj4 {10}; // one parametr, same as obj2

}
```

For functions that have optional arguments:
```C++
int function(int data = 0){ //
	return data;
}

int main(){
	function(); // data = 0, returns 0 as default
	function(10); // returns 10
}
```

if we want to have a class that has members of variable types we need to declare templates:
```c++
template <class type> myclass{
//code
}
```
For more see [[Templates]]

## Inheritance
