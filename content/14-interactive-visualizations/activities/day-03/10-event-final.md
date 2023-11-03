+++
title = "10. Event Final  👩‍🎓👨‍🎓 "
weight = 10
tags = ["plotly"] 
+++

# Government Expenditure

In this activity, you will create a dynamic pie chart using Plotly that displays 2017 data on select categories of government spending.

## Instructions

* You may use the starter files `index.html` and `plots.js` provided in the [Unsolved](Unsolved) folder.

* Using the data in `data.js`, create a pie chart that meets the following criteria:

  * Displays a default dataset.

  * Contains a dropdown menu listing six countries: Australia, Brazil, United Kingdom, Mexico, Singapore, and South Africa.

  * When we select an option from the dropdown menu, our code should retyle the chart to reflect the new data.

  * See the following image for reference.

    ![Images/pie01.png](Images/pie01.png)

## Hint

* Log the provided variables to the console to determine their use in creating the trace object.

* For information about creating pie charts with Plotly, refer to the [Plotly documentation](https://plotly.com/javascript/pie-charts/).

## References

World Bank national accounts data, and OECD National Accounts data files (2021). General government final consumption expenditure (% of GDP). https://data.worldbank.org/indicator/NE.CON.GOVT.ZS

World Health Organization Global Health Expenditure database (apps.who.int/nha/database) via The World Bank (2021). Domestic general government health expenditure (% of GDP). https://data.worldbank.org/indicator/SH.XPD.GHED.GD.ZS

UNESCO Institute for Statistics (uis.unesco.org) via The World Bank (2021). Government expenditure on education, total (% of GDP). https://data.worldbank.org/indicator/SE.XPD.TOTL.GD.ZS

UNESCO Institute for Statistics (uis.unesco.org) via The World Bank (2021). Research and development expenditure. https://data.worldbank.org/indicator/GB.XPD.RSDV.GD.ZS

World Bank national accounts data, and OECD National Accounts data files (2021). GDP (current US$). https://data.worldbank.org/indicator/NY.GDP.MKTP.CD


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
    <title>Dropdown Events</title>
    <script src="https://d3js.org/d3.v7.min.js"></script>
    <script src="https://cdn.plot.ly/plotly-latest.min.js"></script>
</head>
<body>
    <h2>Government Spending</h2>
    <p>Numbers on hover reflect the rounded USD (in millions) spent in each category in 2017.</p>
        <!-- Your code here -->
    <div id="pie"></div>

    <p>Data Sources:<br />
        <ul>
            <li>
                <a href="https://data.worldbank.org/indicator/NE.CON.GOVT.ZS">General government final consumption expenditure (% of GDP)</a>
            </li>
            <li>
                <a href="https://data.worldbank.org/indicator/SE.XPD.TOTL.GD.ZS">Government expenditure on education, total (% of GDP)</a>
            </li>
            <li>
                <a href="https://data.worldbank.org/indicator/SH.XPD.GHED.GD.ZS">Domestic general government health expenditure (% of GDP)</a>
            </li>
            <li>
                <a href="https://data.worldbank.org/indicator/GB.XPD.RSDV.GD.ZS">Research and development expenditure (% of GDP)</a>
            </li>
            <li>
                <a href="https://data.worldbank.org/indicator/NY.GDP.MKTP.CD">GDP (current US$)</a>
            </li>
            </ul>
    </p>
    <script src="data.js"></script>
    <script src="plots.js"></script>
</body>
</html>
```

### plot.js
```js
// Create an array of each country's numbers
let australia = Object.values(data.australia);
let brazil = Object.values(data.brazil);
let uk = Object.values(data.uk);
let mexico = Object.values(data.mexico);
let singapore = Object.values(data.singapore);
let southAfrica = Object.values(data.southAfrica);

// Create an array of category labels
let labels = Object.keys(data.australia);

// Display the default plot
function init() {
  let data = [{
    values: australia,
    labels: labels,
    type: "pie"
  }];

  let layout = {
    height: 600,
    width: 800
  };

  Plotly.newPlot("pie", data, layout);
}

// On change to the DOM, call getData()
d3.selectAll("#selDataset").on("change", getData);

// Function called by DOM changes
function getData() {
  let dropdownMenu = d3.select("#selDataset");
  // Assign the value of the dropdown menu option to a letiable
  let dataset = dropdownMenu.property("value");
  // Initialize an empty array for the country's data
  let data = [];

  if (dataset == 'australia') {
      data = australia;
  }
  else if (dataset == 'brazil') {
      data = brazil;
  }
  else if (dataset == 'uk') {
      data = uk;
  }
  else if (dataset == 'mexico') {
    data = mexico;
  }
  else if (dataset == 'singapore') {
      data = singapore;
  }
  else if (dataset == 'southAfrica') {
    data = southAfrica;
  }
// Call function to update the chart
  updatePlotly(data);
}

// Update the restyled plot's values
function updatePlotly(newdata) {
  Plotly.restyle("pie", "values", [newdata]);
}

init();
```
{{% /expand%}}