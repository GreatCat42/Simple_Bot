## Main Code of Section 2: Organizing

Input: `COMBINATIONS` Dict

Output: `Rel` Dict

```PYTHON
#Program Code for S2-Organizing
Rel={}
for p in COMBINATIONS:
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

### 