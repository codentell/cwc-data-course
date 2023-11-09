+++
title = "06. City Population  👩‍🏫🧑‍🏫 "
weight = 6
tags = ["map"] 
+++

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
  center: [37.09, -95.71],
  zoom: 5
});

// Add a tile layer.
L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
}).addTo(myMap);

// Define a markerSize() function that will give each city a different radius based on its population.
function markerSize(population) {
  return Math.sqrt(population) * 50;
}

// Loop through the cities array, and create one marker for each city object.
for (let i = 0; i < cities.length; i++) {
  L.circle(cities[i].location, {
    fillOpacity: 0.75,
    color: "white",
    fillColor: "purple",
    // Setting our circle's radius to equal the output of our markerSize() function:
    // This will make our marker's size proportionate to its population.
    radius: markerSize(cities[i].population)
  }).bindPopup(`<h1>${cities[i].name}</h1> <hr> <h3>Population: ${cities[i].population.toLocaleString()}</h3>`).addTo(myMap);
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

