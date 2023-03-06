+++
title = "06. Scraping Mars News 👩‍🎓👨‍🎓"
weight = 6
tags = ["scraping"] 
+++

# Mars News

In this activity, you'll get additional web scraping practice by collecting data from a website based on NASA's Mars News.

## Instructions

* First, open up [the website](https://static.bc-edx.com/data/web/mars_news/index.html) in Chrome and become familiar with the layout. In this exercise, you'll scrape the title and the summary of a news article.

* Right-click anywhere on the page, and then click Inspect. In DevTools, search for the HTML elements that you'll use to identify the title and the summary paragraph that you want. Remember to first look for the class of the `<div>` element associated with the news articles, then find the title and summary paragraph classes within that section.

* Now begin the scraping process by importing the necessary libraries and setting up Splinter.

* Use Splinter to visit the website and collect the html. Since this is a real website, you may want to add a delay that will allow the page to load. To do so, include the following code: `browser.is_element_present_by_css('div.list_text', wait_time=1)`. This code accomplishes the following:

    1. The `is_element_present_by_css method` searches for elements with a specific combination of tag (`div`) and attribute (`list_text`), both of which are needed to find the news articles.
    2. The parameter `wait_time=1` tells the browser to wait one second before searching for the specified components.

* Create a BeautifulSoup parser to parse the html from the website.

* Use the `select_one` method from Beautiful Soup to search the html for a `<div>` tag that has the class associated with the news articles. Store your result in a variable.

    > **Note:** The `select_one` method is used to find only the first tag that matches a selector. For example:
    > 
    > ```python
    > soup.select_one(".help_link")
    > # <a class="help_link" href="/help" id="link1">Help</a>
    > ```

* Now find the title of the news article you selected by using the `find` method and the class associated with the article titles. Print your result.

* Use the `get_text` method to extract the text of the news article title that you scraped, and print your result. 

* Now find the summary of the news article you selected by using the `find` method and the class associated with the article summary. Print your result.

* Use the `get_text` method to extract the text of the news article summary that you scraped, and print your result. 

* Congratulations on scraping this NASA website! Now that you have finished, quit your browsing session.

## Hints

* Use the Beautiful Soup documentation for [`get_text`](https://www.crummy.com/software/BeautifulSoup/bs4/doc/#get-text)

## References

[The Mars News website](https://static.bc-edx.com/data/web/mars_news/index.html) is operated by edX Boot Camps LLC for educational purposes only. The news article titles, summaries, dates, and images were scraped from [NASA's Mars News](https://mars.nasa.gov/) website in December 2020. Images are used according to the [JPL Image Use Policy](https://www.jpl.nasa.gov/jpl-image-use-policy), courtesy NASA/JPL-Caltech.

- - -



## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python
# Import Splinter and BeautifulSoup
from splinter import Browser
from bs4 import BeautifulSoup as soup

# Set up Splinter
browser = Browser('chrome')

# Visit the Mars NASA news site
url = 'https://static.bc-edx.com/data/web/mars_news/index.html'
browser.visit(url)
# Optional delay for loading the page
browser.is_element_present_by_css('div.list_text', wait_time=1)

# Scrape the website
html = browser.html

# Create a BeautifulSoup object from the scraped HTML
news_soup = soup(html, 'html.parser')

# Select one news article with select_one()
slide_elem = news_soup.select_one('div.list_text')

# Scrape the title of the news article
title_elem = slide_elem.find('div', class_='content_title')
print(title_elem)

# Extract the text of the title with get_text()
title = title_elem.get_text()
print(title)

# Scrape the summary of the news article
news_p = slide_elem.find('div', class_='article_teaser_body').text
news_p

# Quit your browsing session
browser.quit()
```
{{% /expand%}}