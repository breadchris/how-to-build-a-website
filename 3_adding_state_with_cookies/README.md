# Adding state to an otherwise stateless protocol

## HTTP is 'stateless'

When you are talking with someone in a conversation, there is a context in which you are talking. For example, if someone earlier in the converstaion mentions they "like cats", you can use the phrase "thing you like" to refer to the fact that they "like cats". 

HTTP is a 'stateless' protocol meaning that there is no idea of a context by default. In order to add a context to the conversation between your browser and the server, we use 'cookies' to let both the client and server know what is up. 

Cookies are usually just a _securely_ generated, random value which uniquely identifies a particular user. The server creates this cookie and in the response to a request made by your browser, the server will use the header [Set-Cookie](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Set-Cookie) to instruct your browser to store this provided cookie in its memory and send it along with every request.

Imagine talking to someone, but they have a very hard time remembering who they are talking to. You might devise a plan where they give you a random number, that only you have, and every time you talk to them, the first thing that you say is the random number that you are.

Some sites might set cookies in your browser by simply visiting the site (all of those annoying "we use cookies on this site to ~~track you~~ provide analytics" popups are the site telling you that they do this). A more useful example of cookies takes place after a login. Typically we call this type of cookie a "session cookie" since we establish a session for the user in which they do not have to enter their password on every http request.

## Sessions in Flask

[Documentation](https://flask.palletsprojects.com/en/1.1.x/quickstart/#sessions)

```
from flask import Flask, session, redirect, url_for, request
from markupsafe import escape

app = Flask(__name__)

# Set the secret key to some random bytes. Keep this really secret!
app.secret_key = b'_5#y2L"F4Q8z\n\xec]/'

@app.route('/')
def index():
    if 'username' in session:
        return 'Logged in as %s' % escape(session['username'])
    return 'You are not logged in'

@app.route('/login', methods=['GET', 'POST'])
def login():
    if request.method == 'POST':
        session['username'] = request.form['username']
        return redirect(url_for('index'))
    return '''
        <form method="post">
            <p><input type=text name=username>
            <p><input type=submit value=Login>
        </form>
    '''

@app.route('/logout')
def logout():
    # remove the username from the session if it's there
    session.pop('username', None)
    return redirect(url_for('index'))
```

## Homework

Create a registration page
