# UsingMongoDB-MongoBD_MERN-CodingDojo
### MONGO-BD - MERN STACK
### objectives
* Create a database called 'my_first_db'.
```> use my_first_db```
* Create "estudiantes" collection.
> db.createCollection("estudiantes")
* Each document you insert into this collection must have the following format:({name: STRING, home_state: STRING, lucky_number: NUMBER, birthday: {month: NUMBER, day: NUMBER, year: NUMBER}})
* Create 5 students with the appropriate information.
> db.estudiantes.insert({name:"pedro",home_state:"arequipa",lucky_number:8,birthday:{month:8,day:13,year:1999}})
* Get all the students.
> db.estudiantes.find()
* Retrieve all students who are from "arequipa" or "cusco".
> db.estudiantes.find({$or:[{home_state:{$in:["arequipa","cusco"]}}]})
* Get all students whose lucky number is greater than 3
> db.estudiantes.find({lucky_number:{$gt:3}})
* Get all students whose lucky number is less than or equal to 10
> db.estudiantes.find({lucky_number:{$lte:10}})
* Get all the students whose lucky number is between 1 and 9 (inclusive)
> db.estudiantes.find({lucky_number:{$gt:1,$lte:9}})
* Add a field to each collection of students called 'intereses' which is an ARRAY. It should contain the following entries: 'coding', 'brunch', 'MongoDB'. Do this in ONE operation.
> db.estudiantes.update({name:"henry"},{$set:{intereses:["codificacion","brunch","mongoDB"]}})
* Add some unique interests for each particular student in each of your interest arrays.
> db.estudiantes.update({name:"maria"},{$set:{intereses:["codificacion","brunch"]}})
* Add interest 'impuestos' to someone's interest matrix.
> db.estudiantes.update({name:"maria"},{$set:{intereses:["codificacion","brunch","impuestos"]}})
* Remove the 'tax' interest you just added.
> db.estudiantes.update({name:"maria"},{$set:{intereses:["codificacion","brunch"]}})
* Remove all students who are from lima.
> db.estudiantes.remove({'home_state':"lima"}) 
 Delete a student by name.
> db.estudiantes.remove({'name':'julian'})
* Remove a student whose lucky number is greater than 5 (ONLY ONE)
> db.estudiantes.remove({lucky_number:{$gt:5}},true)
* Add a field to each student collection called 'number_of_belts' and set it to 0.
> db.estudiantes.insert({name:"julian",number_of_belts:"increment",sequence_value:0})
> function getNextSequenceValue(sequenceName){ var sequenceDocument = db.estudiantes.findAndModify({ query:{number_of_belts:sequenceName}, update:{$inc:{sequence_value:1}}, new:true }); return sequenceDocument.sequence_value; }
* Increment this field by 1 for all students in Washington (Seattle Dojo).
> db.estudiantes.insert({name:"julian",number_of_belts:getNextSequenceValue("increment")}) 
* Rename the 'name' field to 'nombre'
> db.estudiantes.updateMany({},{$rename:{"name":"nombre"}})
* Delete the 'lucky_number' field.
> db.estudiantes.updateMany({},{$unset:{lucky_number:""}}) 
* Add an 'updated_on' field and set the value to the current date.
> db.estudiantes.insert({name:"jaime",updated_on: new Date()})
