+++
title = "02. first HTML 👩‍🎓👨‍🎓"
weight = 2
tags = ["scraping"] 
+++

In this activity, you will create a simple HTML page.

## Instructions

In a new HTML file, create the basic structure of an HTML document and include in it the following:

* `DOCTYPE` declaration

* `<head>` element with nested `<title>` element

* `<h1>` element with a title of your choice

* An image

* A link to an external page, such as google.com

* An ordered list of things to do on your next vacation

* An unordered list of four bands/musicians you like. To create an unordered list, use the `<ul>` tag.

* You should be checking the rendered HTML in a web browser as you code to make sure you're going in the right direction.

- - -

## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```html
<!DOCTYPE html>
<html lang="en-us">

<head>
  <meta charset="UTF-8">
  <title>My First Page</title>
</head>

<body>
  <!-- Header -->
  <h1>Hello World!</h1>

  <!-- Image -->
  <img
    src="https://static.wikia.nocookie.net/spongebob/images/4/46/SVG_SpongeBob_SquarePants.svg/revision/latest/scale-to-width-down/195?cb=20181117230211"
    alt="Spongebob!" />
  <br />

  <!-- Link with New Tab -->
  <a href="https://www.google.com">Google</a>
  <br />

  <!-- An ordered list -->
  <ol>
    <li>Visit Grand Canyon</li>
    <li>Hike the trails</li>
    <li>Take photos</li>
  </ol>

  <ul>
    <li>Bach</li>
    <li>Mozart</li>
    <li>Beethoven</li>
    <li>Adele</li>
  </ul>
</body>

</html>
```
{{% /expand%}}