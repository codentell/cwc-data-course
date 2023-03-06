+++
title = "06. CSS 👩‍🎓👨‍🎓"
weight = 6
tags = ["scraping"] 
+++

# CSS

## Instructions

* In a new HTML file, create three ordered lists. Each list should have four items.

  * The first should be a list of four cities. The entire list should have an `id` of "cities".

  * The second should be a list of four food entrees. Two of them should contain meat, and two of them should be vegetarian. The meat list items should have a `class` called "meat". The vegetarian list items should have a `class` called "vegetarian".

  * The third should be a list of four movies. Your favorite movie on that list should have an `id` called "favorite". Only that list item should have an `id`.

* In the `style` section, use CSS selectors to color your target elements.

  * Color the entire list of cities purple.

  * Color the meat-containing dishes brown, and the vegetarian dishes green.

  * Color your favorite movie orange.


- - -

## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My First CSS Adventure</title>

    <style>
        #cities {
            color: purple;
        }

        .meat {
            color: brown;
        }

        .vegetarian {
            color: green;
        }

        #favorite {
            color: orange;
        }
    </style>

</head>

<body>

    <ol id="cities">
        <li>New York</li>
        <li>Paris</li>
        <li>Seoul</li>
        <li>Prague</li>
    </ol>

    <ol>
        <li class="meat">Taco</li>
        <li class="meat">Burger</li>
        <li class="vegetarian">Cheese pizza</li>
        <li class="vegetarian">Mac and cheese</li>
    </ol>

    <ol>
        <li id="favorite">Star Wars</li>
        <li>Lion King</li>
        <li>Godfather</li>
        <li>Lord of the Rings</li>
    </ol>
</body>

</html> 
```
{{% /expand%}}