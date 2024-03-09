### Change element types

```
! change element types to legacy ones
alls
et,8,45  ! 185 to 45
et,9,45  
et,10,92 ! 187 to 92
et,11,95 ! 186 to 95

esel,s,ename,,185
emodif,all,type,8
esel,s,ename,,186
emodif,all,type,11
esel,s,ename,,187
emodif,all,type,10
alls
```
