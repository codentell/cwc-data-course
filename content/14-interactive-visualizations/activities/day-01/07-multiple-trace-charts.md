+++
title = "07. Multiple Trace Charts 👩‍🏫🧑‍🏫"
weight = 7
tags = ["plotly"] 
+++

### index.html
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Multi-Trace</title>
  <script src="https://cdn.plot.ly/plotly-latest.min.js"></script>
</head>
<body>
  <div id="plot"></div>
  <script src="plots.js"></script>
</body>
</html>
```

### plot.js
```js
// Create our first trace
let trace1 = {
  x: [0, 1, 2, 3, 4, 5],
  y: [0, 5, 10, 15, 20, 25],
  type: "bar"
};

// Create our second trace
let trace2 = {
  x: [0, 1, 2, 3, 4, 5],
  y: [0, 1, 4, 9, 16, 25],
  type: "scatter"
};

// The data array consists of both traces
let data = [trace1, trace2];

// Note that we omitted the layout object this time
// This will use default parameters for the layout
Plotly.newPlot("plot", data);
```