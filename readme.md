## Installation in ubuntu

https://ubuntu.com/server/docs/databases-postgresql

## Commands to get started
service postgresql
service postgresql status | start | stop | reload 

## Start PostgreSQL in Terminal

#### Default user is postgres
> sudo su postgres  

#### To start the Command line shell for postgres
 - > psql 
#### PSQL Help
 - > psql --help

#### Got error while using the command to login using port and username [Stackoverflow Solution](https://stackoverflow.com/questions/67572004/pgadmin-and-terminal-fatal-password-authentication-failed-for-user)
 - > psql -h localhost -p 5432 -U neerajkumar testdatabase

- #### use ```\c databaseName``` to connect to specific database after logged in using specific user
- #### use ```\?``` to retreive all psql commands
- #### use ```\h``` to retreive all SQL commands
- #### use ```\l``` command to list the available databases in Postgres
- #### use ```\du``` - to list all tha users available in Postgres

### Create and Update user password
 - ```ALTER USER postgres WITH PASSWORD 'newpassword';```
#### or
 - ```alter user postgres with password 'newpassword';```

### Creating Database
 - ```CREATE DATABASE testdatabase;```

### Follow each readme one by one
  - [Create Table Queries and Commands](./create-table.md)
  - [Select Queries and Commands](./select-queries.md)
