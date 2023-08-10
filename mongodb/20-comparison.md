# Comparison Operators

`{ <field> : { <operator> : <value> }}`

- $eg = EQual to 
- $ne != Not Equal to
- $gt > Greater Than
- $gte >= Greater Than or Equal to
- $lt < Less Than
- $lte <= Less Than or Equal to 

**Query**

- `SELECT * FROM users WHERE age >= 25`
```
db.users.find( { age: { $gte: 25 } } );
```
- `SELECT * FROM users where age < 30`
```
db.users.find( { age: { $lt: 30 } } );
```
- `SELECT * FROM users WHERE sex <> 'M'`
```
db.users.find( { sex: { $ne: "M" } } );
```


**Select specific fields - Projection**

`SELECT first_name, last_name FROM users WHERE age < 30`
```
db.users.find( { age: { $lt: 30 } }, {first_name: true, last_name: 1} );

db.users.find( { age: { $lt: 30 } }, {age: false} );
```
