[[08_AlgoDat2_Distance_in_Motion_Planning.pdf]]


## Definition
In most algos the distance need to be computed. (example: nearest neighbor)


## Brute Force for nearest neighbor
Used in the PWS. Compute every distance for every two points. 

## kd-Tree

## LSH
Local sensitive hashing 

*Idea* 
1. The LSH approach is randomized 
2. The algo cab be used to find the nearest of k nearest neigbour to a given point 
3. But it does not compute the exact neighbour.


### Why use LSH 
1. By allowing a minor mismatch of nearest neighbour definition, the algo can compute neighbozrs much faster than a kd-Tree or a brute Force algo. 
2. In motion planning the algos are based of a random data structure that cover the configspace. If we only consider approximation of the nearest neighbors the motion planner still covers the configspace.
3. The LSH approach can be easily parallelized and is therefore used in multi core scenarios. 

### How it works 
1. Configspace with configurations is created 
2. Define a subspace that can be mapped to a hash set. E.g. Circle 
3. Subdivide the circle into an array. 
4. Number the array. 
5. Map each point to an array cell. 

**Idea of LSH:** Points that are lose to each other are mapped to the same array. 

A circle is not a good idea because the pints in the middle which actually are close together will get sorted in different arrays. 

The subspace can have different shapes. 

The LSH approach is often used when the dimension of the search space is very high. 
Each hash function can be queried independently and the major task is to compute the distance in all bucket pints -> the algo can be parallelized easily. 
In lower dimensions (2-3) the kd-Tree is often preferred Although this is way harder to parallelize 


[[09SingleQueryMotionPlannersSummary]]