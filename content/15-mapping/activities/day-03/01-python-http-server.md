+++
title = "01. Python HTTP Server 👩‍🏫🧑‍🏫 "
weight = 1
tags = ["map"] 
+++

# A Little More About CORS

Modern browsers have a **same-origin policy** that generally prevents **scripts** hosted from one web server to make **calls** to another server. Here’s an example:

Let’s say you navigate to a news website and then are served an ad coming from adspamnetwork.com. If browser restrictions aren't in place, and if you happen to be logged in to PayPal, the JavaScript code in the ad might make an API call to PayPal and make unauthorized transfers from your account.

For this reason, browsers restrict a server from one site (adspamnetwork.com, for example) from making a request to a server from another site (paypal.com).

So, how does a website, such as ebay.com, make API calls to PayPal?

**Cross-origin resource sharing (CORS)** is a mechanism that tells browsers to access selected resources from a web server through information in the HTTP headers in a web application. CORS provides a way to allow cross-origin requests.

The following steps allow a website to make API calls to PayPal:

1. The browser generally makes a preflight request to the server.

2. The preflight request checks with the server about whether the browser's origin can make a request to it. The preflight request also gets other details, including the types of requests that the server allows and the types of files that the server permits to be transferred.

3. The browser makes the request. The code on the PayPal server contains a CORS header that explicitly permits ebay.com to make API requests.

For more info about CORS, refer to [MDN Web Docs](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS), [web.dev](https://www.html5rocks.com/en/tutorials/cors/#toc-handling-a-not-so-simple-request) or [Stack Overflow](https://stackoverflow.com/questions/10636611/how-does-access-control-allow-origin-header-work).

- - -


## Local Example
### data.json
```json
{
  "miles": [
    3,
    4,
    5,
    4,
    41,
    15,
    35,
    46,
    26,
    7,
    12,
    19,
    21,
    78,
    3,
    8,
    12,
    15,
    9,
    14,
    25,
    76,
    122,
    16,
    27,
    37,
    22,
    13,
    7,
    5,
    48,
    37,
    19,
    13,
    18,
    7,
    51,
    45,
    40,
    36,
    9,
    7,
    3,
    16,
    10,
    2,
    6,
    1,
    8,
    2,
    3,
    20,
    46,
    15,
    24,
    11,
    11,
    40,
    77,
    38,
    71,
    14,
    30,
    79
  ],
  "new_cars": [
    "Ford",
    "Ford",
    "Ford",
    "Ford",
    "Ford",
    "Ford",
    "Ford",
    "Ford",
    "Ford",
    "Ford",
    "Ford",
    "Ford",
    "Ford",
    "Jeep",
    "Jeep",
    "Jeep",
    "Jeep",
    "Jeep",
    "Jeep",
    "Jeep",
    "Jeep",
    "Jeep",
    "Jeep",
    "Jeep",
    "Jeep",
    "Jeep",
    "Jeep",
    "Jeep",
    "Jeep",
    "Jeep",
    "Chevrolet",
    "Chevrolet",
    "Chevrolet",
    "Chevrolet",
    "Chevrolet",
    "Chevrolet",
    "Chevrolet",
    "Chevrolet",
    "Chevrolet",
    "Chevrolet",
    "Chevrolet",
    "Chevrolet",
    "Chevrolet",
    "Chevrolet",
    "Chevrolet",
    "Chevrolet",
    "Chevrolet",
    "BMW",
    "BMW",
    "BMW",
    "BMW",
    "BMW",
    "BMW",
    "Honda",
    "Honda",
    "Honda",
    "Honda",
    "Honda",
    "Honda",
    "Honda",
    "Honda",
    "Honda",
    "Honda",
    "Honda"
  ]
}
```
### index.html
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Miles for New Cars</title>
  <script src="https://cdn.plot.ly/plotly-latest.min.js"></script>

  <script src="https://d3js.org/d3.v7.min.js"></script>

</head>
<body>
  <div id="plot"></div>
  <script>
    d3.json("data/data.json").then((data) => {
      //  Create the Traces
      let trace1 = {
        x: data.new_cars,
        y: data.miles,
        type: "box",
        name: "Miles on New Cars",
        boxpoints: "all"
      };

      // Create the data array for the plot.
      let plotData = [trace1];

      // Define the plot layout.
      let layout = {
        title: "Miles for New Cars",
        xaxis: { title: "New Cars" },
        yaxis: { title: "Square Root of Miles" }
      };

      // Plot the chart to a div tag with an ID of "plot".
      Plotly.newPlot("plot", plotData, layout);
    });
  </script>
</body>
</html>
```

##  Remote Server Example 

### index.html
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta http-equiv="X-UA-Compatible" content="ie=edge">
  <title>Citibike Stations</title>

  <!-- D3 library -->
  <script src="https://d3js.org/d3.v7.min.js"></script>

</head>
<body>
  <script>
  d3.json("https://gbfs.citibikenyc.com/gbfs/en/station_information.json").then(function(data) {
    console.log(data);
  });
  </script>
</body>
</html>
```

