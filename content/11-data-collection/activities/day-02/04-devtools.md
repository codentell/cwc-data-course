+++
title = "04. DevTools 👩‍🏫🧑‍🏫"
weight = 4
tags = ["scraping"] 
+++

```python
!pip install webdriver-manager

# This version uses selenium 
from selenium import webdriver
from bs4 import BeautifulSoup
from webdriver_manager.chrome import ChromeDriverManager

# Set up using selenium
browser = webdriver.Chrome(ChromeDriverManager().install())

url = "https://stackoverflow.com/questions/tagged/python?sort=MostVotes&edited=true"

browser.get(url)

html = browser.page_source

soup = BeautifulSoup(html, 'html.parser')

soup.find('h1').text

soup.find('h1').text.strip()

questions = soup.find_all('a', class_="s-link")

questions

for question in questions:
    print(question['class'])

questions = [question for question in questions if question['class']==['s-link']]
questions

questions[0]['href']

questions[0].text

browser.quit()
```



