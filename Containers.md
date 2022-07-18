# Vectors
Vectors are onedimensional automatically resiazed **arrays**. Because vectors are essentially arrays, you don't want to have a pointer to a sepcific item in the vector. For example:
```c++
#include <vector>
using std::vector

int main(){
	vector<int> vec; 
	vec.push_back(10); //a memory location is allocated
	
	int ptr = vec.begin() + 0; //learn more about this in iterator
	vec.push_back(20); //a new memory location is allocated with more space
					   //dereferencing ptr is now meaningles 
					   //because memory location of that value has changed
	return 0;
}
```


# Lists
Lists are essentially one-directional linked lists. Lists unlike vectors are non-contiguous meaning that we cannot access items in a list using brackets. Some list functions in stl:
```c++
#include <iostream>
#include <list>
using std::list

int main(){

	list<int> lst;
	lst.push_back(20); //push 10 to the end of the list
	lst.push_front(10); //push 20 to the beginning of the list
	lst.pop_front(); //removes first element of the list
	lst.pop_back(); //removes last element of the list
	auto b = lst.begin(); // begin() returns an iterator to the beginning of list
	auto e = lst.end(); // same for the end of list
	if(lst.empty()) //returns true if the list is empty
		std::cout << "List is empty"
	
	int el = 10;
	lst.remove(el); //removes all instances of el in the list
	
	list<pair<int, int>> pair_list; // we can also create a pair list
	pair_list.fist(); // access 'key' of pair list
	pair_list.second(); //access 'value' of pair lsit
 	 
	return 0;
}
```