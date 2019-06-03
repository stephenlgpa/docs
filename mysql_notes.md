# MySQL on Bash

## Running the MySQL Server

### MySQL Server Status

`service mysql status`

### Start MySQL

`sudo service mysql start`

### Stop MySQL

`sudo service mysql stop`

---

## Setting passwords

### Set the root user's password

`mysqladmin -u root password`

### Running MySQL as a user with password from a command line

`mysql -u root -p`

This runs mysql as user (`-u`) root, showing a password prompt (`-p`).

### Command line options for `mysql`

- `-u`	user
- `-p`	prompt for the account's password to connect
- `-A`	don't reinitialise the autocomplete lookup
- `-B`	run in batch mode
- `-e statement`	execute the given SQL statement
- `-h hostname`	specify a hostname to a remote database server
- `-N`	suppress column names from the result output
- `-?`	list all options

 


