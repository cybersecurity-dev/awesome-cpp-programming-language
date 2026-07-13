# std::format
> std::format is a C++20 formatting library that provides a modern, safe, and readable way to create formatted strings, 
> similar to Python's str.format() and inspired by the {fmt} library.

```cpp
#include <iostream>
int main() {
    int ivalX = 32;
    int ivalY = 64;
    std::cout << "x = " << ivalX << ", y = " << ivalY;
    return 0;
}
```

```cpp
#include <iostream>
#include <sstream>

int main() {
    int ivalX = 32;
    int ivalY = 64;
    std::stringstream ss;
    ss << "x = " << ivalX << ", y = " << ivalY;
    std::cout << ss.str();
    return 0;
}
```


```cpp
#include <iostream>
#include <format>

int main() {
    int ivalX = 32;
    int ivalY = 64;
    std::cout << std::format("x = {}, y = {}", ivalX, ivalY);
    return 0;
}
```


## Positional Arguments

```cpp
#include <iostream>
#include <format>

int main() {
    int ivalX = 32;
    int ivalY = 64;
    std::cout << std::format("x = {1}, y = {0}", ivalY, ivalX) << std::endl;
    return 0;
}
```

## Powerful Number Formatting

```cpp
#include <iostream>
#include <format>

int main() {
    int ivalX = 32;
    int ivalY = 64;
    std::cout << std::format("x = {:3}\ny = {:5}", ivalX, ivalY);
    return 0;
}
```

---

```
- {:d}   // decimal
- {:x}   // hex lowercase
- {:X}   // hex uppercase
- {:o}   // octal
- {:b}   // binary
```

---

```cpp
#include <iostream>
#include <format>

int main() {
    int ivalX = 33;
    std::cout << std::format("Decimal = {0:d}\nHexadecimal = {0:x}\nOctal = {0:o}\nBinary = {0:b}", ivalX);
    return 0;
}
```

