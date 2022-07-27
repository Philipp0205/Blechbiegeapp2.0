[[09_AlgoDat2_The_single_query_motion_planners.pdf]]

## Rapidly-Exploring Random Tree (RRT)
Need 4 parameters: 
The init and goal config. 
A *range-max* value and a *time-max* value.

1. Cinit and Cgoal configurations are known
2. Random config *crand* is computed. 
3. If distance to the cRand pint is larger than the range-max value an "indermediate" pint *Cnew* is created. 
4. *Cnew* gets added to the vertex.
5. The edge between *Cnew* and *Cgoal* is checked for validity. 
6. If valid 
7. If not vlaid a new *crand* is computed. 

## The RRT Connect
The algo builds up two trees. (I think from start and goal config)
In each iteration the algo tried to connect both trees and as soon as the trees are connected the path is found. 
Difference *extend* and *validEdge:* The extend function add also configurations on the edge of the tree. 

## Expansive Space Tree

[[10SamplingSummary]]