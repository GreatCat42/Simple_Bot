## Node:

A Class

Stored in variable: `NODES`

Parameters:

```js
Nodes:4
	*max friction:0.1N
	System Node:1
		*mass:200g
        *max friction:0.2N
	Engines:2
		LEFT/RIGHT
		*mass:100g
		*thrust:1N
	Positioning Node:1
		*mass:100g
```

​	Properties: `x`, `y`, `mass`, `xvel`, `yvel`, `xf`,  `yf`, `thrusts`

​	Methods: `show`, `run`, `move`, `connect(that)`, `getThrust(direction)`,`__init__(type)`, `addForce(force)`, `runThrust`, `getFric`

```python
#Program Code for Node

class Node:
    
    def __init__(this,x,y,type):
       	#Input Parameters
        this.x=x
        this.y=y
        #Setup by Type
        this.type=type;
        if this.type == 'engine' or this.type == 'position':
            this.mass=0.1
            if this.type == 'engine':
                this.thrusts=[]
        if this.type == 'system':
            this.mass=0.2
            #Direction of the machine
            this.direction=[1,0]
        else:
            raise Exception('Unknown Type of Node: '+this.type)
        #Initiation of Values
        this.xForce=0
        this.yForce=0
        this.xVel=0
        this.yVel=0
        
        
            
    def show(this):
        
        pass #Will be added later...
    
    def getThrust(this,mag):
        
        #Adds a Thrust instance into the node
        this.thrusts.append(Thrust(this,mag))
        
    
    def runThrust(this):
        for th in this.thrusts:
            f=th.setForce()
            if f:
                f.affect(this)
            else:
                pass
        
            
    def getFric(this):
        mag=this.mass
        direction=Direction(this.xVel,this.yVel)
        fr=Force(mag,direction)
        fr.affect(this)
        
        
    def move(this):
        
        #Input Values, in Metric
        xForce=this.xForce
        yForce=this.yForce
        xVel=this.xVel
        yVel=this.yVel
        x=this.x
        y=this.y
        mass=this.mass
        
        #Convertion of Values, into C_
        C_XFORCE=xForce/64
        C_YFORCE=yForce/64
        C_XVEL=xVel
        C_YVEL=yVel
        C_X=x*64
        C_Y=y*64
        C_MASS=this.mass
        
        #Calculation
        C_XACC = C_XFORCE / C_MASS
        C_YACC = C_YFORCE / C_MASS
        
        C_XVEL += C_XACC
        C_YVEL += C_YACC
        
        C_X += C_XVEL
        C_Y += C_YVEL
        
        #Convert Back into Metric
        this.xForce=0
        this.yForce=0
        this.xVel=C_XVEL
        this.yVel=C_YVEL
        this.x=C_X/64
        this.y=C_Y/64
        
    def addForce(this,force):
        force.affect(this)
        
    def run(this):
        this.runThrust()
        this.show()
        this.move()
        
    def connect(this,that):
        #Puts a Spring instance into the SPRINGS List Variable
        SPRINGS.append(Spring(this,that))
        
    
            
        
```

