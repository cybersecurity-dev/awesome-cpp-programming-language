# [PIMPL](https://cppreference.com/w/cpp/language/pimpl.html) (_Pointer to Implementation_)
**`"Pointer to implementation"`** or `"pImpl"` is a C++ programming technique that removes implementation details of a class from its object representation by placing them in a separate class, accessed through an opaque pointer. The PIMPL idiom is used to:
- hide implementation details from the header,
- reduce compile-time dependencies,
- provide binary compatibility,
- keep your class ABI stable.

```cpp
#ifndef WIDGET_H
#define WIDGET_H

#include <memory>

class Widget {
public:
    Widget();
    ~Widget();               // needs custom destructor declaration

    void doSomething();
    int getValue() const;

private:
    class Impl;              // Forward declaration
    std::unique_ptr<Impl> p; // Pointer to implementation
};

#endif
```

- Widget::Impl is only forward-declared here.
- std::unique_ptr is preferred; no manual memory management.
- The header is clean and doesn’t expose internal details.

```cpp
#include "widget.h"
#include <iostream>

// Definition of the hidden implementation class
class Widget::Impl {
public:
    void doInternalStuff() {
        std::cout << "Doing internal stuff...\n";
    }

    int value = 42;  // Some internal data
};

// Public API
Widget::Widget()
    : p(std::make_unique<Impl>())
{
}

Widget::~Widget() = default;   // Destructor in .cpp due to incomplete type

void Widget::doSomething() {
    p->doInternalStuff();
}

int Widget::getValue() const {
    return p->value;
}
```
Build a Static Library (**libwidget.a**)

```bash
g++ -std=c++17 -c widget.cpp -o widget.o
```
Build a Shared Library (**libwidget.so**)
```bash
g++ -std=c++17 -fPIC -c widget.cpp -o widget.o
```
- Widget's header only contains the public API, so internal fields/methods don’t leak.
- Widget::Impl is defined in the .cpp file, not exposed to users.
- Changing private data or logic does not require recompiling code that includes widget.h.

```cpp
#include "widget.h"
#include <iostream>

int main() {
    Widget w;
    w.doSomething();
    std::cout << "Value = " << w.getValue() << "\n";
}
```

User compiles and links with the `Static Library`
```bash
g++ -std=c++17 main.cpp -L. -lwidget -o app.out
```

User compiles and links using the `Shared Library`
```bash
g++ -std=c++17 main.cpp -L. -lwidget -o app.out
```

Ensure the runtime loader can find libwidget.so
```bash
LD_LIBRARY_PATH=. ./app.out
```
Or install it to a system directory like /usr/local/lib.
