+++
title = "07. Country GDP 👩‍🎓👨‍🎓 "
weight = 7
tags = ["map"] 
+++

# Country GDP Per Capita

In this activity, we'll add a circle for each of the top 20 countries according to their GDP per capita in USD for 2020.

## Instructions

* Use the starter files `index.html`, `logic.js`, and `style.css` provided in the [Unsolved](Unsolved) folder.

* Add your code to [logic.js](Unsolved/logic.js) to render the following:

    * A circle for each country in the dataset.
    * A radius size that you determine from the country's GDP per capita.
    * A color for each circle that you determine as follows:

      * For countries with more than 100,000 GDP per capita, set the color of the circle to yellow.
      * For countries with more than 75,000 GDP per capita, set the color of the circle to blue.
      * For countries with more than 50,000 GDP per capita, set the color of the circle to green.
      * Render the remaining country circles in violet.

* Make sure that each vector layer has a popup containing the country's name and GDP per capita.

## Hint

* Universally adjust the radius for better visuals.

* Refer to the [Leaflet documentation for Path options](https://leafletjs.com/reference.html#path-option) if you get stuck creating vector layers.

## References

[Google Developer Guides countries.csv](https://developers.google.com/public-data/docs/canonical/countries_csv), licensed under [CC-BY 4.0](https://creativecommons.org/licenses/by/4.0/).

The World Bank (2022), GDP per capita (current US$), https://data.worldbank.org/indicator/NY.GDP.PCAP.CD, licensed under [CC-BY 4.0](https://creativecommons.org/licenses/by/4.0/).

---
## ✅ Solutions
{{%expand "Solutions Click Here" %}}
### index.html
```html
<!DOCTYPE html>
<html lang="en">

<head>
  <meta charset="utf-8">
  <title>Basic Map</title>

  <!-- Leaflet CSS -->
  <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css"
    integrity="sha256-p4NxAoJBhIIN+hmNHrzRCf9tD/miZyoHS5obTRR9BMY="
    crossorigin="" />

  <!-- Leaflet JavaScript code -->
  <script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"
    integrity="sha256-20nQCchB9co0qIjJZRGuk2/Z9VM+kNiyxNV1lvTlZBo="
    crossorigin=""></script>

  <!-- Our CSS -->
  <link rel="stylesheet" type="text/css" href="style.css">
</head>

<body>
  <!-- The div where we'll insert our map -->
  <div id="map"></div>

  <!-- JavaScript files -->
  <script type="text/javascript" src="data.js"></script>
  <script type="text/javascript" src="logic.js"></script>
</body>

</html>
```

### logic.js
```js
// Create a map object.
let myMap = L.map("map", {
  center: [15.5994, -28.6731],
  zoom: 3
});

// Add a tile layer.
L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
}).addTo(myMap);


// Loop through the countries array, and create one marker for each country object.
for (let i = 0; i < countries.length; i++) {

  // Conditionals for country gdp_pc
  let color = "";
  if (countries[i].gdp_pc > 100000) {
    color = "yellow";
  }
  else if (countries[i].gdp_pc > 75000) {
    color = "blue";
  }
  else if (countries[i].gdp_pc > 50000) {
    color = "green";
  }
  else {
    color = "violet";
  }

  // Add circles to the map.
  L.circle(countries[i].location, {
    fillOpacity: 0.75,
    color: "white",
    fillColor: color,
    // Adjust the radius.
    radius: Math.sqrt(countries[i].gdp_pc) * 500
  }).bindPopup(`<h1>${countries[i].name}</h1> <hr> <h3>GDP Per Capita (USD): ${countries[i].gdp_pc}</h3>`).addTo(myMap);
}
```
### style.css
```css
/* Remove the default margin and padding from the body. */
body {
  padding: 0;
  margin: 0;
}

/* Set map, body, and html to 100% of the screen size. */
#map,
body,
html {
  height: 100%;
}

h1 {
  text-align: center;
}
```

{{% /expand%}}

