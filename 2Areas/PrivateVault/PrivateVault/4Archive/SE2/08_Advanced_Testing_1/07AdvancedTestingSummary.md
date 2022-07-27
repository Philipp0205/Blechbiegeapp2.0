

## Mockito
### Doubles 

*Dummy Object*
- null
- or with no functionality. 

*Stub*
- Provides ouput on calls. 
- Sometimes irregular outputs.

A stub is a fake class that comes with programmed return values. It's injected into the class under test to give you absolute control over what's being tested as input. 

A typical stub is a database connection that allows you to mimic any scenario without having a real DB.

*Spy*
- Stubbing
- Records interactions

A spy calls the real methods on an object while a mock calls methods on the double object. 

We generally use **mock when we have to completely mock the object behavior while using spy we will be spying or stubbing specific methods of it**.

*Mock*
- spying 
- configuration / verification of interaction

Mocking removes external dependencies from a unit test in order to create a controlled environment around it. 

A mock is a fake class that can be examined after the test is finished for its interactions with the class under test. 

For example, you can ask it whether a method was called or how many times it was called. 
Typical mocks are classes with side effects that need to be examined.


*Fake Object*
- "light" / "dirty" working implementation
- substitutes the actual object

### Use Case 
*Mockito allows*
- Mocking interfaces -> on-the-fly creation of interface-objects.
- Simple creation of mock-object
- Injection of mock-objects in components under test

*Mock-Objects*
- Can be stubbed -> method-results can be defined.
- Can be verifies -> check that certain interactions have happened 

*Advantages*
Simple usage

*Disadvantages*
Having addition library, learning a framework. 


## Other Tools 

*JUnit*
Test methods at class level

*EclEmma*
Code coverage tool 

*Native Java*
Access or change private (or even constant fields) for test purposes

*ascpectj*
Changing existing behavior, reaching otherwise unreachable code parts

*Selenium*
Browser automation 
Can be used with Junit together 




