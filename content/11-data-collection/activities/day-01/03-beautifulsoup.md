+++
title = "03. BeautifulSoup"
weight = 3
tags = ["scraping"] 
+++

```python
# Introduction to BeautifulSoup
# Import BeautifulSoup

from bs4 import BeautifulSoup


# Store html site as a string
html = """
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
"""

# Create a BeautifulSoup object to parse the html code
soup = BeautifulSoup(html, 'html.parser')

# Print the parser
print(soup)

# Check type of parser object
type(soup)

# Extract and print the head section
print(soup.head)

# Extract the title section
soup.title

# Extract the title text from the title
soup.title.text

# Use the find method to locate the first image
image_html = soup.find("img")
image_html

# Use the find method to locate the first link
link = soup.find('a')
# Print the html for the link
print(link)
# Extract and print the URL
print(link['href'])

# Extract bulleted lists
soup.ol

# Extract the first list item
soup.ol.li

# Extract the text from the first list item
soup.ol.li.text

# Extract the source URL for the image
image_html['src']

# Extract the alt text for the image
image_html['alt']
```