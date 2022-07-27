---
tags: harcon, java
---
[[HaRCon_General]]

# Selektirere Module speichern und laden 

## Selektiere Module speichern

```mermaid 
sequenceDiagram
	participant mwc as MainWindowController
	participant sz as Serializer
	participant ph as ProjectHandler

	mwc --> sz: serializeSelectedModules(Projekt loadedProject, List<Module> modules)
	mwc --> ph: saveProjectWithSelectedModules
	
```

- Selektierte Module werden im `Roaming/harcon/temp/selected-modules.json` gespeichert. 
- Anschließend muss das entsprechende Projekt entpackt und mit der  `selected-modules.json` neu verpackt werden. Das alte zip-Archiv wird gelöscht. 
- `saveProjectWithSelectedModules(String projectName`
	- unZip(projectName)
	- zip()
		- eba.zip
		- sys.sys
		- modules.json
	- deleteOldProjectArchive
		

## Selektierte Module laden 
```mermaid
sequenceDiagram
	participant usr as User
	participant obc as OnboardingController
	participant ph as ProjectHandler
	participant bnh as BordnetDataHandler
	participant mh as ModuleHandler
	participant sz as Serializer
	
	usr -->> obc : 	loadButtonOnClick()
	obc -->> ph : loadProject()
	ph -->> bnh : loadEbaAndSys()
	ph -->> mh : loadSelectedModulesFromModulesJson()
	Note right of ph : Separation of Concerns <br> Bordnetz und Module werden von verschiedenen Klassen geladen 
	
	mh -->> sz : unserializeModulesFromJson()
	
	
```
