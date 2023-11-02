+++
title = "03.  Greek Mapping 👩‍🎓👨‍🎓"
weight = 3
tags = ["plotly"] 
+++

# Mapping with Plotly

In this activity, you will create an array of Greek god search results using the `map` function with the `data.js`dataset.

## Instructions

* You may use the starter files `index.html` and `plots.js` provided in the `Unsolved`

* Create an array of Greek god names from the `data.js` dataset.

* Create an array of Greek god search results from the `data.js` dataset.

* Create a Plotly bar chart with names on the x-axis and search results on the y-axis, like this:

![Greek Mapping](../images/greek_map.png)

* Include a title on the plot.

## Hint

Open the console to see the dataset stored in the variable `data`.

## Reference

Search results retrieved on December 1, 2021 from https://www.google.com.

---


## ✅ Solutions
{{%expand "Solutions Click Here" %}}

```javascript
console.log(searchResults);

// Greek god names
let names = searchResults.map(function (row){
  return row.greekName
});

// Trace for the Greek Data
let trace1 = {
    x: searchResults.map(row => row.greekName),
    y: searchResults.map(row => row.greekSearchResults),
    type: "bar"
  };

// Data trace array
let data = [trace1];

// Apply a title to the layout
let layout = {
  title: "Greek gods search results"
};

// Render the plot to the div tag with id "plot"
Plotly.newPlot("plot", data, layout);
```
{{% /expand%}}