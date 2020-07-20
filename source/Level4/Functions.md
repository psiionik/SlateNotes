# Functions

<!-- TOC -->

- [Functions](#functions)
    - [Functions](#functions-1)
    - [Arrow Functions](#arrow-functions)
    - [Nested Functions](#nested-functions)
    - [Recursive Functions](#recursive-functions)

<!-- /TOC -->

## Functions

* Functions in Javascript are a self-contined, block of code designed to be reused
* Functions can have any number of parameters and the parameters can be of any type
* Functions can return any value or for multiple values, use arrays or objects
    * Functions can also return other functions

## Arrow Functions

* Arrow functions are another way to declare functions
    * Anonymous so they must be set to a variable
* Ex.
```
let something = () {

}
```
* Arrow functions allow for shorter syntax
    * Can have implicit return when only having one line and omitting curly braces
    * Don't need parenthesis if there is only one parameter being passed
* Arrow functions are useful because it bind the "this" keyboard for the object in that object's scope

## Nested Functions

* You can nest functions within the scope of another function
    * Useful because it modularizes the code (if inner function is only useful to that outer function)
    * Also, allows you to reuse names without having to worry about overwriting
* The nested function is within the outer function's scope
    * Means it can only be called within the outer function, can't be called outside the outer function
* Can call a funciton before the definition due to something called [Hoisting](https://www.i-programmer.info/programming/javascript/5364-javascript-hoisting-explained.html)

## Recursive Functions

* Recursive functions are when a function invokes itself within its block of statements
* Recursion is very useful because it unlocks being able to utilize techniques such as divide and conquer, graph traversal, and new approaches to solve problems
* Ex. Factorial recursively
```
function factorial(n) {
    if (n == 1){
        return 1
    }

    return n * factorial(n-1)
}
```
* In recursion the program stores each function call's information and context on the call stack
* When the base case is reached and something returns, the returned value goes to the previous function call's context and that previous function call resumes execution where it left off
* If the recursion doesn't end, the function calls will fill up the call stack and the maximum size is reached
