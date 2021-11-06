# The Simple Bot -- Experimental Project

​	All the links are connected to already-finished parts of this project. Unfinished parts of this project and the framework are shown here.

​	It is recommended to put content onto external files and view them via links when the __word count__ of this document exceeds **400**.

​	A star __```*```__ indicates that the building of a section is in progress. 

## Hardware:

### *Environment:

Variables: `CLOCK`, `NODES`, `SPRINGS`, `RESULTS`,`SECTIONS`, `SECTIONS_MAX`, `SYSTEM`

```
Time:
	1 Tick / Virtual Frame
	16 Ticks / Command Output
	64*64 Ticks / Restarting Simulation
```

```python
SECTIONS=0
SECTIONS_MAX=64


# Run the simulation
while SECTIONS < SECTIONS_MAX:
    # Environment:
    CLOCK=0
    NODES=[]
    SPRINGS=[]

    # Initialize NODES:
    NODE_EnL=Node(-0.34,0,'engine')
    NODE_EnR=Node(0.34,0,'engine')
    NODE_Sys=Node(0,-0.2,'system')
    NODE_Pos=Node(0,0.2,'position')
    NODES=[NODE_EnL,NODE_EnR,NODE_Pos,NODE_Sys]

    # Initialize SPRINGS:
	SPRING_P_S=Spring(NODE_Pos,NODE_Sys)
    SPRING_L_S=Spring(NODE_EnL,NODE_Sys)
    SPRING_L_P=Spring(NODE_EnL,NODE_Pos)
    SPRING_R_S=Spring(NODE_EnR,NODE_Sys)
    SPRING_R_P=Spring(NODE_EnR,NODE_Pos)
    SPRINGS=[SPRING_P_S,SPRING_L_S,SPRING_L_P,SPRING_R_S,SPRING_R_P]

    # Initialize SYSTEM:
    SYSTEM=System(NODE_Sys,NODE_EnL,NODE_EnR,NODE_Pos)
    RESULTS=SYSTEM.log

    # Running the For Loop:
    while CLOCK < 64*64:
        for sp in SPRINGS:
            sp.run()
        for no in NODES:
            no.run()
        SYSTEM.run()
        
        # Run the clock
        CLOCK+=1
    
    # Exit For Loop
    # Analyze
    
    # Section Count +1
    SECTIONS+=1
    
    # Printing time contrast (n virtual seconds per second)
    
# Printing summary and Saving results

        

```

### Nodes:

### <a href='./Links/Node.md'>Class: `Node`</a>



### <a href='./Links/Direction.md'>Function: `Direction(x,y)`</a>



### Springs

### <a href='./Links/Spring.md'>Class: `Spring`</a>



### Forces

### <a href='./Links/Force.md'>Class: `Force`</a>



## Commands:



### *System

### <a href='./Links/IsFactor.md'>Function: `IsFactor(factor,product)`</a>

Class Needed:`System`

​	Properties:`log`, `engineL`, `engineR`, `host`, `positioner`

​	Methods: `command(com)`, `__init__(engineL,engineR)`, `record(type)`, `run`, `sense` 

```python
#Program Code for System

class System:
    def __init__(this,host,engineL,engineR,positioner):
        this.log=[]
        this.engineL=engineL
        this.engineR=engineR
        this.positioner=positioner
        this.host=host
        
    def command(com):
        #Commands interpreted from an int 0~63
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
        
        this.log.record(Event(c_))
        
    def rcom(this):
        #Random commands
        a=randint(0,1)*32
        b=randint(0,1)*8
        c=randint(0,1)*4
        d=randint(0,1)*1
        
        this.command(a+b+c+d)
        
    def run(this):
        #Running once in the loop
        if IsFactor(16,CLOCK):
            this.rcom()
        this.sense()
    
    def sense(this):
        #Sensing (linear, angular) accel, velocity
        pass
    
        
        
        
        
```



### <a href='./Links/Event.md'>Class: `Event`</a>

### <a href='./Links/Event_Format.md'>`ev_type` Format</a>



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





## Other Events:



## Analysis:



### 1. Gathering the Events:

### <a href='./Links/Alg_S1.md'>Main Code:</a>

### <a href='./Links/Pack.md'>Class: Pack</a>



### 2. Organizing and Creating an 'Event-To-Event' Dictionary

### <a href='./Links/EvToEv_Format.md'>Dictionary format</a>

```PYTHON
#Program Code for S2-Organizing
Rel={}
for p in COMBINATION:
    ID=p.ev.id
    fwd=p.fwd
    bwd=p.bwd
    try:
        examine(Rel[ID])
    except KeyError:
        Rel[ID]={ 'cause':{} , 'effect'={} }
    for fev in fwd: #Organise Effects
        f_id=fev.id
        try:
            Rel[ID]['effect'][f_id]+=1
        except KeyError:
            Rel[ID]['effect'][f_id]=1
    
    for fev in fwd: #Organise Causes
        b_id=bev.id
        try:
            Rel[ID]['effect'][b_id]+=1
        except KeyError:
            Rel[ID]['effect'][b_id]=1
    
```

### <a href='./Links/Examine.md'>Function: `examine`</a>



### 3. Analyze the Relationships between Events



### 4. Creating a Guide for the Robot to achieve GOALS



## Units:

### <a href='./Links/Convert.md'>Convertion</a>

## About the Release:

| Structure         | Robot       | Algorithm |
| ----------------- | ----------- | --------- |
| `MassNode-Spring` | `SimpleBot` | `Newt 0`  |





