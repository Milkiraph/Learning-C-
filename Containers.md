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
For more info on [[Iterators]]

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

# Maps
There are two kinds of maps: ordered and unordered. The main difference between them is that unordered maps are faster to work with. Maps are like dictionaries from python: they have keys and values for each element. Main map functions are:
```c++
#include <iostream>
#include <map>
#include <unordered_map>
#include <iterator>
#include <any>

using namespace std;

int main() {

	map<int, int> mp;
	mp.insert(pair<int, int>(1, 10)); 
	mp[2] = 20; // another way to insert into maps
	mp.insert(make_pair(2, 30)); // this is not an error but will 
								 //not do anything new
								 // if you want to have same keys 
								 //multiple times use multi_map

	// we can check if a key exists in a map using 
	if (mp.find(1 /*key*/) == mp.end() ) {
		// code
	}
	// or
	if(mp.count(1) == 0){
		// code
	}


	map<int, int>::iterator itr = mp.begin();
	cout << mp.count(2) << endl;

	cout << "Elements in ordered map:" << endl;
	for (itr; itr != mp.end(); itr++) {
		cout << "\t" << itr->first << "\t" << itr->second << endl;
	}

	unordered_map<int, int> u_mp;
	u_mp.insert(pair<int, int>(1, 10));
	u_mp[2] = 20; // another way to insert into maps

	unordered_map<int, int>::iterator u_itr = u_mp.begin();
	
	cout << "Elements in unordered map:" << endl;
	for (u_itr; u_itr != u_mp.end(); u_itr++) {
		cout << "\t" << u_itr->first << "\t" << u_itr->second << endl;
	}

	// if you want to create a map that can store multiple types like python dict use std::any
	// this is only supported in C++17 and later 
	map<any, any> dict;
	dict.insert(make_pair("string", 10)); // cool heh?

	return 0;
}
```

We have iterators for maps as well. 


# Sets
