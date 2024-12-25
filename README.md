## MONGODB

similar to **NOSQL** - not only structured query language
SQL - stores data in rows and columns with table.
nosql- stored as **documents**
data in each document stored as **field-value** pairs.
similar to json format but primarily called as **bson-binary javascript object notation**
ex:
{
name: 'bharath',
age: 20,
destination: student
},
{
name:
age:
destination
}

**document**- group of field value pairs.
**collection**- group of docs.
**database** - group of collections.

INSTALLATION OF THE MONGODB, COMPASS GUI, AND SHELL-MONGOSH


**databases - mongosh**
show dbs  ---> (*to show all the databases*)

use admin ---> (*to switch to a database named admin*)

use school ---> (*to create a new database named school and switch to it*)

db.createCollection("students") ---> (*to create a collection inside the database. collection named students*)

db.dropDatabase() ---> (to drop the database)


**databases - Compass GUI**
just create database and collection using the create button in compass gui.
