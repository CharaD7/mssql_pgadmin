# Setting up MSSQL and PostgreSQL databases for development on Linux Ubuntu

> This project seeks to help you setup your mssql database,
> restore a backup into the database server, and load the 
> backup into PostgreSQL db server.


## Installing & Setting up MSSQL Server for Ubuntu

- Make sure you have liblber installed using `sudo apt install libldap2-dev`
- Run the [install-mssql.sh](https://github.com/Microsoft/sql-server-samples/blob/master/samples/scripts/install-mssql.sh) script to install mssql server after replacing the variables' values with your actual connection string values


### Preparing MSSQL Server for Database Restore

- Persistently create the backup directory using `sudo mkdir /var/opt/mssql/backup`
- Persistently create the data directory using `sudo mkdir /var/opt/mssql/data`
- Persistently create the log directory using `sudo mkdir /var/opt/mssql/log`
- Move your `.bak` file to the backup directory using `sudo mv <file-name>.bak /var/opt/mssql/backup`


## Installing PostgreSQL Server for Ubuntu
