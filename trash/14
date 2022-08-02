---
marp: true
keywords: 
    - präsentation
    
---


# Erstellung der Biegesequenz
Philipp Kurrle

---

# Recap Dikstra 
---
![bg right:40%](images/dijkstra2.jpg)

<style scoped>
	ol {
		font-size: 23px;
	}
</style>

<!-- 
footer: https://de.wikipedia.org/wiki/Dijkstra-Algorithmus
-->

1. Weise allen Knoten die beiden Attribute „Distanz“ und „Vorgänger“ zu. Initialisiere die Distanz im Startknoten mit 0 und in allen anderen Knoten mit ∞. 
2. Solange es noch unbesuchte Knoten gibt, wähle darunter denjenigen mit minimaler (aufsummierter) Distanz aus und speichere, dass dieser Knoten schon besucht wurde.
3. Berechne für alle noch unbesuchten Nachbarknoten die Gesamtdistanz über die Summe des jeweiligen Kantengewichtes und der bereits berechneten Distanz vom Startknoten zum aktuellen Knoten.
4. Ist dieser Wert für einen Knoten kleiner als die dort gespeicherte Distanz, aktualisiere sie und setze den aktuellen Knoten als Vorgänger.

---

### Demo
- https://algorithms.discrete.ma.tum.de/graph-algorithms/spp-dijkstra/index_en.html


<!-- 
footer: ''
-->


--- 

# Recap A*
- Im Unterschied zu Dijkstra werden zusätzliche Heuristiken hinzugefügt. 
	- z.B. Distanz zum Endpunkt
- Dikstra is uninformed, only uses problem statement
### Demo
- https://algorithms.discrete.ma.tum.de/graph-algorithms/spp-a-star/index_de.html

---

# Paper
Automatic Determination of Bending Sequence in Sheet Metal Products 

![bg right 70%](images/paper.png)


---

Problem has been formulated as a graph search problem.

## Naive Approach
- Generate all possible beinding sequences and check each one of them. 
	- Potential **n! sequences!** (wihtout tools)
	- **O(tnn!)**

![bg right 80%](images/SimpleTree.png)

--- 
## Proposed Approach
**1. Reverse tree:** Start with folded prodcut and unfold step-by-step. 
- The last bending bends are usually the most complex, with reversing the tree more difficult bends are treated first. 
- Impossible bends can be discovered early -> less unnencesary computations.

**2. Separation:** Tool Assigment phase as pre-search phase. 

**3. A*** Reduction in the search domain with the A* Algorithm.
- Use domain specific heuristics to accelarate search. 

---

## Heuristics
According to A* terminology, peanalites are assigned to express the heuristic rules. All penalties are normalized into the range [0,1].
- **Collision** Transisiton from parent to child is immedaatly unfeasable.
- **Tool change**: Tool changing is time-consuming, requiring adjustments and trial bendings. 
- **Manipulations**:  Product must usually be reoriented between one bending operation and the next. 
- **Stability**: preferred state for bending occurs when the product's center of gravity is located between the operator and the machine. 

--- 










