# Coding standard

The most important coding rules goal is the **consistency of the code** *(i.e. no matter who writes the code)*.
In order to reach this goal, the rules must be written so that **it reduces the number of ways to write the code**.
<b>However, they are not absolute. <u>Exceptions can be made if justified.</u></b>

<details open><summary><font size="5" id="coding-rules">Coding rules</font></summary>

Rules that describe the way to implement.
- General
  - Dynamic allocation: **do not use** (i.e. no use of `new`)
  - Exceptions: use only on exceptional events and always with a catch, and only if absolutely required
  - Cast: **use `static_cast`** if possible, else `reinterpret_cast`. **Do not use `dynamic_cast`
  - Comments for:
    - implicit required condition of well running
    - libraries
    - class, function or variable with names that cannot be explicit enough
  - Macros: **do not use**
  - Inheritance: **do not use inheritance** except for interfaces. Use composition over inheritance instead
  - Dead code: **do not use** (no what-if code)
- Headers
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
        2. Standard library headers
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
- Functions
  - Side effect: **avoid side effect functions**
      Exception valid for: data structures, in-out parameters, multiple outputs
  - `Return` instruction: **immediately exit a function when a required condition is not fulfilled**+++++++++++++++++++
    - Parameters 
      - Passing: pass by copy when size <= CPU register size
- Structs
  - Usage: use structs for **mainly public attributes and methods**
    Other rules in `Classes`
- Classes
  - Accessibility: **minimize the accessibility of the class members**
  - Constness: **maximize the constness of the member functions**
- Namespaces
  - `using` instruction: **do not use the `using namespace` instruction**
</details>

<details open><summary><font size="5" id="naming-rules">Naming rules</font></summary>

Rules that describe the way to name.
- General
  - Language: **English** only
  - Word `number`: **do not use `number`. Use `count`, `id` or `index`** *(ex: carId instead of carNumber)*
  - File name: **same as declared/defined class**
- Sources
  - Extension: `.cpp`
- Variables
  - Iteration index: **`i, j, k...` are reserved name for iteration index**
  - Naming: **custom typed must have same name as type in camelCase** *(ex: FileWatcher fileWatcher)*
  - Boolean: **boolean variables must start with `b` or `is`**
  - Modifiers *(as class member)*
    - Constant: **SCREAMING_SNAKE_CASE**
- Functions
  - Case: **camelCase**
  - Boolean: **boolean functions must be understandable as a yes/no question (starting with "is", "has", "contains", ...) **
- Enumerators
  - Enum values case: **SCREAMING_SNAKE_CASE**
- Classes
  - Naming
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
