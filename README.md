# MONGODB

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

**in mongosh**


db.students.insertOne({name: "Spongebob, age: 30, gpa: 8.9"})

 db.students.find()


db.students.insertMany([{name: 'bharat', age: 21, gpa: 8},{name: 'sandy', age: 27, gpa: 8.5},{name: "gary", age: 24, gpa: 9}])


**datatypes in dbs**

strings, integers-whole numbers(no decimal), doubles-(decimals), bool, new Date(), null, arrays ['    ', '   ', "   "], nested objects.


## **sort**

by names in alphabetical order:

db.students.find().sort({name: 1})


sort by reverse alphabetical:
db.students.find().sort({name:-1})

sort by gpa (*small to big*): (1)

 db.students.find().sort({gpa: 1})


sort by gpa (*big to small*): (-1)

db.students.find().sort({gpa: -1})


## **limiting the amount of documents** *returned/printed*


db.students.find().limit(1)


## **find()**

db.students.find({name: "sandy"})

db.students.find({gpa: 10})

db.students.find({gpa: 6, fullTime: true})


db.students.find({},{name: true}). ---> *(gives all names in the docs. here first parameter is called as query parameter, and second parameter is projection parameter)*

## **update documents in mongoDB**


db.students.updateOne({name: 'sandy'},{$set: {fullTime: true}})


db.students.updateOne({_id: ObjectId('676be7046ae0ecce5577f827')}, {$set: {fullTime: false}})

to **remove a field**


db.students.updateOne({_id: ObjectId('676be7046ae0ecce5577f827')}, {$unset: {fullTime: false}})

## **update many fields**

db.students.updateMany({}, {$set: {fullTime: false}})

db.students.updateMany({fullTime: {$exists:false}},{$set:{fullTime:true}})

## **delete docs**

db.students.deleteOne({name: "newName"})

db.students.deleteMany({fullTime: true})

db.students.deleteMany({registerDate: {$exists:false}})


## **Comparison operators**

db.students.find({name:{$ne:"larry"}})

 db.students.find({age:{$gt:20}})

db.students.find({age:{$lt:20}})

db.students.find({age:{$gte:20}})

db.students.find({gpa:{$gte:7,$lte: 10}})

db.students.find({name: {$in: ['sandy', 'patrick', 'name']}})

db.students.find({name: {$nin: ['sandy', 'patrick', 'name']}})

## **logical operators**

$and

$not

$nor

$or


db.students.find({$and: [{gpa: {$gte:7}}, {age: {$lte: 15}}]})

db.students.find({$or: [{gpa: {$gte:7}}, {age: {$lte: 15}}]})
