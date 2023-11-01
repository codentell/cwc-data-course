+++
title = "02. Scrape Multiple Pages 👩‍🏫🧑‍🏫"
weight = 2
tags = ["scraping"] 
+++


# Scrape Multiple Pages
```python
from splinter import Browser
from bs4 import BeautifulSoup
browser = Browser('chrome')
url = 'http://quotes.toscrape.com/'
browser.visit(url)
html = browser.html
soup = BeautifulSoup(html, 'html.parser')
# Scrape all quotes on a single page
quotes = soup.find_all('span', class_='text')

for quote in quotes:
    print(quote.text)

# Automate clicking the Next button
browser.links.find_by_partial_text('Next').click()
# Use a for loop to visit the first five pages
for x in range(1, 6):
    html = browser.html
    soup = BeautifulSoup(html, 'html.parser')
    quotes = soup.find_all('span', class_='text')
    for quote in quotes:
        print('page:', x, '----------')
        print(quote.text)
    browser.links.find_by_partial_text('Next').click()


browser.quit()
 
```


