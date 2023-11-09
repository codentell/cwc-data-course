+++
title = "03. Marker Clusters  👩‍🏫🧑‍🏫 "
weight = 3
tags = ["plotly"] 
+++

# Rodent Report Map

In this activity, you'll visualize reports of rodent sightings in New York City (NYC).

## Instructions

* Use the starter files `index.html`, `static/js/logic.js`, and `static/css/style.css` provided in the [Unsolved](Unsolved) folder.

* Check out [the data for all 311 (police non-emergency) service requests in NYC](https://data.cityofnewyork.us/Social-Services/311-Service-Requests-from-2010-to-Present/erm2-nwe9/data).

* Build a query URL for the data that only returns rodent complaints from 2016.

    **Note:** To start, limit the data that's returned to 100 data points.

* After you successfully plot your rodent data, incorporate the [Leaflet.markercluster](https://github.com/Leaflet/Leaflet.markercluster) plugin.

    **Note:** Cluster plugins can help to declutter a map that has tons of data on it.

## Bonus

If you finish plotting the rodent-sighting data on the map, use the 311 service requests data to plot a similar graph for a different type of data.

## Hint

You can increase the data limit to 10,000 after you get the cluster plugin working. But, be aware that plotting 10,000 normal markers on a map might slow down your computer a lot.

—

## ✅ Solutions
{{%expand "Solutions Click Here" %}}

### index.html
```html
<!DOCTYPE html>
<html lang="en-us">
  <head>
    <meta charset="UTF-8">
    <title>Marker Clusters</title>
    
    <!-- Leaflet CSS -->
    <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css"
    integrity="sha256-p4NxAoJBhIIN+hmNHrzRCf9tD/miZyoHS5obTRR9BMY="
    crossorigin=""/>
    
    <!-- Leaflet JavaScript code -->
    <script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js"
    integrity="sha256-20nQCchB9co0qIjJZRGuk2/Z9VM+kNiyxNV1lvTlZBo="
    crossorigin=""></script>

    <!-- D3 library -->
    <script src="https://d3js.org/d3.v7.min.js"></script>

    <!-- Marker cluster JavaScript code -->
    <script type="text/javascript" src="https://unpkg.com/leaflet.markercluster@1.0.3/dist/leaflet.markercluster.js"></script>

    <!-- Marker cluster CSS -->
    <link rel="stylesheet" type="text/css" href="https://unpkg.com/leaflet.markercluster@1.0.3/dist/MarkerCluster.css">
    <link rel="stylesheet" type="text/css" href="https://unpkg.com/leaflet.markercluster@1.0.3/dist/MarkerCluster.Default.css">

    <!-- Our CSS -->
    <link rel="stylesheet" type="text/css" href="static/css/style.css">

  </head>
  <body>

    <div id="map"></div>

    <!-- Our JavaScript -->
    <script type="text/javascript" src="static/js/logic.js"></script>

  </body>
</html>
```

### logic.js"
```js
// Creating the map object
let myMap = L.map("map", {
  center: [40.7, -73.95],
  zoom: 11
});

// Adding the tile layer
L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
}).addTo(myMap);

// Store the API query variables.
// For docs, refer to https://dev.socrata.com/docs/queries/where.html.
// And, refer to https://dev.socrata.com/foundry/data.cityofnewyork.us/erm2-nwe9.
let baseURL = "https://data.cityofnewyork.us/resource/fhrw-4uyv.json?";
let date = "$where=created_date between'2016-01-01T00:00:00' and '2017-01-01T00:00:00'";
let complaint = "&complaint_type=Rodent";
let limit = "&$limit=10000";

// Assemble the API query URL.
let url = baseURL + date + complaint + limit;

// Get the data with d3.
d3.json(url).then(function(response) {

  // Create a new marker cluster group.
  let markers = L.markerClusterGroup();

  // Loop through the data.
  for (let i = 0; i < response.length; i++) {

    // Set the data location property to a variable.
    let location = response[i].location;

    // Check for the location property.
    if (location) {

      // Add a new marker to the cluster group, and bind a popup.
      markers.addLayer(L.marker([location.coordinates[1], location.coordinates[0]])
        .bindPopup(response[i].descriptor));
    }

  }

  // Add our marker cluster layer to the map.
  myMap.addLayer(markers);

});
```
{{% /expand%}}