[[AUTOSAR_Architecture_and_Design_SYD_WS2021 1.pdf]]

De-facto open industry standard for **auto**motive **s**oftware **ar**chitecture. 
"Cooperate on standards - compete on implementation"

## Objectives
- Serviceability over the entire product life cycle
- Abstraction of hardware from software
- Improvement in software quality 
- Competition is focused onto OEM-relevant features 
- Reusability of functions across vehicle networks across OEM boundaries. 

## Characteristics of Embedded Systems 
- Connected with other systems 
- Hardware and software are not separated 
- Monolith software 
- Only whole software image can be updated 
- Working in real world an in real time 

# Layered Design Pattern
## Characteristics 
- System structured vertically in parts = layers 
- Each layer is defined by its abstraction level
- Lay has clear definition 
- Layers are stacked, each layer depends only on the layers below
- Each layer has a clear interface to above 

## Pro
- Changes of source code have only local effect 
- APIs based on abstraction level may be standardized
- Layers can be exchanged
- Decomposition with clear components on abstraction 

## Cons 
- Performance
- Definition of layer is not always clear 
- New functionality may not fit  into structure 

![[Pasted image 20220131113200.png]]

# Generator Design Pattern
- Code is generated from config
	- Config instead of programming
	- Reduced dev time 
	- Easier to write - less errors
	- Easier to read - easier to check 
- Code fits exactly to the concrete system
	- Higher performance 
	- Less code 

## Pros
- Time reduction in development
- Application can easily be changed 
- Performance 

## Cons 
- Generator need to be reliable 
- High investment 
- Static 


