#lecture-note |  #t

---

# Sampling
- What is sampling based and why is it special? 
- Sample
	- Use random function to sample the cspace
	- Check if samples are free of collision
	- If so, store config in data structure
	- Apply algos for this set of points to inf a patch from one to another
- Why does this work?
	- We don't need to explicitly compute cspace
	- We approximate the free space  by random samples and hop that this approximation is sufficient to solve the problem 