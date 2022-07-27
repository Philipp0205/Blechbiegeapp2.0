# Variables Summary 
## Difference Variables Imperative and OOP Languages 
- Variables in imperative and oop languages mirror the Von-Neumann-Architecture
	- A processor performing all computations
	- A Memory storing all variables
	- Variables values can be accessed and altered 
- Variables in function languages are named placeholders for function results
	- Var values can be accesses 
	- Variables cannot be altered 

## Attributes 
**Name** 
- Language like Java are case sensitive
- Often reserved keywords are used but keyword which are introduces later can break existing programs ]]
	
**Address**
- The address of a variables is a non-constant value during the program runtime 
	- Stack variables 
	- Heap variables 
- Aliasing possible 
	- Harder to understand 
	- Should not be used in multiprocesssed processes. Because all cores have to coordinate the access to the variable and that can the to concession.  
	- Java solved the problem with lambdas. Separates work on multiple cores. 

**Value** + Binding 

**Type**

**Lifetime**

**Visibility (Scope)**

## Binding 
- A binding is an association, such as between an attribute and an entity. 
- What is the type of the null literal in java? 
	- The mythical class which inherits from every class you know 
		- NullClass

```java
public Class NullClass extends Object, Integer, String, Student, File {
	public final static NullClass null = ; 
}
```
- In Eiffel this is called anyclass 

## Binding Times 
- Language design time 
- Lang implementation time 
- Compile time 
- Load time 
- Runtime 

## Coercion 
- Coersion is implicit conversion. 
- Explicit conversion is casting 

```
double x, y; 
x = 3;            // implicitly coercion (coercion) 
y = (double) 5;   // explicitly coercion (casting) 
```
- When you take a variables of one type and convert it's value to another type when performing an operation that is **coercion**.

**Another example**
```java
double x, y;
x = 3;            // implicitly coercion (coercion)
y = (double) 5;   // explicitly coercion (casting)
```

## Lifetime 
**Static**
- Binding to a memory cell takes place before program starts and is never releases 

**Stack-dynamic**
- Storage bindings are created when declaration is executed



## Difference Dynamic Static Scoping
- Static scope 
	- Based on program text
	- To connect variable name reference to a variable the compiler need to find the declaration first. 
	- Search process: declarations, first locally, then in increasingly larger enclosing scopes until it is found
	- Encourages many globals
- Dynamic
	- Not the textual layout determines data access but the calling order


## Type
## Explicit and Implicit Declaration 
- An explicit declaration is a program statement used for declaring the type of a variable 
- 
- Implicit declaration is a default mechanism for specifying types of variables 

```
// I think this means something like this 
// Explicist 
int test = 1; 

// Implicit
test = 1.0 
```

### Strongly + Weakly typed 
- A programming language is strongly typed if type errors are always detected
- Programming languages are often categorized according to their type checking
	- Strongly typed languages 
	- Weakly typed languages 
	
![[Strong_Weak_Typing.png]]

Advantage of strong typing: Allows the detection of misuses of variables that result in type errors 
	- Languages
		- Java is almost 
		- Pascal is mostly 
		- Ada is, almost 
		
# Anki cards (outdated)
TARGET DECK: CPL_03_Variables

START
Basic
What is the difference between variables in imperative and oop languages?
Back:
- Variables in imperative and oop languages mirror the Von-Neumann-Architecture
	- A processor performing all computations
	- A Memory storing all variables
	- Variables values can be accessed and altered 
- Variables in function languages are named placeholders for function results
	- Var values can be accesses 
	- Variables cannot be altered 
END

START
Basic
What are the **attributes** of a variable? 
Back:
- Name 
- Address
- Value 
- Type 
- Lifetime 
- Visibility 
END

START
Basic
What is the difference between **dynamic** and **static** scoping?
Back:
- Static scope 
	- Based on program text
	- To connect variable name reference to a variable the compiler need to find the declaration first. 
	- Search process: declarations, first locally, then in increasingly larger enclosing scopes until it is found
	- Encourages many globals
- Dynamic
	- Not the textual layout determines data access but the calling order
END

START
Basic
What is the difference between **strongly and weakly typed** languages? 
Back:
- A programming language is strongly typed if type errors are always detected
- Programming languages are often categorized according to their type checking
	- Strongly typed languages 
	- Weakly typed languages 

![[Strong_Weak_Typing.png]]

- Advantage of strong typing: Allows the detection of misuses of variables that result in type errors 
	- Languages
		- Java is almost 
		- Pascal is mostly 
		- Ada is, almost 
END

START
Basic

Back:

END

