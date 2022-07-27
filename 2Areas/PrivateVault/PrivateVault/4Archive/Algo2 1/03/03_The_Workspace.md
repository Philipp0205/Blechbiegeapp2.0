## Continous workspace

## Backtraking algorithm
- Two different rules where it checks each field around the mouse 
- When there anre not more white fields the last field will get deleted from the stack 

### Exercise
![[4Archive/Algo2 1/03/Exercise.png]]
- Use N/W/S/E

00 x
10 x
20 x
30 x
31 x 

01
02
12
13
23
33

### Solution
![[4Archive/Algo2 1/03/Solution.png]]

Write x achsis first and the y achsis

## What are the workspaces of our examples? 
- piano example: fixed boudaries
- engine example: no boundaries
- puzzle: the moving part is the robot the othe one is the boundary 

## Definition of configuration space
- Has 6 degrees of freedom (DOF)

car example
	- front and back = x 
	- rotation in frong = phi
	- = 2 degrees of freedim
	
trailer example: 
- The angle between trailer and truck is not a DOF.

### Recap
- The configuratoin space C is the space of all possbile configuratoins (movements) of the robot A. 


	