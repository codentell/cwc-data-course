+++
title = "01. CSS Identifier"
weight = 1
tags = ["scraping"] 
+++

```python
from bs4 import BeautifulSoup
html = """
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
"""

# Parse the code with Beautiful Soup
soup = BeautifulSoup(html, 'html.parser')

# Match elements by ID
cities = soup.find('ol', id='cities')

cities

# Find all matches
city_list_items = cities.find_all('li')

# Print all the cities
for city in city_list_items:
    print(city)

# Print the text of all the cities
for city in city_list_items:
    print(city.text)

# Same as above, as a list comprehension
[city.text for city in city_list_items]

# All list items on the page
all_items = soup.find_all('li')

# All list items on the page
all_items = soup.find_all('li')

# Create a list of the text in each list item
[item.text for item in all_items]

# Match items by class
meat_items = soup.find_all('li', class_='meat')

# Create a list of the text in each meat item
[meat.text for meat in meat_items]

# Find the vegetarian items using the vegetarian class
vegetarian_items = soup.find_all('li', class_='vegetarian')

# Create a list of the text of the vegetarian items
[v.text for v in vegetarian_items]

```