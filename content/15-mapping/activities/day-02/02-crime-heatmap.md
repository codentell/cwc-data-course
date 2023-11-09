+++
title = "02. Crime heatmap  👩‍🏫🧑‍🏫 "
weight = 2
tags = ["map"] 
+++


### index.html
```html
<!DOCTYPE html>
<html lang="en-us">

  <head>
    <meta charset="UTF-8">
    <title>SF Crime</title>

    <!-- Leaflet JavaScript code -->
    <script src="https://unpkg.com/leaflet@1.3.3/dist/leaflet.js" integrity="sha512-tAGcCfR4Sc5ZP5ZoVz0quoZDYX5aCtEm/eu1KhSLj2c9eFrylXZknQYmxUssFaVJKvvc0dJQixhGjG2yXWiV9Q==" crossorigin=""></script>

    <!-- Leaflet heatmap plugin-->
    <script type="text/javascript" src="static/js/leaflet-heat.js"></script>
    
    <!-- D3 library -->
    <script src="https://d3js.org/d3.v5.min.js"></script>

    <!-- Leaflet CSS -->
    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.3.3/dist/leaflet.css" integrity="sha512-Rksm5RenBEKSKFjgI3a41vrjkw4EVPlJ3+OiI65vTjIdo9brlAacEuKOiQ5OFh7cOI1bkDwLqdLw3Zg0cRJAAQ==" crossorigin="" />
    
    <!-- Our CSS  -->
    <link rel="stylesheet" href="./static/css/style.css" />

  </head>

  <body>

    <div id="map"></div>

    <!-- JavaScript file -->
    <script type="text/javascript" src="static/js/just-crime.js"></script>
    <!-- <script type="text/javascript" src="static/js/heatmap.js"></script> -->


  </body>

</html>

```


### just-crime.js
```js
var myMap = L.map("map", {
  center: [37.7749, -122.4194],
  zoom: 13
});

// Adding the tile layer
L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
}).addTo(myMap);

var url = "https://data.sfgov.org/resource/cuks-n6tp.json?$limit=1000";

d3.json(url).then(function(response) {

  console.log(response);

  for (var i = 0; i < response.length; i++) {
    var location = response[i].location;

    if (location) {
      L.marker([location.coordinates[1], location.coordinates[0]]).addTo(myMap);
    }
  }

});
```