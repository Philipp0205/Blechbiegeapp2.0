
# Syntax Semantics Summary 

##  Definition
The *syntax* describes its form and structure. 
The *semantics* describes the meaning of a program. 

##  Context Free Grammars (CFG)

### Remove Left Recursion

Left recursive rule: 
$$\begin{equation}
A \rightarrow A \alpha / \beta
\end{equation}$$

Formula to resolve left recursion
$$\begin{aligned}
A \rightarrow \beta A' \\
A' \rightarrow \alpha A' / \epsilon
\end{aligned}$$

### Left Refactoring
Grammar with common prefixes
$$\begin{aligned}
A \rightarrow a \alpha 1 | a \alpha 2 | a \alpha 3 \\
\end{aligned}$$
Left Factored grarmmar
$$\begin{aligned}
A \rightarrow  aA' \\
A' \rightarrow \alpha1 | \alpha2 | \alpha3
\end{aligned}$$


### Sources 
https://www.gatevidyalay.com/left-recursion-left-recursion-elimination/


## Syntax Trees 
Syntax trees are abstract or compact repesentations for parse trees. 
The are also called *Abstract Syntax Trees.*


## Grammar Ambiguity
> A grammar is said to be ambiguous if for any string generated by it, it produces more thane one 
> - Parse tree
> - Or derivation tree
> - Or syntax tree
> - Or leftmost derivation
> - Or rightmost derivation

### Example for leftmost derivation
w = id + id x id
```
E -> E + E | E x E | id

E -> E + E 
-> id + E 
-> id + E x E 
-> id + id x E 
-> id + id x id 


E -> E x E 
-> E + E x E 
-> id + E x E 
-> id + id x E 
-> id + id x id 
```
Since two leftmost derivations exist for string w, therefore the grammar is ambiguous. 
