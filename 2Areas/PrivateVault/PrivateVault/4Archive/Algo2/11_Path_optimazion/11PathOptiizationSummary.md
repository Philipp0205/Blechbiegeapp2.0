[[11_Path_optimization.pdf]]

## Cost functions
To determine if a path is optimal cost functions are used eg. 
- Shortest path from start to goal 
- Maximum clearance to environment
- Little rotations 
- Limited energy. 

## Examples for path optimization 
### Shorter path 
1. Sample the computed path 
2. Take a random point 
3. Get neighbours and try to connect them directly 
4. If works, move the random pint to the mid 

### Clearance 
1. Sample computed path 
2. Take random point 
3. Compute minimal distance to obstacles 
4. Push point away from it 
5. Check if you can still connect to neighbors. 


## * Versions 
The star-versions of classic sampling based motion planners apply path optimization during the algo and not in post-processing. 

*Advantages*
- time complexity of star algos not higher than classical ones 
- Provide the optimal path

*Disadvantages*
- Explore the configspace less effective
- Optimal motion are not necessary on the solution path 
- The solution path can contain "high costs" movements 
- Do not perform well with narrow passages 
- Slow in higher dimensions 

- [x] #task Star algo example 📅 2021-07-14

## Ant Colony Algorithm 
More pheromone is dropped on shorter paths. 

*At what time is the algo applied?*	
After the MP algo for path optimization. 


### Using ACO to optimize result path 
1. Compute path with a tree-based planner 
2. Sample the surrounding of the path 
3. Connect to a graph, using NN 
4. Put some initial pheromones on the solution path
5. Let ants optimize path

Alternative to Djiksta, but can only used for scenarios with huge amount of samples or if multiple goals our roundtrip is needed. 
Otherwise, go with Dijkstra. 

## Traveling Sailsman Problem 
- Given graph with x amount of nodes 
- A sales man shall visit all nodes. 
- Start node is end not (circle trip) 

*Approach* 
1. Compute path with roadmap-based planner. 
2. Same as for tree-based. If noly start or goal given -> go with Dijkra

ACO can solve the traveling sailsman problem. 

*For what type of algos do you think this this algo most useful?*
The ACO Algo can be useful for tree-based planner AND for roadmap-based planners. 

For a tree-based planner it should only be used for scenarios with a huge amount of samples, if multiple goals or a roundtrip is needed. The same goes of roadmap-based planners. 
If this is not the case better go with Dijksta. 


## Note on algo types 
*Roadmap-based planners*
sPRM 

*Tree based planners*
RRT

[[13GPUMotionPlanningSummary]]