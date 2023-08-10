# Implement stacks and queues 

**Features**:
- first in, first out
- first in, last out

---

**FIFO**
```
LPUSH work:queue:ids 101
LPUSH work:queue:ids 237

RPOP work:queue:ids
RPOP work:queue:ids
```

**FILO**
```
LPUSH work:queue:ids 101
LPUSH work:queue:ids 237

LPOP work:queue:ids
LPOP work:queue:ids
```
