[[svv_handout_updated.pdf]]

# Recap 
Maybe in exam: 
- shows code and asks for halting problem. Does it terminate?

# Basics of Software Test 
- Software Testing is not Debugging 
- Does not proof correctness. Only show that the given test case in the given environment is properly handled
- Good testing data increases trustworthiness of software

Can be done by 
- Devs
- Specialized testers
- Automated testing equipment
Roleconflicts possible. 


## Types
**Blackbox Test** No kowledge of nor access to the internals of the program
**Whitebox Test** good knowledge of the internals of the programs 
**Grebox tests** knowing something about the programs internals. 

## How much testing is enough
- Exhaustive testing is impossible 

### Non-Exhaustive Testing 
- Test cases with **valid** and **invalid** data. 
- Random data possible as well 

## Fuzz testing 
What happens if you feed software more or less **randomly created data**?

**Approaches** 
- Test the operating system resilience.
- ... 

### Testing App Resilience 

### Systematic Testing 
- Relies on software testers to create test cases
- Typically try to test software with as few as possible test cases.
- Most important task is test data selection

## Test case selection 
### Production data
- Using real data may be problematic (GDPR) 
- Security concers
- 


### Manual Creation

# Statement & Branch Coverage (video?)

# Condition Coverage

# Code Coverage Practice 
- Statement coverage
- Branch coverage
- Condition coverage

