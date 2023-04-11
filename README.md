# Simple Data Access Layer
This is a very simple sample Data Access Layer (DAL) that accesses both PostgreSQL and MongoDB by only changing one line of code. The DAL can be accessed via http://localhost:3000 with a simple API to fetch all the data, fetch one record, and add a new record.
## Install and Setup
Download or clone the github repository and notice the very simple folder structure. The simple API runs from the root folder of the app and the services folder contains the PostgreSQL and MongoDB DAL code. Te get the code running you will need to;
1. Create databases in both MongoDB and PostgreSQL named "Auth".
2. In this database you will need either a collection or a table name "Logins".
3. In the services folder there are two files named logins.json and logins.sql.
   * the logins.json contains json that can be loaded into the MongoDB collection
   * the logins.sql contains the CREATE statement for the PostgreSQL logins table.
4. In the mdb.js file you will need to alter the uri to point at your instance of MongoDB
## The .env file
You are going to need to add a configure a .env file with the following attributes.
```
SESSION_SECRET=[place_your_secret_here]
PGUSER=[place_your_postgresql_username_here]
PGHOST=localhost
PGDATABASE=Auth
PGPASSWORD=[place_your_postresql_password_here]
PGPORT=5432
PORT=3000
```
## Adding Data
* The MongoDB Auth.logins collection will contain data from loading the json file from the previous step.
* You add data to the PostgreSQL "Logins" table by using the API
``` http://localhost:3000/create?email=new@new&password=new&username=new ```
## Using the simple API
* to list all the logins ``` http://localhost:3000/logins ```
* to list one login 
   * For mongodb you need the objectid ``` http://localhost:3000/logins/642ef05914856e9f7370b8da ``` 
   * For postgresql you need the pk value as an integer; 1,2,4... ``` http://localhost:3000/logins/4 ``` 
* to add a new login ``` http://localhost:3000/create?email=new@new&password=new&username=new ```
