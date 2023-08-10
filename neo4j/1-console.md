# docker run
```
docker run -p7474:7474 -p7687:7687 -p7473:7473 -d --name node4j docker.io/bitnami/neo4j:5.1.0
```
# Access server 

http://localhost:7474/browser/

user: **neo4j**
password: **bitnami**


# Nodes
`()`, `(n)` - represent a node

## Labels
Nodes in a graph are typically labeled. Labels are used to group nodes and filter queries against the graph.
- `()` - anonymous node
- `(n)` - variable _n_, a reference to a node used later
- `(:Person)` - anonymous node of type _Person_
- `(p:Person)` - variable _p_, a reference to a node of type Person
- `(p:Actor:Director)`	- variable _p_, a reference to a node of types Actor and Director

# Relationships
`[]`, `[:REL_TYPE]` - represent a relationship

- `()-[]->()` - the first node has a relationship to the second node
- `()<-[]-()` - the second node has a relationship to the first node

# Properties
A node and a relationship can have properties.
`{propertyKey: propertyValue}`