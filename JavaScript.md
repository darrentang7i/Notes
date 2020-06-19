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

## Arrays
