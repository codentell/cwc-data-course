+++
title = "04. School District  👩‍🎓👨‍🎓 "
weight = 4
tags = ["map"] 
+++

# Choropleth Map of Florida Family Data

In this activity, you and a partner will create a choropleth map that depicts the number of employed people with school-aged children in Florida school districts.

## Background

* A **choropleth map** has areas that are shaded or patterned in proportion to the statistical variable that the map represents. It also provides a way to easily depict how a measurement varies across a geographical area. It does this by showing the level of variability within a region.

* You and your partner will use a plugin named [leaflet-choropleth](https://github.com/timwis/Leaflet-choropleth) to create this map. You can find the plugin in the `dist` folder of the repository.

* You'll work your way through this activity step by step with your partner. We'll review what everyone did for each step before moving to the next one.

## Instructions

This activity is broken into four steps, which include several sub-steps.

You will use the following starter files for this activity:

* [index.html](Unsolved/index.html)

* [static/js/logic.js](Unsolved/static/js/logic.js)

* [static/css/style.css](Unsolved/static/css/style.css)

### Step 1: Explore the Data

1. Get all the data with D3 and log it to the console.

2.  In Google Chrome, open `index.html, open DevTools, and then go to the Console tab.

3. Explore the data by using the console. Find where the data stores the estimated employed population with school-aged children (`DP03_16E`) for each feature.

  * Note that the amount of data is large, so it might take up to 30 seconds for it to load.

### Step 2: Download the Plugin

1. Download `choropleth.js` from the `leaflet-choropleth` repository and place it in your `js` folder.

2.  In your `index.html` file, uncomment the following line:

  * `<script type="text/javascript" src="static/js/choropleth.js"></script>`

### Step 3: Add Popups

1. Using the [leaflet-choropleth documentation](https://github.com/timwis/leaflet-choropleth) as a guide, create a new choropleth layer.

  * Change the `valueProperty` to the property that you want to base the map on.

  * Define an `onEachFeature` method that binds a popup containing the value of the feature to the layer. Display the school district and the estimated population count.

  * Though it's not required, you may wish to include additional data to display in this popup by exploring the [metadata](https://www.arcgis.com/sharing/rest/content/items/de3da5068f334fbca9c876786062b6ef/info/metadata/metadata.xml?format=default&output=html). For example, `DP03_75E` contains data about the estimated total income and benefits for families.

### Step 4: Add a Legend

1. Consult the [leaflet-choropleth examples](https://github.com/timwis/leaflet-choropleth/blob/gh-pages/examples/legend/) to help you in creating a legend. Be sure to include following:

  * Use `L.control` to add a control (and to choose its position).

  * Use `L.DomUtil.create('div', 'info legend')` to create a `<div>` with the `info` and `legend` classes,

  * Loop through the colors and values of your choropleth data, and then add them with `div.innerHTML`,

  * Return `div` when done.

## Hints

* As you examine the GeoJSON data, look for `DP03_16E`, the code which indicates the estimated employed population with children aged 6–17.

* Check out the [colorbrewer2](http://colorbrewer2.org/) website, which supplies color schemes (in hex values) that you can use to customize a choropleth map.

## References

National Center for Education Statistics (2020). ACS-ED 2014-2018 Total Population: Economic Characteristics (DP03). https://data-nces.opendata.arcgis.com/datasets/nces::acs-ed-2014-2018-total-population-economic-characteristics-dp03/about

  * Metadata available at https://www.arcgis.com/sharing/rest/content/items/de3da5068f334fbca9c876786062b6ef/info/metadata/metadata.xml?format=default&output=html

—


### style.css
```css
body {
  padding: 0;
  margin: 0;
}

#map,
body,
html {
  height: 100%;
}

.leaflet-popup-content {
  text-align: center;
}

/* CSS from the leaflet-choropleth documentation */
.legend {
  color: #555;
  padding: 6px 8px;
  font: 12px Arial, Helvetica, sans-serif;
  font-weight: bold;
  background: white;
  background: rgba(255,255,255,0.8);
  box-shadow: 0 0 15px rgba(0,0,0,0.2);
  border-radius: 5px;
}
.legend ul {
  list-style-type: none;
  padding: 0;
  margin: 0;
  clear: both;
}
.legend li {
  display: inline-block;
  width: 30px;
  height: 22px;
}
.legend .min {
  float: left;
  padding-bottom: 5px;
}
.legend .max {
  float: right;
}

h1 {
  text-align: center;
}
```

### index.html
```html
<!DOCTYPE html>
<html lang="en-us">
  <head>
    <meta charset="UTF-8">
    <title>Income Choropleth</title>

    <!-- Leaflet CSS -->
    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css"
    integrity="sha256-p4NxAoJBhIIN+hmNHrzRCf9tD/miZyoHS5obTRR9BMY="
    crossorigin=""/>

    <!-- Leaflet JavaScript code-->
    <script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"
    integrity="sha256-20nQCchB9co0qIjJZRGuk2/Z9VM+kNiyxNV1lvTlZBo="
    crossorigin=""></script>

    <!-- D3 library -->
    <script src="https://d3js.org/d3.v7.min.js"></script>

    <!-- Step 2 -->
    <!-- leaflet-choropleth JavaScript -->
    <script type="text/javascript" src="static/js/choropleth.js"></script>

    <!-- Our CSS -->
    <link rel="stylesheet" type="text/css" href="static/css/style.css">

  </head>
  <body>

    <!-- The div where we'll insert our map -->
    <div id="map"></div>

    <!-- Our JavaScript -->
    <script type="text/javascript" src="static/js/logic-step1.js"></script>
    <!-- <script type="text/javascript" src="static/js/logic-step3.js"></script> -->
    <!-- <script type="text/javascript" src="static/js/logic-step4.js"></script> -->

  </body>
</html>
```

### logic.js
```js
// Creating the map object
let myMap = L.map("map", {
  center: [27.96044, -82.30695],
  zoom: 7
});

// Adding the tile layer
L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
}).addTo(myMap);

// Load the GeoJSON data.
let geoData = "https://2u-data-curriculum-team.s3.amazonaws.com/dataviz-classroom/v1.1/15-Mapping-Web/ACS-ED_2014-2018_Economic_Characteristics_FL.geojson";

// Get the data with d3.
d3.json(geoData).then(function(data) {

  // Create a new choropleth layer.
  let geojson = L.choropleth(data, {

    // Define which property in the features to use.
    valueProperty: "DP03_16E",

    // Set the color scale.
    scale: ["#ffffb2", "#b10026"],

    // The number of breaks in the step range
    steps: 10,

    // q for quartile, e for equidistant, k for k-means
    mode: "q",
    style: {
      // Border color
      color: "#fff",
      weight: 1,
      fillOpacity: 0.8
    },

    // Binding a popup to each layer
    onEachFeature: function(feature, layer) {
      layer.bindPopup("<strong>" + feature.properties.NAME + "</strong><br /><br />Estimated employed population with children age 6-17: " +
        feature.properties.DP03_16E + "<br /><br />Estimated Total Income and Benefits for Families: $" + feature.properties.DP03_75E);
    }
  }).addTo(myMap);

  // Set up the legend.
  let legend = L.control({ position: "bottomright" });
  legend.onAdd = function() {
    let div = L.DomUtil.create("div", "info legend");
    let limits = geojson.options.limits;
    let colors = geojson.options.colors;
    let labels = [];

    // Add the minimum and maximum.
    let legendInfo = "<h1>Population with Children<br />(ages 6-17)</h1>" +
      "<div class=\"labels\">" +
        "<div class=\"min\">" + limits[0] + "</div>" +
        "<div class=\"max\">" + limits[limits.length - 1] + "</div>" +
      "</div>";

    div.innerHTML = legendInfo;

    limits.forEach(function(limit, index) {
      labels.push("<li style=\"background-color: " + colors[index] + "\"></li>");
    });

    div.innerHTML += "<ul>" + labels.join("") + "</ul>";
    return div;
  };

  // Adding the legend to the map
  legend.addTo(myMap);

});
```