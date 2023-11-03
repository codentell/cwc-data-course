+++
title = "04.   D3 Select 👩‍🎓👨‍🎓"
weight = 4
tags = ["plotly"] 
+++

# D3 Select

In this activity, you will use D3 to add a new row of data to a table.

## Instructions

* You may use the starter files `index.html` and `static/js/app.js` provided in the [Unsolved](Unsolved) folder.

* Use D3 to:

  * Convert the Bootstrap table into a striped table.

  * Select the table body and append a new row and cells for the new student name and grade.

* If you have time, try adapting your solution to complete the bonus.

  * Loop through a list of students and create a new row per item.

## Hint

Review [Bootstrap Striped Tables](http://getbootstrap.com/docs/3.3/css/#table-striped).

---


## ✅ Solutions
{{%expand "Solutions Click Here" %}}
### index.html
```js
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Document</title>
  <script src="https://d3js.org/d3.v7.min.js"></script>
  <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u"
    crossorigin="anonymous">
</head>

<body>

  <div class="container">
    <div class="row">
      <div class="col-md-12">
        <!-- Student Grades -->
        <table class="grades table">
          <thead>
            <tr>
              <th>Name</th>
              <th>Grade</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td>Malcolm</td>
              <td>80</td>
            </tr>
            <tr>
              <td>Zoe</td>
              <td>85</td>
            </tr>
            <tr>
              <td>Kaylee</td>
              <td>99</td>
            </tr>
            <tr>
              <td>Simon</td>
              <td>99</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>


</body>
<script src="static/js/app.js"></script>

</html>
```


### app.js
```js
// The new student and grade to add to the table
let newGrade = ["Wash", 79];

// Use D3 to select the table
let table = d3.select("table");

// Use D3 to create a bootstrap striped table
// http://getbootstrap.com/docs/3.3/css/#table-striped
table.classed("table-striped", true);

// Use D3 to select the table body
let tbody = d3.select("tbody");

// Append one table row `tr` to the table body
let row = tbody.append("tr");

// Append one cell for the student name
row.append("td").text(newGrade[0]);

// Append one cell for the student grade
row.append("td").text(newGrade[1]);
```
{{% /expand%}}

