# Coding standard

The most important coding rules goal is the **consistency of the code** *(i.e no matter who writes the code)*.  
In order to reach this goal, the rules must be written in a way that **reduces the count of available applications**.  
<b>However, they are not absolute, <u>exceptions can be done if justified.</u></b>

<details open><summary><font size="5" id="coding-rules">Coding rules</font></summary>

Rules that describe the way to implement.
- General
  - Friendship: **no friendship.**
  - Shared pointers: **only for child classes of interfaces.**
  - Dynamic allocation: **no dynamic allocation** (i.e no use of `new`).
  - Exceptions: **no exception.**
  - Cast: **use `static_cast`** if possible, else `reinterpret_cast`. **No use of `dynamic_cast` or `C style cast`.**
  - Comments for:
    - implicit required condition of well running
    - libraries
    - class, function or variable with name that cannot be enough explicit
  - Macros: **no macro.**
  - Aliases: **use `using` keyword instead of `typedef` keyword and only for function type.**
  - Lambda: **use `std::funtcion` as type but declare with a `lambda function`**
  - Inheritance: **avoid inheritance** except for interfaces. Favor composition over inheritance.
  - Dead code: **no dead code** (no what-if code).
  - File: **only 1 class per file.**
- Headers
  - Header inclusion: **no forward declaration**
  - Header guard: `#pragma once`
    - Declaration order
      - Accessibility order:
          1. public
          2. protected
          3. private
      - Categories order:
          1. Sub-classes
          2. Static methods
          3. Static members
          4. Non-static methods
          5. Non-static members
- Sources
  - Definition order: **same order as declared.**
    - Include order
        In alphabetical order for each category:
        1. Corresponding header
        2. Standard library
        3. External depedencies hearders
        4. Project hearders
- Variables
  - Declaration
    - Instruction: **only 1 declaration per line**. This rule also applied for class member.
    - Initialization: **initialize variable on declaration if possible.** This rule also applied for class member.
  - Scope: **declare variable only inside a method or a class.**
  - Pointer/Reference: **use references instead of pointers when value is not optionnal**, unless object contained in a data structure.
  - Constness: **maximize the constness of variables.**
  - Primitive type: **use strong primitive type** *(ex: `uint32_t`, `double_t`).*
  - Type: **use most accurate type** *(ex: `istringstream` instead of `stringstream`).*
  - `auto` keyword: **use only for lambda, loop-variable and type longer than 15 characters.**
- Functions
  - Inline functions: **only trivial setters and getters.**
  - Side effect: **avoid side effect functions**  
      Exception valid for: data structures, in-out parameters, multiple outputs.
  - `Return` instruction: **Immediately exit a function when a required condition is not fulfilled.**
    - Parameters
      - Default value: **no default value.**
      - Passing: **pass primitive types by value, pass any other types by reference.**
- Structs
  - Usage: use structs for **mainly public attributes and methods**.  
    Other rules in `Classes`.
- Classes
  - Constructor: **no implicit conversion**, use keyword `explicit`.
  - Virtual: **declare destructor as virtual for classes that contain virtual methods.**
  - Sub-classes: **no sub-classes.**
  - Accessibility: **minimize the accessibility of class members.**
  - Constness: **maximize the constness of member functions.**
  - Static: **static class implemented as singleton**, all static methods call their corresponding private member method
- Namespaces
  - Usage: **no namespaces, use classes**, exepct for `from_string` and `to_string` for enumerators.
  - `using` instruction: **no use of `using namespace` instruction.**
- Enumerators
  - Converters: **define `from_string` and `to_string` in the namespace correspoding to the enum.**
</details>

<details open><summary><font size="5" id="naming-rules">Naming rules</font></summary>

Rules that describe the way to name.  
- General
  - Language: **English.**
  - Word `number`: **no use of `number`, use `count`, `id` or `index`** *(ex: carId instead of carNumber).*
  - Plural: **no plural, describe as a container** *(ex: carList instead of cars).*
  - File name: **same as declared/defined class**, SnakeCase without leading `E_` for enum.
- Headers
  - Extension: `.h` if associated with a `.cpp` file, else `.hpp`
  - Content: `.h` files only contain declarations, `.hpp` files contain both declarations and definitions.
- Sources
  - Extension: `.cpp`
- Variables
  - Iteration index: **`i, j, k...` are reserved name for iteration index.**
  - Case: **camelCase.**
  - Naming: **custom typed must have same name as type in camelCase** *(ex: FileWatcher fileWatcher)*.
  - Boolean: **boolean variables must start with `b` or `is`.**
  - Container: **container variables must end with the type of the container** *(ex: std::map<string, int> nameAgeMap)*.
  - Modifiers *(as class member)*
    - Private/Protected/Public: **no marker.**
    - Constant: **SCREAMING_SNAKE_CASE.**
    - Static: **no marker.**
- Functions
  - Overloading: **functions name must be unique**, except for templated functions.
  - Case: **camelCase.**
  - Boolean: **boolean functions must start with `b` or `is`.**
  - Modifiers *(as method member)*
    - Private/Protected/Public: **no marker.**
    - Static: **no marker**, only a leading `p_` for corresponding private method of singleton.
- Enumerators
  - Case: **SCREAMING_SNAKE_CASE with leading `E_` and trailing `_TYPE`.**
  - Enum values case: **SCREAMING_SNAKE_CASE.**
  - Namespace: **same name as enum without leading `E_`.**
- Classes
  - Naming
    - Modifiers
      - Interface *(only virtual pure methods)*: **leading `I` immediately followed by PascalCase and should end with `able`** *(ex: IPlayable)*.
      - Abstract: **leading `A` immediately followed by PascalCase.**
      - Static *(only static methods)*: **no marker.**
      - Templated: **no marker.**
    - Order:
      1. Data involved *(ex: Car, Shoe, Key)* *(still no plural)*.
      2. Data processing method *(ex: Watcher, Cleaner, Filter)*.
    - Extension: **child class name must finish with parent name.**  
      Abbreviate the parent name if length is greater than `15`.  
      Add a comment in parent to define the used abbreviation.
    Other rules in `Types`.
- Types
  - Case: **PascalCase**
</details>

<details open><summary><font size="5" id="format-rules">Format rules</font></summary>

All format rules to apply defined by [clang-format file](.clang-format).
</details>
<br>
