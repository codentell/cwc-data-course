+++
title = "03. City Markers  👩‍🎓👨‍🎓"
weight = 3
tags = ["map"] 
+++

# City Markers

In this activity, you'll create a map and plot markers for five United States cities.

## Instructions

* Use the starter files `index.html`, `logic.js`, and `style.css` provided in the [Unsolved](Unsolved) folder.

* Add markers to your map  for the following US cities:

| City | Latitude | Longitude |
|---|---|---|
| New York | 40.7128 | -74.0059 |
| Los Angeles | 34.0522 | -118.2437 |
| Houston | 29.7604 | -95.3698 |
| Omaha | 41.2524 | -95.9980 |
| Chicago | 41.8781 | -87.6298 |


* For each city, create a marker with a popup that displays the city's name and population. You can either look up the population for each city or make one up for this exercise.

## Bonus

A popup takes a string of HTML. If you finish early, try experimenting with passing different tags or custom CSS.

## Hint

Don't forget to add the marker to your map after creating it.

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

  <!-- JavaScript file -->
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

// An array containing each city's name, location, and population
let cities = [{
  location: [40.7128, -74.0059],
  name: "New York",
  population: 8550405
},
{
  location: [41.8781, -87.6298],
  name: "Chicago",
  population: 2720546
},
{
  location: [29.7604, -95.3698],
  name: "Houston",
  population: 2296224
},
{
  location: [34.0522, -118.2437],
  name: "Los Angeles",
  population: 3971883
},
{
  location: [41.2524, -95.9980],
  name: "Omaha",
  population: 446599
}
];

// Looping through the cities array, create one marker for each city, bind a popup containing its name and population, and add it to the map.
for (let i = 0; i < cities.length; i++) {
  let city = cities[i];
  L.marker(city.location)
    .bindPopup(`<h1>${city.name}</h1> <hr> <h3>Population ${city.population.toLocaleString()}</h3>`)
    .addTo(myMap);
}
```
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

h1 {
  text-align: center;
}
```

{{% /expand%}}