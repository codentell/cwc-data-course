+++
title = "04. Github Pages 👩‍🎓👨‍🎓"
weight = 4
tags = ["map"] 
+++

# Deploy the Citi Bike Project

In this activity, you'll deploy your Citi Bike project files to GitHub Pages.

## Instructions

You've been given a Plotly visualization project with `index.html`, `plot.js`, and `data.json`.

* Deploy the project to GitHub Pages.

## Hint

Consult [GitHub Pages](https://pages.github.com/) for reference. Be sure to select the **Project Site** and **Start from Scratch** options for instructions.

---

### index.html
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Citi Bike</title>

  <!-- D3 -->
  <script src="https://d3js.org/d3.v7.min.js"></script>

  <!-- Leaflet CSS -->
  <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css"
  integrity="sha256-p4NxAoJBhIIN+hmNHrzRCf9tD/miZyoHS5obTRR9BMY="
  crossorigin=""/>

  <!-- Leaflet JavaScript code -->
  <script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"
  integrity="sha256-20nQCchB9co0qIjJZRGuk2/Z9VM+kNiyxNV1lvTlZBo="
  crossorigin=""></script>

  <!-- Our CSS -->
  <link rel="stylesheet" type="text/css" href="static/css/style.css">
</head>
<body>

  <!-- The div that holds our map -->
  <div id="map-id"></div>

  <!-- Our JavaScript file -->
  <script type="text/javascript" src="static/js/logic.js"></script>
</body>

</html>
```
### logic.js
```js
function createMap(bikeStations) {

  // Create the tile layer that will be the background of our map.
  let streetmap = L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
      attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
  });


  // Create a baseMaps object to hold the streetmap layer.
  let baseMaps = {
    "Street Map": streetmap
  };

  // Create an overlayMaps object to hold the bikeStations layer.
  let overlayMaps = {
    "Bike Stations": bikeStations
  };

  // Create the map object with options.
  let map = L.map("map-id", {
    center: [40.73, -74.0059],
    zoom: 12,
    layers: [streetmap, bikeStations]
  });

  // Create a layer control, and pass it baseMaps and overlayMaps. Add the layer control to the map.
  L.control.layers(baseMaps, overlayMaps, {
    collapsed: false
  }).addTo(map);
}

function createMarkers(response) {

  // Pull the "stations" property from response.data.
  let stations = response.data.stations;

  // Initialize an array to hold the bike markers.
  let bikeMarkers = [];

  // Loop through the stations array.
  for (let index = 0; index < stations.length; index++) {
    let station = stations[index];

    // For each station, create a marker, and bind a popup with the station's name.
    let bikeMarker = L.marker([station.lat, station.lon])
      .bindPopup("<h3>" + station.name + "<h3><h3>Capacity: " + station.capacity + "</h3>");

    // Add the marker to the bikeMarkers array.
    bikeMarkers.push(bikeMarker);
  }

  // Create a layer group that's made from the bike markers array, and pass it to the createMap function.
  createMap(L.layerGroup(bikeMarkers));
}


// Perform an API call to the Citi Bike API to get the station information. Call createMarkers when it completes.
d3.json("https://gbfs.citibikenyc.com/gbfs/en/station_information.json").then(createMarkers);
```
### style.css
```css
html,
body,
#map-id {
  height: 100%;
  padding: 0;
  margin: 0;
}
```