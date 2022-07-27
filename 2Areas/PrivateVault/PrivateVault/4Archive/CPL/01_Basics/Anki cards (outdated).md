# Anki cards (outdated)

TARGET DECK: CPL_01_Basics

START
Basic
What are some **Language Domains**?
Back:
- General Purpose 
	- Java, C 
- System Programming
	- Assembler, C, C++,
- Business
	- Cobol
	- Abap
	- adabas
- Scientific
	- Fortran
	- Matlab
	- R
- Symbolic Computation
	- Lisp
	- Scheme
	- Prolog
- Scripting
	- Perl
	- Python
	- Bash
- Web Programming
	- Php
	- JavaScript
- Grey area
	- Markup languages 
		- Tex, LaTex
		- XML
		- SQL
<!--ID: 1623584923284-->
END


START
Basic
What are Language Selection Critereas?
Back:
- Readability
	- Easily read programs 
- Writeability
	- Easily write programs 
- Realiability
	- How often do programs fail
	- hard to detect failures?
- Cost
	- Cost of writing and running
<!--ID: 1623584923311-->
END

START
Basic
Briefly explain the **Von Neumann** and **Harvard Architecture**
Back:
- Von Neumann Architecture
	- Predominant in the area of general computer
	- Program and data are stored in the same mian memory 
		- Program is data 
		- Data is program
	- Memory is separate from CPU
- Harvard Architecture
	- Predominant in area of embedded computer
	- Porgram and data are stored in different areas of memory
		- Program is stored in read only 
		- Data is stored modifiable in RAM
<!--ID: 1623584923326-->
END

START
Basic
Name **Language Categories**
Back:****
- **Imperative**
	- **Central:** variable, assignment, iteration
	- **Samples**: Pascal, C, Fortran
- **Functional**
	- **Central:** Apply functions on parameters
	- **Examples:** LISP, Scheme
- **Logial**
	- **Central:** Specify rules for solutions
	- **Samples:** Prolog
- **Object oriented**
	- **Central:** Combine procedures and data into objects
	- **Samples:** Java, C++, Smalltalk
<!--ID: 1623584923339-->
END

START
Basic
What the some **Implementation Techniques**?
Back:
- **Compiled Language**
	- Separation betweeen development and runtime
		- Java, C, C++
	- Compiler output is byte code or machine code
- **Interpreted Languages**
	- Single environments for development and runtime
		- Python, Perl, PHP
	- Intermedia format may be stored for efficiency
- **Muli-Tier-Approach**
	- Combination of compilatoin and interpretation
	- Compile source code to byte code to machine code
<!--ID: 1623584923351-->
END

START
Basic
What does **Pure Interpreation** mean?
Back:
- The source code is immediately interpreted
- Allow for entering expressions at runtime 
- Tanslation is quite fast, often because typing and variables are not thoroughly checked 
- Execution slower than for compiled languages 
- Oft used for "small" and scripting languages because implementaiton is easy
<!--ID: 1623584923373-->
END

START
Basic
What does **Compilation** mean?
Back:
- Compilatoin is the tranformatoin of source code to machine code
- Translation is slower but execution is faster
- Compilatoin is generaly done in phases
	- **Lexical analysis:** Convert the character stream into a token tream
	- **Syntactic anlysis:** Convert the token stream into a syntax tree
	- **Semantic analysis:** Check for corss dpendencies
	- **Code generation** Generate final code
<!--ID: 1623584923394-->
END