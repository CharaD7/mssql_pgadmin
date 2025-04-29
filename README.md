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
- Install *azuresdatastudio* using `sudo snap install azuredatastudio`
- Ensure Preview Features is enabled in *azuresdatastudio* by going to `File > Preferences > Settings` and searching for `Preview Features`
- Connect to the mssql server using *azuresdatastudio* and restore the database using the `.bak` file



## Installing & Setting up PostgreSQL Server for Ubuntu
- To install PostgreSQL, run the following command:
```bash
sudo apt install postgresql postgresql-contrib
sudo snap install pgadmin4
```
- After installing PostgreSQL, you will need to create a user for the database. Run the following command to create a user named `postgres` with a password of `postgres`:
```bash
sudo -u postgres psql
CREATE USER postgres WITH PASSWORD 'your_password';
```
- You can alternatively change postgres user password using the following command:
```bash
sudo -u postgres psql
ALTER USER postgres WITH PASSWORD 'your_password';
```
- Type `\q` to exit the psql prompt and return to the shell.
- Create your custom database and grant all accress to the user you created:
```bash
CREATE DATABASE your_database_name;
GRANT ALL PRIVILEGES ON DATABASE your_database_name TO postgres;
```


## Restoring MSSQL Database Backup to PostgreSQL
- Install pgloader using `sudo apt install pgloader`
- To restore your MSSQL database backup to your PostgreSQL database, run the following command:
```bash
pgloader mssql://<username>:<password>@<server>:<port>/<database> pgsql://<username>:<password>@<server>:<port>/<database>
```

[!NOTE]

Supplying port number is not  mandatory, unless you have set a custom port number for MSSQL server and/or postgreSQL server.
