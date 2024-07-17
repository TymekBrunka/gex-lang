---
id: syntax-and-design
aliases: []
tags: []
---

<h1 align="center">Gex programming language</h1>

<p align="center">
  <img src="../../img/gex3.svg">
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
  btw _ separator in number declaration does nothing and is not validated, just syntactic sugar

  - #### Int
    ``` c
    type(69)  // -> int
    69        // decimal notation
    69e420    // 69 * 10^420]]
    69_420    // 69420 but with _ separator for clarity
    ```

  - #### Float
    ``` c
    type(0.69) // -> float
    1.0        // implicit declaration of float
    1f         // explicit declaration of float
    69.420f    // explicit declaration of float
    0.062_5    // 0.0625 but with _ separator for 'clarity'
    ```
  - #### Double
    ``` c
    type(0.45d) // -> Double
    1d          // explicit declaration of double
    69.420d     // explicit declaration of double
    0.062_5d    // 0.0625d but with _ separator for 'clarity'
    ```
  - #### Char and String
    Strings can be declared with single and double quotes (' and ")
    char is single character (used in functions that only use single character as argument)
    ``` c
    type("a")      // -> string
    'a'            // a character, if string has length of 1, it can be passed as character
    " im 'banana'" /* string (char[] <- character array (more in the future))
                   note: 2nd string contains single quotes in itself just like 3rd one*/ 
    "I want to break free like this double quote right here\""
    ```
  - #### Bool
    ``` c
    true
    false
    ```
- ### declaring variables and constants
  Variables can be declared with and without `let` keyword.  
  Constants are asigned with `const` keyword.
  You can give variable static type (one type for rest of its lifetime)
  or **type class** (like 'number (name is number and ' is for type classes) which **forces variable to be one of built-in number types**)
  ```js
  hello = "hello"          // asigning "hello" to hello without let keyword
  let world = "world!"     // asigning "world!" world with let keyword
  println(hello.." "..world) // printing "hello world!" to console ( .. is operator for joining 2 strings next to it (concatinating))
  
  let I_am : string        // declaring empty variable of type string
  I_am = "gex"             // its is variable so it can be (re)asigned
  ```
  ``` js
  const fex = "gex"  // asigning "gex" to fex
  fex = "fex"        // trying to change fex resoults an error
  ```
- ### declaring functions
  Functions can be declared with `function` keyword and can not be reasigned when declared this way.
  The other way to declare function is to declare **variable of type `function`** which can be reasigned, if it isn't constant.
  ``` c
  function add(a : 'number, b : 'number) // addition can be only performed with numbers, so I'm using number type class and force a and be to use it
    return a + b // adding 2 numbers together
  end
  println("Sum of 1 and 2 is " .. add(1, 2)) // -> "Sum of 1 and 2 is 3"
  ```
  ``` c
  subtract = function(a : 'number, b : 'number) // asigning function to a variable
    return a - b // subtracting b from a
  end
  println("2 subtracted from 3 gives " .. subtract(3, 2)) // -> "2 subtracted from 2 gives 1"
  ```
  ``` js
  function multiply(a : 'number, b : 'number) /* declaring function before its body
  so function power doesnt complain about lack of function multiply(useful for situations where a depends on b and b on a)*/
  
  function power(a : 'number, b : int) // function power requires function multiply //I'm planing on function overloading but idk
    for i in range(1,b+1) do /* function range with 2 arguments: 1st - start, 2nd - end
      function range generates iterator for for loop. In this case <1, b>*/
      a *= a //multiplying a by a (in-place operator)
    end
    return a
  end
  
  function multiply(a : 'number, b : 'number)
    return a * b //multiplying a by b
  end

  // functions can be nested but this example shows something else
  println("2^10 = " .. power(2, 10)) // -> "2^10 = 1024"
  ```
