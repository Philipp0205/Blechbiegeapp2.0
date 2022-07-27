graph TD

subgraph interoperabilität
IN([Fähgikeit des Artefakts mit anderen Componenten oder Systemem zu interagieren]):::def ---INT[Interoperabilität]:::goal --- N
N[Hohe <br> Homogenität]
 N --> Q[Einheitl. <br>  Technologie] --> SA[Standadisierung  der <br> Anwendungskomponenten]:::metric
  N --> R[Einheitl. <br> Schnittstellen] --> SS[Schnittstellenstandardisierung]:::metric 
  R --> K[Konnektoren]:::metric
end
subgraph anpassbarkeit
	ANPA([Fähigkeit des Systems sich ein Veränderungen der Spezifikation oder der Umwelt anzupassen]):::def 
end 
subgraph modifizierbarkeit
  DM([Charakterisiert den Aufwand zur Änderung des Systems.]):::def --- MO
  MO[Modifizierbarkeit]:::goal --> P[Adäquate Kopplung] --> KO[Hohe <br> Kohäsion]:::metric & LK[Lose Kopplung] & AK[Austauschbare <br> Komponetnen]
  AK:::metric 
  LK:::metric
end
subgraph tauglichkeit
	ANG([Angemessenheit der Funktionen der Software nach Spezifikation]):::def --- TAU[Tauglichkeit]:::goal --> VO[Vorhandenheit der <br> Anfoderungen]:::metric & AN[Angemessenheit der <br> Anforderungen]
	AN:::metric
end
subgraph fehlertolzeranz
	FEHL([Die Fähigkeit des Artefakts den Ausfall Fehler in Komponenten oder der Umgebung zu wiederstehen]):::def --- 
	FEH[Fehlertoleranz]:::goal --> Fehlerbehandlung:::metric
end
subgraph austauschbarkeit

end


classDef metric stroke:gray ,stroke-width:2px ,stroke-dasharray: 5, 5
classDef goal fill:#f96
classDef irr color: gray, stroke:gray, stroke-width:2px, stroke-dasharray: 2,10
classDef def font-style:italic, font-size: 80%



```mermaid
graph TD
subgraph modifizierbarkeit

  DM([Charakterisiert den Aufwand zur Änderung des Systems.]):::def --- MO
  MO[Modifizierbarkeit]:::goal 
  MO --> HH


  subgraph interoperabilität
    HH[Hohe <br> Homogenität] --> PH["[...]"] & PH2["[...]"]
  end
end

subgraph austauschbarkeit
  AUST([Die Fähgikeit des Systems Komponenten auzutauschen]):::def --- AUS[Austauschbarkeit]:::goal
  AUS --> D[Hohe Modularität] --> E[Hohe fachliche <br> Modularität]:::metric
  D --> F[Hohe technische  <br> Modularität]:::metric 
  AUS --> P[Adäquate Kopplung] --> KO[Hohe <br> Kohäsion]:::metric & LK[Lose Kopplung] & AK[Austauschbare <br> Komponetnen]
  AK:::metric 
  LK:::metric
end

classDef metric stroke:gray ,stroke-width:2px ,stroke-dasharray: 5, 5
classDef goal fill:#f96
classDef irr color: gray, stroke:gray, stroke-width:2px, stroke-dasharray: 2,10
classDef def font-style:italic, font-size: 80%
```

## Austauschbarkeit
```mermaid
graph TD
  AUST([Die Fähgikeit des Systems Komponenten auzutauschen]):::def --- AUS[Austauschbarkeit]:::goal
  AUS --> D[Hohe Modularität] --> E[Hohe fachliche <br> Modularität]:::metric
  D --> F[Hohe technische  <br> Modularität]:::metric 
  AUS --> P[Adäquate Kopplung] --> KO[Hohe <br> Kohäsion]:::metric & LK[Lose Kopplung] & AK[Austauschbare <br> Komponetnen]
  AK:::metric 
  LK:::metric

classDef metric stroke:gray ,stroke-width:2px ,stroke-dasharray: 5, 5
classDef goal fill:#f96
classDef irr color: gray, stroke:gray, stroke-width:2px, stroke-dasharray: 2,10
classDef def font-style:italic, font-size: 80%
```

## Modifizerbarkeit
```mermaid
graph TD

  DM([Charakterisiert den Aufwand zur Änderung des Systems.]):::def --- MO
  MO[Modifizierbarkeit]:::goal --> EA[Entwicklungsaufwand] --> KK[Komplexität <br> Artefakt & Komponenten]:::metric & DOC[Dokumentation] 
  MO --> RD[Redundanzfreiheit] --> FR[Funktionale <br> Redundanzfreiheit]:::metric & DR[Datenredundanzefreiheit]
  DR:::metric
  DOC:::metric
  MO --> HH & HM & AKK 



  subgraph interoperabilität
    HH[Hohe <br> Homogenität] --> PH["[...]"] & PH2["[...]"]
  end
  subgraph austauschbarkeit1
    HM[Hohe <br> Modularität] --> PH3["[...]"]
    AKK[Adäquate <br> Kopplung] -->  PH4["[...]"]
  end

classDef metric stroke:gray ,stroke-width:2px ,stroke-dasharray: 5, 5
classDef goal fill:#f96
classDef irr color: gray, stroke:gray, stroke-width:2px, stroke-dasharray: 2,10
classDef def font-style:italic, font-size: 80%
```

## Modifizierbarkeit2
```mermaid
graph TD

  DM([Charakterisiert den Aufwand zur Änderung des Systems.]):::def --- MO
  MO[Modifizierbarkeit]:::goal --> EA[Entwicklungsaufwand] --> KK[Komplexität <br> Artefakt & Komponenten]:::metric & DOC[Dokumentation] 
  MO --> RD[Redundanzfreiheit] --> FR[Funktionale <br> Redundanzfreiheit]:::metric & DR[Datenredundanzefreiheit]
  DR:::metric
  DOC:::irr


classDef metric stroke:gray ,stroke-width:2px ,stroke-dasharray: 5, 5
classDef goal fill:#f96
classDef irr color: gray, stroke:gray, stroke-width:2px, stroke-dasharray: 2,10
classDef def font-style:italic, font-size: 80%
```

# Fehlertoleranz 
```mermaid
graph TD
	FEHL([Die Fähigkeit des Artefakts den Ausfall Fehler in Komponenten <br> oder der Umgebung zu wiederstehen]):::def --- 
	FEH[Fehlertoleranz]:::goal --> Fehlerbehandlung:::metric & FE[Fehlererkennung]
	FE:::metric


classDef metric stroke:gray ,stroke-width:2px ,stroke-dasharray: 5, 5
classDef goal fill:#f96
classDef irr color: gray, stroke:gray, stroke-width:2px, stroke-dasharray: 2,10
classDef def font-style:italic, font-size: 80%

```

# Interoparabilität 
```mermaid 
graph TD
IN([Fähgikeit des Artefakts mit anderen Componenten oder Systemem zu interagieren]):::def ---INT[Interoperabilität]:::goal --- N
N[Hohe <br> Homogenität]
 N --> Q[Einheitliche <br>  Technologie] --> SA[Standadisierung  der <br> Anwendungskomponenten]:::metric
  N --> R[Einheitliche <br> Schnittstellen] --> SS[Sandardisierung der <br> Schnittstellen]:::metric 
  R --> K[Konnektoren]:::metric

classDef metric stroke:gray ,stroke-width:2px ,stroke-dasharray: 5, 5
classDef goal fill:#f96
classDef irr color: gray, stroke:gray, stroke-width:2px, stroke-dasharray: 2,10
classDef def font-style:italic, font-size: 80%
```

# Anpassbarkeit
```mermaid
graph TD
	ANPA([Fähigkeit des Systems sich ein Veränderungen der Spezifikation oder der Umwelt anzupassen]):::def --- AN[Anpassbarkeit]:::goal --> HS[Hohe Skalierbarkeit]:::metric & AD[Adaptonsfähigkeit <br> der Komponenten]
  AD:::metric
classDef metric stroke:gray ,stroke-width:2px ,stroke-dasharray: 5, 5
classDef goal fill:#f96
classDef irr color: gray, stroke:gray, stroke-width:2px, stroke-dasharray: 2,10
classDef def font-style:italic, font-size: 80%
```