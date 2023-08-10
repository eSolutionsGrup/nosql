# Logic Operators

`{ <operator> : [ {statement1}, {statement2}, ...]}`

- $and - match all 
- $or - at least one 
- $nor - fail to match 
- $not - negates

## create _students_ collection
```
db.students.insertMany([
    {
        "name" : "Roxana",
        "sex" : "Female",
        "class" : "VI",
        "age" : 12,
        "score" : 9.89
    },
    {
        "name" : "Lucian",
        "sex" : "Male",
        "class" : "VII",
        "age" : 13,
        "score" : 7.55
    },
    {
        "name" : "Robert",
        "sex" : "Male",
        "class" : "VI",
        "age" : 11,
        "score" : 8.96
    },
    {
        "name" : "Eliza",
        "sex" : "Female",
        "class" : "VIII",
        "age" : 13,
        "score" : 8.25
    },
    {
        "name" : "Bogdan",
        "sex" : "Male",
        "class" : "VI",
        "age" : 11,
        "score" : 9.52
    }
]);
```

Query 
- `SELECT * FROM students WHERE sex = 'Male' AND score >= 8 AND class = 'VI'`
```
db.students.find(
    { $and:[
        {"sex":"Male"},
        {"score":{ $gte: 8 }},
        {"class":"VI"}
        ]
    }
);
```
- `SELECT * FROM students WHERE age >= 12` (using logic operators)
```
db.students.find(
    { "age": { $not:{$lt : 12} } }
);
```
- `SELECT * FROM students WHERE class = 'VI' AND (age = 11 OR age = 12)`
```
db.students.find(
    { $and: [
        {"class":"VI"}, 
        { $or: [
            {"age": {$eq: 11}}, 
            {"age": {$eq: 12}}
        ]}
    ]}
);
```
- `SELECT * FROM students WHERE sex NOT LIKE 'M%'`
```
db.students.find(
    { "sex":{$not: /^M.*/} }
)
```
