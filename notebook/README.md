# C++ reference

## Core Language

### Preprocessor and Basics
- Preprocessor – Comments  
- ASCII chart  

### Basic Concepts
- Keywords  
- Names (lookup)  
- Types (fundamental types)  
- The `main` function  
- Modules (C++20)  
- Contracts (C++26)  

### Expressions
- Value categories  
- Evaluation order  
- Operators (precedence)  
- Conversions – Literals  
- Constant expressions  

### Statements
- `if`, `switch`  
- `for`, range-for (C++11)  
- `while`, `do-while`  

### Declarations and Functions
- Declarations – Initialization  
- Functions – Overloading  
- Coroutines (C++20)  

### Object-Oriented and Templates
- Classes (unions)  
- Templates – Exceptions  
- Freestanding implementations  

## Standard Library (Headers)

## Named Requirements

## Language Support Library

### Utilities
- Program utilities  
- Signals – Non-local jumps  

### Memory and Types
- Basic memory management  
- Variadic functions  
- Source location (C++20)  
- Comparison utilities (C++20)  
- Type support – `type_info`  
- Numeric limits – exception  
- `initializer_list` (C++11)  

### Modern Features
- Coroutine support (C++20)  
- Contract support (C++26)  

## Concepts Library (C++20)

---

# Standard Library Components

## Diagnostics Library
- Assertions – System error (C++11)  
- Exception types – Error numbers  
- `basic_stacktrace` (C++23)  
- Debugging support (C++26)  

## Memory Management Library
- Allocators – Smart pointers  
- Memory resources (C++17)  

## Metaprogramming Library (C++11)
- Type traits – `ratio`  
- `integer_sequence` (C++14)  

## General Utilities Library
- Function objects – `hash` (C++11)  
- Swap – Type operations (C++11)  
- Integer comparison (C++20)  
- `pair`, `tuple` (C++11)  
- `optional` (C++17)  
- `expected` (C++23)  
- `variant` (C++17), `any` (C++17)  
- `bitset` – Bit manipulation (C++20)  

## Containers Library

### Sequence Containers
- `vector`, `deque`, `array` (C++11)  
- `list`, `forward_list` (C++11)  

### Specialized Containers
- `inplace_vector` (C++26)  
- `hive` (C++26)  

### Associative Containers
- `map`, `multimap`, `set`, `multiset`  

### Unordered Containers
- `unordered_map` (C++11)  
- `unordered_multimap` (C++11)  
- `unordered_set` (C++11)  
- `unordered_multiset` (C++11)  

### Views and Adaptors
- Container adaptors  
- `span` (C++20), `mdspan` (C++23)  

## Iterators Library

## Ranges Library (C++20)
- Range factories – Range adaptors  
- Generator (C++23)  

## Algorithms Library
- Numeric algorithms  
- Execution policies (C++17)  
- Constrained algorithms (C++20)  

---

# Specialized Libraries

## Strings Library
- `basic_string` – `char_traits`  
- `basic_string_view` (C++17)  

## Text Processing Library
- Primitive numeric conversions (C++17)  
- Formatting (C++20) – Localization  
- Text encoding (C++26)  
- Regular expressions (C++11)  
  - `basic_regex` – Algorithms  
  - Default regular expression grammar  
- Null-terminated sequence utilities  
  - byte – multibyte – wide  

## Numerics Library
- Common math functions  
- Mathematical special functions (C++17)  
- Mathematical constants (C++20)  
- Basic linear algebra algorithms (C++26)  
- Data-parallel types (SIMD) (C++26)  
- Pseudo-random number generation  
- Floating-point environment (C++11)  
- `complex` – `valarray`  

## Date and Time Library
- Calendar (C++20)  
- Time zone (C++20)  

## Input/Output Library
- Print functions (C++23)  
- Stream-based I/O – I/O manipulators  
- `basic_istream` – `basic_ostream`  
- Synchronized output (C++20)  
- File systems (C++17)  

## Concurrency Support Library (C++11)
- `thread`, `jthread` (C++20)  
- `atomic`, `atomic_flag`  
- `atomic_ref` (C++20) – memory order  
- Mutual exclusion – Condition variables  
- Futures – Semaphores (C++20)  
- Latch (C++20) – Barrier (C++20)  
- Safe reclamation (C++26)  

## Execution Support Library (C++26)

## Feature Test Macros (C++20)
- Language – Standard library – Headers  