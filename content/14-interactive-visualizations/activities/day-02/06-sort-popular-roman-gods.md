+++
title = "06.  Sort Popular Roman Gods 👩‍🎓👨‍🎓"
weight = 6
tags = ["plotly"] 
+++

# Filtering with Plotly

In this activity, you will create an array of popular Roman god search results by using the `filter` function with the `data.js`dataset.

## Instructions

* You may use the starter files `index.html` and `plots.js` provided in the `Unsolved` folder.

* Create a custom function to return Roman gods with more than 100 million search results.

* Create an array of Roman god names from the filtered data.

* Create an array of Roman god search results from the filtered data.

* Create a Plotly bar chart with names on the x-axis and search results on the y-axis. For example:

![Roman Filtering](../images/roman_filter.png)

## Hint

Open the console to see the dataset stored in the variable `data`.

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
    <title>Roman Results</title>
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
console.log(searchResults);

// Create a custom function to return Roman gods with more than 1 million search results
function popular(roman) {
  return roman.romanSearchResults > 1000000;
}

// Call the custom function with filter()
let popularRomans = searchResults.filter(popular);

// Trace for the Roman Data
let trace1 = {
    x: popularRomans.map(row => row.romanName),
    y: popularRomans.map(row => row.romanSearchResults),
    type: "bar"
};

// Data trace array
let data = [trace1];

// Apply a title to the layout
let layout = {
  title: "Popular Roman gods search results"
};

// Render the plot to the div tag with id "plot"
Plotly.newPlot("plot", data, layout);
```
{{% /expand%}}