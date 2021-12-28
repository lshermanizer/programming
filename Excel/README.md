



```
Base!C4:C25   =  a vector of values

Avoidance!C10 =  target value

This formula returns the value from the vector that is cloest (in absolute) to the target:

=INDEX(Base!C4:C25, MATCH(MIN(ABS(Base!C4:C25-Avoidance!C10)),ABS(Base!C4:C25-Avoidance!C10),0))
```
