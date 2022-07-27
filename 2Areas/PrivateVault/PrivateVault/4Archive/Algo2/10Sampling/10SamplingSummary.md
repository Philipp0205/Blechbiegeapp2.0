[[10_AlgoDat2_Sampling_in_Motion_Planning.pdf]]

One major challenge for uniform sampling are **narrow passages**.

## Categories of sampling streategies 

**Configurationsspace-based sampling:** These sampling strategies are, besei the simple collisison check, only using information of the configspace. 
- Uniform Sampling 
- Gaussian Samling
- Bridge Test Sampling

**Workspace-based sampling:** These strategies are using informations of the workspace to guide the sampling. Information like distance of the robot to its surrounding environment.
- Sphere Sampling 
- Medial Axis Sampling 

## Gaussian Sampling
*Gaussian Sampling 1*
1. Create random forbidden config *ci*
2. Distance *d* chosen according to normal distribution.
3. Generate a config *ci'* with distance d from ci.
4. if ci' is free of collision then it gets added to graph 

*Problems*
In order to get config of Cobs we need to do a collisiosn check. 
-> More running time. 
Many configs will be discarded. 

Therefore there are variants. 

*Gaussian Sampling 2*
Idea: 
Postpone the collision check.
You first sample the two configs in the same way as before and then you check if one of the samples is in *Cobs* and the other in *Cfee*. 
-> This lead to more configs that are accede . 


## Sphere Sampling
Includes distance computation in addition to a collision detection. 
**Idea:** Avoid collision detection for configs that are for sure in the free space. 

1. Sample a config 
2. Map it in the workspace 
3. Compute minimal distance to the obstacles 
4. With distance, you can conclude in the config space a sphere that is for sure free of collision.
5. Sample next config. 
6. If the config is not in one of the sphere you go for distance again 
7. If the config is inside of a sphere, no collision detection is needed .


## Medial Axis Sampling
1. Sample a config s from c-space and check if in cfre
2. generate nearest contact point to obstacle (config p)
3. move s away p until it ha to nearest boundary points. 


- Computing the nearest contact config is hard, mostly done with distance 
- Provides smoother paths 
- Not efficient for narrow passage problems 


[[11PathOptiizationSummary]]