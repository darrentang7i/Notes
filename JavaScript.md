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