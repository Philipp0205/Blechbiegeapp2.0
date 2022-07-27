[[06_AlgoDat2_Our_first_motion_planner.pdf]]


## sPRM Algorithm Summary 
The sPRM takes two parameter: *n* the number of samples and *r* the radius for the nearest neighbour search. 

There are two data structures. 
*E* the Edge data structure, stores edges between two configs.
*V* the vertex data structure, stores all configurations.

1. Start and Goal configs are added to the vertex data structure. 
2. *n* samples are computed. Samples in *Cobs* are ignored. 
3. Iterate over all samples and search nearest neighbors in radius *r*.
4. Iterate over all all nearest neighbours and check if there is an valid edge. 
5. When done we get a graph that characterizes *Cfree.*
6. When the start and the goal pints are part of our graph we check if there exists a connection between start and goal. A shortest path algo can be used. 

## Potential Problems with the sPRM
If n is **too little** there are not enough and nos solutions can be found.

If **r is too small** more samples are needed or the solution is not found. 

## How to check for a valid edge 
*Variant 2* 
1. Take a high resolution.
2. Discreize the edge into many samples. 
3. Start the first config and go to goal 
4. If there is an invalid config the edge is invalid. 

*Variant 3*
1. Take high resolution. 
2. Discretize edge into many samples. 
3. Use interval halving .
4. If there is a invalid config edge is invalid.

## What can be parallelized in sPRM?
Adding a config to an array can be par. 
**Low** Benefit. No GPU benefit. 

The collision detection of one config is independent of an other. Collision detection can be parallelized. 
**High Benefit**. GPU benefits as well. 

Parallelizing Diktstra calls can bring benefit if the amount of queries is high.

## Advantages/Disadvantages
*Advantages *
- Is usable for muli-query motion planning 
- Easy to implement and parallelize and GPU relevant 

*Disadvantages*
- Amount of samples has to be defined beforehand 
	- If the motion planning problem is easy -> little samples are needed 
	- Unnecessary time is pesnd to solve the problem 
	- If the motion planning problen is hard -> many samples are needed 
	- Algo has to be called mulitple times with increasing number of samples. 
- Need some extension to solve hard problems 
- Without parallelizing it is one of the slower ones. 


##  Other Notes 
- The exercise will be like this in the exam page 34
- How do we know if we created enough samples?

[[07TransformationInDetailSummary]]