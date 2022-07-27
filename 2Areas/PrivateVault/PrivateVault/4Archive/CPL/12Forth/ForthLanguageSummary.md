# Forth Summary 
- Stack based language 

## Basic commands (not needed for exam)
- `.s` show the stack 
- Whitespace is seperator 
- Functions are called *words*

## The Forth Data Model
Data stack 
Return stack 
Floating point stack 
Locals stack 

## Variables 
### Locals (Local variable definitions)
 Curly braces in a word definition allow you to create local variables in the definition.

```forth
: swap { a b -- b a }
b a ;
```

## Control Structures 
Simple Branches 
Multiple Branches 
General loops
Counted loop
Indefinite loops

...

## Conditionals
Conditionals can only be used *within a colon definition*.

```forth
 : abs ( n1 -- +n2 ) 
   dup 0 < if
   negate
 endif ;
```

**NOTE:** In Forth, `endif` is less commonly used. Typically, the word `then` is used. But that's really confusing for non-forth programmers.

Another example:
```forth
: min ( n1 n2 -- n )
 2dup < if 
  drop
 else
  nip
endif;
```

## Words 
: *name* ;

**Example:**
Divides number by to by putting to on stack and then / 

```forth
: divide 2 / ;
```

**Comments**
`\ comment `

### More complex examples 
*CREATE*
Creates a new dictionary entry

*DOES>*
Marks the end of the compile-time behavior and the beginning of the run-time behavior.

```forth
: CHARACTERS CREATE DUB, ALLOT
	DOES> ( -- addr len) DUP CELL+ SWAP @ ; 
```

**Breakdown**

*CREATE*
Create a new dictionary entry (e.g., ME)

*DUP , ALLOT*
Compiles the count (e.g., twenty) into the first cell of the array for future reference. Then allots an additional twenty bytes beyond the count for the string.

*DOES>*
Marks the beginning of run-time code, leaving the body address of the product-word on the stack at run time.

*DUP*
Copies the body address.

*CELL+*
Advances the address to point past the count, to the start of the character string.

*SWAP @*
Swaps the string address with the count address and fetches the count. The stack now holds ( addr count — ).

### Stack Manipulation 


### Immediate and Postpone 
**Immediate**
The word *immediate* makes a word execute right after the compilation of the definition 

```forth
: name definition ; IMMEDIATE \ generic 
: SAY-HELLO . "HELLO" ; IMMEDIATE \ specific
```

If we put the word *inside* another definition, it will execute at *compile time*.

```forth
: GREET SAY-HELLO ."I SPEAK FORTH" ; HELLO ok 
```

rather than at *execution time*
```forth
GREET I SPEAK FORTH ok
```

**Postpone**
By using *postpone* the compilation semantics of the next word is compiled into the current definition. 

## "Types"
Forth doesn't do any type checking whatsoever. It's not a big deal though, but you should be aware of it.
 * `(none)` - signed integer 
 * `u` - unsigned integer 
 * `c` - character
 * `d` - signed double-cell integer 
 * `ud`, `du` - unsigned double-cell integer
 * `2` - two cells (not-necessarily double-cell numbers)
 * `m`, `um` - mixed single-cell and double-cell operations 
 * `f` - floating-point (note that in stack comments 'f' represents flags, and 'r' represents FP numbers).

## Recursion
```forth

: FACTORIAL ( +n1 -- +n2)
   DUP 2 < IF DROP 1 EXIT THEN
   DUP 1- RECURSE *
;
```


## Fibonacci
```forth
: !"§$%&/() ( n -- n )  
dup 0< if drop 1 else 1- dup 1- recurse swap recurse + endif ;
```


# Exam Question
> Contrary to most other programming languages FORTH does not allow you to use the name of the word being defined inside the definition to call the word recursively, but you must use the predefined word recurse. What does this tell you about the compilation process in FORTH? 

Forth puts all words into a dictionary. When a word is called forth looks up the definition in the dictionary. 
That means the definition of a word in invisible during its own definition. 
To make recursion possible, there Forth uses the keyword `recurse`.

