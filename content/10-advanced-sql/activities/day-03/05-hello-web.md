+++
title = "05. Hello Web "
weight = 5
tags = ["sql"] 
+++

# Hello, Web

In this activity, you will practice setting up a server and defining basic routes with Flask.

## Instructions

* Create an `app.py`, and make the necessary imports.

* Use Flask to create an `app` instance.

* Use route decorators to define the following endpoints:

    * `/`, or your **index route**: This should return a simple string, such as `"Hello, world!"` or `"Welcome to my API!"`

    * `/about`, which should return a string containing your **name** and **current location**

    * `/contact`, which should return a string telling visitors where to email you

* Finally, add code at the end of the file that will allow you to run the server from the command line with `python app.py`.

## Hint

Refer to the [Flask documentation](http://flask.pocoo.org/docs/0.12/quickstart/#a-minimal-application) as you work through this activity.

---

```python
# 1. Import Flask
from flask import Flask


# 2. Create an app
app = Flask(__name__)


# 3. Define static routes
@app.route("/")
def index():
    return "Hello, world!"


@app.route("/about")
def about():
    name = "Peleke"
    location = "Tien Shan"

    return f"My name is {name}, and I live in {location}."


@app.route("/contact")
def contact():
    email = "peleke@example.com"

    return f"Questions? Comments? Complaints? Shoot an email to {email}."


# 4. Define main behavior
if __name__ == "__main__":
    app.run(debug=True)

```