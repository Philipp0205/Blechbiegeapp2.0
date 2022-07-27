# Prolog Summary
## Basic Terminology 
- Facts 
- Rules 
- Query 

## Concepts

```prolog
% fact 
happy(philipp).

% rule 
listens2Music(philipp):- happy(philipp).
```

The :- should be read as *if*. The part on the left hand side of the :- is called the *head* of the rule, the part on the right side is called *body*. 
If the body of the rule is true, then the  head of the rule is true too. 

### Modus Ponens 
If a knowledge base contains a rule head :- body, and Prolog knows that body follows from the information in the knowledge base, then Prolog can infer head. 

This is called **modus ponens**. A

### Unification
Two terms *match* or *unify*, if they are equal or if the  contain variables that can be instantiated in such a way that the resulting terms are equal.

```prolog
?- loves(jay, X) = loves(jay, kathy).
% -> X = kathy
```

### Recursion 
Recursions need one *base case* and a *recursive case*.

Simple Example: [[11PrologSummary#Recursion]]

#### More complex example
```prolog
is_digesting(X,Y) :-  just_ate(X,Y).  
is_digesting(X,Y)  :-  
	just_ate(X,Z),  
	is_digesting(Z,Y).  
 
just_ate(mosquito,blood(john)).  
just_ate(frog,mosquito).  
just_ate(stork,frog).
```

How Prolog processes this query:
```prolog
?- is_digesting(stork, mosquito).
% First rule -> 
just_ate(stork, mosquito).
% Second rule 
just_ate(stork, Z),
is_digesting(Z, mosquito).
% Z can be replaces with frog (unification?)
```

#### Another example 
```prolog
 	
```

For query
```prolog
?- decend(anne, donna).

%Callstack
Call: child(anne, donna) ? creep 
% child(anne, Z) -> unification Z=bridget, Y=donna
% decend(bridget, donna)
Call child(bridget, donna) ? creep
% child(bridget, Z) -> Z = caroline, Y=donna -> 
% descent(caroline, donna)
Call child(caroline, donna) ? creep
true
```

Full callstack: 
```prolog
   Call: (10) descend(anne, donna) ? creep
   Call: (11) child(anne, donna) ? creep
   Fail: (11) child(anne, donna) ? creep
   Redo: (10) descend(anne, donna) ? creep
   Call: (11) child(anne, _12462) ? creep
   Exit: (11) child(anne, bridget) ? creep
   Call: (11) descend(bridget, donna) ? creep
   Call: (12) child(bridget, donna) ? creep
   Fail: (12) child(bridget, donna) ? creep
   Redo: (11) descend(bridget, donna) ? creep
   Call: (12) child(bridget, _12726) ? creep
   Exit: (12) child(bridget, caroline) ? creep
   Call: (12) descend(caroline, donna) ? creep
   Call: (13) child(caroline, donna) ? creep
   Exit: (13) child(caroline, donna) ? creep
   Exit: (12) descend(caroline, donna) ? creep
   Exit: (11) descend(bridget, donna) ? creep
   Exit: (10) descend(anne, donna) ? creep
```

### Cheat sheet 
[[PrologCheatSheet.pdf]]

## Exam questions about Prolog
### Prolog and Scheme mathematical concepts
- They are build around the concept of functional application from 
- Built around the concept of functional application (from λ calculus)
- Uses expressions (evaluate to a value) instead of statements (alter machine state)
- Uses recursion instead of iterative loops

### Search Tree
Knowledge Base:
```prolog
pet(X):- small(X), harmless(X), furry(X).

small(fly).
small(tarantula).
small(guineaPig).

harmless(fly).
harmless(guineaPig).

furry(tarantula).
furry(guineaPig).
```

![[PrologTree.png]]

### Recursion
Knowledge base:
```prolog
find(X,[X|List]).
find(X,[Y|List]) :- find(X,List).
```

**What does the predicate do?**
Recurses down a list to find if a certain input is in the list.

**Base case**
The first line is the base case. It terminates the loop and prevents an infinite recursion. 

The call `find(3,[])` immediately returns false because the list is empty. 

**Call Stack**
```prolog
Call: find(3, [1,2,3,]) ? creep
Call: find(3, [2,3]) ? creep
Call: find(3, [3]) ? creep
Exit: find(3, [3]) ? creep
Exit: find(3, [2,3]) ? creep
Exit: find(3,[1,2,3]) ? creep
true
```