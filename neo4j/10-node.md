# Nodes

## empty node
- **get all**
```
MATCH(n) RETURN n
```
- **create a node** 
    - `CREATE (optionalVariable optionalLabels {optionalProperties})`
```
CREATE (n)

// creating multiple nodes
CREATE
(:Person {name: 'Michael Caine', born: 1933}),
(:Person {name: 'Liam Neeson', born: 1952}),
(:Person {name: 'Katie Holmes', born: 1978}),
(:Person {name: 'Benjamin Melniker', born: 1913})
```

- **delete a node**
```
MATCH (n) DELETE n
```

## nodes with label 
- **create a person node** 
```
CREATE (n:Person)

// node with proprieties 
CREATE (n:Person {name: 'Lucian Neghina', age: 40})
```
- **create school nodes**
```
CREATE (n:School{name:'Sava'})
CREATE (n:School{name:'Lazar'})
```

## filter nodes
- **by label** 
```
MATCH (n:School) RETURN n 

MATCH (n:School) RETURN n LIMIT 1
```
- **by proprieties**
```
MATCH (n: School {name: 'Sava'}) RETURN n 

MATCH (n {name: 'Sava'}) RETURN n 

MATCH (n) WHERE n.name='Sava' RETURN n 
```

## update
- **propriety**
    - `SET n.propertyName = value`, 
    - `SET n = {propertyName1: value1, propertyName2: value2}`
```
MATCH (n:Person) WHERE ID(n) = 1 
SET n.name = 'Gigi'
RETURN n
```
- **label**
    - `SET x:Label`, 
```
MATCH (n:Person) WHERE n.name='Gigi'
SET n:Student
RETURN n

MATCH (n:Person) RETURN n
```

## remove 
`REMOVE n:Label`, `REMOVE n.propertyName`