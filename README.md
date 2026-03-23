<div align="center">
    <p align="center">
        <a href="https://cppreference.com/">
          <img width="10%" src="https://github.com/cybersecurity-dev/cybersecurity-dev/blob/main/assets/Cpp_logo.svg" />
        </a>
    </p>

# **`Awesome`** [C++](https://wikipedia.org/wiki/C%2B%2B) Programming [Language](https://wikipedia.org/wiki/Category:C%2B%2B_libraries) [![Awesome](https://awesome.re/badge.svg)](https://awesome.re) 
[**`C++11`**](https://wikipedia.org/wiki/C%2B%2B11) | [**`C++14`**](https://en.wikipedia.org/wiki/C%2B%2B14) | [**`C++17`**](https://en.wikipedia.org/wiki/C%2B%2B17) | [**`C++20`**](https://en.wikipedia.org/wiki/C%2B%2B20) | [**`C++23`**](https://en.wikipedia.org/wiki/C%2B%2B23) | [**`C++26`**](https://en.wikipedia.org/wiki/C%2B%2B26)
</div>

[![YouTube](https://img.shields.io/badge/YouTube-%23FF0000.svg?style=for-the-badge&logo=YouTube&logoColor=white)](https://youtube.com/playlist?list=PL9V4Zu3RroiUR_6ABLxUUaY-Gcz9tzRm_&si=ASTMXOYiVZ_qV4Ck)
[![Reddit](https://img.shields.io/badge/Reddit-FF4500?style=for-the-badge&logo=reddit&logoColor=white)](https://www.reddit.com/r/cpp/)

<p align="center">
    <a href="https://github.com/cybersecurity-dev/"><img height="25" src="https://github.com/cybersecurity-dev/cybersecurity-dev/blob/main/assets/github.svg" alt="GitHub"></a>
    &nbsp;
    <a href="https://www.youtube.com/@CyberThreatDefence"><img height="25" src="https://github.com/cybersecurity-dev/cybersecurity-dev/blob/main/assets/youtube.svg" alt="YouTube"></a>
    &nbsp;
    <a href="https://cyberthreatdefence.com/my_awesome_lists"><img height="20" src="https://github.com/cybersecurity-dev/cybersecurity-dev/blob/main/assets/blog.svg" alt="My Awesome Lists"></a>
    <img src="https://github.com/cybersecurity-dev/cybersecurity-dev/blob/main/assets/bar.gif">
</p>


## 📖 Contents
- [Containers](#containers)
    - [Vector](#vector)
    - [List](#list)
    - [Deque](#deque)
- [Pointers and References](#pointers-and-references)
    - [std::unique_ptr](#unique_ptr)
- [Expressions](#expressions)
    - [Lambda Expressions](#lambda-expressions)
    - [Value Categories](#value-categories)
- [Functions](#functions)
- [Type Casting](#type-casting)
    - [static_cast](#static_cast)
    - [dynamic_cast](#dynamic_cast)
    - [const_cast](#const_cast)
    - [reinterpret_cast](#reinterpret_cast) 
- [Idioms](#idioms)
    - [RAII](#raii-resource-acquisition-is-initialization)
    - [PIMPL](#pimpl-pointer-to-implementation)
    - [CRTP](#crtp-curiously-recurring-template-pattern)
    - [Erase-Remove](#erase-remove)
    - [Copy on Write](#copy-on-write)
- [Specifiers](#specifiers)
    - [Friend](#friend)
    - [Constexpr (C++11)](#constexpr-c11)
 - [Language Concepts](#language-concepts)   
    - [Virtual Methods](#virtual-methods)
    - [Forward Declaration](#forward-declaration)
    - [Special Member Functions](#special-member-functions)
    - [Rule of N](#rule-of-n)    
        - [The Rule of Three](#the-rule-of-three)
        - [The Rule of Five](#the-rule-of-five)
        - [The Rule of Zero](#the-rule-of-zero)
    - [SFINE](#sfinae-substitution-failure-is-not-an-error)
- [Language Concepts](#language-concepts)
- [Framework and Libraries](#framework-and-libraries)
- [Performance Analysis and Debugging Tool](#performance-analysis-and-debugging-tool)
- [Package Managers](#package-managers)
- [Severals](#severals)
- [Standarts](#standarts)
- [My Other Awesome Lists](#my-other-awesome-lists)
- [Contributing](#contributing)
- [Contributors](#contributors)


## Containers

### [Vector](https://cppreference.com/w/cpp/container/vector.html)

```cpp
#include <vector>
template<class T, class Allocator = std::allocator<T>> class vector;
```
Except for the `std::vector<bool>` partial specialization, the elements are stored contiguously, which means that elements can be accessed not only through iterators, but also using offsets to regular pointers to elements. 

```cpp
std::vector<int> ivec = { 1, 2, 3, 4, 5 };
//lambda expression
auto print = [](const int& n) { std::cout << n << ' '; };
    
std::for_each(ivec.cbegin(), ivec.cend(), print);
std::cout << std::endl;
std::for_each(ivec.crbegin(), ivec.crend(), print);
```

### [List](https://cppreference.com/w/cpp/container/list.html)
```cpp
#include <list>
template<class T, class Allocator = std::allocator<T>> class list;
```

`std::list` is a container that supports constant time insertion and removal of elements from anywhere in the container. Fast random access is **not supported**. It is usually implemented as a **`doubly-linked list`**. Compared to `std::forward_list` this container provides bidirectional iteration capability while being less space efficient.

```cpp
std::list<int> ilist = { 5, 7, 11, 13 };
for (int n : ilist)
std::cout << n << ", ";
std::cout<<"\n-----------------\n";
    
ilist.push_front(0);
ilist.push_back(-1);
std::for_each(ilist.cbegin(), ilist.cend(), [](auto val) { std::cout << val << ", "; });
std::cout << "\n-----------------\n";
    
//insert with using initializer list
ilist.insert(ilist.cend(), { 4, 3, 2, 1 });
for (auto it = ilist.cbegin(); it != ilist.cend(); ++it) {
    std::cout << *it << ", ";
}
```

### [Deque](https://cppreference.com/w/cpp/container/deque.html)


### [Array](https://cppreference.com/w/cpp/container/array.html)
```cpp
#include <array>
template<class T, std::size_t N> struct array;
```
`std::array` is a container that encapsulates fixed size arrays. 

### [Forward List](https://cppreference.com/w/cpp/container/forward_list.html)

### [Inplace Vector](https://cppreference.com/w/cpp/container/inplace_vector.html)


## Pointers and References

### [Smart Pointers](https://wikipedia.org/wiki/Smart_pointer)
Smart pointers enable automatic, exception-safe, object lifetime management.

#### [unique_ptr](https://cppreference.com/w/cpp/memory/unique_ptr.html)
`std::unique_ptr` is a smart pointer that owns (**is responsible for**) and manages another object via a pointer and subsequently disposes of that object when the unique_ptr goes out of scope.

```cpp
{
    unique_ptr<ClassName> uptr(new ClassName);
    uptr -> method_name();
    //....using
} //destructing uptr destroys the ClassName object.
```

#### [shared_ptr](https://cppreference.com/w/cpp/memory/shared_ptr.html)

#### [weak_ptr](https://cppreference.com/w/cpp/memory/weak_ptr.html)

## [Expressions](https://cppreference.com/w/cpp/language/expressions.html)

### [Lambda Expressions](https://cppreference.com/w/cpp/language/lambda.html)

[**`Lambda expression`**](https://wikipedia.org/wiki/Anonymous_function) in computer programming, also called an anonymous function, is a defined function not bound to an identifier.

```cpp
auto make_function(int& iparam)
{
    return [&] { std::cout << iparam << std::endl; };
}

int main()
{
    int ival = 2;
    auto f = make_function(ival); // the use of iparam in f binds directly to ival
    f();
    
    ival = 3;
    f();
    return 0;
}
```

### [Value Categories](https://cppreference.com/w/cpp/language/value_category.html)

- a `glvalue` ("generalized" lvalue) is an expression whose evaluation determines the identity of an object or function.
- a `prvalue` ("pure" rvalue) is an expression whose evaluation.
- an `xvalue` (an "eXpiring" value) is a glvalue that denotes an object whose resources can be reused.
- an `lvalue` is a glvalue that is not an xvalue.

#### [lvalue](https://wikipedia.org/wiki/Value_(computer_science)#lrvalue)

Some programming languages use the idea of l-values and r-values, deriving from the typical mode of evaluation on the left and right-hand side of an assignment statement. An l-value refers to an object that persists beyond a single expression. An r-value is a temporary value that does not persist beyond the expression that uses it.

```cpp
void foo();
int main() {
    int ivala; // Expression 'ivala' is lvalue
    int &ivalb{ivala}; // Expression 'ivalb' is lvalue

    // Expression 'foo' is lvalue
    // address may be taken by built-in address-of operator
    void (*ptrfoo)() = &foo;
```

#### rvalue

#### glvalue
a glvalue (`"generalized"` lvalue) is an expression whose evaluation determines the identity of an object or function.


#### prvalue
#### xvalue

## Functions

### [Coroutines](https://cppreference.com/w/cpp/language/coroutines.html)
A coroutine is a function that can suspend execution to be resumed later. Coroutines are **stackless**: they suspend execution by returning to the caller, and the data that is required to resume execution is stored separately from the stack. This allows for sequential code that executes asynchronously (`e.g. to handle non-blocking I/O without explicit callbacks`), and also supports algorithms on lazy-computed infinite sequences and other uses.

## Type Casting
### [static_cast](https://cppreference.com/w/cpp/language/static_cast.html)
Converts between types using a combination of implicit and user-defined conversions.

### [dynamic_cast](https://cppreference.com/w/cpp/language/dynamic_cast.html)
Safely converts pointers and references to classes up, down, and sideways along the inheritance hierarchy.

### [const_cast](https://cppreference.com/w/cpp/language/const_cast.html)
Converts between types with different cv-qualification.

### [reinterpret_cast](https://cppreference.com/w/cpp/language/reinterpret_cast.html)

## Multithreading
## [Template Metaprogramming](https://wikipedia.org/wiki/Template_metaprogramming)
* [Variadic Template](https://wikipedia.org/wiki/Variadic_template)
* [Expression Templates](https://wikipedia.org/wiki/Expression_templates)
* [Compile-Time Function Execution](https://wikipedia.org/wiki/Compile-time_function_execution)

## Exception Handling

## [Idioms](https://wikipedia.org/wiki/Programming_idiom)

### [RAII](https://wikipedia.org/wiki/Resource_acquisition_is_initialization) (_Resource acquisition is initialization_)
Resource Acquisition Is Initialization or RAII, is a C++ programming technique which binds the life cycle of a resource that must be acquired before use (_allocated heap memory, thread of execution, open socket, open file, locked mutex, disk space, database connection—anything that exists in limited supply_) to the lifetime of an object. RAII guarantees that the resource is available to any function that may access the object. It also guarantees that all resources are released when the lifetime of their controlling object ends, in reverse order of acquisition.

### [PIMPL](https://cppreference.com/w/cpp/language/pimpl.html) (_Pointer to Implementation_)
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

### [CRTP](https://wikipedia.org/wiki/Curiously_recurring_template_pattern) (_Curiously recurring template pattern_)

### [Erase-Remove](https://wikipedia.org/wiki/Erase%E2%80%93remove_idiom)

### [Copy on Write](https://wikipedia.org/wiki/Copy-on-write)


## Specifiers

### Typedef

### Inline

### Virtual Function Specifier

### Explicit Function Specifier

### [Friend](https://cppreference.com/w/cpp/language/friend.html)

The `friend` declaration appears in a class body and grants a function or another class access to private and protected members of the class where the friend declaration appears.

* Friend Function Example
    ```cpp
    class Point2D {
    private:
        int x, y;
    
    public:
        Point2D(int x, int y) : x(x), y(y) {}
    
        // Friend function can access private members
        friend void printPoint(const Point2D &p);
    };
    
    void printPoint(const Point2D &p) {
        std::cout << "Point(" << p.x << ", " << p.y << ")\n";
    }
    
    int main() {
        Point2D p(3, 4);
        printPoint(p);   // friend function can access
    }
    ```

* Friend Class Example

    ```cpp
    class Engine {
    private:
        int hp = 100;
        // Car can access private members of Engine
        friend class Car;
    public:
        Engine() = default;
    };
    
    class Car {
    public:
        void showEnginePower(const Engine& e) {
            std::cout << "Engine horsepower: " << e.hp << "\n";
        }
    };
    
    int main() {
        Engine eW;
        Car cW;
        cW.showEnginePower(eW);
        return 0;
    }
    ```

### Constexpr (C++11)

The **`constexpr`** specifier declares that it is possible to evaluate the value of the entities at `compile time`. 
```cpp
constexpr int factorial(int n) {
    return n <= 1 ? 1 : (n * factorial(n - 1));
}
```
![constexpr](/.assets/constexpr.png)

```cpp
constexpr int fac5 = factorial(5);
static constexpr int const& fac10 = 3628800;
static_assert(fac10 == factorial(10), "factorial failed\n");
```

### Consteval (C++20)

### Constinit (C++20)

## Language Concepts

### [auto](https://cppreference.com/w/cpp/language/auto.html) (_Automatic Type Deduction_)

**`auto`** tells the compiler: "`Deduce the variable's type automatically from the initializer.`"

* Iterators (most common)
```cpp
std::vector<int> v = {2,3,5};
auto it = v.begin();  // replaces vector<int>::iterator
```
* Lambda functions
```cpp
auto printType = [](auto t) { std::cout << typeid(t).name() << std::endl; };
```

* Range-based loops 
```cpp
std::vector<int> ivec = {2,3,5};
for (auto v : ivec) {
    std::cout << v << std::endl;
}
```

* Working with templates
```cpp
template <typename T>
void printType(T param) {
    std::cout << typeid(param).name() << std::endl;
}
```
### ADL (_Argument Dependent Lookup_)

### [Name Mangling](https://wikipedia.org/wiki/Name_mangling)

### [RTTI](https://wikipedia.org/wiki/Run-time_type_information) (_Run-time type information_) 

### [Virtual Methods](https://wikipedia.org/wiki/Virtual_function)
Virtual functions enable `runtime polymorphism` (dynamic dispatch). When you call a virtual function through a base class pointer or reference, C++ decides at runtime which overridden function to execute based on the actual (dynamic) type of the object.

```cpp
struct Basev1 {
    void speak() { cout << "Base v1 speaks\n"; }  // NOT virtual
};

struct Derivedv1 : Basev1 {
    void speak() { cout << "Derived v1 speaks\n"; } // hides Base::speak
};

struct Basev2 {
    virtual void speak() { cout << "Base v2 speaks\n"; }  // virtual
};

struct Derivedv2 : Basev2 {
    void speak() override { cout << "Derived v2 speaks\n"; } // override
};

int main() {
    Derivedv1 dv1;
    Basev1* ptrv1 = &dv1;    // base pointer to a derived object
    ptrv1->speak();      // calls Base::speak (static dispatch)
    
    /*-------------------------------*/
    Derivedv2 dv2;
    Basev2* ptrv2 = &dv2;
    ptrv2->speak();      // calls Derived::speak (dynamic dispatch)

    return 0;
}
```
### [Virtual Tables](https://wikipedia.org/wiki/Virtual_method_table)

### [Forward Declaration](https://wikipedia.org/wiki/Forward_declaration)
* Basic Forward Declaration of `a Class`
   
    ```cpp
    #include <iostream>
    
    // Forward declaration
    class Engine;
    
    class Car {
    public:
        void run(Engine* en); // OK: pointer doesn't require full definition
    };
    
    // Full definition of Engine
    class Engine {
    public:
        void print_spec() { std::cout << "Engine Spec:..\n"; }
    };
    
    void Car::run(Engine* e) {
        e->print_spec(); // OK now, since Engine is fully defined
    }
    
    int main() {
        Car c1;
        Engine e1;
        c1.run(&e1);
        return 0;
    }
    ```
* Forward Declaration of `Functions`
    ```cpp    
    void foo(); // forward declaration
    
    void bar() {
        foo();  // valid because foo is declared
    }
    
    void foo() {
        bar();
    }
    int main() {
        foo();
        bar();
        return 0;
    }
    ```
### [Special Member Functions](https://wikipedia.org/wiki/Special_member_functions)
* (Default) Constructor:
* Copy Constructor:
* Move Constructor:
* Copy Assignment Operator:
* Move assignment Operator:
* Destructor:

Signatures of the special member functions:

| Function                 | Syntax for class `MyClass`                              |
|--------------------------|----------------------------------------------------------|
| (Default) constructor    | `MyClass();`                                             |
| Copy constructor         | `MyClass(const MyClass& other);`                         |
| Move constructor         | `MyClass(MyClass&& other) noexcept;`                     |
| Copy assignment operator | `MyClass& operator=(const MyClass& other);`              |
| Move assignment operator | `MyClass& operator=(MyClass&& other) noexcept;`          |
| Destructor               | `virtual ~MyClass();`                                    |


### [Rule of N](https://cppreference.com/w/cpp/language/rule_of_three.html)

#### [The Rule of Three](https://wikipedia.org/wiki/Rule_of_three_(C%2B%2B_programming))
The `Rule of Three in C++ says`: If a class manages a resource (_e.g., raw new-allocated memory, file handle, socket_), and you need to define any one of these:
* Destructor
* Copy constructor
* Copy assignment operator

#### The Rule of Five
The Rule of Five (C++11 and later) extends the Rule of Three.
If your class manages a resource (_e.g., heap memory, file descriptors, sockets, mutexes_), and you define any of the special member functions, you typically need to implement all five:
* Destructor
* Copy constructor
* Copy assignment operator
* Move constructor
* Move assignment operator

#### The Rule of Zero
If your class doesn’t manage resources directly (no raw new/delete, no manual file handles, etc.), you don’t need to write any of the special member functions (_destructor, copy/move ctor, copy/move assignment_).

### [SFINAE](https://wikipedia.org/wiki/Substitution_failure_is_not_an_error) (_Substitution failure is not an error_)

```cpp
// Primary template: enabled only if T::size() is valid
template <typename T>
auto print_size(const T& x, int)
-> decltype(x.size(), void())   //SFINAE - based return type checks. Try to evaluate x.size()
                                //If x.size() is valid -> the whole expression becomes void
                                //If x.size() is NOT valid -> substitution fails -> SFINAE kicks in
{
    std::cout << "x.size() = " << x.size() << "\n";
}

// Fallback overload: used if above substitution fails
template <typename T>
void print_size(const T&, ...)   // ellipsis = lowest priority match
{
    std::cout << "No size() available.\n";
}
int main() {
    std::vector<int> ivec{ 2, 3, 5, 7, 11 };
    std::string str = "Hello World!.";
    int ival = 42;

    print_size(ivec, 0);   // has size() -> prints size
    print_size(str, 0);    // has size() -> prints size
    print_size(ival, 0);   // no size() -> fallback
    return 0;
}
```

## Framework and Libraries

### Testing and Mocking Framework
- [Catch2](https://github.com/catchorg/Catch2) - A modern, C++ native, test framework for unit-tests, TDD and BDD - using C++14, C++17 and later.
- [Google Test](https://github.com/google/googletest) - [Google](https://google.github.io/googletest/) Testing and Mocking Framework

### Network
- [POCO](https://github.com/pocoproject/poco) - The [POCO C++](https://pocoproject.org/) Libraries are powerful cross-platform open-source C++ libraries for building network- and internet-based applications that run on desktop, server, mobile, IoT, and embedded systems.

### RPC (_Remote Procedure Call_)
- [gRPC](https://github.com/grpc/grpc) - A high performance, open source universal [RPC framework](https://grpc.io/docs/languages/cpp/quickstart/).

## Performance Analysis and Debugging Tool
- [Orbit](https://github.com/google/orbit) - Orbit is a standalone profiler and debugging tool for Windows and Linux. Its main purpose is to help developers understand and visualize the execution flow of a complex application.
- [Tracy Profiler](https://github.com/wolfpld/tracy) - A real time, nanosecond resolution, remote telemetry, hybrid frame and sampling [profiler](https://tracy.nereid.pl/) for games and other applications.

## Package Managers
- [vcpkg](https://github.com/microsoft/vcpkg) - [vcpkg](https://vcpkg.io/) is a free C/C++ package manager for acquiring and managing libraries.
- [Conan](https://github.com/conan-io/conan) - The open-source C and C++ package [manager](https://conan.io/).

## Severals
- [Doxygen](https://doxygen.nl/) -  Doxygen is a widely-used documentation generator tool in software development.
- [{fmt}](https://github.com/fmtlib/fmt) - A modern formatting [library](https://fmt.dev/).
- [JSON for Modern C++](https://github.com/nlohmann/json) - [JSON](https://json.nlohmann.me/) for Modern C++.
- [pybind11](https://github.com/pybind/pybind11) - Seamless [operability](https://pybind11.readthedocs.io/en/stable/) between C++11 and Python.
- [spdlog](https://github.com/gabime/spdlog) - Fast C++ logging library.


## Standarts

### [C++17](https://wikipedia.org/wiki/C%2B%2B17) [![YouTube](https://img.shields.io/badge/YouTube-%23FF0000.svg?logo=YouTube&logoColor=white)](https://youtube.com/playlist?list=PL9V4Zu3RroiUQgR_mRQUqaaqMr0dqOMx9&si=eeZgwJukCid0gg_I)

#### [std::variant](https://cppreference.com/w/cpp/utility/variant.html)
#### [std::basic_string_view](https://cppreference.com/w/cpp/string/basic_string_view.html)
#### [std::any](https://cppreference.com/w/cpp/utility/any.html)

### [C++20](https://wikipedia.org/wiki/C%2B%2B20) [![YouTube](https://img.shields.io/badge/YouTube-%23FF0000.svg?logo=YouTube&logoColor=white)](https://youtube.com/playlist?list=PL9V4Zu3RroiVw5A7UAF80nrGjqa4YHH5V&si=Qs-HYOl3nWr1aW_S)

#### [Modules](https://cppreference.com/w/cpp/language/modules.html)
#### [std::atomic_ref](https://cppreference.com/w/cpp/atomic/atomic_ref.html)
#### [std::barrier](https://cppreference.com/w/cpp/thread/barrier.html)
#### [std::jthread](https://cppreference.com/w/cpp/thread/jthread.html)
#### [std::latch](https://cppreference.com/w/cpp/thread/latch.html)

### [C++23](https://wikipedia.org/wiki/C%2B%2B23) [![YouTube](https://img.shields.io/badge/YouTube-%23FF0000.svg?logo=YouTube&logoColor=white)](https://youtube.com/playlist?list=PL9V4Zu3RroiUDgZNWp3jEfVCekz3zyqlR&si=9ydOxTrqNAMecWHX)

#### [std::generator](https://cppreference.com/w/cpp/coroutine/generator.html)
#### [std::mdspan](https://cppreference.com/w/cpp/container/mdspan.html)

### [C++26](https://wikipedia.org/wiki/C%2B%2B26) [![YouTube](https://img.shields.io/badge/YouTube-%23FF0000.svg?logo=YouTube&logoColor=white)](https://youtube.com/playlist?list=PL9V4Zu3RroiUMnYOdxU8Qyl58Y8d65csM&si=UT8y6spBSphgR1le)

#### [Contracts](https://cppreference.com/w/cpp/language/contracts.html)

## Compiler/Debugger
- [MSVC & GCC & Clang](https://github.com/cybersecurity-dev/PowerShell-Toolkit/#install-c-cpp) - installation step of MSVC/GCC/Clang compiler in **Windows**
- [GCC & Clang](https://github.com/cybersecurity-dev/Bash-Toolkit/#install-c-cpp) - installation step of GCC/Clang compiler in **Linux**
- [OnlineGDB](https://www.onlinegdb.com/) - **Online** compiler and debugger for C/C++

##

### My Other Awesome Lists
You can access the my other awesome lists [here](https://cyberthreatdefence.com/my_awesome_lists)

### Contributing
[Contributions of any kind welcome, just follow the guidelines](contributing.md)!

### Contributors
[Thanks goes to these contributors](https://github.com/cybersecurity-dev/awesome-cpp-programming-language/graphs/contributors)!

[🔼 Back to top](#awesome-c-programming-language-)
