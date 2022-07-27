# Basic Summary 
## Language Domains 
General Purpose 
- Java, C 
- System Programming
	- Assembler, C, C++,
- Business
	- Cobol, Abap, adabas
- Scientific
	- Fortran, Matlab, R
- Symbolic Computation
	- Lisp, Prolog (Lisp and Prolog are languages for reasoning about abstract content), Scheme
- Scripting
	- Perl, Python, Bash
- Web Programming
	- Php, JavaScript
- Markup languages
	- Tex, LaTex, XML, SQL
**Artificial intelligence**
- Pyton, Prolog, R, Lisp (Scheme)

**Number with many and not many of keywords**
- COBOL 357, C# 102, C++ 82
- Dart 54, Java 50 
- Python 35, Elm 25, Lua 25
- Smalltalk 6, iota 2

**Oldes newest**
- Assembly language (1949), LISP 1958, FORTTAN 1957, COBOL (1959)
- Swift (2014), Kotlin (2011), Dart (2011), TypeScript (2012)

## Language Selection Criteria 
- Readability
	- Easily read programs 
- Writeability
	- Easily write programs 
- Realiability
	- How often do programs fail
	- hard to detect failures?
- Cost
	- Cost of writing and running

## Language Types 
**Imperative**
- **Central:** variable, assignment, iteration
- **Samples**: Pascal, C, Fortran

**Functional**
- **Central:** Apply functions on parameters
- **Examples:** LISP, Scheme

**Logial**
- **Central:** Specify rules for solutions
- **Samples:** Prolog

**Object oriented**
- **Central:** Combine procedures and data into objects
- **Samples:** Java, C++, Smalltalk
	
## Implementation Techniques 
**Compiled Language**
- Separation between development and runtime
	- Java, C, C++
- Compiler output is byte code or machine code

Compiles languages are converted directly into machine code that can be executed. 
-> Faster and more efficient in execution. 
-> But additional time needed to complete entire compilation

**Interpreted Languages**
- Single environments for development and runtime
	- Python, Perl, PHP
- Intermedia format may be stored for efficiency

Interpreters run through every line and execute each command. 
-> Can be more flexible with features like dynamic typing. Smaller program size 


**Muli-Tier-Approach**
- Combination of compilatoin and interpretation
- Compile source code to byte code to machine code
	
## Pure Interpretation	
- The source code is immediately interpreted
- Allow for entering expressions at runtime 
- Tanslation is quite fast, often because typing and variables are not thoroughly checked 
- Execution slower than for compiled languages 
- Oft used for "small" and scripting languages because implementaiton is easy

## Compilation 
- Compilatoin is the tranformatoin of source code to machine code
- Translation is slower but execution is faster
- Compilatoin is generaly done in phases
	- **Lexical analysis:** Convert the character stream into a token tream
	- **Syntactic anlysis:** Convert the token stream into a syntax tree
	- **Semantic analysis:** Check for corss dpendencies
	- **Code generation** Generate final code

## Macro languages 
A macro instruction is a group of programming instructions that have been compressed into a simpler form and appear as a single instruction.

When used a macro expand from its compressed form into its actual instruction details.

First used in assembler language rather than higher level languages. 
**Macro Languages**
- M4
- Tex

**Languages which support macros**
- Lisp / Scheme 
- C 
- Assembler 

## High level / Low level
The main difference between between a *high level language* and a *low level language* is that Programmers can easily understand or interpret a high level languages. 

On the other hand machines can easily understand low level languages in comparison to human beings.
![[ComparisonHighLevelLowLevelLanguage.png]]

## Type Inference
Type interference refers to the automatic detection of the type of an expression in a formal language. 

**Languages**
C++, Haskell, 


## New programming language based on old one or not 
- There are arguments for both 
- Evolving languages tend to get complicated. More features are not always better 
- Recent languages have shown that good design and simplicity sells good 
	- See the Go programming language which is liked for it's simplicity 
	- It's not how many features are language has it's about the perfect set of features for one use case. 
- In my opinion everyone loves Kotlin, because it's a well designed programming language. Another example is Swift. 
- So to make a beautiful language it needs to be designed from the ground up and should not be based on an old language . 
- But there are sucessfull languages like Python which is written in C. 
- BUT you need to write the language in something. And that language is mostly C. 
	- Most languages are implemented in C or in a hybrid of C
- It depend on the use case. For some new languages it might be enough to extend an old one. 