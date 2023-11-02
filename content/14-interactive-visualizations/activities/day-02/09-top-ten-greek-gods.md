+++
title = "09.  Top 10 Greek Gods 👩‍🎓👨‍🎓"
weight = 8
tags = ["plotly"] 
+++


# Sorting and Slicing with Plotly

In this activity, you will sort, slice, and reverse the [data.js](Unsolved/data.js) dataset to build a horizontal bar chart of the top 10 Greek god search results.

## Instructions

* You may use the starter files `index.html` and `plots.js` provided in the [Unsolved](Unsolved) folder.

* Sort the data by Greek search results in descending order.

* Slice the first 10 objects of the array for the plot.

* Reverse the array to compensate for Plotly's horizontal bar chart defaults.

* Create a Plotly bar chart with names on the x-axis and search results on the y-axis. For example:

![Greek Top Ten](Images/greek_top_ten.png)

## Hint

Review the [Plotly documentation](https://plotly.com/javascript/horizontal-bar-charts/) to research how to make a bar chart horizontal.

## Reference

Search results retrieved on December 1, 2021 from https://www.google.com.

---



## ✅ Solutions
{{%expand "Solutions Click Here" %}}
### index.html
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Top Greek gods</title>
    <script src="https://cdn.plot.ly/plotly-latest.min.js"></script>
</head>
<body>
    <div id="plot"></div>
    <script src="data.js"></script>
    <script src="plots.js"></script>
</body>
</html>
```
### plot.js
```js
// Sort the data by Greek search results descending
let sortedByGreekSearch = searchResults.sort((a, b) => b.greekSearchResults - a.greekSearchResults);

// Slice the first 10 objects for plotting
let slicedData = sortedByGreekSearch.slice(0, 10);

// Reverse the array to accommodate Plotly's defaults
slicedData.reverse();

// Trace1 for the Greek Data
let trace1 = {
  x: slicedData.map(object => object.greekSearchResults),
  y: slicedData.map(object => object.greekName),
  text: slicedData.map(object => object.greekName),
  name: "Greek",
  type: "bar",
  orientation: "h"
};

// Data array
let data = [trace1];

// Apply a title to the layout
let layout = {
  title: "Greek gods search results",
  margin: {
    l: 100,
    r: 100,
    t: 100,
    b: 100
  }
};

// Render the plot to the div tag with id "plot"
Plotly.newPlot("plot", data, layout);
```
{{% /expand%}}