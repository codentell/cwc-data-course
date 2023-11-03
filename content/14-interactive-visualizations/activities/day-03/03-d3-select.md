+++
title = "03. D3 Select  👩‍🏫🧑‍🏫 "
weight = 3
tags = ["plotly"] 
+++

### index.js
```js
// Select the text of an HTML element
let text1 = d3.select(".text1").text();
console.log("text1 says: ", text1);

let text2 = d3.select("#text2").text();
console.log("text2 says: ", text2);

// Modify the text of an HTML element
d3.select(".text1").text("Hey, I changed this!");

// Capture the HTML of a selection
let myLink = d3.select(".my-link").html();
console.log("my-link: ", myLink);

// Select an element's child element
// An object is returned
let myLinkAnchor = d3.select(".my-link>a");
console.log(myLinkAnchor);

// Capture the child element's href attribute
let myLinkAnchorAttribute = myLinkAnchor.attr("href");
console.log("myLinkAnchorAttribute: " + myLinkAnchorAttribute);

// Change an element's attribute
myLinkAnchor.attr("href", "https://python.org");

// Use chaining to join methods
d3.select(".my-link>a").attr("href", "https://nytimes.com").text("Now this is a link to the NYT!!");

// Select all list items, then change their font color
d3.selectAll("li").style("color", "blue");

// Create a new element
let li1 = d3.select("ul").append("li");
li1.text("A new item has been added!");

// Use chaining to create a new element and set its text
let li2 = d3.select("ul").append("li").text("Another new item!");
```

### index.html
```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>D3 Select</title>
  <script src="https://d3js.org/d3.v7.min.js"></script>

</head>

<body>
  <h1>This is an H1</h1>
  <div class="text1">This div has a class</div>
  <div id="text2">This div has an id</div>
  <div class="my-link">
    <a href="https://github.com/d3/d3-selection">D3 Home</a>
  </div>

  <div class="deeplink">
    <div class="outer">
      <div class="inner">
        <a href="https://github.com/d3/d3-selection">D3 Select</a>
      </div>
    </div>
  </div>

  <ul>
    <li>Item 1</li>
    <li>Item 2</li>
    <li>Item 3</li>
  </ul>
</body>
<script src="static/js/index.js"></script>

</html>
```