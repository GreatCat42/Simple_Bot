# The Simple Bot -- Experimental Project

​	All the links are connected to already-finished parts of this project. Unfinished parts of this project and the framework are shown here.

​	It is recommended to put content onto external files and view them via links when the __word count__ of this document exceeds **400**.

​	A star __```*```__ indicates that the building of a section is in progress. 

## Hardware:

### Environment:

Variables: `CLOCK`, `NODES`, `SPRINGS`, `RESULTS`,`SECTIONS`, `SECTIONS_MAX`, `SYSTEM`

```python
SECTIONS=0
SECTIONS_MAX=64
COMBINATIONS=[]

# Run the simulation
while SECTIONS < SECTIONS_MAX:
    # Environment:
    CLOCK=0
    NODES=[]
    SPRINGS=[]
    SYSTEM=System()
    RESULT=SYSTEM.log

    # Initialize NODES:
	#Don't forget to add SYSTEM to the System Node
    NODE_EnL=Node(-0.34,0,'engine')
    NODE_EnR=Node(0.34,0,'engine')
    NODE_Sys=Node(0,-0.2,'system')
    NODE_Pos=Node(0,0.2,'position')

    # Initialize SPRINGS:


    # Initialize RESULT:


    #Running the For Loop:
    while CLOCK < 64*64:
        for sp in SPRINGS:
            sp.run()
        for no in NODES:
            no.run()
        SYSTEM.run()
    
    #Exit For Loop
    #Collect Info:
    COMBINATIONS.append(RESULT.combinations)
    
#Analysis

        

```



### <a href='./Links/Node.md'>Class: `Node`</a>

### <a href='./Links/Direction.md'>Function: `Direction(x,y)`</a>

### *Springs

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
		*max friction:0.1N
```

Class Needed: `Spring`

​	Properties: `node0`, `node1`,`k`, `l0`

​	Methods: `show`, `run`,`__init__(node0,node1)`, `retForce`

```python
#Program Code for Spring
class Spring:
    
    def __init__(this,node0,node1,k,l0):
        this.node0=node0
        this.node1=node1
        this.k=k
        this.l0=l0
        
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



### Forces

### <a href='./Links/Force.md'>Class: `Force`</a>



## *Commands:



### *System

Parameters:

```
Time:
	1 Tick / Virtual Frame
	16 Ticks / Command Output
	8 Ticks / Stat Recording
	64 Ticks / Result Recording
	##ENVIRONMENT## 64*64 Ticks / Restarting Simulation
```

### <a href='./Links/IsFactor.md'>Function: `IsFactor(factor,product)`</a>

Class Needed:`System`

​	Properties:`log`, `engineL`, `engineR`, `#time**(REPLACED BY "CLOCK" IN THE ENVIRONMENT)**`, `host`, `positioner`

​	Methods: `command(com)`, `__init__(engineL,engineR)`, `record(type)`, `run`

```python
#Program Code for System

#Only records information when it is the EXACT time. Records a None otherwise.
class System:
    def __init__(this,host,engineL,engineR,positioner):
        this.log=Log()
        this.engineL=engineL
        this.engineR=engineR
        this.positioner=positioner
        this.host=host
        
    def command(com):
        c=com
        
        d0=0
        while c >= 32:
            c-=32
            d0+=1
        
        d1=0
        while c>8:
            c-=8
            d1+=1
            
        d2=0
        while c>4:
            c-=4
            d2+=1
            
        d3=c
        
        c_=Command(d0,d1,d2,d3)
        c_.execute()
        
        
        
```

Class Needed: `Log`

​	Properties: `commands`, `stats`, `results`, `combinations`

​		Sub-lists for `combinations`: `commands(at index 0)`, `stats(at index 1)`, `results(at index 2)`

​	Methods: `run`, `remember`,`__init__`, `scan`

~~~Python
#Program Code for Log

~~~

Class Needed: `###Event`

​	Properties: `type`, `time`, `content`

​	Methods: `__init__(type,time,content)`

```python
#Program Code for Event
```

### <a href='./Links/Command.md'>Class: `Command`</a>

### <a href='./Links/Command_Format.md'>`Command` Format</a>

### <a href='./Links/Thrust.md'>Class:`Thrust`</a>

### <a href='./Links/Timer.md'>Class: `Timer`</a>



Variable Needed: `CLOCK`

```python
#Routines containing CLOCK:
```

Variable Needed: `SYSTEM`

```python
#SYSTEM is an instance of the class System, with a property 'host' set to the 'system' node for rapid information interchange.
```





## Stats:

## Results:

## Analysis:

## Units:

### <a href='./Links/Convert.md'>Convertion</a>



