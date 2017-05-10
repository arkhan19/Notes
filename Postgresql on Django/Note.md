# Prepare PostgreSQL for Django
### Open Terminal/Command prompt

Open `postgresql`:

```
$ psql

```

Resulting in something like:

```
psql (9.6.2)
Type "help" for help.

f3n1xx=#
```
Where `f3n1xx` would be your username.


Create database with new database user:

```
f3n1xx=# CREATE DATABASE testdb;
f3n1xx=# CREATE USER testadminuser WITH PASSWORD 'password';
f3n1xx=# ALTER ROLE testadminuser SET client_encoding TO 'utf8';
f3n1xx=# ALTER ROLE testadminuser SET default_transaction_isolation TO 'read committed';
f3n1xx=# ALTER ROLE testadminuser SET timezone TO 'UTC';
f3n1xx=# GRANT ALL PRIVILEGES ON DATABASE testdb TO testadminuser;
```


To Exit:

	f3n1xx=# \q



### Install & Test with Django
	

Install/upgrade virtualenv

	sudo pip install virtualenv --upgrade
	cd ~/Desktop
	mkdir newenv
	cd newenv
	virtualenv .
	source bin/activate
	pip install django psycopg2
	django-admin.py startproject testdb
	cd testdb


Update your `Django` `DATABASES` settings (`settings.py`) to:

	DATABASES = {
	    'default': {
	        'ENGINE': 'django.db.backends.postgresql_psycopg2',
	        'NAME': 'testdb',
	        'USER': 'testadminuser',
	        'PASSWORD': 'password',
	        'HOST': 'localhost',
	        'PORT': '',
	    }
	}



### PostgreSQL Commands (Basics)

Open `postgresql`

	$ psql


Open `postgresql` With User & Database:


	$ psql -U testadminuser testdb



List all Databases:

	f3n1xx=# \list


Select Database:

	f3n1xx=# \connect testdb


Delete (drop) Database from `postgresql`:

	f3n1xx=# DROP DATABASE testdb;



Delete (drop) Database from Command line:

	$ dropdb testdb


Connect & List all tables:

	f3n1xx=# \connect testdb
	testdb=# \dt


Drop a table

	f3n1xx=# \connect testdb
	testdb=# \dt
	testdb=# DROP TABLE auth_group CASCADE;

------------------------------------------------------------------------------------------------------------------------------------------
[Migrating Sqlite3 to Postgresql](http://stackoverflow.com/questions/4581727/convert-sqlite-sql-dump-file-to-postgresql/4581921#4581921)
