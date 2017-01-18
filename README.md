![logo](https://www.mysql.com/common/logos/logo-mysql-170x115.png)

# What is MySQL?

MySQL is the world's most popular open source database. With its proven performance, reliability and ease-of-use, MySQL has become the leading database choice for web-based applications, covering the entire range from personal projects and websites, via online shops and information services, all the way to high profile web properties including Facebook, Twitter, YouTube, Yahoo! and many more.

For more information and related downloads for MySQL Server and other MySQL products, please visit http://www.mysql.com.

# MySQL Snap Image
The MySQL snap image is an experimental release of MySQL for the snap universal Linux package system (http://snapcraft.io/).
This image should be used for testing only, and is not suitable for a production environment.

## Commands
- mysql.client: Runs the MySQL client
- mysql.server: Runs the MySQL server
- mysql.startup: Initializes database if necessary, then starts the server
- mysql.help: Shows this document

## Usage guide
The MySQL snap requires access to the process-control interface. You connect it by running:
 snap connect mysql:process-control core:process-control

### Running the snap
* Install the snap as usual
* Run sudo snap connect mysql:process-control ubuntu-core:process-control
* Run mysql.startup to initialize and start the server
* Run mysql.client -uroot -p

### Running the snap a system service
Running MySQL as a system service requires root access, but the server itself should never run as root, so it drops privileges to a dedicated user. This user must own the server files and directories. Currently snapd blocks access to creating users and changing process user, so the only way to do this is to disable the restrictions by installing the snap with the --devmode argument.

### Files and directories
The first time you run mysql.startup, it will generate the following in $HOME/snap/mysql/common (if run as root, /var/snap/mysql/common is used instead):
- conf/my.cnf: Basic configuration file
- data/: Data directoriy
- files/: Default location for the secure-file-priv option
- log/: Location of error log
- run/: Location of sock and pid files
