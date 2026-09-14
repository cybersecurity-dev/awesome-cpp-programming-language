# `inline` Variables

> inline variable is a feature introduced in C++17 that solves a common problem with global and static variables defined in header files.

> Inline variable not about performance. Just like modern inline functions are mainly about the `One Definition Rule` (**ODR**), 

> inline variables are about allowing multiple identical definitions across translation units.

## The Problem Before C++17

```cpp
// config.h
const int MaxSize = 100;
```

```cpp
// config.h

int counter = 0;   // BAD
```

Including this header in multiple translation units causes: `multiple definition of 'counter'`

But with `inline int counter = 0` , The linker merges all definitions into one. So there will be exactly one shared variable in the program.

The most important distinction is:
- **`const`** = run-time constant
- **`constexpr`** = compile-time constant
- **`static`** = one shared object (for `class members`) or internal linkage (`namespace scope`)
- **`inline`** = can be defined in a header and included by many translation units without linker errors.
