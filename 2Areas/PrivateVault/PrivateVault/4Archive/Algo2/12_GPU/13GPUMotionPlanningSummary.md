[[13_AlgoDat2_Using_the_GPU_for_motion_planning.pdf]]


## Parallelizing sPRM
- Sampling can be parallelized 
- Edge validation can be parallelized 
	- Validating the edges is the most expensive task 

*Edge validation*
Every thread takes on of the collisions detections ans as soon as one config is invalid it calls the other threads to stop. 

*Problems* 
- Stopping all threads is not immediate 
- To stop each thread is an overhead 

A better approach might be *lazy planning.*

## Lazy Planning 
1. Sampling all configs like in normal sPRM 
2. Compute neighbors and draw edges 
3. Do **NOT** check if the edges are free of collision. -> Lazy 
4. Compute shortest path
5. Check edges for collision
6. If there is an edge in collision remove that edge and compute new shortest path 
7. Remove until solution path is found. 

## The A* Algorithm 
Used to find optimal paths in graphs with positive weights.
Extension of the Dijkstra Algo. 


## Parallelizing the RRT
Not easy to parallelize. 

*Problem*
Plan parallelizing of the edge computations lead to a clustering of tree branches. -> Tree is no longer expanding efficient. 

*Solution*
Make sure, that each thread is not "working" in the same area/direction. 
For this samples are compute that have the property that the distance to its next sample is at least r. 
With this, each sample has a disk associated to it. 
You have to compute samples until the whole configurations space is covered. 

1. Each thread samples a config. 
2. The closest vertex to this same is v 
3. Each thread check for the closest poisson disk sample to v.
4. If it is the same for two threads only the faster one is allowed to add the edge.

[[14CRRRTConnect]]