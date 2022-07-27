
- What is the minimal resolution
- Translation
	- Every obstacle of 0.9 thickness has to be captured
	- Robot is moved by 5
		- 5/0.9 = 5,5
- Rotation
	- Needs to be rotated about 45°
	- Length 20
		- 20 * cos(45°)/20 * sin(45°)
		- = 14,14 / 14,14
	- sqrt((14,2-20)² + (14,2-0)²) = 15,33
	- Largest distance is 15,33
	- 15,33 units / 0.9 diameter = 17,03 steps
	- Resolution/CS = 18
- Combined
	- max(6,18) = 18
	- -> A resoluton if 18 is needed, this means 18 collision calls


- Question: Where is the max point where are robot can move
	- In you example the upper corner
	- Distance we need to compute is the the length of the line 