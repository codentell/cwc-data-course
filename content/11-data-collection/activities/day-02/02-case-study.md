+++
title = "02. Case Study 👩‍🎓👨‍🎓"
weight = 2
tags = ["scraping"] 
+++

# CSS Case Study

In this activity, you’ll use CSS selectors in a basic web scraping example. First, you’ll use the class selector. Then, you’ll use the id selector.

## Instructions

* Import BeautifulSoup.

* Save the provided HTML code as a Python string.

* Convert the HTML string into a BeautifulSoup object.

* Use the `find_all` function to retrieve **all** of the elements that belong to the `odd` class. 

* Save the results to a variable.

* Display the results by using a `for` loop.

Now that you’ve identified HTML elements by using the CSS `class` selector, you’ll do the same but using the `id` selector. Recall that a `class` can contain multiple elements but that an `id` must be unique.

* Extract the text from a paragraph element that has an `id` of `first`.

* Print your result.

- - -


## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python
# Import BeautifulSoup
from bs4 import BeautifulSoup as soup

# Save the provided HTML code as a Python string.
html = """
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>

    <style>
        .even {
            color: blue;
        }

        .odd {
            color: green;
        }
    </style>

</head>

<body>
    <div>
        <p class="odd" id="first">First</p>
        <p class="even" id="second">Second</p>
        <p class="odd" id="third">Third</p>
    </div>

    <div>
        <p class="even" id="fourth">Fourth</p>
        <p class="odd" id="fifth">Fifth</p>
        <p class="even" id="sixth">Sixth</p>
    </div>
</body>

</html>
"""

# Convert the HTML string into a BeautifulSoup object.
html_soup = soup(html, 'html.parser')

# Use the `find_all` function to retrieve **all** of the elements that belong to the `odd` class. 
# Save the results to a variable.
odds = html_soup.find_all("p", class_="odd")

# Display the results by using a `for` loop.
for odd in odds:
    print(odd)

# Extract the text from a paragraph element that has an `id` of `first`.
# Print your result.
first = html_soup.find("p", id="first")
print(first.text)

```
{{% /expand%}}