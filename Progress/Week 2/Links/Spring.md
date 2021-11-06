## Spring
A class

Stored in variable: `SPRINGS`

Parameters:

```js
Springs:5
	Pos-Sys:1
	Pos-EngineL:1
	Pos-EngineR:1
	Sys-EngineL:1
	Sys-EngineR:1
		*coefficient_k:20N/m
		*initial length:0.4m
```

Class Needed: `Spring`

​	Properties: `node0`, `node1`,`k`, `l0`

​	Methods: `show`, `run`,`__init__(node0,node1)`, `retForce`

```python
#Program Code for Spring
class Spring:
    
    def __init__(this,node0,node1):
        this.node0=node0
        this.node1=node1
        this.k=20
        this.l0=0.4
        
    def run(this):
        F=this.getForce()
        F.affect(node0)
        F.reverse()
        F.affect(node1)
        
    def getForce(this):
        #Two lines of preapration
        n0=this.node0
        n1=this.node1
        
        #Calculating the magnitude
        l=((n0.x-n1.x)**2+(n0.y-n1.x)**2)**0.5
        mag=(l-this.l0)*this.k
        
        #Calculating the direction
        d=direction(n1.x-n0.x,n1.y-n0.y)
        
        #Return!
        return Force(mag,d)
        
        
        
        
        
        
```

