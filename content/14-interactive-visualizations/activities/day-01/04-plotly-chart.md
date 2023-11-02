+++
title = "04.  Plotly chart 👩‍🎓👨‍🎓"
weight = 4
tags = ["plotly"] 
+++

# My First Plotly Chart

In this activity, you will create your first Plotly bar chart by using the variables you created in the previous activity. Your chart will show three books you've read as well as the number of times you've read them.

## Instructions

* In the `plots.js`file, copy the following variables you created from the previous activity:

    * `name`
    * `title`
    * `books`
    * `timesRead`

* In the Plotly `trace1` object, assign the correct `x` and `y` values for a vertical bar chart.

* Open the `index.html` file to see your first Plotly bar chart.

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
    <title>Basic Charts</title>
    <script src="https://cdn.plot.ly/plotly-latest.min.js"></script>
</head>
<body>
    <div id="plot"></div>
    <script src="plots.js"></script>
</body>
</html>
```
### plot.js
```javascript
let name = 'Travis Taylor'

let title = `${name}'s First Plotly Chart`

let books = ["The Visual Display of Quantitative Information", "Automate the Boring Stuff", "Data Science from Scratch"]

let timesRead = [100, 50, 25]

let trace1 = {
  x: books,
  y: timesRead,
  type: 'bar'
};

let data = [trace1];

let layout = {
  title: title
};

Plotly.newPlot("plot", data, layout);
```
{{% /expand%}}