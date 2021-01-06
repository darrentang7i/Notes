# JavaScript

## Variables
There are several ways of declaring variables in JavaScript, among them are:   
```js
var variableName = 123 //limits scope to immediate function body
let variableName = 123 //limits scope to enclosed block { }
const variableName = 123  
```

 

## Ternary Operator
```js
return (condition ? ifTrue: ifFalse)
```
## Console.log()
The console.log() method is used to print messages to the console

```js
console.log("Message")
```

## String Formatting
String concatenation can be done in multiple ways in JavaScript. You can use the '+' operator or with template literals - `text ${expression}`
```js
let service = 'credit card'
let month = 'May 30th'
console.log('Your ' + service + 'bill is due on ' + month)
console.log(`Your ${service} bill is due on ${month})

```

## Comparison
Other languages: `==`  
JavaScript: `===`

## Functions

In Javascript, there is no need to declare the types of each variable passed in as input. 
Functions can be defined in a number of ways:

1. Function keyword

```js
//Named Function
function sum (num1, num2) {
    return num1 + num2;
}
```

2. Function Expressions  
```js
const dog = function() {
    return 'Woof!'
};
```

3. Arrow Function
```js
const sum = (num1, num2) => {
    return num1 + num2;
};

//with one arg
const checkWeight = weight => {
    console.log(`Weight is ${weight} kg`);
};
```

Use function expressions when you need to limit the scope of the function, ie. not global scope like with the function keyword

Function names can also be assigned to variables, and passed into other functions as parameters
```js
functionName = () => return true;
const newName = functionName; //now, newName() will exectue functionName()
```


## Arrays

Unlike Arrays in C++, arrays in JavaScript can store variables of multiple types
```js
let arrName = [1, true, "asdf"];
```
### Array Length
To get the length of an array, call `arr.length`
```js
const arr = [1, 2, 3];
console.log(arr.length) //3
```
### Push and Pop
By default, the `.push()` and `.pop()` methods treat the array as a stack. That is, elements are pushed to the back, and popped from the back. Note that `.pop()` also returns the element that is removed.

```js
const fruits = ['apple', 'oranges']
fruits.push('pear') //fruits = ['apple', 'oranges', 'pear']
fruits.pop() //fruits = ['apple', 'oranges'] and 'pear' is returned
```

### Other Methods

```js
arr.unshift()  //removes first element, and returns it
arr.slice(start_idx, end_idx) // returns a shallow copy of a portion of the arr, non mutating
arr.indexOf(element) //returns the index of an element
```

When arrays are passed into a function, they are essentially passed by reference

### Sorting Arrays

```js
var points = [30, 1, 20]
points.sort(function(a,b) { return a-b }); //sorts ascending
points.sort(function(a,b) { return b-a }); //sorts descending
```

### Iterators

- `.forEach()`
executes a callback function for each element of an array
```js
const fruits = ['mango', 'apple']
//both of these do the same thing
fruits.forEach(item => console.log(item));
fruits.forEach(function(item){
    console.log(item);
})
```

- `.map()` executes a callback function for each element of an array, and returns a new array made up of the returned values of the callback function. The original array does ***NOT*** get altered
```js
const animals = ['hen', 'elephant']
//returns ['h', 'e']
const secretMessage = animals.map(animal => {
    return animal[0];
}) 
```

- `.filter()` filters out certain elements from an original array, and returns a new array with all elements for which the callback function returns true
```js
const words = ['chair', 'pillow']
//returns ['chair']
const shortWords = words.filter (word => {
    return word.length < 6;
})
```

- `findIndex()` returns the index of the first element that evaluates to true in the callback function
```js
const jumbledNums = [123, 25, 5]
//returns 2
const lessThanTen = jumbledNums.findIndex(num => {
    return num < 10;
})
```
- `reduce()` returns a single value after iterating through the elements of an array. It takes in a callback function with two parameters `(accumulator, currentValue)` as arguments.
```js
const numbers = [1, 2, 4, 10]
//returns 17
const summedNums = numbers.reduce((accumulator, currentValue) => {
    return accumulator += currentValue;
})
```

- `.every()` and `.some()` checks if every word has a certain attribute, and checks if there exists some word with a certain attribute respectively
```js
const words = ['unique', 'uncanny']
console.log(words.some((word) => {
    return word.length < 6;
}));
```

## Objects

Objects store collections of key-value pairs.

The dot (`.`) operator and `[]` operator can be used to access elements. To delete properties, use the `delete` keyword.
```js
let spaceship = {
    homePlanet: "Earth",
    color: 'Silver'
};

delete spaceship[color]
```

Methods can also be put into objects, and objects can be nested
```js
let spaceShip = {
    methodOne() {
        console.log('Hello World');
    },
    methodTwo() {
        //do something
    },
    passengers: [{name: 'a'}] //array of objects
}
```

By default, objects are passed ***by reference*** into functions.

### For ... in

To iterate over the keys of an object, a `for ... in` loop can be used
```js
let mobile = {
    brand: 'Samsung',
    model: 'Galaxy Node 9'
};
for (let key in mobile){
    console.log(`${key}: ${mobile[key]}`);
}
```

To access elements from within objects, you must use the `this` keyword. Be sure not to use arrow function syntax when using `this` in a method.

By convention, private variables in JS are marked with a preceding underscore:
```js
const robot = {
    //this is a private variable
    _energyLevel:100
};
```
### Getter and Setter Methods
- Getter methods get and return internal properties of an object
- Setter methods reassign values of existing properties of an object
```js
const robot = {
    _name = 'ROB',
    get fullName() {
        return this._name;
    }
    set fullName(newName){
        this._name = newName;
    }
};
```

### Factory Functions
Allows the creation of many instances of an object quickly
```js
const robotFactory = function (model, mobile){ 
    return {
        model: model,
        mobile: mobile
    }
};
```
### Destructuring Assignment Shorthand Syntax
Object properties can be extracted into specific variable values
```js
const residence = vampire.residence;
//shorthand for this is 
const {residence} = vampire;
```

The opposite also works for object creation
```js
const activity = 'Surfing';
const beach = {activity}
console.log(beach); // {activity: 'Surfing'}
```
### Built in Object Methods
```js
Object.keys(objName) //returns an array of all keys in objName
Object.entries(objName) //returns and array of all key value pairs in objName
Object.assign(target, source) //returns target object, and copies all properties from one or more source objects to target
```

## Classes

Constructors in JavaScript are simply called `constructor`. The `new` keyword marks the creation of an instance of a class.
```js
class Dog {
    constructor(name) {
        this._name = name;
    }
}
//creates a new instance of the dog class
const halley = new Dog("Halley");
```

In classes, commas are not required between methods.

With static methods, you can limit access to the method to the class itself, and not on an instance of a class.

```js
class Animal {
    constructor(name) {
        this._name = name;
    }
    static func(){ 
        //do something
    }
}
```

JavaScript supports inheritance, and it is done with the `extends` keyword. A child class constructor calls the parent class constructor with the `super()` method.
```js
class cat extends Animal {
    constructor(name, usesLitter) {
        super(name);
        this._usesLitter = usesLitter;
    }
}
```

## Modules

- Modules are reusable pieces of code that can be exported from one program and imported for use in another program.  

### Importing and Exporting in Node.js
The require function can be used to import code from another file into current scripts
```js
const moduleA = require("./module-a.js"); //note that the .js is optional
```
To export modules, assign the object to the `exports` property of `module`.
```js
let Airplane = {};
Airplane.myAirplane = "StarJet";
module.exports = Airplane;
```
### Importing and Exporting with ES6 JavaScript
The `import` keyword can be used to import functions, and `export default` can be used to export singular objects/functions.

```js
//In "moduleA.js"
let Menu = {}
export default Menu;

//In main.js
import Menu from './moduleA.js';
//now everything in Menu can be accessed
```
Here are some additional ways of importing/exporting with ES6
```js
//exporting by var names
//"menu.js"
let Specialty = "pasta";
let food = "burgers";
export {Specialty, food};
//OR
export {Specialty as chefsSpecial}; //now u import chefsSpecial, since it is an alias for Specialty

//In main.js
import {Specialty, food} from "./menu";
```

## Promises
Pormises are objects that represent the eventual outcome of an asynchronous operation. A promise object can be in one of 3 states:
- **Pending**: The initial state, where the value is not yet available
- **Fulfulled**: The operation is successfully completed, and promise has resolved value
- **Rejected**: The operation has failed 

### Creating a JavaScript Promise Object
Creating a promise object requires the use of the `new` keyword. The promise object constructor takes in an executor function as the argument. This function is responsible for resolving or rejecting the promise.
```js
const executorFunc = (resolve, reject) => {
    resolve('Resolved');
}
const promise = new Promise(executorFunc);
```

As shown above, the executor function takes 2 functions as its arguments, the predefined `resolve()` and `reject()` functions.

### setTimeout()
`setTimeout()` is an asynchronous JavaScript function which executes a code block through a callback function after a set delay in ms.
```js
const loginAlert = () => {
    alert('Login');
}
setTimeout(loginAlert, 6000);
```

### .then() method
The `.then()` method of a JS promise object can be used to get the eventual result (or error) of the asynchronous operation. `.then()` accepts 2 function arguments, first one is called if resolved, second if rejected.

```js
const promise = new Promise((resolve, reject) => {
    setTimeout(() => {
        resolve('Result');
    }, 200)
})

Promise.then(handleSuccessFunc, hendlFailureFunc);
```

`.then()` methods can also be chained if the previous `.then()` method returns a Promise.

### .catch() method for handling rejection

The `.catch()` method of a JS promise object handles failures.

```js
Promise.then(handleSuccessFunc, handleFailureFunc);
//can be refactored to
Promise.then(handleSuccessFunc).catch(handleFailureFunc)
```

### Common Mistakes 
1. Nesting Promises instead of chaining
```js
//DONT DO THIS!!
returnsFirstPromise().then((firstResolveVal) => {
    return returnsSecondValue(firstResolveVal)
    .then((secondResolveVal) => {
        console.log(secondResolveVal);
    })
})
```
It is always better to chain promises rather than nesting them

2. Forgetting to `return` a promise  
If chaining multiple promises, remember to `return` on all promises except for the last one, so there is logic to handle.

### Promise.all()
This method accepts an array of promises as argument, and returns a single promise. If **every** promise in the array resolve, the promise returned will resolve with an array containing the resolved value from each promise in the arg array. If **any one** function from the initial array rejects, the promise returned will immediately reject with the reason that promise rejected.

```js
let myPromises = Promise.all([returnsPromOne(), returnsPromTwo()]);
```

## Async Await
### Async
The `async` keyword is used to write functions that handle asynchronous actions. Async functions **always** return a promise. It can return in one of 3 ways:  
1. If nothing is returned from the function, return a promise with resolved value of `undefined`
2. If a non-promise value is returned from the function, return a promise resolved to that value
3. If a promise is returned from the function, simply return that promise
```js
async function fivePromise() { return 5; }

fivePromise().then(resolvedValue=> {
    console.log(resolvedValue);
}) //prints 5
```
### Await
The `await` keyword can **only** be used inside an `aync` function. `await` is an operator that returns the resolved value of a promise. `await` halts or pauses the execution of our `async` function until the promise is resolved.
```js
async function asyncFuncExample() {
    let resolvedValue = await myPromise(); //without await keyword, resolved value will be something like "Promise {<pending>}"
    console.log(resolvedValue);
}
```

The power of `async...await` lies within scenarios where we have a series of asynchronous actions which depend on one another. With native promise syntax, we would have to use a chain of `.then()` functions, but using `async...await` greatly simplifies the process.

## Error Handling
To handle errors with `async...await`, we can use `try...catch` statements. This way, we can catch both synchronous and asynchronous errors!
```js
async function hostDinnerParty() {
    try {
        let food = await cookBeanSouffle();
    }
    catch(error) {
        console.log(error);
    }
}
```


# Misc 

- parseInt() parses a string argument and returns an integer of the specified base

```js
const parsed = parseInt('0xF', 16); //parsed = 15
```