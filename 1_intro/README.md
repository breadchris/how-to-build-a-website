# Intro to Website Development

## What are websites?

### HTML, CSS, JS

#### HTML

HyperText Markup Language

The structure of a page. Elements are nested in the DOM (Document Object Model).

#### CSS

Cascading Style Sheets

Make your site look pretty. Text too small? `font-size: 300px`. Page feeling cramped? `* { padding: 100px }`. Don't like your text being right side up? `.upsidedown { transform: rotateX(180deg); }`

#### JS

JavaScript

Bring the page alive. HTML and CSS can make your site look pretty, but JavaScript lets you give your page some movement. With HTML hyperlinks and forms it is possible to give a page some life, but JavaScript offers a more customizable user experience (you do not have to rely on the browser's default behavior for inputs, links, etc.).

You can do some real fun things:
```
(function(){javascript:var s=document.createElement('script');s.setAttribute('src','https://nthitz.github.io/turndownforwhatjs/tdfw.js');document.body.appendChild(s);})();
```

### The Internet

The Internet, as it was once described by Alaskan Senator Ted Stevens, is just a "a series of tubes". And if you are ever wondering why your Internet is slow on a given day, he goes on to explain "if you don't understand, those tubes can be filled and if they are filled, when you put your message in, it gets in line and it's going to be delayed by anyone that puts into that tube enormous amounts of material, enormous amounts of material."

When you load a page, your computer, a client, is asking a server for some information. This information, in the world of browsers and websites, is asked for and responded in a standardized way so that everyone involved can understand what is being talked about. This standard is called HTTP.

An example of a client could be:
Your phone, laptop, weird chinese IoT light that you put in your house, ~~NSA listening device~~ Amazon Alexa. 

And the servers these devices talk to are numerous and something we will talk about and build in this class.

#### HTTP
HyperText Transfer Protocol

The protocol for servers and clients to communicate with each other. More on this later.

If you are so inclined to read this: [RFC](https://tools.ietf.org/html/rfc2616) you will be rewarded with endless HTTP knowledge.

#### Inspecting network traffic

In your browser you can typically right click on a page and find an option that says "Inspect" or "Development Tools" and this will let you take a look under the hood.

In this view, there is usually a "Network" tab that you can go to and see what your browser is doing every time you load a page.

## Introduction to Flask

We will be using the Python web framework [Flask](https://flask.palletsprojects.com/en/1.1.x/) to build a website. To simplify development for now, we will also be using `repl.it` to build and run our servers.

Using the code:
```
from flask import Flask
app = Flask(__name__)

@app.route('/')
def hello_world():
    return 'Hello, World!'

app.run(host="0.0.0.0")
```
Checkout this code running on repl.it [here](https://repl.it/@breadchris/minimal-flask-example).

We can get a simple hello world program up and running. Congrats! You have made a server!

Now that your server is live, we can take the url (which you can find in the right pane) and access it from any device that we have that has an internet connection!

Let's do something interesting with this code now. The `hello_world` function is like any other Python function you have written before. So you can add any python code to it that you want!

### Route handlers

[docs](https://flask.palletsprojects.com/en/1.1.x/quickstart/#routing)

### The request object

[docs](https://flask.palletsprojects.com/en/1.1.x/quickstart/#the-request-object)

