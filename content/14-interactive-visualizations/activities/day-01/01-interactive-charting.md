+++
title = "01. Interactive Charting 👩‍🏫🧑‍🏫"
weight = 1
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
    <title>Basic Charts</title>
    <script src="https://cdn.plot.ly/plotly-latest.min.js"></script>
</head>
<body>
    <div id="plot"></div>
    <script>
        let xData = [1, 2, 3, 4, 5];
        let yData = [1, 2, 4, 8, 16];
    </script>
    <script src="plots.js"></script>
</body>
</html>
```

### plot.js
```js
let trace1 = {
  x: xData,
  y: yData
};

let data = [trace1];

let layout = {
  title: "A Plotly plot"
};

Plotly.newPlot("plot", data, layout);
```