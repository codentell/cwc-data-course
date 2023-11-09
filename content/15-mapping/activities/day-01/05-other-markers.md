+++
title = "05. Other markers 👩‍🎓👨‍🎓"
weight = 5
tags = ["map"] 
+++

# Other Markers

In this activity, you'll create three vector shapes to use as markers.

## Instructions

* Use the starter files `index.html`, `logic.js`, and `style.css` provided in the [Unsolved](Unsolved) folder. Create the following vector layers, and then add them to the map:

* A red circle over the city of Dallas (`[32.7767, -96.7979]`)

* A line connecting NYC (`[40.7128, -74.0060]`) to Toronto (`[43.6532, -79.3832]`)

* A polygon that covers the area inside Atlanta (`[33.7490, -84.3880]`), Savannah (`[32.0809, -81.0912]`), Jacksonville (`[30.3322, -81.6557]`), and Montgomery (`[32.3792, -86.3077]`)

## Hint

* Note that the [logic.js](Unsolved/logic.js) file contains some starter code.

* Use the Vector Layers section of the [Leaflet documentation](https://leafletjs.com/reference.html#toc) for reference.

---


## ✅ Solutions
{{%expand "Solutions Click Here" %}}

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

  <!-- JavaScript file -->
  <script type="text/javascript" src="logic.js"></script>
</body>

</html>
```

### logic.js
```js
// Create our initial map object.
// Set the longitude, latitude, and starting zoom level.
let myMap = L.map("map").setView([39.8283, -98.5795], 5);

// Add a tile layer (the background map image) to our map.
// Use the addTo() method to add objects to our map.
L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
}).addTo(myMap);


// Create a red circle over Dallas.
L.circle([32.7767, -96.7979], {
  color: "red",
  fillColor: "red",
  fillOpacity: 0.75,
  radius: 10000
}).addTo(myMap);

// Connect a black line from NYC to Toronto.
let line = [
  [40.7128, -74.0060],
  [43.6532, -79.3832]
];
L.polyline(line, {
  color: "black"
}).addTo(myMap);

// Create a purple polygon the covers the area in Atlanta, Savannah, Jacksonville, and Montgomery.
L.polygon([
  [33.7490, -84.3880],
  [32.0809, -81.0912],
  [30.3322, -81.6557],
  [32.3792, -86.3077]
], {
  color: "purple",
  fillColor: "purple",
  fillOpacity: 0.75
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