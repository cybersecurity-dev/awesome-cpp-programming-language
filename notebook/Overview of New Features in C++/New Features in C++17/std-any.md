# std::any
> `std::any` is a type-safe container introduced in C++17 (and available in C++20) that can hold a value of any copyable type.
  
```cpp
#include <iostream>

int main()
{
    const void* ptr = new int(64);

    std::cout << "Val: "
              << *(static_cast<const int*>(ptr))
              << std::endl;

    delete static_cast<const int*>(ptr);

    ptr = "Hello World!..";

    std::cout << "Val: "
              << static_cast<const char*>(ptr)
              << std::endl;
    return 0;
}

```

---

```cpp
#include <iostream>
#include <any>

int main() {
    std::any any_val = 64;
    std::cout << std::any_cast<int>(any_val) << std::endl;
    
    any_val = std::string("Hello World!..");
    std::cout << std::any_cast<std::string>(any_val) << std::endl;
    return 0;
}
```

```cpp
std::any any_val;
if (!any_val.has_value()) {
    std::cout << "empty";
}
```

```cpp
#include <any>
#include <iostream>

int main() {
    std::any any_val = 64;
    std::cout << std::any_cast<int>(any_val) << std::endl;
    
    if (any_val.has_value()) {
        std::cout << "Not Empty\n";
    }

    any_val.reset();

    if (!any_val.has_value()) {
        std::cout << "Empty\n";
    }

    any_val = std::string("Hello World!..");
    std::cout << std::any_cast<std::string>(any_val) << std::endl;
    return 0;
}
```


## Comparison with **`std::variant`**

**std::any** can hold: **`any type`**

But `std::variant`:

```cpp
std::variant<int, std::string> value;
```

Can hold:

```
int
or
std::string
```