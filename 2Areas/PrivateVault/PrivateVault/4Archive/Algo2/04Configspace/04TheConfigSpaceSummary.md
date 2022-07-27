[[04_AlgoDat2_The_Configuration_Space.pdf]]

Motion planning is not done in the workspace. It is done in the *configuration space*. 
The config space is an additional space in the algorithm. All algos are defined in the configspace. 

## Definition
The configspace is not related to the workspace W itself, but to the motion definition of the robot A. 

The configspace C is the space of all possible configurations (movement) of robot A. 

In most cases  the configspace consists of 
- Rotational DOFs
- Translational DOFs

## What are the DOGS in our examples?
- Piano Mover Problem 
- Engine move problem
- Puzzle
- Parking
- Vacuum cleaner
- Robot with hand 


## Configurations
### Cfree and Cops
The configspace is subdivided into two sets of configurations: 
- Configurations where the robots in collision. *Cobs*.
- Configurations where the robot is free of collision. *Cfree*.

### Special configs
Cinit and Cgoal are special configurations.

## How does the configspace look like?

[[05SamplingInMotionPlanningSummary]]