# List 

## ADD 
### add an item to a list (left side - at the beginning)
```
// LPUSH key value

lpush orders:1 product:2
```

### add an item at the end of the list
```
// RPUSH key value

rpush orders:1 products:100
```

### add multiple values
```
// LPUSH key value [value ...]

// RPUSH key value [value ...]
```

### GET
_note:_ `get` works only with **String**
```
// LRANGE ket start_index end_index

lrange orders:1 0 -1 // get all 

```

## DELETE
### remove the first item
```
// LPOP key [count]

lpop orders:1

lrange orders:1 0 -1
```

### remove the last item
```
// RPOP key [count]

rpop orders:1
```

## Others commands 
- `LLEN key` 
- `LINDEX key index`
- `LTRIM key start stop`
- `LMOVE source destination <LEFT | RIGHT> <LEFT | RIGHT>`

https://redis.io/commands/lpop/ 