# Primitive Obsession
Refs: [[Refractoring Kurs]]
Tags: #refactoring 

---
![[Pasted image 20201123143506.png]]
Primitive Obsession is using primitive data types to represent domain ideas. For example, we use a String to represent a message, an Integer to represent an amount of money, or a Struct/Dictionary/Hash to represent a specific object.

### Recipe 1: Replace Set of Field with Object
If you have a large variety of primitive fields, it may be possible to logically group some of them into their own class. Even better, move the behavior associated with this data into the class too. For this task, try Replace Data Value with Object.

![[ReplaceDataValueWithObject.png]]

### Recipe 2: Primitive Fields in Mehod Parameters
If the values of primitive fields are used in method parameters, go with Introduce Parameter Object or Preserve Whole Object.

#### Introduce Parameter Object
![[IntrodouceParameterObject.png]]

##### Preserver Whole Object
![[PreserverWholeObject.png]]

### Recipe 3: Get Rid of Type Codes
When complicated data is coded in variables, use Replace Type Code with Class, Replace Type Code with Subclasses or Replace Type Code with State/Strategy.

#### Replace Type Code With Class
![[ReplaceCodeWithClass.png]]
#### Replace Type Code with Subclasses
![[ReplaceCodeWithSubclasses.png]]
#### Replace Type Code with State/Strategy
![[ReplaceCodeWithStateStrategy.png]]

### Recipe 4: Replace Array with Object
If there are arrays among the variables, use Replace Array with Object.

![[ReplaceArrayWithObject.png]]