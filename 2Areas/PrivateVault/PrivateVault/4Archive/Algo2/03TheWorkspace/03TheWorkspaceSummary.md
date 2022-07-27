# Summary 
[[03_AlgoDat2_The_Workspace.pdf]]

## What is the workspace?
The world which contains the robot and the obstacles. 

## Backtracking algorithm
Two different rules where it checks each field around the mouse 

When there anre not more white fields the last field will get deleted from the stack 

### Backtracking Exercise
![[4Archive/Algo2/03TheWorkspace/Exercise.png]]

Write x achsis first and the y achsis. 

*When to use backtracking*
- When the workspace is two dimensional 
- When the amount of discrete intervals is "small"
- When the robot can only move in two dimensions. 
- When storage and performance are not relevant.

## What are the workspaces of our examples? 
There are two-dimensional and three-dimensional Workspaces.

Piano example: fixed boundaries
![[WR2.png]]
engine example: no boundaries
![[WR3.png]]
puzzle: the moving part is the robot the othe one is the boundary 
![[WR3.png]]

## Collision detection
The most challenging task in the workspace.

*Voxmap PontShell Algorithm*
Used in the practical work study. 

1. Convert obstacles in workspace into pixel/voxel field.
2. All covered pixels are black.
3. Take robot and discretize border to points. 
4. Test for all points whether it is on a black pixel. 
5. If no point is in black pixel -> Robot is free of collision.

```python
class VRP {
	
	#sPRM.py
	def __init__(self, configspace, workspace): 
		self.vertex = []; # contains only configs free of collision.
		n = 0; # number of samples 
	
	def compute_samples(self, n, range_x, range_y):
		for x in range(n):
			sample = (random.randint(0, range_x), random.randint(0, range_y))
			
			if self.workspace.isInCollision(sample[0], sample[1]):
				self.vertex.append(sample)
	
	# workspace.py 
	def is_robot_in_collision(self, x, y): 
		difference = int(self.robotImage.size[0]/2)	
		x_edges = x - difference, x + difference 
		y_edges = y - difference, y + difference 
	
	for i in range(x_edges[0], x_edges[1]): 
		for j in range(y_edges[0], y_edges[1]): 
			if not self.envArray[j, i]: 
				return True
	return False
	
}
```

## How to model the robot and obstacles
*In 2D* 
The robot and obstacles are models with polygons.

*In 3D* 
The robot and obstacles are models with polyhedra
-> In practice triangle sets

[[02IntroMotionPlanningSummary]]
[[04TheConfigSpaceSummary]]