+++
title = "02.   D3 JSON 👩‍🎓👨‍🎓"
weight = 2
tags = ["plotly"] 
+++

# D3.json

In this activity, you will use D3.json to make API calls to SpaceX.

## Instructions

* You may use the starter files `index.html` and `demo.js` provided in the [Unsolved](Unsolved) folder.

* Use D3.json to make an API call and return the following:

  * Current information regarding the Roadster.

  * Information regarding all capsules.

## Hint

Review the [SpaceX API Docs](https://github.com/r-spacex/SpaceX-API/tree/master/docs#rspacex-api-docs).

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
  <title>Document</title>
</head>
<body>
  <h1>Open the console!</h1>
  <script src="https://d3js.org/d3.v7.min.js"></script>
  <script src="demo.js"></script>
</body>
</html>
```
### demo.js
```js
// Get the Roadster endpoint
const roadster = "https://api.spacexdata.com/v4/roadster";

// Fetch the JSON data and console log it
d3.json(roadster).then(function(data) {
  console.log(data);
});

// Get the capsules endpoint
const capsules = "https://api.spacexdata.com/v4/capsules";

// Fetch the JSON data and console log it
d3.json(capsules).then(function(data) {
  console.log(data);
});
```
{{% /expand%}}
