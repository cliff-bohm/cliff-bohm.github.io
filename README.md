"# cliff-bohm.github.io" 



## PathFollowWorld
 agents are tested to see if they can follow a path.
 maps are loaded where locations are either off path, forward, left, right, or goal
 agents start on one end of the path (indicated by the map) facing the correct direction
 agents have a down sensor that allows them to see the value on the current location

 agents have 3 outputs where 100 = left, 010 = right, 110 = forward, XX1 = reverse (X = 0 or 1)

 parameters can be used to alter input formatting and other aspects of world.

 Parameters Notes (not in parameter descriptions):
   - if 'useRandomTurnSymbols' values are selected per generation per map,
       all agents will see same symbols per map)
   - if 'evaluationsPerGeneration' > 1, new symbols are generated for each evaluation
   - if symbol is delivered as binary, then not turn will be represented by 0.
       if symbolValueMax = 3, 3 symbols will be used with 2 bits (i.e. 01,10,11)
 if symbolValueMax = 4, 4 symbols will be used with 3 bits (i.e. 001,010,011,100)

 score in PathFollowWorld is number of forward and turn locations visited + time left if goal is reached and all locations were visited
 NOTE: since turns are interaly converted to forwards when visted, agents actually only recive points for being on forwards.



map files are raw text files with the following rules
the first line of the file is the map size (x,y)
the second line of the file is inital facing direction for the agent
     where 0 = north, 1 = north east, 2 = east, and so on till 7 = north west
the following lines are the map:
0 = empty
1 = forward
2 = right
3 = left
4 = goal
X = startingLocation

the hash (or pound sign) in the first potision of a line indicates a comment which are ignored
blank lines are ignored

example map:
---
6,6
1
000000
0X1120
000002
000002
003120
040000


---

## Visualizing Behavior
the directory Processing_Visualizer contains a script that can be run with processing:
you can get processing here: [https://processing.org/](https://processing.org/)
When you first open processing  you may need to click on the top right pull down
menu and select "Add Mode..." and then install (Python Mode for Processing) 

In order to use this script, you will need to run the world in visualize mode.
The best way to do this is the follow steps:
1) run MABE with PathFollowWorld and be sure that the Archivist is set to LODwAP
2) create a new text file with the name "population_loader.plf"
3) add one line to that file: MASTER = greatest 1 by ID from { 'LOD_organisms.csv' }
4) run MABE as you did before, but add the following paramers
(remeber -p is the commen line flag for paramers)
-p GLOBAL-initPop = population_loader.plf GLOBAL-mode = visualize
5) this should generate 'pathVisualization.txt'
6) double click on the processing script to open processing
6) edit the processing script so that the path to your pathVisualization.txt file is correct
7) press play on the processing interface (top left)
left and right arrows can be used to change the speed

If you have run with mq, the simplest way to visualize is to copy the LOD_data.csv and LOD_organisms.csv for the condition/replicate you want to see to the directory with MABE and your settings files, and then follow the same steps.
