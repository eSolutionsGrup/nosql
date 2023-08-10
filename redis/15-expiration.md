# TTL (time to Live)
```
TTL customer:1000

// -1 live forever
// -2 it is gone
```

## define expire in 10 sec
```
EXPIRE customer:1000 10

TTL customer:1000
TTL customer:1000
TTL customer:1000
```
## define expire when set the key 
```
// SETEX key expire value

SETEX demo 10 "ttl msg"

TTL demo
```
