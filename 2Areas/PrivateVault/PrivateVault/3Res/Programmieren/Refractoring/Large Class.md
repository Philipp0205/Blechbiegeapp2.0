# Large Class
Refs: [[Refractoring Kurs]]
Tags: #refactoring

---
![[Pasted image 20201123143515.png]]
Classes can get large over time. 

### Recipe 1: Extract Class
Extract Class helps if part of the behavior of the large class can be spun off into a separate component.

![[3_Resources/Programmieren/Refractoring/ExtractClass.png]]

### Recipe 2: Extract Subclass
Extract Subclass helps if part of the behavior of the large class can be implemented in different ways or is used in rare cases.

![[ExtractSubclass.png]]

### Recipe 3: Extract Interface
Extract Interface helps if it's necessary to have a list of the operations and behaviors that the client can use.

![[Extract Interface.png]]

### Recipe 4: Sepearte GUI and Domain Data
If a large class is responsible for the graphical interface, you may try to move some of its data and behavior to a separate domain object. In doing so, it may be necessary to store copies of some data in two places and keep the data consistent. Duplicate Observed Data offers a way to do this.

![[DuplicateObservedData.png]]
