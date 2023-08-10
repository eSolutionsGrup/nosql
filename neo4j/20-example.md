# DockerHub 

---

**create container registry**
```
CREATE (n: Registry {name: 'dockerhub'})
```
**create organization**
```
CREATE (n:Organization {name: 'eSol'})
```
**container repository**
```
CREATE (n: Repository {name: 'hello-world'})
CREATE (n: Repository {name: 'neo4j'})
CREATE (n: Repository {name: 'java'})
```
**create relationships**
```
MATCH (registry:Registry {name:'dockerhub'}), (org:Organization {name:'eSol'})
CREATE (org)-[:REGISTRY]->(registry)

MATCH (repo:Repository {name:'hello-world'}), (org:Organization {name:'eSol'})
CREATE (repo)-[:ORGANIZATION]->(org)

MATCH (repo:Repository {name:'java'}), (org:Organization {name:'eSol'})
CREATE (repo)-[:ORGANIZATION]->(org)
```
**add docker images**
```
CREATE (n:Image {
    digest: '12345',
    os: 'linux/amd64'
});

CREATE (n:Image {
    digest: '22222',
    os: 'linux/amd64'
})
```
**relate the images**
```
MATCH (image:Image), (repo: Repository)
WHERE repo.name = 'neo4j' AND image.digest = '12345'
CREATE (repo)-[:LATEST]->(image)

MATCH (image:Image), (repo: Repository)
WHERE repo.name = 'neo4j' AND image.digest = '12345'
CREATE (repo)-[:TAG {name:'5.1.0'}]->(image)
```

**FIND latest _neo4j_ docker image**
```
MATCH (:Repository {name:'neo4j'})-[:LATEST]->(img:Image) 
RETURN img

// version 5.1.0
MATCH (:Repository {name:'neo4j'})-[:TAG {name:'5.1.0'}]->(img:Image) 
RETURN img
```