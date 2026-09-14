# std::stacktrace

> std::stacktrace is another major feature added in C++23 (header <stacktrace>).

> It allows a program to capture and inspect the current call stack at runtime without relying on platform-specific APIs.

> Before C++23, obtaining a stack trace was typically:
 - platform-dependent (backtrace() on Linux, CaptureStackBackTrace() on Windows)
 - required external libraries (Boost.Stacktrace, libunwind)
 - difficult to make portable

```cpp
#include <iostream>
#include <stacktrace>

void report() {
    std::cout << std::stacktrace::current() << "\n";
}
void foo() {
    std::cout << "foo()" << std::endl;
    report();
}
void bar() {
    std::cout << "bar()" << std::endl;
    foo();
}

int main() {
    bar();
    return 0;
}
```

```
main()
 └── bar()
      └── foo()
            └── report()
                   └── capture trace
```

Useful Information Per Frame:

- frame.description();
- frame.source_file();
- frame.source_line();


```cpp
#include <iostream>
#include <stacktrace>

void report() {
    auto trace = std::stacktrace::current(); 
    for (const auto& frame : trace)
        {
            std::cout << frame.description() << std::endl;
            // std::cout << frame.source_file() << std::endl;
            // std::cout << frame.source_line() << std::endl;
        }
}
void foo() {
    std::cout << "foo()" << std::endl;
    report();
}
void bar() {
    std::cout << "bar()" << std::endl;
    foo();
}

int main() {
    bar();
    return 0;
}
```

Better Diagnostics

- Without stacktrace:
    ```cpp
    throw std::runtime_error("Failed: File read error!");
    ```
- With stacktrace:
    ```cpp
    auto trace = std::stacktrace::current();
    std::cerr << "Failed: File read error!";
    std::cerr << trace;
    ```

Works Well with `std::expected`:

```cpp
#include <iostream>
#include <stacktrace>
#include <expected>

struct ErrorWithStrace {
    std::string emsg;
    std::stacktrace trace;
};

std::expected<int, ErrorWithStrace> foo() {
    return std::unexpected(ErrorWithStrace{"error:foo()", std::stacktrace::current()});
}

auto bar() {
    return foo();
}

int main() {
    auto rval = bar();
    if (rval.has_value()) {
        std::cout << rval.value() << std::endl;
    }
    else {
        std::cout << rval.error().emsg << std::endl;
        std::cout << rval.error().trace << std::endl;
    }

    return 0;
}
```
