# PRIMARY KEY (partition key + cluster key)

```
USE demo;

CREATE TABLE IF NOT EXISTS restaurant_by_country(
    country text,
    name text,
    cuisine text,
    PRIMARY KEY( (country), name )
) WITH CLUSTERING ORDER BY(name DESC);

DESCRIBE TABLE restaurant_by_country;
```

```
INSERT INTO restaurant_by_country (country, name, cuisine) 
    VALUES ( 'USA', 'KFC', 'fast food' );
INSERT INTO restaurant_by_country (country, name, cuisine) 
    VALUES ( 'RO', 'La Mama', 'traditional' );

```

- FILTER
```
SELECT * FROM restaurant_by_country WHERE country = 'RO';
```

## EXERCISE
insert new rows:

| country | name | cuisine |
| --- | --- | --- |
| RO | KFC | fast food |
| RO | McDoanald's | fast food |
---

```

INSERT INTO restaurant_by_country (country, name, cuisine) 
    VALUES ( 'RO', 'KFC', 'fast food' );

INSERT INTO restaurant_by_country (country, name, cuisine) 
    VALUES ( 'RO', 'McDoanald''s', 'fast food' );
```

- FILTER by cluster key
```
SELECT * FROM restaurant_by_country WHERE country = 'RO' AND cuisine = 'fast food';

SELECT * FROM restaurant_by_country WHERE country = 'RO' AND name = 'KFC';
```

# SECONDARY INDEXES 
the data are partitioned across multiple nodes, 
each node must maintain its own copy of a secondary index based on
the data stored in partitions it owns.

NOT recommended:
- columns with __high cardinality__
- columns with __very low data cardinality__
- columns that are __frequently _updated_ or _deleted_.__


```
CREATE INDEX ON restaurant_by_country ( cuisine );

DESC TABLE restaurant_by_country ;
```

- FILTER
```
SELECT * FROM restaurant_by_country WHERE cuisine = 'fast food'
```

