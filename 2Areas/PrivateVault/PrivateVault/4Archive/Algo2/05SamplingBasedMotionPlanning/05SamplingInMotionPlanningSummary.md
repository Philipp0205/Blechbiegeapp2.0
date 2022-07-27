#lecture-note 

![[05_AlgoDat2_Sampling_based_motion_planning.pdf]]

## Uniform Sampling
1. Use random function to sample the Cspace
2. Check if samples are free of collision
3. If so, store config in data structure
4. Apply Algos for this set of points to inf a patch from one to another

## Why does this work?
We don't need to explicitly compute Cspace.

We approximate the free space by random samples and hop that this approximation is sufficient to solve the problem .

## Challenges of uniform sampling 
- To cover whole configspace a lot of samples have to be computes.
- Each configurations mus be checked for validity. 
- The collision detect has to be very fast for the algorithm to be fast as well. 

[[06TheSPRMSummary]]