# Creating and using a database

A database gives your website persistent state. Just like cookies give state between a client and a server, a database gives state to your entire application. If your server gets rebooted or you want to make a backup of your data, a database is for you!

There are so many different types of databases out there and some that don't even use SQL (MongoDB, Redis, etc.). SQL is very good at modeling attributes about objects you have in your code. 

For this example, we will be using Sqlite which is a very simple database implementation that exists as a single file (other databases like MySQL have entire server applications which require some setup, we are just going to keep it simple for now).

## SQL

Structured Query Language

This is basically just English as a programming language (until it isn't and then the queries get really complex, but we don't need to worry about that for now :). 

We will be focusing on creating a table, inserting data into it, and then getting data from that table.

### CREATE TABLE

```
CREATE TABLE Persons (
    PersonID INTEGER PRIMARY KEY AUTOINCREMENT,
    LastName TEXT,
    FirstName TEXT,
    Address TEXT,
    City TEXT
);
```
[reference](https://www.w3schools.com/sql/sql_ref_create_table.asp)

[Sqlite Datatypes](https://www.sqlite.org/datatype3.html)

You can only have one `PRIMARY KEY`

### INSERT INTO

```
INSERT INTO Persons (LastName, FirstName, Address, City) VALUES ('Thompson', 'Chris', '123 Lol Street', 'NoWhere');
```

[reference](https://www.w3schools.com/sql/sql_ref_insert_into.asp)

### SELECT

Select everything from `Persons`

```
SELECT * FROM Persons;
```

Select only people whose first name is `Chris`

```
SELECT * FROM Persons WHERE FirstName = 'Chris';
```

Select only people's first and last names if they live in Poolesville.

```
SELECT FirstName, LastName FROM Persons WHERE City = 'Poolesville';
```

[reference](https://www.w3schools.com/sql/sql_ref_select.asp)

#### Playing with it

[repl](https://repl.it/@breadchris/flask-login-with-database)

* Create SQL for database
* Query for the user in login

## SQLAlchemy

Writing SQL queries as strings is just a typo waiting to happen. While it can be sometimes better to do more complex queries by hand, we typically just want to do basic Create, Retreive, Update, and Delete (CRUD) operations on our data. If this is the case for our application, SQLAlchemy is super useful to us. 

This library is an ORM (Object-Relational Mapping) meaning that our objects that we have "modeled" in memory can directly relate to data which is stored in our database.

When we declare a model in code and register it with SQLAlchemy, it knows to go ahead and ensure a table exists for that object. When we go and save a new object, the object's member variables get serialized into an SQL query and it automagically gets inserted into the database!

[Documentation](https://flask-sqlalchemy.palletsprojects.com/en/2.x/quickstart/#a-minimal-application)
