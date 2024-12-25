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



## indexes
- allows quick lookup of a field
- but takes memory, therefore slows down the insert, remove, update operations
-  use them wisely
.find({}).explain('executionStats') ---> this shows the time needed to search or find  [linear search]


.createIndex({name:1})

1 --> ascending order
-1 --> descending order

- by using the index we jus examine only that particular index, therefore no huge execution time to search or do operations on it on particular, but takes more memory.

.getIndexes()

.dropIndex("name1")

db.students.createIndex({name:1})

db.students.find({name:"sandy"}).explain('executionStats')

db.students.getIndexes()

db.students.dropIndex('name_1')

- better to use when we use a lot of searching but not a lot of updating

## Collections
(lil in depth)

**return/print  collections**

show collections

**capped collections , max fields & auto indexing**

db.createCollection("teachers", {capped: true, size: 100000, max: 100},{autoIndexId: false})

**drop collection**

db.courses.drop()
