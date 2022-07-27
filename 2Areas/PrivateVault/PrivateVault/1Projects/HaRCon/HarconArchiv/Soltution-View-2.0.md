---
tags: harcon, documentation, programming
---
Refs:  [[]]

# Aufbau
- Zwei Tabellen:
	- Vergleichstabelle - `ConnectorName`, `Templatenname` und `FitValue`. 
	- Detailtabelle - Detailansicht, anders je nach FitFunction

# Implementation
- ComparisonTable(String)
- DetailTable(String)
	- Muss dynamisch sein. 

```mermaid
sequenceDiagram
	participant user as User
	participant ff as FitFunction
	participant ct as ComparisonTable
	participant dt as DetailTable
	
	user -->> ff : useFitFunction()
	
	
```

```mermaid 
classDiagram
	class ComparisonTableModel { 
		-template:Template
		-connectorConnector
		-fitValue:String
		public ComparisonTable(Connector, Template)	
	}
	class DetailTableModel { 
		-fitFunction:FitFunctoin
		-comparisonTableModel
	}


```	
	
	
