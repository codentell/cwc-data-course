+++
title = "08.  Multiple Trace charts 👩‍🎓👨‍🎓"
weight = 8
tags = ["plotly"] 
+++

# Greek vs. Roman Mythology

In this activity, you will compare search results between Greek and Roman mythology to determine whether the Greek or Roman name for the god is more popular.

![Gods Search Results](../images/plot.png)

## Instructions

Ancient Roman gods were often counterparts to or imports of Greek gods. For example, the Greek god Zeus became the Roman god Jupiter through an etymological transformation from Zeus to Zeus Pater ("Father Zeus") to Jupiter. (Classical Latin lacked a "J" consonant.)

In today's world, are these gods better known by their Roman names or Greek names?

Your task is to plot the number of search results for both Roman and Greek names, returned for each god, which will visually answer the previous question. To do so, follow these steps:

* Examine the data in `data.js`. Note the names of properties in each data object.

  * To accomplish this task, you will need to create two traces, one for Roman gods, and another for Greek gods. You may use the starter file `plots.js` for this.

* To define the data for each plot point in a trace, use a `for` loop on the dataset. For each trace:

  * For the x-axis, provide an array of the paired string of Greek and Roman god names, e.g., Amphitrite-Salacia.

  * For the y-axis, provide an array of search results for Greek and Roman god names in their separate traces.

* Open `index.html` in Chrome to view your plot.

## Reference

Search results figures retrieved on December 1, 2021 from https://www.google.com.

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
    <title>Greek vs Roman</title>
    <script src="https://cdn.plot.ly/plotly-latest.min.js"></script>
</head>
<body>
    <div id="plot"></div>
    <script src="data.js"></script>
    <script src="plots.js"></script>
</body>
</html>
```

###  plots.js
```javascript
// Initialized arrays
let names = []
let greekNames = []
let romanNames = []
let greekSearchResults = []
let romanSearchResults = []

// For loop to populate arrays
for (let i = 0; i < searchResults.length; i++) {
  row = searchResults[i];
  names.push(row.pair);
  greekNames.push(row.greekName);
  romanNames.push(row.romanName);
  greekSearchResults.push(row.greekSearchResults);
  romanSearchResults.push(row.romanSearchResults);
}

// Trace1 for the Greek Data
let trace1 = {
  x: names,
  y: greekSearchResults,
  text: greekNames,
  name: "Greek",
  type: "bar"
};

// Trace 2 for the Roman Data
let trace2 = {
  x: names,
  y: romanSearchResults,
  text: romanNames,
  name: "Roman",
  type: "bar"
};

// Create data array
let data = [trace1, trace2];

// Apply a title to the layout
let layout = {
  title: "Greek vs Roman gods search results",
  barmode: "group",
  // Include margins in the layout so the x-tick labels display correctly
  margin: {
    l: 50,
    r: 50,
    b: 200,
    t: 50,
    pad: 4
  }
};

// Render the plot to the div tag with id "plot"
Plotly.newPlot("plot", data, layout);
```
{{% /expand%}}
