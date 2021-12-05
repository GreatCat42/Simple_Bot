## Force

A Class

​	Properties: `mag`, `direction`

​	Methods:`__init__(mag,direction)`, `affect(node)`

~~~python
#Program Code for Force
class Force:
    def __init__(this,mag,direction):
        this.mag=mag
        this.direction=direction
        this.dx=this.mag*this.direction[0]
        this.dy=this.mag*this.direction[1]
        
    def affect(this,node):
        node.xForce+=this.dx
        node.yForce+=this.dy
        
    def reverse(this):
        this.direction[0]=-this.direction[0]
        this.direction[1]=-this.direction[1]
        this.__init__(this.mag,this.direction)
        
        
    
~~~

