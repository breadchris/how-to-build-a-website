# HTTP Methods and HTML

## HTTP Methods

### GET

> The GET method requests a representation of the specified resource. Requests using GET should only retrieve data.

### POST

> The POST method is used to submit an entity to the specified resource, often causing a change in state or side effects on the server.

### Other HTTP Methods

HEAD, PUT, DELETE, CONNECT, OPTIONS, TRACE, PATCH

[more info](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods)

### Testing HTTP methods against your website

[API Tester](https://apitester.com/) or [curl](https://curl.haxx.se/docs/manual.html) (you should get comfortable with using curl, it is such a useful tool

## HTML

Flask [rendering templates](https://flask.palletsprojects.com/en/1.1.x/quickstart/#rendering-templates)

### Creating an HTML Form

We will need to know a little more about `<form>` and `<input>`.

A quick note on website accessibility: using native compontents like this vs. using `<div>` and styling it how you want and programming the actions you need in javascript will help those who use screenreaders or rely on keyboard shortcuts to natigate around a page.

Homework: Watch [Intro to HTML](https://www.khanacademy.org/computing/computer-programming/html-css/intro-to-html/v/making-webpages-intro) on Khan Academy

#### Form

The atributes `action` and `method` are important. `action` is the URL route which will be requested once the form is submitted. `method` is the HTTP method which will be used when making the request.

[w3schools reference](https://www.w3schools.com/tags/tag_form.asp)


#### Input

The attribute `type` lets us specify how the input will show up (we will use `"text"` and `"password"`. And the attribute `name` is the name of the variable that will be set in the HTTP request to the server.

[w3schools reference](https://www.w3schools.com/tags/tag_input.asp)

### CSS

Reference: [w3schools css](https://www.w3schools.com/css/default.asp)

Homework: Watch [Intro to CSS](https://www.khanacademy.org/computing/computer-programming/html-css/intro-to-css/pt/css-basics)

## Flask Templates

`render_template`

The template folder will typically be named `templates` and placed in the root of our project. In this folder we will place `*.html` files which will be rendered by the Jinja2 templating engine that Flask uses.

#### Rendering data from Python to HTML

app.py
```
from flask import render_template
@app.route('/hello/<name>')
def hello(name=None):
	return render_template('hello.html', name=name)
```

hello.html
```
<html>
	<p>Hello, {{ name }}</p>
</html>
```

#### Adding some style to your site

```
<html>
	<style> 

		.login-container {
			color: white;
			background-color: red;
		}
		
	</style>

	<div class="login-container">
		<p>This background is red, and the text is white!</p>
	</div>
</html>
```
