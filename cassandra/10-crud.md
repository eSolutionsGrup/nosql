# CQLSH - Cassandra Query Language 
```
docker exec -ti nosql_c1_1 cqlsh
```

# CRUD
```
# show databases
DESCRIBE KEYSPACES;

# create databases
CREATE KEYSPACE demo WITH replication = {'class': 'SimpleStrategy', 'replication_factor': '1'} AND durable_writes = true;

USE demo;

# show tables
DESCRIBE TABLES;

# create a table 
CREATE TABLE IF NOT EXISTS books (
    bookid UUID,
    author TEXT,
    title TEXT,
    year INT,
    categories SET <TEXT>,
    added TIMESTAMP,
    PRIMARY KEY (bookid)
);

# show table details 
DESCRIBE TABLE books;

DESCRIBE KEYSPACE demo;
```

- INSERT
```
INSERT INTO books (bookid, author, title, year, categories, added)
    VALUES( uuid(), 'Agatha Christie', 'Crima din Orient Express', 1934, {'politist', 'crima', 'drama'},  toTimeStamp(now()) );


INSERT INTO books (bookid, author, title, year, categories, added)
    VALUES( uuid(), 'Radu Tudoran', 'Toate panzele sus', 1954, {'aventuri'},  toTimeStamp(now()) );
```

- SELECT 
```
SELECT * FROM books;

SELECT * FROM books WHERE bookid = 133100ce-97ac-4719-9a2f-8ca9714a5ba3;
```

- UPDATE 
```
UPDATE books SET categories = {'aventuri', 'mister'} WHERE bookid = 133100ce-97ac-4719-9a2f-8ca9714a5ba3;

SELECT * FROM books WHERE bookid = 133100ce-97ac-4719-9a2f-8ca9714a5ba3;
```

- UPSERT
```
INSERT INTO books (bookid, author, title, year, categories, added)
    VALUES( 133100ce-97ac-4719-9a2f-8ca9714a5ba3, 'Radu Tudoran', 'Toate panzele sus', 1954, {'aventuri'},  toTimeStamp(now()) );

UPDATE books SET categories = {'aventuri', 'mister'} WHERE bookid = 133100ce-97ac-4719-9a2f-8ca9714a5ba3;    
```

- DELETE
```
DELETE FROM books WHERE bookid = 133100ce-97ac-4719-9a2f-8ca9714a5ba3;

SELECT * FROM books;
```
