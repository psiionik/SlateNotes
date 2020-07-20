# Primitive Types

<!-- TOC -->

- [Primitive Types](#primitive-types)
    - [Numbers](#numbers)
    - [Exercises with Numbers](#exercises-with-numbers)
    - [Strings](#strings)
    - [Exercises with Strings](#exercises-with-strings)
    - [Booleans](#booleans)
    - [Null and Undefined](#null-and-undefined)

<!-- /TOC -->

## Numbers

* Numbers in Javascript represent any kind of Integer, Decimal, or hexadecimal
    * Numbers can be positive, negative, or prefixed with "0x" to denote hexadecimal
* Javascript represents all numbers as "floats" meaning there will be problems with precision
* Ex. 0.1 * 0.1 = 0.0100000000000000000002
* Solution is to not store decimal numbers
    * If a number has 2 decimals, multiply by 100 before storing

## Exercises with Numbers

* In Javascript "number" is different than "Number" as the latter represents the object type of the number
* There are several Number properties that can be utilized
    * Get max possible integer value "Number.MAX_SAFE_INTEGER"
* There are also additional Number object methods
    * Can check if numbers are integers or finite
    * Can parse strings into floats or integers
* When you create a new Number object, it has some instance methods that allow you to format the value
    * Most of the methods such as .toFixed() or .toPrecision() round the internal value
    * Access the primitive value using .valueOf()

## Strings 

* Strings in Javascript are just a sequence of characters
* Can be defined with
    * Single quotes: ''
    * Double quotes: ""
    * Template literals (backtick) ``
* Can concatentate variables with strings or multiple strings with "+" operator
* Template literals allow for easy concatentation of strings and expressions
    * Use ```${somevariable or expression}``` syntax
 
## Exercises with Strings

* Strings have a bunch of useful methods
    * Each of the methods are case sensistive and do not immutable, meaning they don't mutate the original string
* Some useful methods are
    * trim
    * subString
    * split
    * repeat
    * search
* Full list [here](https://thejsbootcamp.com/fWpWQfJ6UAMRiAXAvbB9/14-primitive-types/04/)

## Booleans

* Booleans in Javascript represent "true" and "false"
* Useful for comparison values and controlling the flow of the program using conditionals
* There are "truthy" and "falsy" values which translate to true or false in a conditional
    * The falsy values are:
        * 0
        * -0
        * NaN
        * undefined
        * null
        * ''
    * Rest are truthy

## Null and Undefined

* Javascript reserves "null" and "undefined" as special types with only one value
* "null" represents the absence of a value
* "undefined" represents that a variable is not initialized and the value is absent
    * In functions with no return value or unintialized parameter







