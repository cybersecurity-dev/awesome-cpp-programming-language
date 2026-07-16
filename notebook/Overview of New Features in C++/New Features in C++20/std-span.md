# std::span
> **`std::span`** is one of the most useful additions in C++20. 

> It provides a lightweight view over a contiguous sequence of objects without owning the data.

std::span is:
- A non-owning view of contiguous memory
- Usually implemented as pointer + size
- Zero-copy and very lightweight
- Safer than raw pointers
- Works with arrays, std::array, and std::vector
- Supports slicing (first, last, subspan)
- Excellent for function parameters

```cpp
#include <iostream>
void print_container(int *data, std::size_t size) {
    for (std::size_t i = 0; i < size; ++i)
        std::cout << data[i] << ' ';
    std::cout << std::endl;
}
int main() {
    int arr[] = { 1, 2, 3, 4, 5 };
    print_container(arr, 5);
    return 0;
}

```

---

```cpp
#include <iostream>
#include <span>
void print_container(std::span<int> values)
{
    for (const int &v : values)
        std::cout << v << ' ';
    std::cout << std::endl;
}
int main() {
    int arr[] = { 1, 2, 3, 4, 5 };
    print_container(arr);
    return 0;
}
```
> A span typically contains only: `pointer + length`

Fixed-Size Span

```cpp
#include <iostream>
#include <span>

void print_container(std::span<int, 3> values)
{
    for (const int &v : values)
        std::cout << v << ' ';
    std::cout << std::endl;
}
int main() {
    int arr3[] = { 1, 2, 3, };
    int arr5[] = { 1, 2, 3, 4, 5 };
    print_container(arr3); //Ok
    print_container(arr5); //Error
    return 0;
}
```
Easy Subranges:

```cpp
#include <iostream>
#include <span>

void print_container(std::span<int> values)
{
    for (const int &v : values.subspan(1,2))
        std::cout << v << ' ';
    std::cout << std::endl;
}
int main() {
    int arrA[] = { 1, 2, 3, 4, 5 };
    int arrB[] = { 2, 3, 5, 7, 11, 13 };
    print_container(arrA);
    print_container(arrB);
    return 0;
}
```
