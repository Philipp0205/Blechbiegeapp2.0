#lecture-note |  #motion-planning #algorithms #datastructures

---
 
- Presentation of the sPRM
	- input 
		- init config and goal config
			- brackets = there can be muliple 
		- r = radius
		- n = amount of samples
	- E = Edge data structure 
		- all edges between two configs are stored
	- V = Vertex data structure
		- stores all configs
	- foreach 
		- loop over all pairs aif inits and goals
			- Add all point to V 
	- for 
		- union samples with V 
		- Remember: we don't know cobs 
	- for each
		- (two foreach loops usualy mean a quadradic algo)
		- Iterate over all samples and search all neighbours -
			- Neares nabour search
			- U are all neighbours
		- foreach
			- Iterator over all neighbours (U)
				- check if line can drawn
	- foreach
		- iteate of all sets (init, goal)
		- if start and goal point are pat of the path
			- shortest path
		- else
- ...

- The exercise will be like this in the exam page 34


- How do we know if we created enough samples?


