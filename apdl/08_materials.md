# Materials

```
mtlist              ! list materials
/pnum,mat,1         ! display material numbers
esel,s,mat,,1       ! select elements of material #1

emodif,all,mat,10   ! change all selected elements to material #10

_matid=1
mp,mu,10,0          ! change friction coef of material #10 to 0
mp,alpx,_matid,0    ! change thermal expansion coef of material # _matid to 0
```
