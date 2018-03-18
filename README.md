## What is eFood?
eFood is a small scale online order management system.
It uses Bootstrap at front end and Django at backend.

# Configuring project:

- Install and run Postgresql
 - Reffer https://www.postgresql.org/download/

- Create Database and User, grant all privilages. Modify ~~mysite/settings.py~~ accordinlgy
 - ``` $ psql
 - ``` # CREATE DATABASE myproject;
 - ``` # CREATE USER myprojectuser WITH PASSWORD 'password';
 - ``` # ALTER ROLE myprojectuser SET client_encoding TO 'utf8';
 - ``` # ALTER ROLE myprojectuser SET default_transaction_isolation TO 'read committed';
 - ``` # ALTER ROLE myprojectuser SET timezone TO 'UTC';
 - ``` # GRANT ALL PRIVILEGES ON DATABASE myproject TO myprojectuser;
 - ``` # \q

- Install pip
 - ``` $ easy_install pip

- Install virtual environment
 - ``` $ pip install virtualenv

- Make a directory for virtual environment
 - ``` $ mkdir /root/django_env

- Create virtual environment for django project
 - ``` $ virtualenv /root/django_env/

- Activate the virtual env
 - ``` $ source /root/django_env/bin/activate

- Install django and postgresql binding, we are using python3.6 and need to install stable version like “django 1.11”.
 - ``` $ pip install django==1.11 psycopg2

- Go to project directory and create the tables in the database for efood app
 - ``` $ cd mysite
 - ``` $ python manage.py migrate
 - ``` $ python manage.py migrate

- Run Server on local machine
 - ``` $ python manage.py runserver


# Directory Structure:

mysite/
|__ manage.py
|__ README.md
|__ mysite/
|   |__ __init__.py
|    |__ settings.py
|    |__ urls.py
|    |__ wsgi.py
|__ efood/
    |__ admin.py
    |__ apps.py
    |__ __init__.py
    |__ models.py
    |__ tests.py
    |__ urls.py
    |__ views.py
    |__ migrations/
    |   |__ __init__.py
    |__ static/
    |   |__ efood/
    |	|   |__ *.js    # js, css etc files
    |__ templates/
	|__ efood/
            |__ *.html  # html templates


# All product names, logos, and brands are property of their respective owners.
