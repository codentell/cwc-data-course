+++
title = "01. Intro to D3  👩‍🏫🧑‍🏫 "
weight = 1
tags = ["plotly"] 
+++

### demo.js
```js
const url = "https://api.spacexdata.com/v4/launchpads";

// Promise Pending
const dataPromise = d3.json(url);
console.log("Data Promise: ", dataPromise);

// Fetch the JSON data and console log it
d3.json(url).then(function(data) {
  console.log(data);
});
```