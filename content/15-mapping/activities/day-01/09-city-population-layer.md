+++
title = "09. City Population Layer 👩‍🎓👨‍🎓 "
weight = 9
tags = ["map"] 
+++


# City Population Layers

In this activity, you'll expand on a previous activity by adding an overlay to represent state populations. This layer will appear on the map as white circle vectors.

## Instructions

* Use the starter files `index.html`, `logic.js`, and `style.css` provided in the [Unsolved](Unsolved) folder.

* Open the [logic.js](Unsolved/logic.js) file in the `Unsolved` folder.

* Add logic to this file as follows:

    * Create a layer group for city markers and a separate layer group for state markers. Note that the `cityMarkers` and `stateMarkers` arrays contain all the markers, which have been created for you. Store these layer groups in variables named `cities` and `states`.

    * Create a `baseMaps` object to contain the `street` and `topo` tiles, which have already been defined.

    * Create an `overlayMaps` object to contain the `State Population` and `City Population` layers.

    * Add a `layers` key to the options object in the `L.map` method, and set its value to an array that contains our `street`, `states`, and `cities` layers. These will determine which layers display when the map first loads.

    * Create a layer control, and pass it the `baseMaps` and `overlayMaps` objects. Add the layer control to the map.

## Hint

* Refer to the Leaflet [Layer Groups and Layers Control tutorial](http://leafletjs.com/examples/layers-control/) if you need help.

* If everything is correct, you can toggle between the Street Map and Topographic Map base layers and turn the State Population and City Population overlays on and off.

## Reference

U.S. 2020 Decennial Census, retrieved from https://data.census.gov/cedsci/

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
// A function to determine the marker size based on the population
function markerSize(population) {
  return Math.sqrt(population) * 50;
}

// Define arrays to hold the created city and state markers.
let cityMarkers = [];
let stateMarkers = [];

// Loop through locations, and create the city and state markers.
for (let i = 0; i < locations.length; i++) {
  // Setting the marker radius for the state by passing population into the markerSize function
  stateMarkers.push(
    L.circle(locations[i].coordinates, {
      stroke: false,
      fillOpacity: 0.75,
      color: "white",
      fillColor: "white",
      radius: markerSize(locations[i].state.population)
    })
  );

  // Set the marker radius for the city by passing the population to the markerSize() function.
  cityMarkers.push(
    L.circle(locations[i].coordinates, {
      stroke: false,
      fillOpacity: 0.75,
      color: "purple",
      fillColor: "purple",
      radius: markerSize(locations[i].city.population)
    })
  );
}

// Create the base layers.
let street = L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
})

let topo = L.tileLayer('https://{s}.tile.opentopomap.org/{z}/{x}/{y}.png', {
	attribution: 'Map data: &copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors, <a href="http://viewfinderpanoramas.org">SRTM</a> | Map style: &copy; <a href="https://opentopomap.org">OpenTopoMap</a> (<a href="https://creativecommons.org/licenses/by-sa/3.0/">CC-BY-SA</a>)'
});

// Create two separate layer groups: one for the city markers and another for the state markers.
let states = L.layerGroup(stateMarkers);
let cities = L.layerGroup(cityMarkers);

// Create a baseMaps object.
let baseMaps = {
  "Street Map": street,
  "Topographic Map": topo
};

// Create an overlay object.
let overlayMaps = {
  "State Population": states,
  "City Population": cities
};

// Define a map object.
let myMap = L.map("map", {
  center: [37.09, -95.71],
  zoom: 5,
  layers: [street, states, cities]
});

// Pass our map layers to our layer control.
// Add the layer control to the map.
L.control.layers(baseMaps, overlayMaps, {
  collapsed: false
}).addTo(myMap);
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
```

{{% /expand%}}