# std::println
> `std::println` is part of the new C++23 <print> library, which brings Python/Rust-style formatted output directly into the standard library.

> Think of it as: ` std::print(...) + '\n' `


```cpp
#include <print>

int main()
{
    std::println("Hello World!..");
    return 0
}
```

Instead of:
```cpp
std::cout << "Name: "  << name
          << ", Age: " << age << std::endl;
```
you can write:
```cpp
std::println("Name: {}, Age: {}", name, age);
```
std::println uses the same formatting syntax as std::format.

Main question: If I can already do **std::format("x={}", x)**, why do we need `std::println()`?

```cpp
auto s = std::format("param = {}", 64);
```
s = "param = 64"

Nothing is printed. so we need to add:

```cpp
std::cout << s << std::endl;
```
so `std::println` formats and prints directly

```cpp
std::println("param = {}", 64);
```

and std::format returns a temporary string so println brings `Performance Benefit`

- std::format  `->` sprintf() style string creation (_produce a string_)
- std::print   `->` print without newline (_format + output_)
- std::println `->` print with newline (_format + output + newline_)