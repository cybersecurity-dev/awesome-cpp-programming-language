# std::variant
> std::variant is one of the most important features added in C++17. It provides a type-safe union.

> A type-safe tagged union.

```cpp
union Data
{
    int i;
    double d;
};
```

Problems:
- Not type-safe.
- You must manually track which member is active.


```cpp
Data data;
data.i = 42;

std::cout << data.d;    // Undefined behavior
```


```cpp
#include <iostream>
#include <variant>

int main()
{
    std::variant<int, double> value;
    value = 42;
    value = 3.14;
    std::cout << std::get<double>(value) << std::endl;
    return 0;
}
```

std::variant<int, double, std::string> value;
> value can be : `int` _OR_ `double` _OR_ `std::string`


```cpp
#include <iostream>
#include <variant>

int main()
{
    std::variant<int, double> value;
    value = 42;
    value = 3.14;

    if (std::holds_alternative<int>(value)) {
        std::cout << "Contains int\n";
    }
    if (std::holds_alternative<double>(value)) {
        std::cout << "Contains double\n";
    }

    std::cout << std::get<double>(value) << std::endl;
    return 0;
}
```

## Safer Access with `std::get_if`:

```cpp
#include <iostream>
#include <variant>

int main()
{
    std::variant<int, double> value;
    value = 42;
    value = 3.14;

    if (auto *ptr = std::get_if<int>(&value)) {
        std::cout << *ptr << std::endl;
    }
    if (auto* ptr = std::get_if<double>(&value)) {
        std::cout << *ptr << std::endl;
    }
    return 0;
}
```

Main advantages:

- Type-safe
- Replaces unsafe unions
- No manual type tracking
- No dynamic allocation requirement
- Works with std::visit
- Compile-time checked

## Works with std::visit

```cpp
#include <iostream>
#include <variant>
#include <string>
#include <type_traits>
#include <format>

int main()
{
    std::variant<int, double, std::string> val = std::string("Hello World!..");

    std::visit([](auto&& value) {
            using T = std::decay_t<decltype(value)>;

            if constexpr (std::is_same_v<T, int>) {
                std::cout << "Integer: " << value << std::endl;
            }
            else if constexpr (std::is_same_v<T, double>) {
                std::cout << "Double: " << value << std::endl;
            }
            else if constexpr (std::is_same_v<T, std::string>) {
                std::cout << std::format("\"{}\" string length is : {}", value, value.length()) << std::endl;
            }
        },
        val
    );

    return 0;
}
```

## Visiting Multiple Variants

```cpp
#include <iostream>
#include <variant>

int main()
{
    std::variant<int, double> v1 = 10;
    std::variant<int, double> v2 = 2.2;

    std::visit([](auto a, auto b) { 
        std::cout << a + b << std::endl; 
        }, 
        v1, v2 
    );
    return 0;
}
```