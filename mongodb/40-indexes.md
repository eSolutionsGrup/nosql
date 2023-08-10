# Indexes
- make query more efficient 
- improve query performance

`db.collection("books").find({"rating":10})`
- scan each doc to examine a specific field 
- what happen when you have thousand of docs?

**Use an index where you need it for specific queries:**
- return a subset of docs 
- when you have a vary large amount of docs and you need to sort 

## Create 

- download: https://www.dickimaw-books.com/latex/admin/html/samplecsv.shtml
- query 
```
db.books.find( {price:19.99} )

db.books.find( {price:19.99} ).explain('executionStats')
```
- create index `{ <field> : <-1 or 1>}, [{name: "<index name>"}]` (`-1` = desc, `1` = asc)
```
db.books.createIndex( { price: 1 } )
```
- show index 
```
db.books.getIndexes()
```
- drop index
```
db.books.dropIndex( {price: 1} )
```
- explain 
```
db.books.createIndex( { price: 1 }, {name:"priceidx"} )

db.books.find( {price:19.99} ).explain('executionStats')
db.books.find( {price : { $gte: 19.99}} ).explain('executionStats')
```

- **compound index**
https://www.mongodb.com/docs/manual/core/index-compound/