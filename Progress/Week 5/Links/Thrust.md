## Thrust
A Class


​	Properties:`timer`, `host`, `mag`

​	Methods: `setForce`, `__init__(host,mag)`

```python
#Program Code for Thrust:
class Thrust:
    def __init__(this,host,mag):
        this.host=host
        this.mag=mag
        this.timer=Timer(16)
    
    def setForce(this):
        if this.timer.running():
            direction=SYSTEM.direction[:]#Get Direction
            mag=this.mag
            return Force(mag,direction)
        else:
            return None
            
            
            
            
```

