---
tags: harcon, programming
---

# FitFunctions Funltionsweise

- Es gibt eine FitFunction welche einen `DkConnctor` und einen `DkTemplateSlot` vergleicht.
- Map der Kombinationen erstellen `Map<DkConnector, DkTemplateSlot>`
	- `connector.getCavities.size()` (int)
	- `templateSlot.getTemplatePins().size()`(int)
- Für jede Kombination einen FitValue errechnen

## Problem
Ich möchte am Ende zu jeem Fit-Value vielleicht auch den dazugehörigen Connector oder TemplateSlot. Deshalb sollten die kompletten Objekte gespeichert werden. 

Allerdings werden deutlich verschiedene Models benötigt weil sich die zu vergleichenden Objekte unterscheide. 

- Als Input wird immer ein `eba` und ein `sys` benötigt und dann werden bestimmte element davon verlgichen
	- Verglichen können z.B.  `DkConnector` und `DkTemplateSlot`.


- 
	

