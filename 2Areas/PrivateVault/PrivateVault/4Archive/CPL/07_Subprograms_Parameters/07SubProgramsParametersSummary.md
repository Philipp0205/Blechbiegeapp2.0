# Sub-Programs Summary 

## Types of subprograms 
- A collection of statements that can be re-used.
- **Types**
	- **Procedures**
		- Return nor value, side effects only
	- **Functions**
		- Return a value, are not supposed to have side effects, but usually do anyway
	- **Methods**
		- Like functions, but special in their dependence on a calling object. 


## Structure 
- **Call**
	- Explicit request to execute the subprogram
- **Header**
	- is the first part of the definition, containing the name, the kind and the formal parameters of the subprogram 
- **Signature**
	- Is the number, order and types of its parameters
- **Protocol**
	- Is a subprograms signature and if it returns a value its return type

```java

//header (name) 
public void test() {
	// signatrue
	sysout(...);
	// protocol	
	return null;
}

//call 
test();
```

## Design Issues 
- **What parameter passing methods are provided?**
	- The transmission of parameters to and from the called subprograms is called **parameter passing**
	- **Parameter Uses**
		- Pass values to the subprogram (in mode)
		- Pass result from the subprogram (out mode)
		- Read value from parameter and modify it (inout mode)
	- **Techniques**
		- Pass-by-value
		- Pass-by-result
			- Used to communicate results back to caller (out mode)
		- Pass-by-value-result
		- Pass-by-reference
			- The subprogram get an access path (eg. memory address, all modes)
			- Aliasing possible
		- Pass-by-name
- **Are parameter types checked?**
- **Can subprograms be overloaded?**
- **Can subprogram be generic?**

## Parameter passing 
**Pass-by-value**
Function creates copy of the argument. The copy has the same value as the original. 

**Pass-by-reference**
No separate argument created but a reference to the argument is passed.

**Pass-by-value-result**
Like pass-by-value but at the very end instead of discarding the copies of the variables these copies are written back to the original arguments at the very end of the function. 

**Pass-by-name**
Actual parameters textually replace formal variables.

# Anki Cards (outdated)

TARGET DECK: CPL_07_Subprograms

START
Basic
What is a **subprogram** and which types are there?
Back:
- A collection of statements that can be re-used
- **Types**
	- **Procedures**
		- Return nor value, side effects only
	- **Functions**
		- Return a value, are not supposed to have side effects, but usually do anyway
	- **Methods**
		- Like functions, but special in their dependence on a calling object. 
END


START
Basic
How is a subprogram structured? 
Back:
- **Call**
	- Explicit request to execute the subprogram
- **Header**
	- is the first part of the definition, containing the name, the kind and the formal parameters of the subprogram 
- **Signature**
	- Is the number, order and types of its parameters
- **Protocol**
	- Is a subprograms signature and if it returns a value its return type
END

START
Basic
What are the **design issues** of Subprograms?
Back:
- **What parameter passing methods are provided?**
	- The transmission of parameters to and from the called subprograms is called **parameter passing**
	- **Parameter Uses**
		- Pass values to the subprogram (in mode)
		- Pass result from the subprogram (out mode)
		- Read value from parameter and modify it (inout mode)
	- **Techniques**
		- Pass-by-value
		- Pass-by-result
			- Used to communicate results back to caller (out mode)
		- Pass-by-value-result
		- Pass-by-reference
			- The subprogram get an access path (eg. memory address, all modes)
			- Aliasing possible
		- Pass-by-name
- **Are parameter types checked?**
- **Can subprograms be overloaded?**
- **Can subprogram be generic?**
END

START
Basic

Back:

END

START
Basic

Back:

END

