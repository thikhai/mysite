# What is eFood?
eFood is a small scale online order management system.
It uses Bootstrap at front end and Django at backend.

## Configuring project:

- Clone the project.
~~~
$ git clone https://github.com/thikhai/mysite.git
~~~
- Install pip
~~~
$ easy_install pip
~~~
- Install virtual environment
~~~
$ pip install virtualenv
~~~
- Make a directory for virtual environment
~~~
$ mkdir /root/django_env
~~~
- Create virtual environment for django project
~~~
$ virtualenv /root/django_env/
~~~
- Activate the virtual env
~~~
$ source /root/django_env/bin/activate
~~~
- Install django and postgresql binding, we are using python3.6 and need to install stable version like “django 1.11”.
~~~
$ pip install django==1.11 psycopg2 psycopg2-binary
~~~
- Install and run Postgresql. Refer [Guide](https://www.postgresql.org/download/)
- Create Database and User, grant all privilages.
~~~
  $ sudo su - postgres
  $ psql
  # CREATE DATABASE myproject;
  # CREATE USER myprojectuser WITH PASSWORD 'password';
  # ALTER ROLE myprojectuser SET client_encoding TO 'utf8';
  # ALTER ROLE myprojectuser SET default_transaction_isolation TO 'read committed';
  # ALTER ROLE myprojectuser SET timezone TO 'UTC';
  # GRANT ALL PRIVILEGES ON DATABASE myproject TO myprojectuser;
  # \q
~~~
- Modify `mysite/settings.py` with database setting we just created.
~~~
$ cd mysite/

$ vi mysite/settings.py

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'myproject',
        'USER': 'myprojectuser',
        'PASSWORD': 'password',
        'HOST': 'localhost',
        'PORT': '5432',
    }
}
~~~
- Go to project directory and create the tables in the database for efood app
~~~
$ python manage.py makemigrations
$ python manage.py migrate
~~~

**Note** : If getting error:
`django.db.utils.OperationalError: FATAL:  Ident authentication failed for user "myprojectuser"`
then change `ident` to `md5` in  `/var/lib/pgsql/10/data/pg_hba.conf`:

~~~
# IPv6 local connections:
host    all             all             ::1/128                 ident
~~~

- After making above change restart postgres service:
~~~
$ systemctl restart postgresql-10
$ python manage.py makemigrations
$ python manage.py migrate
~~~

- Run Server on local machine
~~~
$ python manage.py runserver
~~~

## Directory Structure:
~~~
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

~~~

##### All product names, logos, and brands are property of their respective owners.
