# Javascript Basics

<!-- TOC -->

- [Javascript Basics](#javascript-basics)
    - [Introduction to Javascript](#introduction-to-javascript)
    - [Javascript History](#javascript-history)
    - [Javascript Syntax Intro](#javascript-syntax-intro)
        - [White Space](#white-space)
        - [Case Sensitive](#case-sensitive)
        - [Literals](#literals)
        - [Identifiers](#identifiers)
        - [Comments](#comments)
        - [Semicolons](#semicolons)
    - [Values](#values)
    - [Variables](#variables)
        - [const](#const)
        - [let](#let)
    - [Types](#types)
    - [Basic Expressions](#basic-expressions)
    - [Operators](#operators)
    - [Precedence Rules](#precedence-rules)
    - [Comparison Operators](#comparison-operators)
    - [Conditionals](#conditionals)

<!-- /TOC -->

## Introduction to Javascript

* Javascript is mainly used to create:
    * Websites
    * Web applications
    * Server-side applications using NodeJS
* Can be also used to create mobile applications, create programs for microcontrollers, or create smartwatch applications
* Javascript features are:
    * high level - provides abstractions to lower level code
        * Has garbage collection, provides abstracts and constructs such as classes that allow you to deal with powerful variables and objects
    * dynamic - executes things at runtime such as:
        * dynamic typing
        * late binding
        * reflection
        * functional programming
        * object runtime alteration
        * closures
    * dynamically typed - variables don't enforce types, can reassign values of different types
    * loosely typed - no enforcing of types on a variable, but leads to issues with type safety and type checking
    * interpreted - unlike C++ or Java, Javascript is interpreted meaning that it doesn't neeed to compile the code into machine code
    * multi-paradigmed - Javascript does not enforce a certain programming style
        * Unlike C which enforces an imperative style or Java which enforces an object-oriented style
        * Javascript gives you the option to program in an object-oriented style using ES6 classes or a functional style with first-class functions

## Javascript History

* First scripting language natively supported by web browsers that gives it an advantage
    * Other languages need to be compiled into Javascript
* Javascript now has grown past just the client-side applications by being able to write server-side code as well as power databases, develop embedded applications, mobile apps, etc.

## Javascript Syntax Intro

### White Space

* Javascript doesn't care about the amount of spaces or line breaks
* Stick to a style and use linters such as **Prettier**

### Case Sensitive

* Javascript is case sensitive
* "Something" is not the same as "something"

### Literals

* The values that is written into the source code
* Can be things like numbers, strings, arrays, functions, objects, etc.

### Identifiers

* Sequence of characters that are used to identify a variable, function, or object
* Characters include: letters, dollar sign, underscore, numbers

### Comments

* Single line comments using "//"
* Ex.
```
// This is a comment
function test() {
    //...
}
```
* Multi-line comments using "/* */"
* Ex.
```
/* This is
a multi
line
comment
*/
```

### Semicolons

* In Javascript, semicolons are necessary at the end of each line, but now Javascript intepreters are smart enough to add semi-colons on the end of each line
* Not necessary unlesss it must be absolutely specified

## Values

* "hello" is a value and is of type "string"
* Values have a type such as "string" or "number" but each type has their own characteritics
* When needing to save a value, you create a variable and pass the reference of the value to the variable
    * The variable has a name and the value is what is stored inside it so that you can later access the value through the variable name

## Variables

* A variable is a reference to a value using a label
    * This is done to reference it and use it later in a program
* 3 ways to declare a variable
    * let
    * const
    * var

### const

* "const" refers to a constant reference to a value
    * This means that the value of the variable cannot change
* "const" doesn't mean constant meaning that the value cannot change
    * It just means that it cannot be reassigned
    * Objects that are referenced with const can have their internal values changed

### let

* A way of declaring variable that allows for changing the value of the variable
* Better to use const if you know that the variable won't be reassigned since it leads to less code bugs

## Types

* When assigning a value to a variable, you give it a "type"
* Since Javascript is loosely typed, the type of the variable can be reassigned to a host of another type
* 2 main types:
    1. Primitive types
        * Numbers
        * Strings
        * Booleans
        * Symbols
        * null
        * undefined
    2. Object types
        * Anything that is not a primitive type 
        * Objects have special properties and methods that can be used to act on those properties

## Basic Expressions

* Expression is a single unit of Javascript code that the Javascript engine can evaluate and return a value
* Different types of basic expressions
    * Primary - just one type or value
    * Arithmetic - involving a variable and an operator and result in a number
    * String - expressions that result in strings
    * Logical - expressions that use logical operators and resolve into a boolean value 

## Operators

* Operators take in 1 - 3 operands to combine them in to a more complicated expression
* Examples of binary operators (2 operands)
    * "=" - assignment
    * "+" - addition
        * Doubles as a string concatenator when dealing with strings
    * "-" - subtraction
    * "/" - division
        * Dividing by 0 gives an "Infinity" value
    * "%" - Remainder 
        * Remainder with 0 gives "NaN" (not a number)
    * "*" - multiplication
    * "**" - exponentation or power

## Precedence Rules

* When there are multiple operators within one expression, there are precedence rules that come into play
* In this table is the operators with their precedence (higher the in the table means higher precedence)

<table>
    <tr>
        <th>
            Operator
        </th>
        <th>
            Description
        </th>
    </tr>
    <tr>
        <td>
            */%
        </td>
        <td>
            Multiplication/Division/Remainder
        </td>
    </tr>
    <tr>
        <td>
            +-
        </td>
        <td>
            Addition/Subtraction
        </td>
    </tr>
    <tr>
        <td>
            =
        </td>
        <td>
            Assignment
        </td>
    </tr>
</table>

* Operators that are on the same precedence level get executed sequentially from left to right

## Comparison Operators

* These operators are used for comparing the values of 2 operands
* It always returns a boolean value
* 4 equality operators
    * "===" - equal to and type is equal
    * "!==" - not equal to and type is not equal
    * "==" - equal to
    * "!=" - not equal to
* 4 inequality operators
    * ">" - greater than
    * "<" - less than
    * ">=" greater than or equal to
    * "<=" less than or equal to

## Conditionals

* Conditionals allow you to take one route or another depending on the result of an expression
* Conditional checks whether the result of the expression is true or false 
    * If number is passed, it is always true unless the number is 0
    * If string is passed, it is always true unless it is the empty string ""
* After the conditional a statement must be added to execute
    * Put inside things called "blocks" which are represented by the curly braces "{}"
* An "Else" statement can be added to the second part of the if statement for executing statements in the case that the conditional is false
