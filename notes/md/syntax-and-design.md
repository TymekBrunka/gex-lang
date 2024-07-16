<h1 align="center">Gex programming language</h1>

<p align="center">
  <img style="width: min(30vw, 30vh);" src="../../img/gex3.svg">
</p>

Gex language is (or is supposed to be) **dynamicly typed lua like language** with:
- static types and type classes (when type or type class is not assigned, then varaible's type can change at runtime)
- classes
- function decorators
- traits (like in haskel fun a -> a takes value of type a and returns value of type a)
- and maybe pointers

easly embedable with ability to overrite operators and [library permision system](./lib-perm-system.md).

#### Targeted systems:
- linux
- macos
- linux
- android
- ios

<h2 align="center">base lib</h2>

Base lib is base for Gex programing language containing basic types, classes, operators and functions
necesary for Gex language to function properly.
Base lib isn't library, so you dont have to import it, it is build into interpreter.

- ### comment
``` c
//this is comment
/*
 this is multiline
 comment
*/
```

- ### basic types

  - #### Int
    ``` c
    69        // decimal notation
[[1721036641-DQEM|    69e420    // 69 * 10^420]]
    ```
  
  - #### Float
    ``` cs
    1.0     //implicit declaration of float
    1f      //explicit declaration of float
    69.420f //explicit declaration of float
    ```
  - #### Double
    ``` cs
    1d      //explicit declaration of double
    69.420d //explicit declaration of double
    ```
  - #### Char and String

    char is single character (used in functions)
    ``` c
    "a"         // a character, if string has length of 1, it can be passed as character
    "im banana" // string (char[] <- character array (more in the future))
    ```
  - #### Bool
    ``` c
    true
    false
    ```
- ### declaring variables and constants
  Variables can be assigned with and without `let` keyword.  
  
  ```js
  
  ```
