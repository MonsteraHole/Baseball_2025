# Baseball_2025
Updated/other skills

# Data cleaning 

This data set contains many data points we do not want or need, such as different leagues. Since baseball is a sport where players are getting traded all the time, much of the data needs to be grouped by player and year to get an accurate representation of the season as a whole. Ive also taken the liberty of limiting results to the years 1920-2025. This data cleaning brought our unique rows from 128,598 to 90,972
<details>
  <summary>Code</summary>
 
  ```sql
with e1 as(
SELECT 
	playerID,
    yearid,
    sum(g)	as g,
    sum(ab)	as ab,
    sum(r)	as r,
    sum(h)	as h,
    sum(2b)	as 2b,
    sum(3b)	as 3b,
    sum(hr)	as hr,
    sum(rbi) as rbi,
    sum(sb)	as sb,
    sum(cs)	as cs,
    sum(bb)	as bb,
    sum(so)	as so,
    sum(ibb)	as ibb,
    sum(hbp)	as hbp,
    sum(sh)	as sh,
    sum(sf)	as sf,
    sum(gidp)	as gidp
FROM baseball_2025.batting
where lgid in ('NL', 'AL') and yearid > 1920
group by playerid, yearID)

select count(distinct playerID)
from e1 
where playerid not in (select playerid from pitching)
```
</details>


# Batters vs Pitchers 

![Batters vs Pitchers](pitchervsbatter.PNG)
