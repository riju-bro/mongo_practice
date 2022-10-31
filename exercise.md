# MongoDB Practice

MongoDB Exercise in mongo shell

Connect to a running mongo instance, use a database named `mongo_practice`.


## Insert Document

Insert the following data into movies collection 

```javascript
[
    {
        title : "Fight Club",
        writer : "Chuck Palahniuk",
        year : 1999,
        actors : [
        "Brad Pitt",
        "Edward Norton"
        ]
    },
    {
        title : "Pulp Fiction",
        writer : "Quentin Tarantino",
        year : 1994,
        actors : [
        "John Travolta",
        "Uma Thurman"
        ]
    },
    {
        title : "Inglorious Basterds",
        writer : "Quentin Tarantino",
        year : 2009,
        actors : [
        "Brad Pitt",
        "Diane Kruger",
        "Eli Roth"
        ]
    },
    {
        title : "The Hobbit: An Unexpected Journey",
        writer : "J.R.R. Tolkein",
        year : 2012,
        franchise : "The Hobbit"
    },
    {
    title : "The Hobbit: The Desolation of Smaug",
    writer : "J.R.R. Tolkein",
    year : 2013,
    franchise : "The Hobbit"
    },
    {
        title : "The Hobbit: The Battle of the Five Armies",
        writer : "J.R.R. Tolkein",
        year : 2012,
        franchise : "The Hobbit",
        synopsis : "Bilbo and Company are forced to engage in a war against an array of combatants and keep the Lonely Mountain from falling into the hands of a rising darkness."
    },
    {title : "Pee Wee Herman's Big Adventure"},
    {title : "Avatar"}

]

```

## Answer
```javascript
db.movies.insertMany(givenArray)
```

## Query / Find Documents

query the `movies` collection to

1. get all documents
1. get all documents with `writer` set to "Quentin Tarantino"
1. get all documents where `actors` include "Brad Pitt"
1. get all documents with `franchise` set to "The Hobbit"
1. get all movies released in the 90s
1. get all movies released before the year 2000 or after 2010

## Query / Find Documents Answer
1.
```javscript
db.movies.find()
```
2.
```javascript
db.movies.find({writer: "Quentin Tarantino"})
```
3.
```javascript
db.movies.find({actors: "Brad Pitt"})
```
4.
```javascript
db.movies.find({franchise: "The Hobbit"})
```
5.
```javascript
db.movies.find({year: {$gte: 1990, $lt: 2000}})
```
6.
```javascript
db.movies.find(
    {
        $or: [
            {year: {$lt: 2000}},
            {year: {$gt: 2010}}
        ]
    }
)
```


## Update Documents

1. add a synopsis to "The Hobbit: An Unexpected Journey" : "A reluctant hobbit, Bilbo Baggins, sets out to the Lonely Mountain with a spirited group of dwarves to reclaim their mountain home - and the gold within it - from the dragon Smaug."
1. add a synopsis to "The Hobbit: The Desolation of Smaug" : "The dwarves, along with Bilbo Baggins and Gandalf the Grey, continue their quest to reclaim Erebor, their homeland, from Smaug. Bilbo Baggins is in possession of a mysterious and magical ring."
1. add an actor named "Samuel L. Jackson" to the movie "Pulp Fiction"

## Update Documents Answer

1.
```javascript
db.movies.updateOne(
    {title: "The Hobbit: An Unexpected Journey"},
    {$set: {synopsis: "A reluctant hobbit, Bilbo Baggins, sets out to the Lonely Mountain with a spirited group of dwarves to reclaim their mountain home - and the gold within it - from the dragon Smaug."}}
)
```
2.
```javascript
db.movies.updateOne(
    {title: "The Hobbit: The Desolation of Smaug"},
    {$set: {synopsis: "The dwarves, along with Bilbo Baggins and Gandalf the Grey, continue their quest to reclaim Erebor, their homeland, from Smaug. Bilbo Baggins is in possession of a mysterious and magical ring."}}
)
```
3.
```javascript
db.movies.updateOne(
    {title: "Pulp Fiction"},
    {$push: {actors: "Samuel L. Jackson"}}
)
```

## Text Search

1. find all movies that have a synopsis that contains the word "Bilbo"
1. find all movies that have a synopsis that contains the word "Gandalf"
1. find all movies that have a synopsis that contains the word "Bilbo" and not the word "Gandalf"
1. find all movies that have a synopsis that contains the word "dwarves" or "hobbit"
1. find all movies that have a synopsis that contains the word "gold" and "dragon"

## Delete Documents

1. delete the movie "Pee Wee Herman's Big Adventure"
1. delete the movie "Avatar"

## Delete Documents Answer
1.
```javascript
db.movies.deleteOne({title: "Pee Wee Herman's Big Adventure"})
```
2.
```javascript
db.movies.deleteOne({title: "Avatar"})
```


## Insert Documents

Insert the following data into `persons` collection

```javascript
[
    {
        name: "Sue Ramsey",
        age: 35,
        country: "Algeria"
    },
    {
        name: "Leah McLaughlin",
        age: 29,
        country: "Japan"
    },
    {
        name: "Luke Chandler",
        age: 20,
        country: "Argentina"
    },
    {
        name: "Douglas Harrington",
        age: 29,
        country: "United Kingdom"
    },
    {
        name: "Esther Lamb",
        age: 30,
        country: "Italy"
    },
    {
        name: "Viola Gomez",
        age: 34,
        country: "United States"
    },
    {
        name: "Beatrice Webster",
        age: 17,
        country: "India"
    },
    {
        name: "Steve Webster",
        age: 33,
        country: "Japan"
    },
    {
        name: "Mollie Estrada",
        age: 24,
        country: "Russia"
    },
    {
        name: "Susie Fisher",
        age: 28,
        country: "Canada"
    },
    {
        name: "Loretta Reynolds",
        age: 27,
        country: "United States"
    },
    {
        name: "Lou Campbell",
        age: 34,
        country: "France"
    },
    {
        name: "Marion Henry",
        age: 33,
        country: "India"
    },
    {
        name: "Daniel Thomas",
        age: 20,
        country: "Italy"
    },
    {
        name: "Sarah Palmer",
        age: 18,
        country: "India"
    },
    {
        name: "Emilie Stevenson",
        age: 35,
        country: "Japan"
    },
    {
        name: "Manuel Knight",
        age: 33,
        country: "United Kingdom"
    },
    {
        name: "Nathan Howell",
        age: 29,
        country: "Germany"
    },
    {
        name: "Brent Thornton",
        age: 21,
        country: "United States"
    },
    
]
```

## Answer
```javascript
  db.persons.insertMany(givenData)
```
