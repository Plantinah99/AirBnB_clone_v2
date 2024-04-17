# AirBnB Clone - Database Storage

## Table of Contents
- [Introduction](#introduction)
- [Project Overview](#project-overview)
- [Learning Objectives](#learning-objectives)
- [Requirements](#requirements)
- [File Structure](#file-structure)
- [Tests](#tests)
- [Database Setup](#database-setup)
- [Storage Engines](#storage-engines)
- [Models](#models)
- [Relationships](#relationships)
- [Conclusion](#conclusion)

## Introduction

This project is the continuation of the AirBnB clone project, where the goal is to create a web application that mimics the functionality of the AirBnB website. In this phase, the focus is on transitioning the storage system from a file-based storage (FileStorage) to a database-based storage (DBStorage) using SQLAlchemy. This modification of the project is by Hector Macassa and Plantinah Tshukudu.

## Project Overview

The objective of this project is to implement a database storage engine that can handle various models and their relationships. The project includes the following tasks:

1. Forking the existing codebase and updating the repository name to `AirBnB_clone_v2`.
2. Ensuring all existing unit tests pass with both storage engines (FileStorage and DBStorage).
3. Implementing a new storage engine, `DBStorage`, that uses SQLAlchemy to interact with a MySQL database.
4. Updating the existing models to work with the new `DBStorage` engine, including the addition of SQLAlchemy-specific attributes and relationships.
5. Implementing a new model, `Amenity`, and its relationship with the `Place` model.
6. Ensuring the console application (command interpreter) works with both storage engines.

## Learning Objectives

By the end of this project, you should be able to explain the following concepts to anyone, without the help of Google:

- What is Unit testing and how to implement it in a large project
- What are `*args` and how to use them
- What are `**kwargs` and how to use them
- How to handle named arguments in a function
- How to create a MySQL database
- How to create a MySQL user and grant it privileges
- What ORM means
- How to map a Python Class to a MySQL table
- How to handle 2 different storage engines with the same codebase
- How to use environment variables

## Requirements

The project has the following requirements:

- Python Scripts:
  - Allowed editors: `vi`, `vim`, `emacs`
  - All files will be interpreted/compiled on Ubuntu 20.04 LTS using Python 3.8.5
  - All files should end with a new line
  - The first line of all files should be exactly `#!/usr/bin/python3`
  - A `README.md` file, at the root of the folder of the project, is mandatory
  - The code should use the `pycodestyle` (version 2.8.\*) style guide
  - All files must be executable

- Python Unit Tests:
  - Allowed editors: `vi`, `vim`, `emacs`
  - All files should end with a new line
  - All test files should be inside a folder `tests`
  - You have to use the `unittest` module
  - All test files should be Python files (extension: `.py`)
  - All test files and folders should start by `test_`
  - Your file organization in the `tests` folder should be the same as your project
  - All tests should be executed by using this command: `python3 -m unittest discover tests`
  - You can also test file by file by using this command: `python3 -m unittest tests/test_models/test_base_model.py`

- SQL Scripts:
  - Allowed editors: `vi`, `vim`, `emacs`
  - All files will be executed on Ubuntu 20.04 LTS using MySQL 8.0
  - Your files will be executed with SQLAlchemy version 1.4.x
  - All files should end with a new line
  - All SQL queries should have a comment just before (i.e., syntax above)
  - All SQL keywords should be in uppercase (SELECT, WHERE, ...)
  - A `README.md` file, at the root of the folder of the project, is mandatory
  - The length of your files will be tested using `wc`

## File Structure

The project's file structure is as follows:

```
AirBnB_clone_v2/
├── console.py
├── models/
│   ├── __init__.py
│   ├── base_model.py
│   ├── engine/
│   │   ├── __init__.py
│   │   ├── file_storage.py
│   │   └── db_storage.py
│   ├── user.py
│   ├── state.py
│   ├── city.py
│   ├── amenity.py
│   ├── place.py
│   └── review.py
├── tests/
│   └── test_models/
│       ├── __init__.py
│       ├── test_base_model.py
│       ├── test_user.py
│       ├── test_state.py
│       ├── test_city.py
│       ├── test_amenity.py
│       ├── test_place.py
│       └── test_review.py
├── setup_mysql_dev.sql
├── setup_mysql_test.sql
└── README.md
```

## Tests

To run the unit tests for the project, use the following command:

```
python3 -m unittest discover tests
```

This command will run all the tests in the `tests` directory.

You can also run tests for a specific file by using the following command:

```
python3 -m unittest tests/test_models/test_base_model.py
```

This command will run the tests for the `BaseModel` class.

## Database Setup

The project requires a MySQL database for the `DBStorage` engine. The necessary setup scripts are provided in the `setup_mysql_dev.sql` and `setup_mysql_test.sql` files.

To set up the development database, run the following command:

```
cat setup_mysql_dev.sql | mysql -hlocalhost -uroot -p
```

To set up the test database, run the following command:

```
cat setup_mysql_test.sql | mysql -hlocalhost -uroot -p
```

## Storage Engines

The project supports two storage engines:

1. **FileStorage**: The original storage engine that uses a JSON file to store the data.
2. **DBStorage**: The new storage engine that uses a MySQL database to store the data.

The storage engine to be used is determined by the `HBNB_TYPE_STORAGE` environment variable.

## Models

The project includes the following models:

- `BaseModel`: The base class for all other models, providing common attributes and methods.
- `User`: Represents a user of the AirBnB application.
- `State`: Represents a state.
- `City`: Represents a city.
- `Amenity`: Represents an amenity.
- `Place`: Represents a place (e.g., a rental).
- `Review`: Represents a review of a place.

Each model is implemented as a Python class that inherits from the `BaseModel` class and includes the necessary SQLAlchemy-specific attributes and relationships.

## Relationships

The project includes the following relationships between the models:

- `User` has a one-to-many relationship with `Place` and `Review`.
- `State` has a one-to-many relationship with `City`.
- `City` has a one-to-many relationship with `Place`.
- `Place` has a many-to-many relationship with `Amenity`.
- `Place` has a one-to-many relationship with `Review`.

These relationships are implemented using SQLAlchemy's relationship features, including foreign keys and association tables.

## Conclusion

This project demonstrates the transition from a file-based storage system to a database-based storage system using SQLAlchemy. By implementing the `DBStorage` engine, the project can now handle more complex data models and relationships, providing a more robust and scalable storage solution for the AirBnB clone application.

