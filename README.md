# Coding standard

The most important coding rules goal is the **consistency of the code** *(i.e. no matter who writes the code)*.
In order to reach this goal, the rules must be written so that **it reduces the number of ways to write the code**.
<b>However, they are not absolute. <u>Exceptions can be made if justified.</u></b>

<details open><summary><font size="5" id="coding-rules">Coding rules</font></summary>

Rules that describe the way to implement.
- General
  - Friendship: **do not use**
  - Shared pointers: **only for child classes of interfaces**
  - Dynamic allocation: **do not use** (i.e. no use of `new`)
  - Exceptions: **do not use**
  - Cast: **use `static_cast`** if possible, else `reinterpret_cast`. **Do not use `dynamic_cast` or `C style cast`**
  - Comments for:
    - implicit required condition of well running
    - libraries
    - class, function or variable with names that cannot be explicit enough
  - Macros: **do not use**
  - Aliases: **use the `using` keyword instead of the `typedef` keyword and only for the function types**
  - Lambda: **use `std::function` as the type but declare it with a `lambda function`**
  - Inheritance: **do not use inheritance** except for interfaces. Use composition over inheritance instead
  - Dead code: **do not use** (no what-if code)
  - Files: **only one class per file**
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
  - Definition order: **same order as declared**
    - Include order
        In alphabetical order for each category:
        1. Corresponding header
        2. Standard library
        3. External depedencies headers
        4. Project headers
- Variables
  - Declaration
    - Instruction: **only one declaration per line**. This rule also applies for class members
    - Initialization: **if possible, initialize variable on declaration**. This rule also applies for class members
  - Scope: **declare the variable only inside a method or a class**
  - Pointer/Reference: **use references instead of pointers when the value is not optionnal**, unless the object is contained in a data structure
  - Constness: **maximize the constness of variables**
  - Primitive type: **use only strong primitive types** *(ex: `uint32_t`, `double_t`)*
  - Type: **use the most accurate types** *(ex: `istringstream` instead of `stringstream`)*
  - `auto` keyword: **use only for lambda, loop-variable and types that are longer than 15 characters**
- Functions
  - Inline functions: **use only trivial setters and getters**
  - Side effect: **avoid side effect functions**
      Exception valid for: data structures, in-out parameters, multiple outputs
  - `Return` instruction: **immediately exit a function when a required condition is not fulfilled**
    - Parameters
      - Default value: **no default value**
      - Passing: **pass primitive types by value, pass any other types by reference**
- Structs
  - Usage: use structs for **mainly public attributes and methods**
    Other rules in `Classes`
- Classes
  - Constructor: **do not use implicit conversions**, use the `explicit` keyword
  - Virtual: **declare the destructor as a virtual for classes that contain virtual methods**
  - Sub-classes: **do not use**
  - Accessibility: **minimize the accessibility of the class members**
  - Constness: **maximize the constness of the member functions**
  - Static: **static class implemented as singleton**, all static methods must call their corresponding private member method
- Namespaces
  - Usage: **no namespaces, use classes**, except for `from_string` and `to_string` for enumerators
  - `using` instruction: **do not use the `using namespace` instruction**
- Enumerators
  - Converters: **define `from_string` and `to_string` in the namespace correspoding to the enum**
</details>

<details open><summary><font size="5" id="naming-rules">Naming rules</font></summary>

Rules that describe the way to name.
- General
  - Language: **English** only
  - Word `number`: **do not use `number`. Use `count`, `id` or `index`** *(ex: carId instead of carNumber)*
  - Plural: **no plural, describe as a container** *(ex: carList instead of cars)*
  - File name: **same as declared/defined class**, SnakeCase without leading `E_` for enum
- Headers
  - Extension: `.h` if associated with a `.cpp` file, else `.hpp`
  - Content: `.h` files only contain declarations, `.hpp` files contain both declarations and definitions.
- Sources
  - Extension: `.cpp`
- Variables
  - Iteration index: **`i, j, k...` are reserved name for iteration index**
  - Case: **camelCase**
  - Naming: **custom typed must have same name as type in camelCase** *(ex: FileWatcher fileWatcher)*
  - Boolean: **boolean variables must start with `b` or `is`**
  - Container: **container variables must end with the type of the container** *(ex: std::map<string, int> nameAgeMap)*
  - Modifiers *(as class member)*
    - Private/Protected/Public: **do not use any marker**
    - Constant: **SCREAMING_SNAKE_CASE**
    - Static: **do not use any marker**
- Functions
  - Overloading: **function names must be unique**, except for templated functions
  - Case: **camelCase**
  - Boolean: **boolean functions must start with `b` or `is`**
  - Modifiers *(as method member)*
    - Private/Protected/Public: **do not use any marker**
    - Static: **do not use any marker**, only a leading `p_` for the corresponding private method of the singleton
- Enumerators
  - Case: **SCREAMING_SNAKE_CASE with leading `E_` and trailing `_TYPE`**
  - Enum values case: **SCREAMING_SNAKE_CASE**
  - Namespace: **same name as enum without leading `E_`**
- Classes
  - Naming
    - Modifiers
      - Interface *(only virtual pure methods)*: **leading `I` immediately followed by PascalCase and should end with `able`** *(ex: IPlayable)*
      - Abstract: **leading `A` immediately followed by PascalCase**
      - Static *(only static methods)*: **do not use any marker**
      - Templated: **do not use any marker**
    - Order:
      1. Data involved *(ex: Car, Shoe, Key)* *(still no plural)*
      2. Data processing method *(ex: Watcher, Cleaner, Filter)*
    - Extension: **the child class name must end with its parent class name**
      Abbreviate the parent name if its length is greater than `15`
      Add a comment just above the parent class to define the used abbreviation
    Other rules in `Types`
- Types
  - Case: **PascalCase**
</details>

<details open><summary><font size="5" id="format-rules">Format rules</font></summary>

All of the format rules to apply are defined in the [clang-format file](.clang-format).
</details>
<br>

# Licence

MIT Licence. See [LICENSE file](LICENSE).
Please refer me with:

	Copyright (c) Nicolas VENTER All rights reserved.
