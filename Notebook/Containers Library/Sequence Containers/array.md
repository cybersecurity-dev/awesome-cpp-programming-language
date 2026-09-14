# [Array](https://cppreference.com/w/cpp/container/array.html)

```cpp
#include <array>
template<class T, std::size_t N> struct array;
```
`std::array` is a container that encapsulates fixed size arrays. 

```cpp
std::array<int, 4> iarray1{ {5, 2, 3, 7} };
std::sort(iarray1.begin(), iarray1.end());

for (const auto& i : iarray1)
    std::cout << i << ' ';
std::cout << std::endl;

std::array<int, 3> iarray2 = { 7, 11, 13 };
std::ranges::reverse_copy(iarray2, std::ostream_iterator<int>(std::cout, " "));
std::cout << std::endl;
return 0;
```
outputs:

```powershell
2 3 5 7
13 11 7
...exited with code 0 (0x0).
Press any key to close this window . . .
```