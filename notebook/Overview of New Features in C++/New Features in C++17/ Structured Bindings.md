#  Structured Bindings

> Structured Bindings is a feature introduced in C++17 that allows you to unpack (decompose) objects like tuples, pairs, arrays, and structs into individual variables.
> Instead of accessing members with .first, .second, or object fields, you can directly bind them to variables.

```cpp
#include <iostream>
#include <utility>

int main() {
    std::pair<int, std::string> p = {01, "Alice"};

    int id = p.first;
    std::string name = p.second;
    std::cout << id << " " << name << std::endl;
    return 0;
}

```
With structured bindings:
```cpp
#include <iostream>
#include <utility>

int main() {
    std::pair<int, std::string> person = {1, "Alice"};

    auto [id, name] = person;
    std::cout << id << " " << name << std::endl;
    return 0;
}

```

---

```cpp
#include <iostream>
#include <tuple>

int main() {
    std::tuple<int, double, std::string> data = {1, 1.67, "Alice"};

    std::cout << std::get<0>(data) << std::endl;
    std::cout << std::get<1>(data) << std::endl;
    std::cout << std::get<2>(data) << std::endl;
    return 0;
}
```

With structured bindings:

```cpp
#include <iostream>
#include <tuple>

int main() {
    std::tuple<int, double, std::string> data = {1, 1.67, "Alice"};

    auto [number, value, text] = data;

    std::cout << number << std::endl;
    std::cout << value  << std::endl;
    std::cout << text   << std::endl;
    return 0;
}
```

Array with structured bindings:

```cpp
#include <iostream>

int main() {
    int arr[3] = {11, 13, 17};

    auto [a, b, c] = arr;

    std::cout << a << " " << b << " " << c << std::endl;
    return 0;
}
```