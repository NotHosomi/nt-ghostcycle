# nt-ghostcycle
A neotokyo plugin for cycling the ghost spawn for more consistent, strategic gameplay

Uses a set of coordinates from a textfile to spawn the ghost each round according to a spawn order

***
Perhaps implement a cvar that selects whether to use two middle ghost spawns, or just one

Snilah:
>less is better imo
>at least in regards to how competitive the scenario
>with tournaments/scrims being the most competitive and pubs the least
>so roughly; 2 close 1 middle for scrims
>maybe 2 close 2 middle in pugs
>and in pubs i actually dont think the random spawns with lots of variety is a bad thing at all by default
***

some pseudocode
===============
```SourcePawn
OnMapLoad()
{
    enum spawnpoints
	ATK_CLOSE
	MIDDLE
	DEF_CLOSE
	MIDDLE2



    if (4 neo_ghostspawnpoints)
	for 0 to 4
	    spawnpoints <- neo_ghostspawnpoint coordinates
    else
	spawnpoints <- nt_mapname_ctg.txt (containing three sets of coordinates for ghost spawns)



    delete all neo_ghostspawnpoints
}




OnNewRound()
{
    spawnpicker = roundnumber MOD 8
    switch spawnpicker 
    {
        case 0:	  create weapon_ghost at spawnpoints MIDDLE1
        case 1:	  create weapon_ghost at spawnpoints MIDDLE2
        case 2:	  create weapon_ghost at spawnpoints ATK_CLOSE
        case 3:	  create weapon_ghost at spawnpoints ATK_CLOSE
        case 4:	  create weapon_ghost at spawnpoints MIDDLE2
        case 5:	  create weapon_ghost at spawnpoints MIDDLE1
        case 6:	  create weapon_ghost at spawnpoints DEF_CLOSE
        case 7:	  create weapon_ghost at spawnpoints DEF_CLOSE
	//can this be optimized further?
    }
}
```
