+++
title = "08.  Sort and Slice 👩‍🎓👨‍🎓"
weight = 8
tags = ["plotly"] 
+++

# Sorting and Slicing

In this activity you will sort, slice, and reverse the following array:

```javascript
numArray = [9.9, 6.1, 17.1, 22.7, 4.6, 8.7, 7.2];
```

## Instructions

* Use the starter files `index.html` and `sliceSort.js` provided in the [Unsolved](Unsolved) folder.

* Sort the array in descending order and assign the results to a variable.

* Sort the array in ascending order using an arrow function.

* Slice the first five elements of the sorted ascending array and assign them to a variable.

* Reverse the array order.

---


## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```js
// An unsorted array
let numArray = [9.9, 6.1, 17.1, 22.7, 4.6, 8.7, 7.2];

// Sort the array in descending order and assign the results to a variable
let sorted = numArray.sort(function sortFunction(a, b) {
  return b - a;
});
console.log(sorted);

// Reverse the array order
sorted.reverse();
console.log(sorted);

// Slice the first five elements of the sorted array and assign to a variable
let sliced = sorted.slice(0, 5);
console.log(sliced);
```
{{% /expand%}}