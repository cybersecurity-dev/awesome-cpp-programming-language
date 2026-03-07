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

C++11, C++14, C++17, C++20, C++23, C++26


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
- [Idioms](#idioms)
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

#### lvalue
#### rvalue
#### glvalue
#### prvalue
#### xvalue

## Functions
### [Coroutines](https://cppreference.com/w/cpp/language/coroutines.html)

## Type Casting
### [static_cast](https://cppreference.com/w/cpp/language/static_cast.html)
### [const_cast](https://cppreference.com/w/cpp/language/const_cast.html)
### [dynamic_cast](https://cppreference.com/w/cpp/language/dynamic_cast.html)
### [reinterpret_cast](https://cppreference.com/w/cpp/language/reinterpret_cast.html)

## Multithreading
## [Template Metaprogramming](https://wikipedia.org/wiki/Template_metaprogramming)
* [Variadic Template](https://wikipedia.org/wiki/Variadic_template)
* [Expression Templates](https://wikipedia.org/wiki/Expression_templates)
* [Compile-Time Function Execution](https://wikipedia.org/wiki/Compile-time_function_execution)

## Exception Handling

## Idioms
### [RAII](https://wikipedia.org/wiki/Resource_acquisition_is_initialization) (_Resource acquisition is initialization_)
### [PIMPL](https://cppreference.com/w/cpp/language/pimpl.html) (_Pointer to Implementation_)
### [CRTP](https://wikipedia.org/wiki/Curiously_recurring_template_pattern) (_Curiously recurring template pattern_)
### [Erase-Remove](https://wikipedia.org/wiki/Erase%E2%80%93remove_idiom)
### [Copy on Write](https://wikipedia.org/wiki/Copy-on-write)


## Language Concepts
### auto (_Automatic Type Deduction_)
### ADL (_Argument Dependent Lookup_)
### [Name Mangling](https://wikipedia.org/wiki/Name_mangling)
### [RTTI](https://wikipedia.org/wiki/Run-time_type_information) (_Run-time type information_) 
### [Virtual Methods](https://wikipedia.org/wiki/Virtual_function)
### [Virtual Tables](https://wikipedia.org/wiki/Virtual_method_table)
### [Forward Declaration](https://wikipedia.org/wiki/Forward_declaration)
### [The rule of Three/Five/Zero](https://cppreference.com/w/cpp/language/rule_of_three.html) 
### [SFINAE](https://wikipedia.org/wiki/Substitution_failure_is_not_an_error) (_Substitution failure is not an error_)

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
