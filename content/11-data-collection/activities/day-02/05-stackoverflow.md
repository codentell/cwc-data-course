+++
title = "05. StackOverflow 👩‍🎓👨‍🎓"
weight = 5
tags = ["scraping"] 
+++

# Stack Scrape

In this activity, you will scrape Stack Overflow's Python page and store the results in a Python list of dictionaries.


## Instructions

Visit [Stack Overflow's Python page](https://stackoverflow.com/questions/tagged/python?sort=MostVotes&edited=true) with Splinter's automated browser. Scrape information from all the questions on the first page. For each question, use BeautifulSoup to scrape the following pieces of information:

* The summary (e.g. 'What does the "yield" keyword do?' for the first question)

* The number of votes for that question

* The excerpt (the longer text below the summary)

As you scrape, use Chrome's DevTools to identify elements and their CSS selectors, which you will then use in BeautifulSoup.

Next, organize your information into a Python list of dictionaries. That is, information from each question will be organized into a dictionary like the below, and a list will contain all these dictionaries.

```python
{'summary': 'What does the "yield" keyword do?',
  'votes': '11692',
  'excerpt': "What is the use of the yield keyword in Python? What does it do?\nFor example, I'm trying to understand this code1:\ndef _get_child_candidates(self, distance, min_dist, max_dist):\n    if self._leftchild ..."}
```

Don't forget to close your automated browser!

## Reference

[Stack Overflow](https://stackoverflow.com) [user contributions](https://stackoverflow.com/help/licensing) are licensed under a [CC BY-SA](https://creativecommons.org/licenses/by-sa/4.0/) license.

- - -

Note: Mac might block this chromedriver so take a look at this https://timonweb.com/misc/fixing-error-chromedriver-cannot-be-opened-because-the-developer-cannot-be-verified-unable-to-launch-the-chrome-browser-on-mac-os/

## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python
# Import dependencies
# this version uses splinter
from splinter import Browser
from bs4 import BeautifulSoup

# Launch the browser
browser = Browser('chrome')


# Set the URL to visit to a variable
url = "https://stackoverflow.com/questions/tagged/python?sort=MostVotes&edited=true"

# Send the browser to the URL
browser.visit(url)

# Save the HTML from the browser
html = browser.html

# Create a BeautifulSoup object from the HTML
soup = BeautifulSoup(html, 'html.parser')

# Find all divs that contain a question
question_divs = soup.find_all('div', class_="s-post-summary js-post-summary")

# Find the summary text of the first question
question_divs[0].find("a", class_="s-link").text

# Find the vote count text of the first question
question_divs[0].find("span", class_="s-post-summary--stats-item-number").text

# Find and strip the excerpt text of the first question
question_divs[0].find("div", class_="s-post-summary--content-excerpt").text.strip()

# Create an empty list to store the questions
question_list = []

# Create a for loop to extract the information
for question in question_divs:
    # Extract the summary
    summary = question.find("a", class_="s-link").text

    # Extract the votes
    votes = question.find("span", class_="s-post-summary--stats-item-number").text

    # Extract the excerpt
    excerpt = question.find("div", class_="s-post-summary--content-excerpt").text.strip()

    # Create a dictionary to store the information
    question_dict = {"summary": summary,
                     "votes": int(votes),
                     "excerpt": excerpt}

    # Append the dictionary to the question list
    question_list.append(question_dict)

# Display the question list
question_list

# Close the browser
browser.quit()

```
{{% /expand%}}