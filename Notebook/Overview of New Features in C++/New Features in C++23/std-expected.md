# std::expected

std::expected is a new vocabulary type introduced in C++23 (header <expected>) that represents:

> Either a successful result (T) or an error (E)

It's similar to Rust's `Result<T, E>`, Haskell's Either, or std::optional<T> with the important addition that it can carry **`error information`**.

`Access`:

```cpp
#include <expected>
#include <string>
#include <iostream>

std::expected<int, std::string> parse_number(const std::string& s) {
    if (s.empty()) 
        return std::unexpected("empty string");
    return std::stoi(s);
}

int main() {
    auto r = parse_number("64");
    if (r.has_value()) {
        std::cout << r.value() << std::endl;
    }
    else { 
        std::cout << r.error() << std::endl;
    }
    return 0;
}
```

---
`Shorter:`

```cpp
#include <string>
#include <expected>
#include <iostream>

std::expected<int, std::string> parse_number(std::string_view s) {
    if (s.empty()) 
        return std::unexpected("empty string");
    return std::stoi(std::string(s));
}

int main() {
    auto result = parse_number("64");
    if (result) {
        std::cout << *result << std::endl;
    }
    else { 
        std::cout << result.error() << std::endl;
    }
    return 0;
}
```