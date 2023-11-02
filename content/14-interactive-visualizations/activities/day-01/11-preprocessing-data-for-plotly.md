+++
title = "11.  Preprocessing Data for Plotly 👩‍🎓👨‍🎓"
weight = 11
tags = ["plotly"] 
+++

# Preprocessing Data with Functions for Plotly

In this activity, you will create functions that preprocess films from the Pagila database and create a bar chart of average values by content rating.

## Instructions

* Using the `films.js`array of movies from the Pagila database, and the starter file `plots.js`, create a function that will calculate averages by content rating (i.e., G, PG, PG-13, and R) of one of the following metrics:

  * Rental rate (`rental_rate`)
  * Length (`length`)
  * Replacement cost (`replacement_cost`)

* With the calculated averages, create a function that will generate a Plotly bar chart with the average values.

* After you have the functions working, try changing the metric to update the bar chart.

* Remember to use `index.html`] to view your bar chart as you progress with your code.

## Hint

You will need to use conditionals, loops, and functions to complete this activity. You may find it helpful to review the following two activities:

* 06-Stu_Iteration_and_Conditionals

* 10-Stu_Creating-Functions

## Reference

Devrim Gündüz (2021) _Pagila_. Retrieved from: [https://github.com/devrimgunduz/pagila](https://github.com/devrimgunduz/pagila)

---

## ✅ Solutions
{{%expand "Solutions Click Here" %}}
### index.html
```js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Films</title>
    <script src="https://cdn.plot.ly/plotly-latest.min.js"></script>
</head>
<body>
    <div id="plot"></div>
    <script src="films.js"></script>
    <script src="plots.js"></script>
    <!-- <script src="refactored.js"></script> -->
</body>
</html>
```
### plot.js
```js
et ratings = ['G', 'PG', 'PG-13', 'R'];

// Metric variable for function inputs
let metric = "length";
// let metric = "rental_rate";
// let metric = "replacement_cost";

// Create a function to calculate the annual average of a metric 
function metricMean(films, rating, metric) {
  // Initialize variables to increment
  let count = 0;
  let total = 0;
  
  // Loop through the array of films
  for (let i = 0; i < films.length; i++) {
    
    // Store the film at index `i` for evaluation
    row = films[i];

    // Compare `rating` value to `rating` provided as argument
    if (row.rating == rating){

      // Increment by `metric` argument value
      total += row[metric];
      // Increment by one
      count += 1;
    }
  }
  
  // Calculate the average value
  let meanValue = total / count;

  // Return the calcuated average
  return meanValue;
}

// Invoke the metric average function
// Calculate the average for each rating individually
let metricG = metricMean(films, "G", metric);
let metricPG = metricMean(films, "PG", metric);
let metricPG_13 = metricMean(films, "PG-13", metric);
let metricR = metricMean(films, "R", metric);

// Creat an array of rating averages
let metricArray = [metricG, metricPG, metricPG_13, metricR];

// Create a function to plot the rating average metric results
function plotMetric(metricArray, ratings, metric){

  let trace1 = {
    x: ratings,
    y: metricArray,
    type: "bar"
  }

  let data = [trace1]

  // Pass metric to chart title
  let layout = {
    title: `Pagila Rental Films Average ${metric}`
  };

  Plotly.newPlot("plot", data, layout);
}

// Invoke the plot creating function
plotMetric(metricArray, ratings, metric);
```
### refactored.js
```js
let ratings = ['G', 'PG', 'PG-13', 'R'];

// Metric variable for function inputs
let metric = "length";
// let metric = "rental_rate";
// let metric = "replacement_cost";

// Function to calculate and plot the average of a metric by rating
function plotMetric(films, ratings, metric) {
  // Initialize an array to hold metric averages
  let metricArray = [];

  // Loop through the array of ratings
  for (let i =0; i < ratings.length; i++) {
    // Store the rating at index `i` for evaluation
    rating = ratings[i];

    // Initialize variables to increment
    let count = 0;
    let total = 0;

    // Loop through the array of films
    for (let j = 0; j < films.length; j++) {
      // Store the film at index `j` for evaluation
      row = films[j];

      // Compare `rating` value to `rating` provided as argument
      if (row.rating == rating){

        // Increment by `metric` argument value
        total += row[metric];
        // Increment by one
        count += 1;
      }
    }
    // Calculate the average value
    let meanValue = total / count;

    // Append the average value to the  `metricArray`
    metricArray.push(meanValue);
  }
  
  // Assign `ratings` array argument to `x`
  // Assign the `metricArray` with averages for each rating to `y`
  let trace1 = {
    x: ratings,
    y: metricArray,
    type: "bar"
  }

  let data = [trace1];

  // Pass metric to chart title
  let layout = {
    title: `Pagila Rental Films Average ${metric}`
  };

  Plotly.newPlot("plot", data, layout);
}

// Invoke the plotting function
plotMetric(films, ratings, metric);
```
{{% /expand%}}

