---
layout: post
title:  "Python-Flask"
date:   2016-04-02 23:00:00
categories: CPSC350
color: amber
---

Python-Flask - A microframework with less overhead

# Python-Flask

So Python-Flask is what we ended up using in CPSC350. I emded up liking Python-Flask because there was not too much overhead when it comes to backend code. That being said, I do believe that the industry standard of Python backend code is using Django. Flask is not as hard to learn as Django, but I have noticed many errors with Flask when it comes to keeping sessions; it was a bit annoying.

# What does the code look like?

Like I had said before, Flask is not as hard to learn as Django because in order to make a call to the server, you need to know what you are going to name that call in Flask like a function.

``` Python

@app.route('/', methods=['GET', 'POST'])
def index():
	#Insert the rest of the code here

```

The first line is what the server sided call is named for the frontend and the second line is creating a function in Python to handle the call.

# Psycopg2

In order to handle database connections and queries, it was necessary to use Psycopg2. Psycopg2 is a Python library that can make database connection to PostgreSQL databases. All you needed to do was download the library and make a function to wrap a Psycopg2 function.

``` Python

def connect_to_db():
    return psycopg2.connect('dbname=session user=bryan password=password host=localhost')

```

And after that you can easily make database connections and queries.

#### Make a Database Connection

``` Python

db = connect_to_db()
cur = db.cursor(cursor_factory=psycopg2.extras.DictCursor)

```

Don't worry about what is in the parameter for db.cursor(). It just makes sure that the results come out as a Python Dictionary-esk container

#### Run a Query

``` Python
query = 'SELECT * FROM stores WHERE (lower(name) LIKE %s OR lower(type) LIKE %s) AND zip = %s ORDER BY name'
cur.execute(query, substitutions)
results = cur.fetchall()

```

It's easy to tell what is going on. cur.execute is taking 2 parameters, a query and substitutions. I premade a query and in the query, I want to replace every %s with something that is needed for the query. The query has to be a String and the substitutions has to be in a Python Tuple.

The results are returned by storing the data into a variable and using cur.fetchall() or cur.fetchone(), depending on what you need. cur.fetchall() grabs all results while cur.fetchone() grabs only the first one.