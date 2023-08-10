
## SET & GET
```
set customer:1000 lucian

get customer:1000

set customer:1500 roxana
```

## search a key
```
EXISTS customer:1000

EXISTS customer:1
```

## KEYS vs SCAN
__KEYS__
- blocks DB until complete
- never use in __production__

__SCAN__
- iterates using a cursor 

```
keys * 
keys customer:1*

scan 0 MATCH customer:1* scan 0 MATCH customer:1*
```

## DELETE
```
del customer:1500
get customer:1500

unlink customer:1000
get customer:1000


// delete all
FLUSHALL
```

## only INSERT or UPDATE 
```
// two steps 
exists test:1
exists customer:1234 

// insert only
set test:1 value NX
set test:1 "new value" NX

// update only 
set test:1 updated XX
get test:1
set test:100 demo XX
```