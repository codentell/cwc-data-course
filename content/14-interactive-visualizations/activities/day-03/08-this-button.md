+++
title = "08. This Button  👩‍🎓👨‍🎓"
weight = 8
tags = ["plotly"] 
+++

# Vote Star Wars

In this activity, you will use D3 and the `this` keyword to create a single-click handler for upvotes and downvotes.

## Instructions

Use the starter files `index.html`, `static/js/app.js`, and `static/css/style.css` provided in the [Unsolved](Unsolved) folder, and do the following:

* Use D3 to select both the `upvote` and `downvote` buttons on the page in a single D3 object.

* Make sure the click handler does the following:
  * Select the current vote count from the `<h3>` tag.

  * Use the `this` keyword to reference the correct button in order to utilize that button’s `value` attribute.

  * Increment or decrement the count, using the button’s `value` attribute.

  * Update the vote count `<h3>` tag using D3.

## Hints

* Don't forget to use the `.on` function to attach the click handler to the buttons.

* Check the `value` attribute on the buttons in the `index.html` file to decide how you might use the value.

* You will need to use `parseInt` to convert the `<h3>` vote count to a number before you can add or subtract from it.

---

## ✅ Solutions
{{%expand "Solutions Click Here" %}}

### index.html
```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>Star Wars</title>
    <script src="https://d3js.org/d3.v7.min.js"></script>
    <link
      rel="stylesheet"
      href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css"
      integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u"
      crossorigin="anonymous"
    />
    <link rel="stylesheet" href="static/css/style.css" />
    <style>
      body {
        background-color: black;
      }

      .jumbotron {
        background: #ba9766 linear-gradient(#ba9766, #fae6ca);
        background-size: 100% 100%;
        overflow: auto;
        width: 100%;
        height: 100%;
        margin: 0;
        padding: 0;
      }
    </style>
  </head>

  <body>
    <div class="container">
      <div class="jumbotron" style="text-align:center">
        <h2>Vote for your favorite star wars episode</h2>
        <h3>Episode: <span class="star-wars"></span></h3>
        <div class="row">
          <div class="col-md-offset-4 col-md-4"><h3 class="counter">0</h3></div>
        </div>
        <div class="row">
          <div class="col-md-offset-4 col-md-4">
            <button type="button" class="btn btn-default btn-lg upvote" value=1>
              <span class="glyphicon glyphicon-circle-arrow-up"></span> Upvote
            </button>
            <button type="button" class="btn btn-default btn-lg downvote" value=-1>
              <span class="glyphicon glyphicon-circle-arrow-down"></span> Downvote
            </button>
          </div>
        </div>
      </div>
    </div>

    <div id="stars"></div>
    <div id="stars2"></div>
    <div id="stars3"></div>

    <script src="static/js/app.js"></script>
  </body>
</html>
```

### app.js
```js
// Randomly select an episode number for Star Wars
let text = d3.select(".star-wars")
  .text(Math.floor(Math.random() * 9) + 1);

// Select the counter h3 element
let counter = d3.select(".counter");

// Select the buttons and use D3 `.on` to attach a click handler
d3.selectAll("button").on("click", function() {

  // Create a variable for the button selected
  let button = d3.select(this);

  // Create a variable to hold the increment or decrement
  let vote = parseInt(button.attr('value'))

  // Create a variable to hold the current counter value
  let currentCount = parseInt(counter.text())

  // Update the counter value
  currentCount += vote;

  // Set the counter h3 text to the new count
  counter.text(currentCount);

});
```

{{% /expand%}}
