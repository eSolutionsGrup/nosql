# Hash 

## ADD
```
// HSET key field value [field value ...]

hset person name Lucian
hset person age 42
```
**update**
```
hset person name 'Lucian Neghina'
```

## GET
```
// HGET key field
hget person name

// HGETALL key
hgetall person
```

## DELETE 
```
// HDEL key field [field ...]
hdel person age
```

## Others commands 
- `HLEN key`
- `HEXISTS key field` 
- `HKEYS key`
- `HSCAN key cursor [MATCH pattern] [COUNT count]`