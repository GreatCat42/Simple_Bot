## Class: `Command`

​	Properties: `content`, `host`

​	Methods: `execute`

```python
#Program Code for Command:
class command:
    def __init__(this,*digits):
        this.digits=digits
    
    def execute(this):
        d0=this.digits[0]
        d1=this.digits[1]
        d2=this.digits[2]
        d3=this.digits[3]
        
        magL=d0*2-1
        magL*=d1
        
        SYSTEM.engineL.thrusts.append(Thrust(SYSTEM.engineL,magL))
        
        magR=d2*2-1
        magR*=d3
        
        SYSTEM.engineR.thrusts.append(Thrust(SYSTEM.engineR,magR))
        
        
        
        
```


