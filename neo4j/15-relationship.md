# Relationship

- **find the nodes that we want to relate**
```
MATCH (p:Person), (s:School)
WHERE p.name = 'Gigi' AND s.name = 'Sava'
RETURN p,s 
```
- **create a relation** 
    - `CREATE (x)-[:REL_TYPE]->(y)`
```
MATCH (p:Person), (s:School)
WHERE p.name = 'Gigi' AND s.name = 'Sava'
CREATE (p)-[:STUDIED_AT]->(s)


MATCH (n) RETURN n
```
- **bidirectional relation**
    - `CREATE (x)-[:REL_TYPE]->(y)`, `CREATE (x)<-[:REL_TYPE]-(y)`
```
MATCH (p1:Person {name:'Gigi'}), (p2:Person {name:'Lucian Neghina'})
CREATE (p1)-[:FRIEND]->(p2)


MATCH (p1:Person {name:'Gigi'}), (p2:Person {name:'Lucian Neghina'})
CREATE (p1)<-[:FRIEND]-(p2)


MATCH (n) RETURN n
```
- **create all in one command**
```
CREATE (p1:Person {name:'Roxana'})-[:FRIEND]->(p2:Person {name:'Eliza'})
```

- **update relation**
    - `SET r.propertyName = value`, 
    - `SET r = {propertyName1: value1, propertyName2: value2}`, 
    - `SET r += {propertyName1: value1, propertyName2: value2}`
```
MATCH (:Person {name:'Gigi'})-[rel:STUDIED_AT]->(:School {name:'Sava'})
SET rel.promotion = 2020
RETURN rel
```

- **delete relation**
```
MATCH (:Person {name:'Gigi'})-[rel:STUDIED_AT]->(:School {name:'Sava'})
DELETE rel
```

- **delete node and his relationships**
```
MATCH (n:Student) DELETE n

MATCH (n:Student) DETACH DELETE n
```