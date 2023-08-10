# Aggregation Framework
`db.<collection>.aggregate([ {stage1}, {stage2}, {... stageN} ], {options})`

**Pipeline**
- Composition of stages
- Configurable for transformation
- Flow like an assembly line
- Arranged in multiple ways

- `find` vs `aggregate` 
```
db.users.find( {first_name: "Lucian"}, {_id: 0, "age":0} )

db.users.aggregate([
    { $match: {first_name: "Lucian"} },
    { $project: {_id: 0, "age":0}}
])
```

**insert**
```
db.orders.insertMany( [
   { _id: 0, name: "Pepperoni", size: "small", price: 19, quantity: 10 },
   { _id: 1, name: "Pepperoni", size: "medium", price: 20, quantity: 20 },
   { _id: 2, name: "Pepperoni", size: "large", price: 21, quantity: 30 },
   { _id: 3, name: "Cheese", size: "small", price: 12, quantity: 15 },
   { _id: 4, name: "Cheese", size: "medium", price: 13, quantity:50 },
   { _id: 5, name: "Cheese", size: "large", price: 14, quantity: 10 },
   { _id: 6, name: "Vegan", size: "small", price: 17, quantity: 10 },
   { _id: 7, name: "Vegan", size: "medium", price: 18, quantity: 10 }
] )
```

- `SELECT count(*) as m FROM orders WHERE size = 'medium'`
```
db.orders.aggregate([
    { $match: {size: "medium"} },
    { $count: 'm' }
])
```
- `SELECT name, sum(quantity) FROM orders WHERE size = 'medium'`
```
db.orders.aggregate( [
   { $match: { size: "medium" } },
   { $group: { _id: "$name", totalQuantity: { $sum: "$quantity" } } }
] )
```

- calculate totalPrice 
```
db.orders.aggregate( [
   { $project: { name:1, size:1, price:1, quantity:1, totalPrice: { $multiply: ["$price", "$quantity"] } } }
] )
```
---

### Stage 
- $project : (reshape - 1:!)
- $match : (filter - n:1)
- $group : (aggregate - n:1)
- $sort : (sort - 1:1)
- $skip : (skip - n:1)
- $limit : (limit - n:1)
- $unwind : (normalize(flatten) - n:1)
- $out : (output - n:1)
- $redget : (authorization )
- $geonear : (location based query )


---
- **Exercise**: calculate totalSaleAmount by pizza
```
db.orders.aggregate( [
    { $group : {
        _id: "$name",
        totalSaleAmount: { $sum: { $multiply: ["$price", "$quantity"] }}
    }}
])


db.orders.aggregate( [
   { $project: { name:1, totalPrice: { $multiply: ["$price", "$quantity"] } } },
   { $group : {
        _id: "$name",
        totalSaleAmount: { $sum: "$totalPrice" } }
   }
] )
```

https://github.com/changx03/m121-aggregation 