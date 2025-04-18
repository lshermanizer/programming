```

esel,s,real,,1402 ! select a contact surface and write nodal contact soln
nsle
prns,cont

rsys,14 ! write total force on the surface, in local coordinate system (so Fz is normal load)
fsum,rsys,cont
/output,term
rsys,0
```
