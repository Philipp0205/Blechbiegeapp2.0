
# Project
- Big bitmap (flat)
- Small bitmap (robot)


## Compute Distance 
$$
\begin{equation}
\sqrt{(centerX- x) * 2 + (centerY - y) * 2}
\end{equation}
 $$ 
 
 ## Create nodes 
 - List of samples 
 - Give each sample id 
 
 | id  | x   | y   |
 | --- | --- | --- |
 | 1   | 12  | 13  |
 | 2   | 15  | 15  |
 | 3   | 1   | 2   |

 - Compute distances for each sample and add them to list

 | id1 | id2 | length |
 | --- | --- | ------ |
 | 1   | 2   | 5      |
 | 1   | 3   | 6      |
 | 3   | 1   | 2      |
 |     |     |        |
 |     |     |        |



# Performance

### Before  (500 samples)
- Parallelising sample generatoin 
```python
start = time.perf_counter()
# This takes a long time
self.draw_free_graph(neighbours_lengths, samples)
print(f"Completed Execution in {time.perf_counter() - start} seconds")
```

"Completed Execution in 13.920885 seconds"

After
