# Messaging app 

**Features**:
- cache the five most recent messages 

---


```
lpush chat:1 "mesaj 1"
ltrim chat:1 0 4
lrange chat:1 0 -1

lpush chat:1 "mesaj 2"
ltrim chat:1 0 4
lrange chat:1 0 -1

lpush chat:1 "mesaj 3"
ltrim chat:1 0 4
lrange chat:1 0 -1

lpush chat:1 "mesaj 4"
ltrim chat:1 0 4
lrange chat:1 0 -1

lpush chat:1 "mesaj 5"
ltrim chat:1 0 4
lrange chat:1 0 -1

lpush chat:1 "mesaj 6"
ltrim chat:1 0 4
lrange chat:1 0 -1
```
