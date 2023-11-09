+++
title = "10. GeoJson 👩‍🎓👨‍🎓 "
weight = 10
tags = ["map"] 
+++

# GeoJSON

In this activity, you'll work with GeoJSON data from the [U.S. Geological Survey (USGS)](http://earthquake.usgs.gov) to make plot markers representing occurrences of earthquakes.

## Instructions

* Use the starter files `index.html`, `logic.js`, and `style.css` provided in the [Unsolved](Unsolved) folder.

* Open the [logic.js](Unsolved/logic.js) file.

*  Note that your starter code places an API call to the USGS Earthquake Hazards Program API. Take a moment to study the `features` array that we extract from the response.

* Add logic to create a GeoJSON layer that contains all the features retrieved from the API call, and add the layer directly to the map. You can reference today's previous activities and the Leaflet [Using GeoJSON with Leaflet](http://leafletjs.com/examples/geojson/) tutorial.

* Create an `overlayMaps` object by using the newly created earthquake GeoJSON layer. Pass `overlayMaps` to the layer control.

## Bonus

* Create a separate overlay for the GeoJSON and a base layer by using the `street` tile layer and the `topo` tile layer. Add these to a layer control. If you get stuck, refer to the previous activity.

* Add a popup to each marker to display the time and location of the earthquake at that location.

## Hint

Refer to the following Leaflet documentation:

* [GeoJSON](http://leafletjs.com/reference.html#geojson)

* [Using GeoJSON with Leaflet tutorial](http://leafletjs.com/examples/geojson/)

If you want to reformat the time from the GeoJSON data for the bonus, you may wish to use the JavaScript method [Date()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Date)

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