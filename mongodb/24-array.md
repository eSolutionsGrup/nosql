# Array Operators

- $all - contains all the given elements 
- $elemMatch - an element from array satisfies all the specified criteria
- $size - base by array length 

## insert
```
db.inventory.insert([
   { item: "journal", qty: 25, tags: ["blank", "red"], dim_cm: [ 14, 21 ] },
   { item: "notebook", qty: 50, tags: ["red", "blank"], dim_cm: [ 14, 21 ] },
   { item: "paper", qty: 100, tags: ["red", "blank", "plain"], dim_cm: [ 14, 21 ] },
   { item: "planner", qty: 75, tags: ["blank", "red"], dim_cm: [ 22.85, 30 ] },
   { item: "postcard", qty: 45, tags: ["blue"], dim_cm: [ 10, 15.25 ] }
]);
```

## query base on Array  

-  `SELECT * FROM inventory WHERE tags = contains("red")`
```
db.inventory.find( { tags: "red" } )
```

- `SELECT * FROM inventory WHERE tags = array("red", "black")`
```
 db.inventory.find( { tags: ["red", "blank"] } );

 db.inventory.find( { tags: ["blank", "red"] } );
```

- `SELECT * FROM inventory WHERE tags = contains("red", "black")`
```
db.inventory.find( { tags: { $all: ["red", "blank"] } } )
```

-- `SELECT * FROM inventory WHERE dim_cm has e > 15 and dim_cm has e < 20` :)))
```
db.inventory.find( { dim_cm: { $gt: 15, $lt: 20 } } )
```

- -- `SELECT * FROM inventory WHERE dim_cm has (e > 15 and e < 20)`
```
db.inventory.find( { dim_cm: { $elemMatch: { $gt: 15, $lt: 20 } } } )
```

