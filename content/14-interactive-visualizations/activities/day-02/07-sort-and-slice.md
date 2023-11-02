+++
title = "07.  Sort and Slice 👩‍🏫🧑‍🏫"
weight = 7
tags = ["plotly"] 
+++


## slicing 
```js
// Array of names
let names = ["Jane", "John", "Jimbo", "Jedediah"];

// Slice the first two names
let left = names.slice(0, 2);
// Returns elements at index position 0 and 1, but not 2.
console.log(left);

// Slice the last two names
let right = names.slice(2, 4);
// Returns elements at index position 2 and 3, but not 4.
console.log(right);
```

## sorting
```js
// Sort the array in descending order
let numArray = [1, 2, 3];
numArray.sort(function compareFunction(firstNum, secondNum) {
  // resulting order is (3, 2, 1)
  return secondNum - firstNum;
});

// Returns [3, 2, 1]
console.log(numArray);

// Sort the array in ascending order
let numArray2 = [3, 2, 1];
numArray2.sort(function compareFunction(firstNum, secondNum) {
  // resulting order is (1, 2, 3)
  return firstNum - secondNum;
});

// Returns [1, 2, 3]
console.log(numArray2);

// Sort the array in ascending order, using an arrow function
let numArray3 = [3, 2, 1];
numArray3.sort((firstNum, secondNum) => firstNum - secondNum);
console.log(numArray3);

// Reverse the array
let numArray4 = [1, 2, 3];
numArray4.reverse()
console.log(numArray4);
```