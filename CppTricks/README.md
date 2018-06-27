# Some C++ Tricks
 ## Vector as map value, insert new key and push back immediately
 ## Sub1

## Vector as map value, insert new key and push back immediately
[Reference](https://stackoverflow.com/questions/31166751/vector-as-map-value-insert-new-key-and-push-back-immediately-c)

 - `std::map::operator[]`

`mapped_type& operator[] (const key_type& k);`

If _k_ matches the key of an element in the container, the function returns a reference to its mapped value.

If _k_ does not match the key of any element in the container, the function inserts a new element with that key and returns a reference to its mapped value. Notice that this always increases the container size by one, even if no mapped value is assigned to the element (the element is constructed using its default constructor).

A similar member function, `map::at`, has the same behavior when an element with the key exists, but **throws an exception** when it does not.


## Sub1
