+++
title = "10.  Creating Functions 👩‍🎓👨‍🎓"
weight = 10
tags = ["plotly"] 
+++

# Statistical Functions

In this activity, you'll create functions that will calculate the mean, variance, and standard deviation of a dataset.

## Instructions

* Using the movie array provided in the `starter code file`, create functions that will return statistical values from any given array of data.

  * `movieScore = [4.4, 3.3, 5.9, 8.8, 1.2, 5.2, 7.4, 7.5, 7.2, 9.7, 4.2, 6.9]`

* Create functions that will find the following:

  * Mean
  * Variance
  * Standard deviation

* Each function should `console.log` both the name of the statistic used and its value. For example, "The Mean is: 33.3".

* The functions should be able to take any array of numbers and return the statistical value.

* After you have the functions working with the movie dataset, run them on the following additional data points:

  * `monthlyAvgRainFall = [3.03, 2.48, 3.23, 3.15, 4.13, 3.23]`
  * `mileRunTimes = [5.06, 4.54, 5.56, 4.40, 7.10]`

## Hint

* Remember to open your `index.html` in Chrome and check the DevTools console as you proceed.

* Use the JavaScript Math library to handle calculations needing exponents or square roots.

* If you want to review how to calculate variance and standard deviation, see the following pages:

  * [Variance](https://stats.stackexchange.com/questions/212650/variance-explanation)
  * [Standard Deviation](https://www.mathsisfun.com/data/standard-deviation.html)

---


## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```javascript
/ Array of movie ratings
let movieScore = [4.4, 3.3, 5.9, 8.8, 1.2, 5.2, 7.4, 7.5, 7.2, 9.7, 4.2, 6.9];

// Mean is the average of all the values.
function mean(arr) {
  let total = 0;
  for (let i = 0; i < arr.length; i++) {
    total += arr[i];
  }
  let meanValue = total / arr.length;

  return meanValue;
}

// Variance can be found by subtracting the mean from each number in the data set,
// squaring the result, and then averaging the square differences.
function variance(arr) {
  let meanValue = mean(arr);
  let total = 0;

  for (let i = 0; i < arr.length; i++) {
    total += (arr[i] - meanValue) ** 2;
  }
  let varianceValue = total / arr.length;
  return varianceValue;
}


// Standard deviation is the square root of the variance
function standardDeviation(arr) {
  let varianceValue = variance(arr);
  let standardDeviationValue = Math.sqrt(varianceValue);

  return standardDeviationValue;
}

// Print to the console the Movie Statistical Analysis
console.log("Movie Statistical Analysis");
console.log("--------------------------");
console.log(`The mean is : ${mean(movieScore)}`);
console.log(`The variance is : ${variance(movieScore)}`);
console.log(`The standard deviation is : ${standardDeviation(movieScore)}`);
console.log("");

// Print to the console the Rainfall Statistical Analysis
let monthlyAvgRainFall = [3.03, 2.48, 3.23, 3.15, 4.13, 3.23];
console.log("Rainfall Statistical Analysis");
console.log("--------------------------");
console.log(`The mean is : ${mean(monthlyAvgRainFall)}`);
console.log(`The variance is : ${variance(monthlyAvgRainFall)}`);
console.log(`The standard deviation is : ${standardDeviation(monthlyAvgRainFall)}`);
console.log("");

// Print to the console the Running Statistical Analysis
let mileRuns = [5.06, 4.54, 5.56, 4.40, 7.10];
console.log("Mile Run Statistical Analysis");
console.log("--------------------------");
console.log(`The mean is : ${mean(mileRuns)}`);
console.log(`The variance is : ${variance(mileRuns)}`);
console.log(`The standard deviation is : ${standardDeviation(mileRuns)}`);
console.log("");
```
{{% /expand%}}