[[SE2 - Metrics. Part 1.pdf]]
[[SE2 - Metrics. Part 2.pdf]]

[[SE2 - Metrics 1. Exercise.pdf]]
[[SE2 - Metrics 2. Exercise.pdf]]



## Martin Metrics
*Afferent Coupling (CA)*
The number of classes outside this package that depend on classes in this package. 
Indicator for the *responsibility* of the package. 

*Efferent Coupling (CE)*
The number of classes within this package that depended on classes outside the package. 
Indicator for the *independence* of the package. 

*Instability*
I = Ce / (Ce + Ca)

*Distance*
D = | A + I | - 1

*Abstractness*
A = abstract Cl.+Int. / all Classes

### Martin Metrics and layered Architecture
CA should increase from top to bottom 
CE should Decrease from top to bottom

Distance should be lower on the top and higher at bottom 

The numbers should be monotonic -> same direction or same number.