<!--
Maintainer:   jeffskinnerbox@yahoo.com / www.jeffskinnerbox.me
Version:      0.0.0
-->


<div align="center">
<img src="https://raw.githubusercontent.com/jeffskinnerbox/blog/main/content/images/banners-bkgrds/work-in-progress.jpg" title="These materials require additional work and are not ready for general use." align="center" width=420px height=219px>
</div>


* [The Flask Mega-Tutorial](https://blog.miguelgrinberg.com/post/the-flask-mega-tutorial-part-i-hello-world)



[Flask][01] is a [Web Framework][05] written in Python.
It is classified as a micro-framework because it does not require particular tools or libraries.
It has no database abstraction layer, form validation,
user/app authentication, database  Object–relational mapping (ORM), input validation, data sanitization,
or any other components where pre-existing third-party libraries provide these common functions.
Flask only provides components that are essential, such as routing, request handling, sessions, and so on.
For the other functionalities, the developer can write a custom module or use a [Flusk extension][09].
This approach avoids unnecessary boilerplate code, which is not even being used.

Flask is used for the backend,
but it makes use of a templating language called [Jinja2][04] which is used to create
HTML, XML or other markup formats that are returned to the user via an HTTP request.
Also, Flask is compliant with the Web Server Gateway Interface (WSGI) standard.
This specifications ([PEP333][03]) concerning the communication between a web server and a client application.


------


# Building a Blog With Flask
While many sources have been used for this document,
For Flask Blog work I followed mainly the article ["How To Make a Web Application Using Flask in Python 3"][06] for development
and ["How To Serve Flask Applications with Gunicorn and Nginx on Ubuntu 18.04"][08] for deployment.
In addition to Flask, I will make use of the following tools:

* **[Bootstrap toolkit][02]** will be used to style applications, making them more visually appealing.
Bootstrap will help you incorporate responsive web pages (works well on mobile browsers)
without writing your own HTML, CSS, and JavaScript code to achieve these goals.
* **[Jinja template engine][04]** to dynamically build HTML pages using familiar Python
concepts such as variables, loops, lists, and so on.
* **[SQLite database][07]** is used by the application to store content,
and add a new post, click on the title of a post to view, add, edit, or delete contents of an existing post.
* **[Pipenv][10]** automatically creates and manages a `virtualenv` for your projects,
as well as adds/removes packages from your `Pipfile` as you install/uninstall packages.
It also generates the ever-important `Pipfile.lock`, which is used to produce deterministic builds.

Sources:

* [Python Flask Tutorial - Getting Started with Flask](https://scoutapm.com/blog/python-flask-tutorial-getting-started-with-flask)
* [How To Make a Web Application Using Flask in Python 3][06]
* [Flask Tutorial](https://www.tutorialspoint.com/flask/index.htm)
* [Flask Quickstart](https://flask.palletsprojects.com/en/2.2.x/quickstart/#)
* [Python Flask Tutorial - Getting Started with Flask](https://scoutapm.com/blog/python-flask-tutorial-getting-started-with-flask)
* [Flask Web Development, One Drop at a Time](https://www.fullstackpython.com/flask.html)
* [Python Flask tutorial: Build your first Flask application!](https://www.educative.io/blog/python-flask-tutorial)
* [How To Install Python 3 and Set Up a Programming Environment on an Ubuntu 22.04 Server](https://www.digitalocean.com/community/tutorials/how-to-install-python-3-and-set-up-a-programming-environment-on-an-ubuntu-22-04-server)

#### Step 1: Setup Python 3 - DONE
Ubuntu 22.04 and other versions of Debian Linux ship with Python 3 pre-installed.
To make sure that your versions are up-to-date, update your local package index:

```bash
# upgrade your linux packages
sudo apt update && sudo apt -y upgrade

# check your python 3 version
$ python3 -V
Python 3.10.6

# install pip for version 3 of python
sudo apt install -y python3-pip pipenv

# packages & development tools for robust programming environment
sudo apt install -y build-essential libssl-dev libffi-dev python3-dev
```

#### Step 2: Setting Up a Virtual Environment - DONE
Virtual environments enable you to have an isolated space on your server for Python projects,
ensuring that each of your projects can have its own set of dependencies
that won’t disrupt any of your other projects.
While there are a few ways to achieve a programming environment in Python,
I'll be using the `venv` module here,
which is part of the standard Python 3 library.

```bash
# install venv for python 3
sudo apt install -y python3-venv

# create directory for python programming environments
mkdir environments

# create an venv environment for your 1st project
cd environments
python3 -m venv flask_blog

# view the environment
$ ls flask_blog/
bin/  include/  lib/  lib64@  pyvenv.cfg
```

#### Step 3: Installing Flask and Creating Base Application - DONE
Now install Python packages and isolate your project code away from the
main Python system installation.

```bash
# activate your python venv environment
cd flask_blog
source ./bin/activate

# install flask
pip3 install flask

# confirm the installation
$ python -c "import flask; print(flask.__version__)"
2.2.3
```

Now that the programming environment is set up,
we'll create our first Flask application in the file `app.py`:

```python
from flask import Flask

app = Flask(__name__)

@app.route('/')
def hello():
    return 'Hello, World!'


if __name__ == '__main__':
    app.run(debug=True, port=5002)
```

Now tell Flask where to find the application and what mode it should operate:

```bash
# run the application on port 5002 using the 'flask run' command
export FLASK_DEBUG=true
flask run -p 5002
#OR
flask run --debug -p 5002

#OR using python
python app.py
```

Now go to your browser and enter `localhost:5002` to see the webpage served up by Flask.

#### Step 4: Using HTML Templates - DONE
Web applications mainly use HTML to display information,
so you’ll now work on incorporating HTML files in the app.
Flask provides a `render_template()` helper function that allows use of the Jinja template engine.
This will make managing HTML much easier by writing your HTML code in
`.html` files as well as using logic in your HTML code.
You’ll use these templates to build all of your application pages.

Update your `app.py` file to look like this:

```python
from flask import Flask, render_template

app = Flask(__name__)

@app.route('/')
def index():
    return render_template('index.html')


if __name__ == '__main__':
    app.run(debug=True, port=5002)
```

If you execute this now, you will get a browser full of errors (try it!).
We are going to fix this error now.
First, create a directory called `templates` inside your `flask_blog` directory.
Within `flask_blog` create a directory call `static` and `static/css`.

```bash
# create the directories to hold html, and style sheets
cd flask_blog
mkdir templates static
mkdir static/css
```

Then inside `templates`, create a file called `index.html` with this content:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <link rel="stylesheet" href="{{ url_for('static', filename= 'css/style.css') }}">
    <title>FlaskBlog</title>
</head>
<body>
   <h1>Welcome to FlaskBlog</h1>
</body>
</html>
```

Then inside `css`, create a file called `style.css` with this content:

```css
h1 {
    border: 2px #eee solid;
    color: brown;
    text-align: center;
    padding: 10px;
}
```

We are going to be changing the `index.html` file to incorporate not only CSS,
but also templates in a moment but lets first test just the `style.css` file with:

```bash
# visual check the use of the style.css file
python3 app.y

# try these url's in your browser
#     localhost:5002
```

Now change the `index.html` file so it makes use of the templates.
Place the following in the `index.html` file:

```html
{% extends 'base.html' %}

{% block content %}
    <h1>{% block title %} Welcome to FlaskBlog {% endblock %}</h1>
{% endblock %}
```

Now create a template file within `templates` called `base.html`:

```html
<!doctype html>
<html lang="en">
  <head>
    <!-- Required meta tags -->
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

    <!-- Bootstrap CSS -->
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">

    <title>{% block title %} {% endblock %}</title>
  </head>
  <body>
    <nav class="navbar navbar-expand-md navbar-light bg-light">
        <a class="navbar-brand" href="{{ url_for('index')}}">FlaskBlog</a>
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNav">
            <ul class="navbar-nav">
            <li class="nav-item active">
                <a class="nav-link" href="#">About</a>
            </li>
            </ul>
        </div>
    </nav>
    <div class="container">
        {% block content %} {% endblock %}
    </div>

    <!-- Optional JavaScript -->
    <!-- jQuery first, then Popper.js, then Bootstrap JS -->
    <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js" integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpbzo5smXKp4YfRvH+8abtTE1Pi6jizo" crossorigin="anonymous"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.7/umd/popper.min.js" integrity="sha384-UO2eT0CpHqdSJQ6hJty5KVphtPhzWj9WO1clHTMGa3JDZwrnQq4sF86dIHNDz0W1" crossorigin="anonymous"></script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/js/bootstrap.min.js" integrity="sha384-JjSmVgyd0p3pXB1rRibZUAYoIIy6OrQ6VrjIEaFf/nJGzIxFDsf4x0xIM+B07jRM" crossorigin="anonymous"></script>
  </body>
</html>
```

Now test what we have created with templates:

```bash
# visual check the use of the base.html file
python3 app.y

# try these url's in your browser
#     localhost:5002
```

#### Step 5: Setting up the Database - DONE
In this step, I'll set up aSQLite  database to store data for the blog posts application.
I’ll also populate the database with a few example entries.

Since the data mainly consists of blog posts,
I'll create a table called `posts` with the necessary columns.
I’ll also create a `.sql` file that contains SQL commands to create the posts table with a few columns.
I’ll then use this file to create the database.

First create a file called `schema.sql` inside the `flask_blog` directory:

```
DROP TABLE IF EXISTS posts;

CREATE TABLE posts (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    created TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
    title TEXT NOT NULL,
    content TEXT NOT NULL
);
```

Now create a file named `init_db.py` inside the `flask_blog` directory:

```python
import sqlite3

connection = sqlite3.connect('database.db')


with open('schema.sql') as f:
    connection.executescript(f.read())

cur = connection.cursor()

cur.execute("INSERT INTO posts (title, content) VALUES (?, ?)",
            ('First Post', 'Content for the first post')
            )

cur.execute("INSERT INTO posts (title, content) VALUES (?, ?)",
            ('Second Post', 'Content for the second post')
            )

connection.commit()
connection.close()
```

Now I'll create the database using the `init_db.py` Python script:

```bash
# create the sqlite database
python init_db.py
```

#### Step 6: Displaying All Posts - DONE
Now that I have set up your database, I'll modify the `index()`
view function to display all the posts you have in your database.

Open the `app.py` file to make modifications so it looks like this:

```python
import sqlite3
from flask import Flask, render_template

def get_db_connection():
    conn = sqlite3.connect('database.db')
    conn.row_factory = sqlite3.Row
    return conn

app = Flask(__name__)

@app.route('/')
def index():
    conn = get_db_connection()
    posts = conn.execute('SELECT * FROM posts').fetchall()
    conn.close()
    return render_template('index.html', posts=posts)

if __name__ == '__main__':
    app.run(debug=True, port=5002)
```

Now that you’ve passed the posts you fetched from the database to the `index.html` template,
you need to make modifications to `index.html` file.

Open the `index.html` file to make modifications so it looks like this:

```html
{% extends 'base.html' %}

{% block content %}
    <h1>{% block title %} Welcome to FlaskBlog {% endblock %}</h1>
    {% for post in posts %}
        <a href="#">
            <h2>{{ post['title'] }}</h2>
        </a>
        <span class="badge badge-primary">{{ post['created'] }}</span>
        <hr>
    {% endfor %}
{% endblock %}
```

Now test what we have created with `app.py` and `index.html` changes made:

```bash
# visual check the use of the app.py and index.html files
python3 app.py

# try these url's in your browser
#     localhost:5002
```

#### Step 7: Displaying a Single Post - DONE
In this step, you’ll create a new Flask route with a view function
and a new HTML template to display an individual blog post by its ID.

To respond with a 404 page, you need to import the `abort()` function.
To support this, add `from werkzeug.exceptions import abort`,
add the `get_post()` function right after the `get_db_connection()` function,
and a new `app.route()` function to support the new variable `post_id` that will be returned
all in the `app.py` file:

```python
import sqlite3
from flask import Flask, render_template
from werkzeug.exceptions import abort

def get_db_connection():
    conn = sqlite3.connect('database.db')
    conn.row_factory = sqlite3.Row
    return conn

def get_post(post_id):
    conn = get_db_connection()
    post = conn.execute('SELECT * FROM posts WHERE id = ?',
                        (post_id,)).fetchone()
    conn.close()
    if post is None:
        abort(404)
    return post

app = Flask(__name__)

@app.route('/')
def index():
    conn = get_db_connection()
    posts = conn.execute('SELECT * FROM posts').fetchall()
    conn.close()
    return render_template('index.html', posts=posts)

@app.route('/<int:post_id>')
def post(post_id):
    post = get_post(post_id)
    return render_template('post.html', post=post)


if __name__ == '__main__':
    app.run(debug=True, port=5002)
```

Within the `templates` directory, create the new `post.html` file.
This will be similar to the `index.html` file,
except that it will only display a single post,
in addition to also displaying the contents of the post:

```html
{% extends 'base.html' %}

{% block content %}
    <h2>{% block title %} {{ post['title'] }} {% endblock %}</h2>
    <span class="badge badge-primary">{{ post['created'] }}</span>
    <p>{{ post['content'] }}</p>
{% endblock %}
```

And change the value of the `href` attribute from `#` to `{{ url_for('post', post_id=post['id']) }}`
in the `index.html` file:

```html
{% extends 'base.html' %}

{% block content %}
    <h1>{% block title %} Welcome to FlaskBlog {% endblock %}</h1>
    {% for post in posts %}
        <a href="{{ url_for('post', post_id=post['id']) }}"post>
            <h2>{{ post['title'] }}</h2>
        </a>
        <span class="badge badge-primary">{{ post['created'] }}</span>
        <hr>
    {% endfor %}
{% endblock %}
```

Now test what has been created within the `index.html`, `app.py`, and `post.html` changes made:

```bash
# visual check the use of the app.py and index.html files
python3 app.py

# try these url's in your browser
#     localhost:5002
#     localhost:5002/1
#     localhost:5002/2
#     localhost:5002/3     # you should get a 404 error as expected
```

With this, you’ve now finished building the part of the application responsible
for displaying the blog posts in your database.
Next, you’ll add the ability to create, edit, and delete blog posts to your application.

#### Step 8: Modifying Posts for Create, Edit, Delete

##### Creating a New Post - DONE
We are now going to add functionality to create a post.
I’ll create a  template file called `create.html` and modifications to `app.py`
to enable the creation of a post by providing its title and content.

Create the template file `create.html` inside your `templates` directory:

```html
{% extends 'base.html' %}

{% block content %}
<h1>{% block title %} Create a New Post {% endblock %}</h1>

<form method="post">
    <div class="form-group">
        <label for="title">Title</label>
        <input type="text" name="title"
               placeholder="Post title" class="form-control"
               value="{{ request.form['title'] }}"></input>
    </div>

    <div class="form-group">
        <label for="content">Content</label>
        <textarea name="content" placeholder="Post content"
                  class="form-control">{{ request.form['content'] }}</textarea>
    </div>
    <div class="form-group">
        <button type="submit" class="btn btn-primary">Submit</button>
    </div>
</form>
{% endblock %}
```

Next add some functionality to the `base.htkl` file so that it looks like this:

```html
<!doctype html>
<html lang="en">
  <head>
    <!-- Required meta tags -->
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

    <!-- Bootstrap CSS -->
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/css/bootstrap.min.css" integrity="sha384-ggOyR0iXCbMQv3Xipma34MD+dH/1fQ784/j6cY/iJTQUOhcWr7x9JvoRxT2MZw1T" crossorigin="anonymous">

    <title>{% block title %} {% endblock %}</title>
  </head>
  <body>
    <nav class="navbar navbar-expand-md navbar-light bg-light">
        <a class="navbar-brand" href="{{ url_for('index')}}">FlaskBlog</a>
        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
            <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNav">
            <ul class="navbar-nav">
            <li class="nav-item active">
                <a class="nav-link" href="#">About</a>
            </li>
            <li class="nav-item">
                <a class="nav-link" href="{{url_for('create')}}">New Post</a>
            </li>
            </ul>
        </div>
    </nav>
    <div class="container">
         {% for message in get_flashed_messages() %}
             <div class="alert alert-danger">{{ message }}</div>
         {% endfor %}
        {% block content %} {% endblock %}
    </div>

    <!-- Optional JavaScript -->
    <!-- jQuery first, then Popper.js, then Bootstrap JS -->
    <script src="https://code.jquery.com/jquery-3.3.1.slim.min.js" integrity="sha384-q8i/X+965DzO0rT7abK41JStQIAqVgRVzpbzo5smXKp4YfRvH+8abtTE1Pi6jizo" crossorigin="anonymous"></script>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/popper.js/1.14.7/umd/popper.min.js" integrity="sha384-UO2eT0CpHqdSJQ6hJty5KVphtPhzWj9WO1clHTMGa3JDZwrnQq4sF86dIHNDz0W1" crossorigin="anonymous"></script>
    <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.3.1/js/bootstrap.min.js" integrity="sha384-JjSmVgyd0p3pXB1rRibZUAYoIIy6OrQ6VrjIEaFf/nJGzIxFDsf4x0xIM+B07jRM" crossorigin="anonymous"></script>
  </body>
</html>
```

Next we add multiple functions to the `app.py` file so that it looks like this:

```python
import sqlite3
from flask import Flask, render_template, request, url_for, flash, redirect
from werkzeug.exceptions import abort

def get_db_connection():
    conn = sqlite3.connect('database.db')
    conn.row_factory = sqlite3.Row
    return conn

def get_post(post_id):
    conn = get_db_connection()
    post = conn.execute('SELECT * FROM posts WHERE id = ?',
                        (post_id,)).fetchone()
    conn.close()
    if post is None:
        abort(404)
    return post

app = Flask(__name__)
app.config['SECRET_KEY'] = 'password'

@app.route('/')
def index():
    conn = get_db_connection()
    posts = conn.execute('SELECT * FROM posts').fetchall()
    conn.close()
    return render_template('index.html', posts=posts)

@app.route('/<int:post_id>')
def post(post_id):
    post = get_post(post_id)
    return render_template('post.html', post=post)

@app.route('/create', methods=('GET', 'POST'))
def create():
    if request.method == 'POST':
        title = request.form['title']
        content = request.form['content']

        if not title:
            flash('Title is required!')
        else:
            conn = get_db_connection()
            conn.execute('INSERT INTO posts (title, content) VALUES (?, ?)',
                         (title, content))
            conn.commit()
            conn.close()
            return redirect(url_for('index'))
    return render_template('create.html')


if __name__ == '__main__':
    app.run(debug=True, port=5002)
```

Now test what you created for creating a new post:

```bash
# visual check the use of the app.py and index.html files
python3 app.py

# try these url's in your browser
#     localhost:5002
#     localhost:5002/1
#     localhost:5002/create   # go a head and creat a post
```

##### Editing a Post - DONE
You’ll also want to edit your existing posts.
I'll create an edit template called `edit.html`,
add functionality to `index.html`.

Create the template file `edit.html` inside your `templates` directory:

```html
```

Next add functionality to the `index.html` file so that it looks like this:

```html
```

Next add functionality to the `app.py` file so that it looks like this:

```python
```

Now test what you created for editing a new post:

```bash
# visual check the use of the app.py and index.html files
python3 app.py

# try these url's in your browser
#     localhost:5002
#     localhost:5002/1
#     localhost:5002/3/edit   # go a head and edit a post
```

##### Deleting a Post
 In this step I will add the delete functionality to the application.

Add functionality to the `app.py` file so that it looks like this:

```python
```

Make modifications to the `edit.html` file so it looks like this:

```html
```

Now test what you created for editing a new post:

```bash
# visual check the use of the app.py and index.html files
python3 app.py

# try these url's in your browser
#     localhost:5002
#     localhost:5002/create   # go a head a create a post
#     localhost:5002/4/edit   # go a head and edit a post
```

#### Step 9: Disable Virtual Environment - DONE

```bash
# deactivate your python venv environment
cd flask_blog
deactivate
```


------


# Building a Microservice With Flask
Build a simple but real-world useable REST API
Following REST and Microservice Arch Best Practices

We'll be building a simple API that goes over the performing some basic CRUD operations on a datastore of books (or as it happens, in this case, a List of Dictionaries).

We're going to use a simple Python Dictionary for storage, But it can easily be swapped in with a real database solution, should you need to. But for the sake of simplicity, I've decided to go with a simple List of Dictionaries

Sources:

* [How to Deploy Microservices with Docker](https://www.linode.com/docs/guides/deploying-microservices-with-docker/)
* [Getting started with Microservices and Docker](https://www.coditation.com/blog/getting-started-with-microservices-and-docker)
* [Build and Deploy a REST API Microservice with Python Flask and Docker](https://dev.to/swarnimwalavalkar/build-and-deploy-a-rest-api-microservice-with-python-flask-and-docker-5c2d)
* [BUILD MICROSERVICE ARCHITECTURE (MSA) REST API USING THE USING FLASK](https://www.topcoder.com/thrive/articles/build-microservice-architecture-msa-rest-api-using-the-using-flask)
* [Microservices in Python using Flask Framework | Dockerize and Deploy to Kubernetes with Helm](https://www.youtube.com/watch?v=SdTzwYmsgoU)

#### Step 1: Setup Python 3 Virtual Environment - DONE
Just like what was done, in detail, for the Flask Blog created above,
set up your Python 3 virtual environment:

```bash
# upgrade your linux packages
sudo apt update && sudo apt -y upgrade

# check your python 3 version
$ python3 -V
Python 3.10.6

# install pip for version 3 of python
sudo apt install -y python3-pip pipenv

# packages & development tools for robust programming environment
sudo apt install -y build-essential libssl-dev libffi-dev python3-dev

# install venv for python 3
sudo apt install -y python3-venv

# create directory for python programming environments
mkdir environments

# create an venv environment for your 1st project
cd environments
python3 -m venv flask_microservice

# view the environment
$ ls flask_microservice/
bin/  include/  lib/  lib64@  pyvenv.cfg

# activate your python venv environment
cd flask_microservice
source ./bin/activate

# install flask
pip3 install Flask flask_restful

# confirm the installation
$ python -c "import flask; print(flask.__version__)"
2.2.3
```

Now that the programming environment is set up,
as a test, I'll create a Flask application in the file `app-1.py`:

```python
from flask import Flask

app = Flask(__name__)

@app.route('/')
def hello():
    return 'Hello, World!'


if __name__ == '__main__':
    app.run(debug=True, port=5002)
```

Now tell Flask where to find the application and what mode it should operate:

```bash
# via an environment variable, tell flask where to find the application
# and run it in development mode
export FLASK_APP=app
export FLASK_ENV=development

# run the application on port 5002 using the 'flask run' command
flask run -p 5002

#OR using python
python app-1.py
```

Now go to your browser and enter `localhost:5002` to see the webpage served up by Flask.

#### Step 2: Setup the Application (`app-1.py`) - DONE
First declare a List containing several Dictionaries, representing individual 'Book' elements
and a Dictionary to determine the schema for the book object,
as expected by the API.
(This will help with validating requests later):

```python
from flask import Flask
from flask_restful import Resource, Api, reqparse, abort, marshal, fields

# initialize flask
app = Flask(__name__)
api = Api(app)

# dictionary to store all of the books
books = [{
    "id": 1,
    "title": "Zero to One",
    "author": "Peter Thiel",
    "length": 195,
    "rating": 4.17
},
    {
    "id": 2,
    "title": "Atomic Habits ",
    "author": "James Clear",
    "length": 319,
    "rating": 4.35
}
]

# schema for the book request json
bookFields = {
    "id": fields.Integer,
    "title": fields.String,
    "author": fields.String,
    "length": fields.Integer,
    "rating": fields.Float
}


# resource: individual book routes
class Book(Resource):
    def __init__(self):
        # initialize the flask request parser and add arguments as in an expected request
        self.reqparse = reqparse.RequestParser()
        self.reqparse.add_argument("title", type=str, location="json")
        self.reqparse.add_argument("author", type=str, location="json")
        self.reqparse.add_argument("length", type=int, location="json")
        self.reqparse.add_argument("rating", type=float, location="json")
        super(Book, self).__init__()

    # GET - returns a single book object given a matching id
    def get(self, id):
        book = [book for book in books if book['id'] == id]
        if(len(book) == 0):
            abort(404)
        return{"book": marshal(book[0], bookFields)}

    # PUT - given an id
    def put(self, id):
        book = [book for book in books if book['id'] == id]
        if len(book) == 0:
            abort(404)
        book = book[0]
        # loop through all the passed agruments
        args = self.reqparse.parse_args()
        for k, v in args.items():
            # check if the passed value is not null
            if v is not None:
                # if not, set the element in the books dict with the 'k' object to the value provided in the request.
                book[k] = v
        return{"book": marshal(book, bookFields)}

    def delete(self, id):
        book = [book for book in books if book['id'] == id]
        if(len(book) == 0):
            abort(404)
        books.remove(book[0])
        return 201


class BookList(Resource):
    def __init__(self):
        self.reqparse = reqparse.RequestParser()
        self.reqparse.add_argument(
            "title", type=str, required=True, help="The title of the book must be provided", location="json")
        self.reqparse.add_argument(
            "author", type=str, required=True, help="The author of the book must be provided", location="json")
        self.reqparse.add_argument(
            "length", type=int, required=True, help="The length of the book (in pages)", location="json")
        self.reqparse.add_argument(
            "rating", type=float, required=True, help="The rating must be provided", location="json")

    def get(self):
        return{"books": [marshal(book, bookFields) for book in books]}

    def post(self):
        args = self.reqparse.parse_args()
        book = {
            "id": books[-1]['id'] + 1 if len(books) > 0 else 1,
            "title": args["title"],
            "author": args["author"],
            "length": args["length"],
            "rating": args["rating"]
        }
        books.append(book)
        return{"book": marshal(book, bookFields)}, 201


api.add_resource(BookList, "/books")
api.add_resource(Book, "/books/<int:id>")


if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5002)
```

Now tell Flask where to find the application and what mode it should operate:

```bash
# run the application on port 5002 using the 'flask run' command
export FLASK_DEBUG=true
flask run -p 5002
#OR
flask run --debug -p 5002

#OR using python
python app-1.py
```

Now go to your browser and enter `localhost:5002` to see the webpage served up by Flask.
an alternative is to use Curl:

```bash
# query for a list of all the books
$ curl localhost:5002/books
{"books": [{"id": 1, "title": "Zero to One", "author": "Peter Thiel", "length": 195, "rating": 4.17}, {"id": 2, "title": "Atomic Habits ", "author": "James Clear", "length": 319, "rating": 4.35}]}

# pretty print - query for a list of all the books
$ curl -s -X GET http://localhost:5002/books | jq -C '.'
{
  "books": [
    {
      "id": 1,
      "title": "Zero to One",
      "author": "Peter Thiel",
      "length": 195,
      "rating": 4.17
    },
    {
      "id": 2,
      "title": "Atomic Habits ",
      "author": "James Clear",
      "length": 319,
      "rating": 4.35
    }
  ]
}
```

#### Step 3: xxx
#### Step 4: xxx
#### Step 5: xxx
#### Step 6: xxx





[01]:https://flask.palletsprojects.com/en/2.2.x/
[02]:https://getbootstrap.com/
[03]:https://peps.python.org/pep-3333/
[04]:https://jinja.palletsprojects.com/en/3.1.x/
[05]:https://www.fullstackpython.com/web-frameworks.html
[06]:https://www.digitalocean.com/community/tutorials/how-to-make-a-web-application-using-flask-in-python-3
[07]:https://sqlite.org/index.html
[08]:https://www.digitalocean.com/community/tutorials/how-to-serve-flask-applications-with-gunicorn-and-nginx-on-ubuntu-18-04
[09]:https://flask.palletsprojects.com/en/2.2.x/extensions/
[10]:https://pipenv-fork.readthedocs.io/en/latest/#

[20]:
[21]:
[22]:
[23]:
[24]:
[25]:
[26]:
[27]:
[28]:
[29]:
[30]:


