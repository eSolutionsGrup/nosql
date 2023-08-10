# Embedded Documents

## create _inventory_ collection
```
db.inventory.insertMany([
   { item: "journal", qty: 25, size: { h: 14, w: 21, uom: "cm" }, status: "A" },
   { item: "notebook", qty: 50, size: { h: 8.5, w: 11, uom: "in" }, status: "A" },
   { item: "paper", qty: 100, size: { h: 8.5, w: 11, uom: "in" }, status: "D" },
   { item: "planner", qty: 75, size: { h: 22.85, w: 30, uom: "cm" }, status: "D" },
   { item: "postcard", qty: 45, size: { h: 10, w: 15.25, uom: "cm" }, status: "A" }
]);
```

- `SELECT * FROM inventory`
```
db.inventory.find( {} )
```
- `SELECT * FROM inventory WHERE status = "D"`
```
db.inventory.find( { status: "D" } )
```
- `SELECT * FROM inventory WHERE status in ("A", "D")`
```
db.inventory.find( { status: { $in: [ "A", "D" ] } } )
```
- `SELECT * FROM inventory WHERE status = "A" AND qty < 30`
```
db.inventory.find( { status: "A", qty: { $lt: 30 } } )
```
- `SELECT * FROM inventory WHERE status = "A" OR qty < 30`
```
db.inventory.find( { $or: [ { status: "A" }, { qty: { $lt: 30 } } ] } )
```

