# Securing your site

## Preventing SQL Injections

Binding parameters to queries

```
from sqlalchemy.sql import text
with engine.connect() as con:

    data = ( { "id": 1, "title": "The Hobbit", "primary_author": "Tolkien" },
             { "id": 2, "title": "The Silmarillion", "primary_author": "Tolkien" },
    )

    statement = text("""INSERT INTO book(id, title, primary_author) VALUES(:id, :title, :primary_author)""")

    for line in data:
        con.execute(statement, **line)
```

## Password Hashing

Websites are hacked [all the time]()https://haveibeenpwned.com/), it is important when you are storing a user's information that you are handling it as securely as possible.

Hashes are one way functions which are supposed to maintain the input level of entropy, but often change the size of the input data. These functions are also deterministic, meaning for a given input, there is always the same output. However, a one to one mapping of output to input is not guarunteed.

Of course with this property of a hash function, [hash collision research](https://shattered.io/) is a thing and a concern for a lot of people who rely on hashes to associate unique values with some identity (such as passwords).


[flask-bcrypt](https://flask-bcrypt.readthedocs.io/en/latest/)

### Brute forcing passwords

Password reuse - On another site, a user could be using the same password. When that other site is breached, the hacker can try that password on other sites.

Rainbow tables - Hash every combination of characters and try to do a quick lookup of that hash.

Never double hash your passwords, that does not make them more secure.

The best passwords look like: [Horse battery staple correct](https://xkcd.com/936/)

## 2-Factor Authentication

In the case that a hacker is able to reuse a password from another site, 2-factor authentication can thwart their ability to do anything.

[Google Account Hygine](https://security.googleblog.com/2019/05/new-research-how-effective-is-basic.html)

Let's try implementing a [Time-based One-time Password](https://en.wikipedia.org/wiki/Time-based_One-time_Password_algorithm) in our login flow.

[Adding two factor authentication in Flask](https://blog.miguelgrinberg.com/post/two-factor-authentication-with-flask)

## Forgot password

How would we want to implement this?
