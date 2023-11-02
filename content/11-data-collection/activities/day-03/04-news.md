+++
title = "04. News 👩‍🎓👨‍🎓"
weight = 4
tags = ["scraping"] 
+++


# News Scraping

* In this activity, you will scrape news summaries across multiple pages from the Global Voices news [site](https://globalvoices.org/page/2/).

## Instructions

* Open page 2 of [Global Voices news](https://globalvoices.org/page/2/). Use DevTools to identify the elements that contain the data you need to scrape.

* Within your Jupyter notebook, use Splinter to click on any popup or lightbox to make it disappear.

* Create an empty list to store your article summaries.

* Create a function that will perform your web scraping. The function should perform the following tasks:

  * Collect the HTML from the browser.

  * Parse the HTML and save it as a Beautiful Soup object.

  * On any given page, scrape the **title** and the **date** of each article.

    > **Note:** The date is in the format `DD _MM YYYY`. See if you can strip the underscore before you save the date.

  * For each article summary, the title and the date should be structured as a dictionary. All dictionaries should be contained in a Python list.

* Create a `for` loop that will:

  * Call your web scraping function to scrape the article summaries on a page.
  
  * Click the button to go to the next page of older articles.
  
  * Repeat the process for a total of five pages.

* Import the scraped data (a list of dictionaries) into a Pandas dataframe. Using Python, Pandas, or both, convert the dates into a usable datetime type.

* Remember that you should begin on page 2, and move on to older stories.

* Below is an abbreviated example of what your scraped data might look like.

  ```python
  [{'header': 'Portugal: Human rights activist fighting racism wins international award',
    'date': '29 _12 2021'},
  {'header': 'Where is Qatari human rights defender Noof Al-Maadeed?',
    'date': '29 _12 2021'}]
  ```

## Hint

* Consider using Pandas' [`to_datetime`](https://pandas.pydata.org/docs/reference/api/pandas.to_datetime.html) method to convert the dates.

## Reference

[Global Voices](https://globalvoices.org) is a news website that releases its content under a Creative Commons license ([CC-BY-3.0](https://creativecommons.org/licenses/by/3.0/)). This means you are free to scrape the content and redistribute it, as long as you give credit to the source (provide attribution).

- - -


## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python
from splinter import Browser
from bs4 import BeautifulSoup

browser=Browser('firefox')
# Visit the URL
url = "https://globalvoices.org/page/2/"
browser.visit(url)

# Parse the HTML
html = browser.html
soup = BeautifulSoup(html, 'html.parser')
# Close the dialogue box
browser.links.find_by_partial_text("No thanks").click()
# Create a function to perform the web scraping
def get_summary():
    # Collect the HTML from the browser
    html = browser.html
    # Parse the HTML with Beautiful Soup
    soup = BeautifulSoup(html, 'html.parser')
    
    # Save the main area of the web page to a variable
    main_area = soup.find("div", class_="post-archive-container")
    
    # Find all the articles in the main area of the web page
    articles = main_area.find_all("div", class_="gv-promo-card-text")
    
    # Create an empty list to hold summaries
    summary_list = []
    
    # Loop through the articles
    for article in articles:
        # Collect the article title
        header = article.find("h3", class_="post-title").text.strip()
        # Collect the article date
        date = article.find("span", class_="datestamp")["title"]
        # Remove the underscore from the date
        date = date.replace('_', '')
        
        # Create the summary dictionary
        summary_dict = {
            "header": header,
            "date": date
        }
        # Append the summary dictionary to the list
        summary_list.append(summary_dict)
        
    # Return the list of summaries
    return summary_list
# Create a loop to collect the article summaries and click to the older article pages 5 times
articles_list = []
for _ in range(5):
    summary = get_summary()
    articles_list.extend(get_summary())
    browser.links.find_by_partial_text("Older").click()
# Print the articles list
articles_list

# Import Pandas
import pandas as pd

# Convert the articles list to a Pandas DataFrame
df = pd.DataFrame(articles_list)
df.head()

# Convert the date column to a datetime data type
df.date = pd.to_datetime(df.date, dayfirst=True)
# Display the DataFrame
df


# Check the DataFrame information to ensure the date is saved as a datetime data type
df.info()
<class 'pandas.core.frame.DataFrame'>
RangeIndex: 105 entries, 0 to 104
Data columns (total 2 columns):

# Close the browser
browser.quit()
```
{{% /expand%}}

