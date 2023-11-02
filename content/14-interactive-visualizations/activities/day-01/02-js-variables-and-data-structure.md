+++
title = "02. JavaScript Variables and Data Structure 👩‍🏫🧑‍🏫"
weight = 2
tags = ["plotly"] 
+++

# Arrays and Objects

```js
// a variable can be initialized as an empty array with two square brackets
let myArray = [];

// elements can be added to arrays with the push() method
myArray.push('alpha');
myArray.push('beta');
myArray.push('gamma');
myArray.push('delta');

console.log(myArray); // output: ['alpha', 'beta', 'gamma', 'delta']

// to access a single element from an array, use index notation
// similar to python, JavaScript uses 0-indexing
console.log(myArray[1]); // output: 'beta'

// elements from arrays can be overwritten by assigning a new value
myArray[3] = 'omega';
console.log(myArray); // output: ['alpha', 'beta', 'gamma', 'omega']

// to access a range of values from the array, use the slice() method.
// slice(start, end) returns a new array of the objects at indexing beginning at `start` and up to (but not including) `end`.
console.log(myArray.slice(1,3)); // output: ['beta', 'gamma']
```


```js
// objects are collections of properties. Properties are key-value pairs
let city = {
    name: "Chicago",
    state: "Illinois",
    area: 234.21,
    nickname: "Second City"
};

// to access a property from a JavaScript object, there are two options
// 1) Bracket notation, similar to python
console.log(city['name']); // output: "Chicago"

// 2) Dot notation (the preferred convention in JavaScript)
console.log(city.state); // output: "Illinois"

// properties can be overwritten by assigning a new value
city.nickname = "The Windy City";
console.log(city);

// to add a property to an existing object, simply assign a value to a new key
city.population = 2695598;
console.log(city);
```

# Variables 
```js
// JavaScript Variables work a lot like Python variables, but they should be initialized with the `let` keyword.

// variables in JavaScript can be assigned string values...
let name = "Homer Simpson";

// ...boolean values...
let isEmployed = true;

// ...numerical values...
let age = 39;
let hourlyWage = 11.99;

// ...or expressions using other variables.
let dailyWage = hourlyWage * 8;
let weeklyWage = dailyWage * 5;

console.log('Hello JavaScript World!');
console.log('We use console.log() to print in JavaScript');
console.log('Why? Because the print() function will try to send the page to your printer!');
console.log(`Did you know that ${name} is ${age} years old and makes $${weeklyWage} per week?`);

// we can also define constant variables with the `const` keyword. This tells JavaScript that the variable can't
// be assigned a new value

const pi = 3.14159265358979;

console.log(`The value of pi is approximately ${pi}, and always will be!`);

pi = 3; // this will give an Uncaught TypeError: Assignment to constant variable.

// JavaScript Objects work a lot like Python dictionaries
let homer = {
  name: "Homer Jay Simpson",
  age: 39
};

let marge = {
  name: "Marjorie Jacqueline Simpson",
  age: 34
};

let bart = {
  name: "Bartholomew JoJo Simpson",
  age: 10
};

let lisa = {
  name: "Lisa Marie Simpson",
  age: 10
};

let maggie = {
  name: "Margaret Simpson",
  age: 1
};

// JavaScript Arrays are a lot like Python lists

let simpsons = [homer, marge, bart, lisa, maggie];

console.log(simpsons);
```