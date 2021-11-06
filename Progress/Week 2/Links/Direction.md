## Direction
A Function

​	Arguments: `x`, `y`

​	returns an ordered pair in the form of a list


```python

def getDirection(x,y):
	d=x*x+y*y
	d=d**0.5
    try:
	    return [x/d,y/d]
    except ZeroDivisionError:
        return [0,-1]

```
