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
Here public is an **access specifier** which means that everything inside it can be accessed by every function in the program. We will see private which can be  accessed only by the functions of the class. There is another access specifier which is called protected which can be accessed by inherited classes ( [[#Inheritance]] ).

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

Likewise we can also have destructors. Destructors are members of class that are called when an oject of that class is going to be destroyed:
```c++
Class myclass{
	public:
		myclass(){ /*code*/ } // constructor
		myclass(int a) : value {a} { /*code*/ } // constructor
		~myclass(){ /*code*/ } // destructor
	
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

Static variables are variables that are not object specific and belong to a class. Thus only one copy of a static variable is created. This can be useful when you want to count number of objects belonging to a class:
```c++
class myclass{
	static int count;
public:
	myclass(){
		count++;
	}
	~myclass(){
		count--;
	}
};

int count; //IMPORTANT NOTE! static variables have to be redeclared in the program
```

When a function is declared inside of a class, it's considered to be an *inline function*. Inline functions are like macros in c++ but in funciton form. They just replace the code:
```c++
class myclass{
	int a;
public:
	void get_data(){ std::cout << a << std::endl; } // an inline function
};

int main(){
	myclass x;
	x.get_data();
	// same as 
	std::cout << x.a << endl;
	return 0;
}
```

## Inheritance
Inheritance is one of the most esseential part of OOP. It allows the creation of hierarchical classifications. A class that is inherited is called *base class*, and the class inherits is called *derived class*. 
General form of class inheritance:
```c++
class derived : public/private/protected base{
//code
};
```
