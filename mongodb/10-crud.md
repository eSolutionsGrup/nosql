# CRUD
https://www.mongodb.com/docs/manual/tutorial/getting-started/

- create a database
```
show dbs;
use demo; // the database is automatically created 

db; // show current database
```

- INSERT into a collection (table)
```
db.users.insertOne({"first_name":"Lucian", "last_name":"Neghina"})
db.users.insertMany([{first_name: "eSol", last_name: "Academy"}, {first_name:"nosql", last_name: "MongoDB"}])

show collections 
show tables
```

- SELECT 
```
db.users.find( {} ) // select * from users
db.users.find( {first_name: "Lucian" } ) // select * from users where first_name='Lucian'
```

- UPDATE
```
db.users.updateOne(
    { first_name: "Lucian" },
    {
        $set: { "age": 42, sex: "M" }
    }
)
```

- UPSERT
```
db.users.replaceOne(
    { first_name: "GIGI" },
    {
        first_name: "GIGI",
        last_name: "masinuta",
        age: 25
    },
    { upsert: true}
)

db.users.replaceOne(
    { first_name: "GIGI" },
    {
        first_name: "Gigi",
        last_name: "Masinuta",
        age: 25
    },
    { upsert: true}
)
```
- DELETE
```
db.users.deleteMany( {} ) // delete all docs
db.users.deleteMany({ first_name: "Lucian" })

db.users.deleteOne({}) // delete first doc
```


## Projection
- `db.<collection>.find({query}, {projection})`
- `db.<collection>.find({query}, { <fields1>: 0, <field2>: 1 })`
- **1** or **true** - include the field 
- **0** or **false** - exclude the field 
