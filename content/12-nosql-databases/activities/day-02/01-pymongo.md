+++
title = "01.  PyMongo 👩‍🏫🧑‍🏫"
weight = 1
tags = ["mongo"] 
+++

```python

# Module used to connect Python with MongoDB
from pymongo import MongoClient
# The default port used by MongoDB is 27017
# https://docs.mongodb.com/manual/reference/default-mongodb-port/
mongo = MongoClient(port=27017)

# Define the 'classDB' database in Mongo
db = mongo.classDB
# Insert a document into the 'classroom' collection
db.classroom.insert_one(
    {
        'name': 'Ahmed',
        'row': 3,
        'favorite_python_library': 'Matplotlib',
        'hobbies': ['Running', 'Stargazing', 'Reading']
    }
)

# Query the classroom collection.
classroom = db.classroom.find()

# See the data in collection
for student in classroom:
    print(student)

# Update a document
db.classroom.update_one(
    {'name': 'Ahmed'},
    {'$set':
        {'row': 4}
     }
)

# Query the classroom collection
classroom = db.classroom.find()

# See the change in collection.
for student in classroom:
    print(student)

# Add an item to a document array
db.classroom.update_one(
    {'name': 'Ahmed'},
    {'$push':
        {'hobbies': 'Listening to country music'}
     }
)

# Query the classroom collection.
classroom = db.classroom.find()

# See the change in collection.
for student in classroom:
    print(student)


# Delete a field from a document
db.classroom.update_one({'name': 'Ahmed'},
                        {'$unset':
                             {'row': ""}
                        }
                        )

# Query the classroom collection
classroom = db.classroom.find()

# See the change in collection.
for student in classroom:
    print(student)

# Delete a document from a collection
db.classroom.delete_one(
    {'name': 'Ahmed'}
)

# Query the classroom collection
classroom = db.classroom.find()

# See the change in collection.
for student in classroom:
    print(student)

 

```