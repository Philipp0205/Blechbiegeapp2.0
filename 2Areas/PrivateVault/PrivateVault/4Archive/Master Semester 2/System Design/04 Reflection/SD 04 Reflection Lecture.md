[[SD - 04 - Reflection.pdf]]

# Reflection 
## Use case 
- A system must be able to adapt his structure dynamically during runtime. 
	- Type structures, classes, methods etc. can change during runtime. 

*Advantage*
High flexibility
*Disadvantage*
Complex code, Risk of runtime problems

Experience shows
- Required high flexibility rarely can be handeled 
- the config effort is usually too big.

## Reflection Workflow 
1. Evaluate Annotation wich denotes that there should be something injected. 
2. Looking for the element which has to be injected (eg. properties file, env variable)
3. You know the name of the element that would bei injected 
4. Create object to be injected
5. Assign element to variable 

# Annotations 
- Annotation allows to add meta-information to classes, methods, or fields. 
- Allows to add, change or select behaviour during runtime instead of changing code. 

## Reflection of Annotations  
- During runtime a program can
	- Access a class or the declared elements of the class 
	- access the annotations of that element 
	- get parameters of the annotation 
	- set/change the behavior of the program according to the parameters

# Code injection
- A field is declared, but not instantiated - it is annotated instead
- The field should be instantiated with a concrete subclass which is retrieved during object creation 

### Approach
- An object of *MyClass* is not directly created but by a Factory. 
- The Factory 
	- creates the object 
	- checks for annotated fields 
	- checks for desired concrete type of the field 
	- creates object of the desired field
	- assigns it to the field 


## Objects
Retrieve class from object 
```java
Class<?> cls = anObject.getClass();

if (anObject instanceof AClass)
...
```

## Fields
```java
// public fields 
cls.getFields();

// all firelds
cls.getDelcatedFields();


// specific fields
cls.getField(name);
cls.getDeclatedField(name)
```

```java
// return the value of the fiels represented by this field 
field.get(Object object)
// sets the field of the given object
field.set(Object object, Object value)
// erases private
field.setAccessible(boolean)
// gived modifiers 
fiel.getModifiers()
// returns true if fields is annoated 
fiels.isAnnotationPresen(Class<? extends Annotation) 
```

## Methods
```java
// returns public methods
cls.getMethods();
// returns all declated methods
cls.getDeclatedMethods();
// get the public method with given signature
cls.getMethod(name, ...type);
cls.getDeclatedMethod(name, ...type);

```

```java
method.invoke(Object obj, Object... args)
method.getParameterTypes();
method.getReturnType();
```

## Constructors
```java
cls.getConstructors();
cls.getDeclatedConstructors();
cls.getDeclaredConstructor(type...typeN)
```

