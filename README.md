# cs50-pset9-finance

## Another fun and exciting project: I built a full-stack web app with Bootstrap UI, Flask back-end, and SQLite3 database.

# DEMO
<img src='https://user-images.githubusercontent.com/58123635/121849668-9eca3480-ccb9-11eb-9b1a-4f1040cd3b6e.png' height='300px' />
<img src='https://user-images.githubusercontent.com/58123635/121849797-cfaa6980-ccb9-11eb-806c-073d6730ea0c.png' height='300px' />
<img src='https://user-images.githubusercontent.com/58123635/121849824-d9cc6800-ccb9-11eb-87e2-afe2aa7243bd.png' height='300px' />
<img src='https://user-images.githubusercontent.com/58123635/121849696-abe72380-ccb9-11eb-8bd1-656effeab191.png' height='300px' />
<img src='https://user-images.githubusercontent.com/58123635/121849719-b7d2e580-ccb9-11eb-8f11-3d8a4d92ba29.png' height='300px' />
Transaction history
<img src='https://user-images.githubusercontent.com/58123635/121849877-e9e44780-ccb9-11eb-85b2-4548e91d2db1.png' height='300px' />
Orders table
<img src='https://user-images.githubusercontent.com/58123635/121850000-1dbf6d00-ccba-11eb-8830-fc6054a27919.png' height='300px' />


# USAGE:

First, you will need to get an API key from [IEX](iexcloud.io/cloud-login#/register/) (free account registration), which lets you download stock quotes via their API (application programming interface) using URLs like https://cloud.iexapis.com/stable/stock/nflx/quote?token=API_KEY

With the API, run the following within a CS50 IDE's terminal: $ export API_KEY=value (value is your acquired personal API KEY)

Start Flask’s built-in web server:
$ flask run

## In this pset, I have implemented:
- App Features: register, quote, buy, index, sell, history
- most of html templates (lots of Jinja dynamic content generation) and their UIs
- application.py (lots of routing, logics, and Sqlite3 QUERIES)
- Design an `orders` table to keep track of all stock transactions by all users. It is stored in finance.db

### Some of my own notes, while watching Week9 lecture [video](https://cs50.harvard.edu/x/2021/weeks/9/)

Flask app file structure:
	• application.py
	• requirements.txt
	• static/
	• templates/

MODEL-VIEW-CONTROLLER (MVC)  design pattern
	- model=SQL(..) the database, 
	- view=what user sees, templates,
  - controller=application.py, the logics that connect M-V, plus routing

- jinja: Used in HTML templates: {{ var }} , {% block x %} {% endblock %}.


Make use of TEMPLATES: factor out a COMMON layout.html
- {% block body %} {% endblock %}
- in index.html, about.html, etc.: {% extends "layout.html" %} {% block body %} the content {% endblock %}

SENDING emails with Flask:
 ![image](https://user-images.githubusercontent.com/58123635/121848227-bdc7c700-ccb7-11eb-8e8e-9a6f35a22a7e.png)

#### Privacy concern: In dev environment: store personal info in virtual environment variables (export username=..., and later retrieve via os.getenv("USERNAME"))

#### It's easy to implement Cookie Session in Flask
- Session: basically, servers plants cookie (i.e. a saved state, a file, a large number) on your device, to help them remember your identity.
- How it works? BROWSER (if have a cookie) sends cookie along with GET requests, and SERVER: validates, then skip login during same sesson, server personal data, etc.
- ENTER Incognito mode: not employing cookies.

*Callback*: a function that will eventually be called, when it has an answer for you.

#### An AJAX call: sends additional HTTP request to server (for chat messages, autocomplete, etc.). So WHEN the response is ready, the callback function would receive the response as its argument.

### NOTE for pset9 Finance:
Primary key vs Unique key:
- A primary key is a column of table which uniquely identifies each tuple (row) in that table. 
- Primary key will not accept NULL values whereas Unique key can accept one NULL value. (a unique column might have rows with NULL values)
- A table can have only primary key (column), and multiple unique keys (columns).
