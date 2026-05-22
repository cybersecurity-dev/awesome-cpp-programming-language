# Initialization

## 1. Direct Initialization
```cpp
int ival(10);
```
* Value is passed directly in parentheses
* Common in constructors and classes

## 2. Copy Initialization
```cpp
int ival = 10;
```
* Looks like assignment, but happens at creation time
* Compiler may create a temporary object and copy it

## 3. List Initialization (C++11)
```cpp
int ival{10};
```
* Uses curly braces {}
* Prevents narrowing conversions
```cpp
int ival1 = 3.5;   // ✅ OK    (value becomes 3)
int ival2{3.5};    // ❌ ERROR (narrowing not allowed)
```

## 4. Value Initialization
```cpp
int ival{};
```
* Initializes to default value
* For int → 0
```cpp
int ival{};   // a = 0
float fval{}; // b = 0.0
```

## 5. Default Initialization
```cpp
int ival;
```
* No initialization
* Value is garbage (undefined) if it's a local variable

## 6. Reference Initialization
```cpp
int ival = 10;
int &rival = ival;
```
* Reference must be initialized at creation
* Cannot exist without referring to something

## 7. Pointer Initialization
```cpp
int *ptr = nullptr;
```
* Good practice to initialize pointers
* Avoids garbage addresses