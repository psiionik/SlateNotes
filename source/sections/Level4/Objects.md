# Objects

<!-- TOC -->

- [Objects](#objects)
    - [Intro to Objects](#intro-to-objects)
    - [Object Properties](#object-properties)
    - [Object Methods](#object-methods)
    - [Prototypes](#prototypes)
    - [Intro to Classes](#intro-to-classes)
    - [Class Constructor](#class-constructor)
    - [Static methods](#static-methods)
    - [Inheritance](#inheritance)
    - [Object Destructuring](#object-destructuring)
    - [Cloning objects](#cloning-objects)
        - [Shallow Copy](#shallow-copy)
    - [Merging Objects](#merging-objects)

<!-- /TOC -->

## Intro to Objects

* In JS any value that is not a primitive type is an object
* Can initialize an object as a "class" by having the "new" keyword before the function call

```javascript
    const myCar = new Car(params)
```

* Objects are always passed by reference

## Object Properties 

* Objects have properties which are defined as key, value pairs
    * Basically a way to attach member variables and information to an object
* Properties can be defined as any string

```javascript
    const car = {
        color: 'blue'
    }
```

    * Special characters can be added, but must be added around quotes
    * Ex.
    ```javascript
        const car = {
            'my color': 'blue'
        }
    ```
* To access the property, use "." (dot notation) or square brackets
    * Ex. ```car.color OR car['my color']```
* Accessing a property that doesn't exist results in a undefined value
* Objects can also have nested properties

```javascript
    const car = {
        brand: {
            name: 'test'
        }
    }
```

* Can update the value of a property later on by using "=" operator
* Can delete a property using "delete" operators
    * Ex. ``` delete car.brand ```

## Object Methods

* Functions can be assigned to objects, making them object methods
* With named function methods, have access to the "this" property of the object, referring to the object's properties

```javascript
let obj = {
    testing: 'Some property',
    namedFunction: function() {
        this.testing // have access to "this"
    }
}
```

* Arrow functions don't make the "this" reference to the object so it is better to not use them in object methods

## Prototypes

* Every Javascript object has a property called prototype
    * Prototype points to a different object
* Object prototypes are used to inherit properties and methods

```javascript
const car = {}
const car = new Object()
```

* Here the prototype of car is Object

* All the properties and methods of the prototype are avaiable to the object that has that prototype
    * All "list" properties and methods are available to list prototype

* The prototypes inherit each other
    * Meaning a new object that inherits extends Array will have Array and Object prototype in its prototype chain
    * It will inherit all properties and methods from Array and Object

## Intro to Classes

* Classes are a way to define a common pattern for multiple objects

```javascript
class Person {
    constructor() {
        this.name = "name"
    }
}

let newPerson = new Person()
```

* This creates a new "Person" object, where "newPerson" is an instance of a Person class

* Classes can hold properties like methods

```javascript
class Person {
    someFunction() {
        console.log(this)
    }
}

let newPerson = new Person()
newPerson.someFunction()
```

## Class Constructor

* A constructor() method is a special method that can be used to set properties of the class when creating a new instance of it

```javascript

class Person {
    constructor(name) {
        this.name = name
    }

    hello() {
        console.log('Hello, I am ' + this.name + "!")
    }
}

let flavio = new Person('flavio')
flavio.hello() // prints 'Hello, I am flavio!'
```

* Can use the "this" keyword to gain access to the object's properties

## Static methods

* Static methods are methods that are allowed to be executed on the class instead

```javascript
class Triple {
    static triple(n = 1){
        return n * 3
    }
}

console.log(Triple.triple(3)) // 9
```

## Inheritance

* Classes can extend other classes, inheriting their properties and methods
* Inside the child class you can reference the parent class by calling super()

```javascript

class Person {
    hello() {
        return "Hello I am a person"
    }
}

class Programmer extends Person {
    hello() {
        return super.hello() + "I am a programmer."
    }
}

let p = new Programmer()
p.hello() // Prints "Hello I am a person I am a programmer."
```

## Object Destructuring

* Given an object, you can extract just certain properties or put them into specific variables

```javascript
let obj = {
    firstName: 'Tom',
    lastName: 'Bob',
    actor: true,
    age: 54
}

const {firstName, age} = obj // firstName has 'Tom', actor has true
```

* Can automatically assign a property to a variable with another name

```javascript
const {firstName: name, actor} = obj
```

* Object destructuring is similar to that of array destructuring except that object destructuring is based on the property names while array destructuring is based on order in array

## Cloning objects

* Javascript types are either primitive or objects
* Primitives are always passed by value in Javascript while objects are always passed by reference
* This mean when cloning objects, bugs can appear in the cloning process

### Shallow Copy

* When just copying the values of one object to another

```javascript
let obj = {
    prim: 2,
    anotherObj: {
        val: 'red'
    }
}

let truck = { ...obj }
```

* Here changing the "prim" property on truck will not change it on "obj"

```javascript
truck.prim = 123123 
console.log(truck.prim) // 123123
console.log(obj.prim) // 2
```

* However, changing the object within "obj" will also change the obj within "truck" and vice versa

```javascript
truck.anotherObj.val = 'blue'
console.log(truck.anotherObj.val) // blue
console.log(obj.anotherObj.val) // blue
```

* This is because objects are passed by reference
* When performing the shallow copy using the "spread" operator, the reference of the anotherObj was copied to "truck" so any changes from either of the objects would be reflected in the other
* Can be mitigated using deep copy libraries like "lodash.clonedeep"
    * Deep copies create a new object entirely, so references aren't shared

* Spread operator "..." is a quick way to perform a shallow copy on objects

## Merging Objects

* Use the spread operator to merge two objects together

```javascript

let obj1 = {
    name: 'obj1',
    testing() {
        console.log(this.name)
    }
}

let obj2 = {
    name2: 'obj2',
    testing2() {
        console.log(this.name)
    }
}

const obj3 = {...obj1, ...obj2} // obj3 has all of the properties in both obj1 and obj2
```

* If two objects have the same property name, it will take the value of the last object in the spread operator
