## Query

### sample_restaurants
- display all the documents in the collection _restaurants_
- display the fields **restaurant_id, name, borough and cuisine, zipcode** (exclude the field _id) for all the documents in the collection _restaurant_
- display the first 5 restaurants which is in the borough Bronx
- find all the restaurants who achieved a score more than 80 but less than 100
- find the restaurants that do not prepare any cuisine of 'American' and their grade score more than 70

### sample_training 
- find all documents where the tripduration was less than or equal to 70 seconds and the usertype was not Subscriber
- find all documents where the tripduration was less than or equal to 70 seconds and the usertype was Customer

---


## Q1
find all documents where the tripduration was less than or equal to 70 seconds and the usertype was not Subscriber
```
db.trips.find( 
    { "tripduration": { "$lte" : 70 },"usertype": { "$ne": "Subscriber" } }
);
```
## Q2 
find all documents where the tripduration was less than or equal to 70 seconds and the usertype was Customer
```
db.trips.find
    { "tripduration": { "$lte" : 70 }, "usertype": { "$eq": "Customer" } }
);

db.trips.find
    { "tripduration": { "$lte" : 70 }, "usertype": "Customer" } }
);
```

## Q3
display all the documents in the collection _restaurants_
```
use sample_restaurants;

db.restaurants.find();
```

## Q4 
display the fields **restaurant_id, name, borough and cuisine, zipcode** (exclude the field _id) for all the documents in the collection _restaurant_
```
db.restaurants.find( 
    {}, 
    {"restaurant_id":1, "name":1, "borough":1, "cuisine":1, "address.zipcode":1, "_id":0}
);
```

## Q5
display the first 5 restaurants which is in the borough Bronx
```
db.restaurants.find( { "borough": "Bronx" } ).limit(5);
```

## Q6
find all the restaurants who achieved a score more than 80 but less than 100
```
db.restaurants.find(
    {
        grades : { 
            $elemMatch:{
                "score":{
                    $gt : 80 , 
                    $lt :100
                }
            }
        }
    }
);
```

## Q7
find the restaurants that do not prepare any cuisine of 'American' and their grade score more than 70
```
db.restaurants.find(
    {
        "cuisine" : {$ne : "American "},
        "grades.score" :{$gt: 70}
    }
);
```