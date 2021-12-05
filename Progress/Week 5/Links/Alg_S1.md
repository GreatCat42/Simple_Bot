## Main Code of Section 1: Gathering

Input: `RESULTS` List

Output: `COMBINATIONS` List, `COUNTS` Dict

```python
#Program Code for S1-Gathering


i=0 # Base inedex used in the Selector Loop

while i < len(RESULTS): #Selector Loop
    ev=RESULTS[i]
    CL=ev.time
    
    try:
        examine(COUNTS[ev.id])
    except KeyError:
        COUNTS[ev.id]=1 
    
    if natural_ev(ev) == False:
        continue
    
    ifwd=0
    while i+ifwd < len(RESULTS):
        fwev=RESULTS[i+ifwd+1]
        CLf=fwev.time
        if CLf-CL > 128:
            break
        else:
            ifwd+=1
    fwd=RESULTS[i+1:ifwd+i+1]
    
    ibwd=0
    while i-ibwd >= 0:
        bwev=RESULTS[i-ibwd-1]
        CLb=bwev.time
        if CL-CLb > 128:
            break
        else:
            ibwd+=1
    
    bwd=RESULTS[i-ibwd:i]
    
    p=Pack(ev,fwd,bwd)
    COMBINATIONS.append(pack)

```

