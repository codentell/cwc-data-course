+++
title = "07. This  👩‍🏫🧑‍🏫 "
weight = 7
tags = ["plotly"] 
+++

### index.html
```html
<!DOCTYPE html>

<html lang="en-us">

<head>
  <meta charset="UTF-8">
  <title>What is `this`?</title>
</head>

<body>
  <button id="button">Click Me</button>
  <button id="button">Click Me 2</button>
  <ul>
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
  </ul>
  <script src="https://d3js.org/d3.v7.min.js"></script>
  <script src="app.js"></script>
</body>

</html>
```

### app.js
```js
d3.selectAll("button").on("click", function() {
  // What will be logged out? What is `this` in this case?
  console.log(this);
  // Answer: It will console log the `button` element.
});

d3.selectAll("li").on("click", function() {
  // you can select the element just like any other selection
  let listItem = d3.select(this);
  listItem.style("color", "blue");

  let listItemText = listItem.text();
  console.log(listItemText);
});
```

