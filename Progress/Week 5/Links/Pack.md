## Class `Pack`

A pack consisting an `ev_id` , and two lists of `ev_id`s of events that took place before and after the Event.

​	Properties: `ev`, `fwd`, `bwd`

​	Methods: `__init__(ev,fwd,bwd)`

```python
#Program Code for Pack
class Pack:
    def __init__(this,ev,fwd,bwd):
        this.id=ev
        this.fwd=fwd
        this.bwd=bwd
```

