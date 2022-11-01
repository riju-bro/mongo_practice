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

## Relationships

### Insert the following documents into a `users` collection

```javascript
[
    {   username : "GoodGuyGreg",
        first_name : "Good Guy",
        last_name : "Greg"
    },
    {
        username : "ScumbagSteve",
        full_name :{
            first : "Scumbag",
            last : "Steve"
        }
        
    }
]
```

## Answer
```javascript
  db.users.insertMany(givenData)
```
### Insert the following array into a `posts` collection

```javascript
[
    {
        username : "GoodGuyGreg",
        title : "Passes out at party",
        body : "Wakes up early and cleans house"
    },
    {
        username : "GoodGuyGreg",
        title : "Steals your identity",
        body : "Raises your credit score"
    },
    {
        username : "GoodGuyGreg",
        title : "Reports a bug in your code",
        body : "Sends you a Pull Request"
    },
    {
        username : "ScumbagSteve",
        title : "Borrows something",
        body : "Sells it"
    },
    {
        username : "ScumbagSteve",
        title : "Borrows everything",
        body : "The end"
    },
    {
        username : "ScumbagSteve",
        title : "Forks your repo on github",
        body : "Sets to private"
    }
]
```
## Answer
```javascript
db.posts.insertMany(givenData)
```

### Insert the following documents into a `comments` collection

```javascript
{
    username : "GoodGuyGreg",
    comment : "Hope you got a good deal!",
    post : [post_obj_id]
}
```
where [post_obj_id] is the ObjectId of the `posts` document: "Borrows something"

```javascript
{
    username : "GoodGuyGreg",
    comment : "What's mine is yours!",
    post : [post_obj_id]
}
```
where [post_obj_id] is the ObjectId of the `posts` document: "Borrows everything"

```javascript
{
    username : "GoodGuyGreg",
    comment : "Don't violate the licensing agreement!",
    post : [post_obj_id]
}
```
where [post_obj_id] is the ObjectId of the `posts` document: "Forks your repo on github

```javascript
{
    username : "ScumbagSteve",
    comment : "It still isn't clean",
    post : [post_obj_id],
}
```
where [post_obj_id] is the ObjectId of the `posts` document: "Passes out at party"

```javascript
{
    username : "ScumbagSteve",
    comment : "Denied your PR cause I found a hack",
    post : [post_obj_id]
}
```
where [post_obj_id] is the ObjectId of the `posts` document: "Reports a bug in your code"


### Don't forget to copy the post_obj_id from the posts collection

## Answer
```javascript
db.posts.insertMany(givenData)
```


## Querying related collections

1. find all users
1. find all posts
1. find all posts that was authored by "GoodGuyGreg"
1. find all posts that was authored by "ScumbagSteve"
1. find all comments
1. find all comments that was authored by "GoodGuyGreg"
1. find all comments that was authored by "ScumbagSteve"
1. find all comments belonging to the post "Reports a bug in your code"

## Querying related collections Answer

1.
```javascript
db.users.find()
```
2.
```javascript
db.posts.find()
```
3.
```javascript
db.posts.find({username: "GoodGuyGreg"})
```
4.
```javascript
db.posts.find({username: "ScumbagSteve"})
```
5.
```javascript
db.comments.find()
```
6.
```javascript
db.comments.find({username: "GoodGuyGreg"})
```
7.
```javascript
db.comments.find({username: "ScumbagSteve"})
```
8.
```javascript
db.posts.aggregate([
    {
        $match: {title: "Reports a bug in your code"}
    },
    {
        $project: {title: 1}
    },
    {
        $lookup: {
            from: "comments",
            localField: "_id",
            foreignField: "post",
            as: "comments"
        }
    },
    {
        $project: {_id: 0}
    }
])
```
