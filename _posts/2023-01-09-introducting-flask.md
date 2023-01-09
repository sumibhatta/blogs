---
layout: post
title: Getting Started with Flask
subtitle: Flask as a Micro Framework
cover-img: /assets/img/flask1.png
thumbnail-img: /assets/img/flask.png
share-img: /assets/img/flask1.png
tags: [flask, webdev, micro-framework]
---

### Introduction

Flask is a web-development micro framework developed in Python. It is beginner friendly and easy to learn and use since it doesn't have any boilerplate code and dependencies. 

It was Developed by **Armin Roancher** as an April Fool's joke which later gained massive popularity and is maintained till today as a Open-Source Project.


### FullStack vs Micro Frameworks

**FullStack Frameworks** are bundled together with Request Routing , Request Processing, MVC, ORM, Security, Code Generation, Template Engines etc. which makes it easier to develop complex applications easy.

Similarly, **Micro Framework** is light-weight and come together with least routing processes to process incoming request and generate output. It only provides the necessary components for web development, such as routing, request handling, sessions, and so on. For the other functionalities such as data handling, the developer can write a custom module or use an extension.It is the first choice to develop REST application and provide REST services to various interface.

Flask is used by Netflix, Reddit, AirBnB, Lyft, Mozilla, MIT, Uber and so on...


### Features

* It provies development server and debugger
* It uses Jinja2 templates
* It is compailent with WSGI 1.0.
* It provides integrated support for unit testing
* Many extensions are available to flask to enhance other functionalities.


### WSGI and JINJA2

**WSGI** (Web Server Gateway Interface) describes specification concerning communication between web server and client application. Flask is 100% WSGI compliant.

Some benifits of WSGI are:
* Flexibility
* Interoperability
* Scalibility
* Efficiency

**JINJA** is a template language in python i.e. we can use it inside HTML so that the contents becomes dynamic.



### Installation and Setup


#### Prerequisits

* System with Python Installed
* A text editor or IDE
* [I am using windows 11]


#### Process

* Install virtualenv

    {% highlight console linenos %}
    py -2 -m pip install virtualenv
    {% endhighlight %} 


* Create an environment

    {% highlight console linenos %}
    python3 -m venv <name_of_env>
    {% endhighlight %} 



* Activate it

    {% highlight console linenos %}
    <name_of_env>\Scripts\activate
    {% endhighlight %} 


* Install flask

    {% highlight console linenos %}
    pip install flask
    {% endhighlight %} 


* Create file hello.py

    {% highlight python linenos %}

    # import FLask module form flask package
    from flask import Flask

    # create Flask object
    app = Flask(__name__)


    # assign url route
    @app.route("/")

    # create view function to tell application what to do
    def hello():
        return "Hello World!"


    # run the application in main
    if __name__ == "__main__":
        app.run(debug = True, host = "0.0.0.0", port = 3000)
    {% endhighlight %} 


* Run the code

    {% highlight console linenos %}

    $env:FLASK_APP = "webapp"

    python -m flask run

    {% endhighlight %} 
    
