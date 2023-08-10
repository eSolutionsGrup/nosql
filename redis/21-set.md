# Set

## ADD an item
```
// SADD key value [value ...]

sadd hobbies snowboarding
sadd hobbies swimming

// added only once 
sadd hobbies swimming
```

## GET 
```
// SMEMBERS key
smembers hobbies

// SSCAN key cursor [MATCH pattern] [COUNT count]
SSCAN hobbies 0 match * count 1
```

## DELETE 
```
// SREM key value [value ...]

srem hobbies swimming
```

## Others commands 
- `SCARD key` 
- `SMOVE source destination member`
- `SDIFF key [key ...]`

https://redis.io/commands/sdiff/