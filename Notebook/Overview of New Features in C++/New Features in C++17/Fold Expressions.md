# Fold Expressions
> Fold Expressions were introduced in C++17.
> Before C++17, variadic templates typically required recursive code. Fold expressions eliminated much of that boilerplate.


```cpp
#include <iostream>

template<typename T>
T sum(T value) {
    return value;
}

template<typename T, typename... Args>
T sum(T first, Args... args) {
    std::cout << "Parameter count: " << sizeof...(Args) << std::endl;
    return first + sum(args...);
}

int main() {
    
    std::cout << sum(1, 2, 3, 4, 5, 6) << std::endl;
    return 0;
}
```

---

```cpp
#include <iostream>

template<typename... Args>
auto sum(Args... args) {
    std::cout << "Parameter count: " << sizeof...(Args) << std::endl;
    return (args + ...);
}

int main() {
    std::cout << sum(1, 2, 3, 4, 5, 6) << std::endl;
    #std::cout << sum(1, 2, 3, 4, 5, 6.2) << std::endl;
    return 0;
}
```

---

```cpp
#include <iostream>

template<typename... Args>
auto sum(Args... args)
{
    std::cout << "Parameter count: "
              << sizeof...(args)
              << std::endl;

    std::cout << "Parameters: ";
    ((std::cout << args << ' '), ...);
    
    std::cout << std::endl;

    return (... + args);
}

int main() {
    std::cout << "Result = "
              << sum(1, 2, 3, 4, 5)
              << std::endl;
    return 0;
}
```

```bash
template<typename... Args>
void foo(Args... args)
{
    std::cout << sizeof...(Args) << '\n';
    std::cout << sizeof...(args) << '\n';
}
```
- `Args...` = template parameter pack (types)
- `args...` = function parameter pack (values)

## Four Types of Fold Expressions

```
(... + args)            // unary left fold
(args + ...)            // unary right fold
(init + ... + args)     // binary left fold
(args + ... + init)     // binary right fold
```

1. `Unary Left Fold`
    ```cpp
    (... + args)
    ```
    ```cpp
    ((1 + 2) + 3)
    ```
2. `Unary Right Fold`
    ```cpp
    (args + ...)
    ```

    ```cpp
    (1 + (2 + 3))
    ```
3. `Binary Left Fold`
    ```cpp
    (init + ... + args)
    ```

    ```cpp
    (10 + ... + args)
    ```

    ```cpp
    (((10 + 1) + 2) + 3)
    ```
4. `Binary Right Fold`
    ```cpp
    (args + ... + init)
    ```

    ```cpp
    (args + ... + 10)
    ```

    ```cpp
    (1 + (2 + (3 + 10)))
    ```
