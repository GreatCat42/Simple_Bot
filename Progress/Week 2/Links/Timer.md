## Timer
A class

​	Properties:`endtime`

​	Methods:`running`

```python
#Program Code for Timer:

class Timer:
    def __init__(this,time):
        this.endtime=CLOCK+time
    
    def running(this):
        if this.endtime >= CLOCK:
            return True
        else:
            return False

#Complete
```

