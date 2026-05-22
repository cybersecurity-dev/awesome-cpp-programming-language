# [List](https://cppreference.com/w/cpp/container/list.html)
```cpp
#include <list>
template<class T, class Allocator = std::allocator<T>> class list;
```

`std::list` is a container that supports constant time insertion and removal of elements from anywhere in the container. Fast random access is **not supported**. It is usually implemented as a **`doubly-linked list`**. Compared to `std::forward_list` this container provides bidirectional iteration capability while being less space efficient.

```cpp
std::list<int> ilist = { 5, 7, 11, 13 };
for (int n : ilist)
std::cout << n << ", ";
std::cout<<"\n-----------------\n";
    
ilist.push_front(0);
ilist.push_back(-1);
std::for_each(ilist.cbegin(), ilist.cend(), [](auto val) { std::cout << val << ", "; });
std::cout << "\n-----------------\n";
    
//insert with using initializer list
ilist.insert(ilist.cend(), { 4, 3, 2, 1 });
for (auto it = ilist.cbegin(); it != ilist.cend(); ++it) {
    std::cout << *it << ", ";
}
```