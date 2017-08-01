##### To start with AWS and Web Development using Python you need Elastic Beanstalk on AWS.

Install the Elastic Beanstalk Command Line Interface (EB CLI)

The Elastic Beanstalk Command Line Interface (EB CLI) is a command line client that you can use to create, configure, and manage Elastic Beanstalk environments. The EB CLI is developed in Python and requires Python version 2.7, version 3.4, or newer.

Note
Amazon Linux comes with Python 2.7 and pip starting with version 2015.03.
The primary distribution method for the EB CLI on Linux, Windows, and macOS is pip, a package manager for Python that provides an easy way to install, upgrade, and remove Python packages and their dependencies. For macOS, you can also get the latest version of the EB CLI with Homebrew.

If you already have pip and a supported version of Python, you can install the EB CLI with the following command:

```
$ pip install --upgrade --user awsebcli
```

The --upgrade option tells pip to upgrade any requirements that are already installed. The --user option tells pip to install the program to a subdirectory of your user directory to avoid modifying libraries used by your operating sytem.

Note
If you encounter issues when you attempt to install the EB CLI with pip, you can install the EB CLI in a virtual environment to isolate the tool and its dependencies, or use a different version of Python than you normally do.
After you install the EB CLI, add the path to the executable file to your PATH variable:

```
Linux – ~/.local/bin
```

```
macOS – ~/Library/Python/3.4/bin
```


To modify your PATH variable (Linux, macOS, or Unix)

1. Find your shell's profile script in your user folder. If you are not sure which shell you have, run echo $SHELL.

```
$ ls -a ~
.  ..  .bash_logout  .bash_profile  .bashrc  Desktop  Documents  Downloads
```

 Bash – .bash_profile, .profile, or .bash_login.
 Zsh – .zshrc
 Tcsh – .tcshrc, .cshrc or .login.

2. Add an export command to your profile script. The following example adds the path represented by LOCAL_PATH to the current PATH variable.
```
export PATH=LOCAL_PATH:$PATH
```

3. Load the profile script described in the first step into your current session. The following example loads the profile script represented by PROFILE_SCRIPT into your current session.

```
$ source ~/PROFILE_SCRIPT
```


```
$ eb --version
```

EB CLI 3.7.8 (Python 3.4.3)
The EB CLI is updated regularly to add functionality that supports the latest Elastic Beanstalk features. To update to the latest version of the EB CLI, run the installation command again.

```
$ pip install --upgrade --user awsebcli
```

If you need to uninstall the EB CLI, use pip uninstall.

```
$ pip uninstall awsebcli
```


```
install PostgreSQL 9 in Mac OSX via Homebrew


Mac OS X Snow Leopard
System Version: Mac OS X 10.6.5
Kernel Version: Darwin 10.5.0


Install notes for PostgreSQL 9.0.1 install using Homebrew:
	sh-3.2# brew install postgresql
	sh-3.2# brew install postgresql
	Warning: It appears you have MacPorts or Fink installed.
	Software installed with MacPorts and Fink are known to cause problems.
	If you experience issues try uninstalling these tools.
	==> Downloading ftp://ftp.ossp.org/pkg/lib/uuid/uuid-1.6.2.tar.gz
	######################################################################## 100.0%
	==> ./configure --disable-debug --without-perl --without-php --without-pgsql --p
	==> make
	==> make install
	/usr/local/Cellar/ossp-uuid/1.6.2: 11 files, 364K, built in 17 seconds
	==> Downloading http://ftp9.us.postgresql.org/pub/mirrors/postgresql/source/v9.0
	######################################################################## 100.0%
	==> ./configure --disable-debug --prefix=/usr/local/Cellar/postgresql/9.0.1 --enable-thread
	==> make install
	==> cd contrib/adminpack; make install
	==> cd contrib/dblink; make install
	==> cd contrib/fuzzystrmatch; make install
	==> cd contrib/lo; make install
	==> cd contrib/uuid-ossp; make install
	==> cd contrib/pg_buffercache; make install
	==> cd contrib/pg_trgm; make install
	==> cd contrib/pgcrypto; make install
	==> cd contrib/tsearch2; make install
	==> cd contrib/vacuumlo; make install
	==> cd contrib/xml2; make install
	==> cd contrib/intarray; make install
	==> cd contrib/pg_upgrade; make install
	==> cd contrib/pg_upgrade_support; make install
	==> cd contrib/hstore; make install
	==> Caveats
	If builds of Postgresl 9 are failing and you have version 8.x installed,
	you may need to remove the previous version first. See:
	  https://github.com/mxcl/homebrew/issues/issue/2510

	To build plpython against a specific Python, set PYTHON prior to brewing:
	  PYTHON=/usr/local/bin/python  brew install postgresql
	See:
	  http://www.postgresql.org/docs/9.0/static/install-procedure.html


	If this is your first install, create a database with:
	    initdb /usr/local/var/postgres

	If this is your first install, automatically load on login with:
	    cp /usr/local/Cellar/postgresql/9.0.1/org.postgresql.postgres.plist ~/Library/LaunchAgents
	    launchctl load -w ~/Library/LaunchAgents/org.postgresql.postgres.plist

	If this is an upgrade and you already have the org.postgresql.postgres.plist loaded:
	    launchctl unload -w ~/Library/LaunchAgents/org.postgresql.postgres.plist
	    cp /usr/local/Cellar/postgresql/9.0.1/org.postgresql.postgres.plist ~/Library/LaunchAgents
	    launchctl load -w ~/Library/LaunchAgents/org.postgresql.postgres.plist

	Or start manually with:
	    pg_ctl -D /usr/local/var/postgres -l /usr/local/var/postgres/server.log start

	And stop with:
	    pg_ctl -D /usr/local/var/postgres stop -s -m fast

	If you want to install the postgres gem, including ARCHFLAGS is recommended:
	    env ARCHFLAGS="-arch x86_64" gem install pg

	To install gems without sudo, see the Homebrew wiki.
	==> Summary
	/usr/local/Cellar/postgresql/9.0.1: 1219 files, 20M, built in 3.4 minutes
	sh-3.2# exit

Init Database:
	Erics-MacBook:~ eric$ initdb /usr/local/var/postgres
	The files belonging to this database system will be owned by user "eric".
	This user must also own the server process.

	The database cluster will be initialized with locale en_US.UTF-8.
	The default database encoding has accordingly been set to UTF8.
	The default text search configuration will be set to "english".

	creating directory /usr/local/var/postgres ... ok
	creating subdirectories ... ok
	selecting default max_connections ... 20
	selecting default shared_buffers ... 2400kB
	creating configuration files ... ok
	creating template1 database in /usr/local/var/postgres/base/1 ... ok
	initializing pg_authid ... ok
	initializing dependencies ... ok
	creating system views ... ok
	loading system objects' descriptions ... ok
	creating conversions ... ok
	creating dictionaries ... ok
	setting privileges on built-in objects ... ok
	creating information schema ... ok
	loading PL/pgSQL server-side language ... ok
	vacuuming database template1 ... ok
	copying template1 to template0 ... ok
	copying template1 to postgres ... ok

	WARNING: enabling "trust" authentication for local connections
	You can change this by editing pg_hba.conf or using the -A option the
	next time you run initdb.

	Success. You can now start the database server using:

	    postgres -D /usr/local/var/postgres
	or
	    pg_ctl -D /usr/local/var/postgres -l logfile start

Run Database:
	Erics-MacBook:~ eric$ pg_ctl -D /usr/local/var/postgres -l /usr/local/var/postgres/server.log start &

Create a Database:
	Erics-MacBook:~ eric$ createdb mydb

Open the mydb database and do some test:
	Erics-MacBook:~ eric$ psql mydb
	psql (9.0.1)
	Type "help" for help.

	mydb=# create table users(id serial, name varchar(25));
	NOTICE:  CREATE TABLE will create implicit sequence "users_id_seq" for serial column "users.id"
	CREATE TABLE
	mydb=# insert into users(name) values('eric');
	INSERT 0 1
	mydb=# insert into users(name) values('lxneng');
	INSERT 0 1
	mydb=# select * from users;
	 id |    name
	----+-------------
	  1 | eric
	  2 | lxneng
	mydb=# \q
```
















To summarize :

# install the binary
$ brew install postgresql

# init it
$ initdb /usr/local/var/postgres

# start the postgres server
$ postgres -D /usr/local/var/postgres

# create your database
$ createdb mydb
Then play around with it:

Erics-MacBook:~ eric$ psql mydb
psql (9.0.1)
Type "help" for help.

mydb=# create table users(id serial, name varchar(25));
NOTICE:  CREATE TABLE will create implicit sequence "users_id_seq" for serial column "users.id"
CREATE TABLE
mydb=# insert into users(name) values('eric');
INSERT 0 1
mydb=# insert into users(name) values('lxneng');
INSERT 0 1
mydb=# select * from users;
 id |    name
----+-------------
  1 | eric
  2 | lxneng
mydb=# \q
