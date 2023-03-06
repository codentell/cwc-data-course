+++
title = "03. Pandas CSS Scrape 👩‍🎓👨‍🎓"
weight = 3
tags = ["scraping"] 
+++

# Pandas Scrape

In this activity, you will use BeautifulSoup to extract information from a simplified version of the official Pandas website.

## Instructions

* Follow these steps to set up for web scraping:

  * Create a new Jupyter notebook and import BeautifulSoup.
  
  * Copy and paste the code of the provided HTML file into a Python string.

  * Create an instance of BeautifulSoup to parse the HTML.

* Use BeautifulSoup to retrieve the following:

  * The **text** of all `h3`-level headers.

  * The text and URLs of only the first section ("Getting Started"). Use the `id` of this section to scrape the data.

  * **All** URLs on the page.

## Bonus

* Each subsection on the page consists of a header, e.g. "Getting Started" and links. Write Python code to automate the collection of headers and link URLs in a logical structure. Below is an example of what you might end up with.

  ```python
  {'Getting Started': ['https://pandas.pydata.org/getting_started.html',
    'https://pandas.pydata.org/docs/getting_started/index.html'],
  'Documentation': ['https://pandas.pydata.org/docs/user_guide/index.html',
    'https://pandas.pydata.org/docs/reference/index.html',
    'https://pandas.pydata.org/docs/development/index.html'],
  'The pandas Community': ['https://pandas.pydata.org/about/index.html',
    'https://stackoverflow.com/questions/tagged/pandas',
    'https://pandas.pydata.org/community/ecosystem.html']}
  ```

* The above data structure is a dictionary. Each key in the dictionary corresponds to a section title, and each dictionary value is a list of the URLs in that section.

- - -

## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python
from bs4 import BeautifulSoup

html = """
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body>
    <h1>pandas</h1>
    <blockquote>pandas is a powerful Python data analysis library. </blockquote>

    <div id="start" class="section">
        <h3 class="section-header">Getting Started</h3>
        <ul class="pandas-ul">
            <a href="https://pandas.pydata.org/getting_started.html">
                <li>Install pandas</li>
            </a>
            <a href="https://pandas.pydata.org/docs/getting_started/index.html">
                <li>Getting started</li>
            </a>
        </ul>
    </div>

    <div id="documentation" class="section">
        <h3 class="section-header">Documentation</h3>
        <ul class="pandas-ul">
            <a href="https://pandas.pydata.org/docs/user_guide/index.html">
                <li>User guide</li>
            </a>
            <a href="https://pandas.pydata.org/docs/reference/index.html">
                <li>API reference</li>
            </a>
            <a href="https://pandas.pydata.org/docs/development/index.html">
                <li>How to contribute to pandas</li>
            </a>
        </ul>
    </div>

    <div id="community" class="section">
        <h3 class="section-header">The pandas Community</h3>
        <ul class="pandas-ul">
            <a href="https://pandas.pydata.org/about/index.html">
                <li>More about pandas</li>
            </a>
            <a href="https://stackoverflow.com/questions/tagged/pandas">
                <li>Have questions?</li>
            </a>
            <a href="https://pandas.pydata.org/community/ecosystem.html">
                <li>The pandas ecosystem</li>
            </a>
        </ul>
    </div>
</body>

</html>
"""
soup = BeautifulSoup(html, 'html.parser')

all_titles = soup.find_all('h3')
all_titles

titles = [title.text for title in all_titles]
titles

# Start section
start_section = soup.find('div', id="start")
start_section

start_description = start_section.find('h3').text
start_description

start_links = start_section.find_all('a')
start_links

start_urls = [link['href'] for link in start_links]
start_urls

all_urls = [link['href'] for link in soup.find_all('a')]
all_urls

# BONUS: Compile a dictionary of titles and URLs
pandas_info_dict = {}

all_divs = soup.find_all('div')
for div in all_divs:
    div_description = div.find('h3').text
    urls = [link['href'] for link in div.find_all('a')]
    pandas_info_dict[div_description] = urls    
pandas_info_dict

# Using a for-loop
alternate_dict = {}
for div in all_divs:
    div_desc = div.find('h3').text
    div_urls = div.find_all('a')
    url_list = []
    for url in div_urls:
        url_list.append(url['href'])
    alternate_dict[div_desc] = url_list        

alternate_dict
```
{{% /expand%}}