# [Vector](https://cppreference.com/w/cpp/container/vector.html)

```cpp
#include <vector>
template<class T, class Allocator = std::allocator<T>> class vector;
```
Except for the `std::vector<bool>` partial specialization, the elements are stored contiguously, which means that elements can be accessed not only through iterators, but also using offsets to regular pointers to elements. 

```cpp
std::vector<int> ivec = { 1, 2, 3, 4, 5 };
//lambda expression
auto print = [](const int& n) { std::cout << n << ' '; };
    
std::for_each(ivec.cbegin(), ivec.cend(), print);
std::cout << std::endl;
std::for_each(ivec.crbegin(), ivec.crend(), print);
```