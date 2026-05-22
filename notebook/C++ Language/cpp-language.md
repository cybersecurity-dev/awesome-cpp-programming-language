# C++ Language

## Basic Concepts
- Comments  
- ASCII chart  
- Punctuation  
- Names and identifiers  
- Types – Fundamental types  
- Object – Scope – Lifetime  
- Definitions and ODR  
- Name lookup  
  - qualified  
  - unqualified (ADL)  
- As-if rule  
- Undefined behavior (UB)  
- Memory – Multithread (C++11)  
- Character sets and encodings  
- Phases of translation  
- The `main` function  
- Modules (C++20)  
- Contracts (C++26)  
- Splice specifiers (C++26)  

## Keywords

## Preprocessor
- `#if`, `#ifdef`, `#ifndef`  
- `#elif`  
- `#elifdef`, `#elifndef` (C++23)  
- `#else`, `#endif`  
- `#define`, `#undef`  
- `#line`  
- `#error`  
- `#include`  
- `#pragma`  
- `#warning` (C++23)  

## Expressions

### General
- Value categories  
- Evaluation order  
- Constant expressions  

### Operators
- Assignment  
- Arithmetic  
- Increment and decrement  
- Logical comparison  
- Member access  
- Call, comma, ternary  
- `sizeof`, `alignof` (C++11)  
- `new`, `delete`  
- `typeid`  
- Reflection (C++26)  
- Alternative representations  

### Comparisons
- Default comparisons (C++20)  
- Operator precedence  

### Conversions
- Implicit  
- Explicit  
- User-defined  
- Usual arithmetic conversions  
- `static_cast`  
- `dynamic_cast`  
- `const_cast`  
- `reinterpret_cast`  

### Literals
- Escape sequences  
- Boolean  
- Integer  
- Floating  
- Character  
- String  
- `nullptr` (C++11)  
- User-defined literals (C++11)  

## Declarations

### General
- Conflicting declarations  
- Storage duration and linkage  
- Translation-unit-local (C++20)  
- Language linkage  

### Namespaces
- Namespace declaration  
- Namespace alias  

### Types
- References  
- Pointers  
- Arrays  
- Structured bindings (C++17)  
- Enumerations  
  - enum  
  - enumerators  

### Specifiers
- `inline`  
- `constexpr` (C++11)  
- `consteval` (C++20)  
- `constinit` (C++20)  
- `decltype` (C++11)  
- `auto` (C++11)  
- `typedef`, type alias (C++11)  

### Advanced
- Elaborated type specifiers  
- Attributes (C++11)  
- Alignas (C++11)  
- `static_assert` (C++11)  

## Initialization
- Default-initialization  
- Value-initialization  
- Copy-initialization  
- Direct-initialization  
- Aggregate initialization  
- List-initialization (C++11)  
- Reference initialization  
- Static non-local initialization  
  - zero  
  - constant  
  - dynamic  
  - ordered / unordered  
- Copy elision (RVO)  

## Functions
- Function declaration  
- Default arguments  
- Variadic arguments  
- Lambda expressions (C++11)  
- Overload resolution  
- Operator overloading  
- Address of an overload set  
- Coroutines (C++20)  
- Replacement functions  

## Statements
- `if`, `switch`  
- `while`, `do-while`  
- `for`, range-for (C++11)  
- `break`, `continue`  
- `goto`, `return`  
- `contract_assert` (C++26)  
- `synchronized`, `atomic` (TM TS)  

## Classes

### General
- Class types  
- Union types  
- injected-class-name  

### Members
- Data members  
- Bit-fields  
- Member functions  
- The `this` pointer  
- Static members  
- Nested classes  
- Derived class  
- Using-declaration  

### Optimization and Inheritance
- Empty base optimization (EBO)  
- Virtual functions  
- Abstract classes (ABC)  

### Specifiers
- `override` (C++11)  
- `final` (C++11)  
- `explicit` (C++11)  

### Access Control
- Member access  
- `friend` specifier  

### Constructors / Destructors
- Constructors and member initializer lists  
- Default constructor  
- Copy constructor  
- Move constructor (C++11)  
- Destructor  

### Assignment
- Copy assignment  
- Move assignment (C++11)  

### Conversion
- Converting constructor  

## Templates

### Basics
- Template parameters and arguments  
- Class template  
- Function template  
- Variable template (C++14)  
- Class member template  

### Advanced
- Deduction guides  
- Class template argument deduction (CTAD) (C++17)  
- Explicit specialization  
- Partial specialization  
- Parameter packs (C++11)  
- `sizeof...` (C++11)  
- Fold expressions (C++17)  
- Pack indexing (C++26)  
- Dependent names (SFINAE)  
- Constraints and concepts (C++20)  
- Requires expressions (C++20)  

## Exceptions
- try block  
- Throwing exceptions  
- Handling exceptions  

### Specifications
- `noexcept` specifier (C++11)  
- Dynamic exception specification (until C++17)  
- `noexcept` operator (C++11)  

## Miscellaneous
- History of C++  
- Extending the namespace `std`  
- Acronyms:  
  - AFO, CPO  
  - IFNDR, NDR  
  - NTBS, NTP  
  - RAO, SOCCC  
  - TMP, TU  

## Idioms
- Curiously Recurring Template Pattern (CRTP)  
- Pointer to implementation (PIMPL)  
- Resource Acquisition Is Initialization (RAII)  
- Rule of three/five/zero  
- Zero-overhead principle  
