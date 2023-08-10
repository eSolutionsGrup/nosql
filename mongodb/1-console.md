### local
```
docker run -it --rm --network nosql_academy mongo:6.0.2 mongosh mongodb://academy:passwd@mongo:27017/
```

https://www.mongodb.com/try/download/compass


### cloud
https://cloud.mongodb.com

**Load Sample Data**
https://www.mongodb.com/docs/guides/atlas/sample-data/

## Connect to my cluster 
    - uri: cluster0.c51zr.mongodb.net
    - user: __esol_nosql__
    - password: __2ab2f8d3-cab9-42d8-b641-39f1e8959fcc__

```
docker run -it --rm mongo:6.0.2 mongosh "mongodb+srv://cluster0.c51zr.mongodb.net/sample_restaurants" --apiVersion 1 --username esol_nosql
```

## Dataset
https://github.com/neelabalan/mongodb-sample-dataset