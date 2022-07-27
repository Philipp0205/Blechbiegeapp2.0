[[4Archive/Verteidigung/Verteidigung Präsentation]]tbd

# Einleitung (5min)
- Guten Tag, Philipp Kurrle. 

## Probleme bisheriger Anwendungsarchitekturen 
- **Eine kleine Geschichte** 
	- Es war ein mal ein Geschäftsprozess. Dieser wurde in enem Anwendungssystem umgesetzt. In Applikationsinseln.
	- Jede Applikation ist entwickelt wie es sein sollte und wie wir es gelernt haben.
	- Applikationsinseln müssen integriert werden über Schnittstellen
		- Inter-Application-Spaghetti
			- ![[Inter-Application-Spaghe![[4Archive/Verteidigung/Inter-Application-Spaghetti.png]]ndschaften. Diese Erfüllen nicht die Anfoderungen
	- Sehr relevant weil es jedes Unternehmen betrifft, welches länger exisitert. 

- **Kernprobleme:**
	- **Agilität**
		- Veränderungen in der Umwelt sind schwer Umsetzbar, da viele unterschiedliche Komponenten und deren Abhängigkeiten beachtet werden müssen. 
	- **Interoperabilität**
		- Organisches Wachstum, es gibt keine übergreifdene IT-Strategie (Aier, Dogan)
		- Keine etablierten Standards. Anwendungssystem und Komponenten haben nicht die Fähigkeit mit anderen Systemen zu interagieren. 
	- **Qualität** 
		- Die Fähgikeit Geschäftsprozesse adäquat umzusetzen.


# Hauptteil (10min)
- **Lösung**
	- EDA ist eine Technologie welche diese genannten Probleme lösen könnte, aber bisher keine Anwenung findet. Kafka ist ein bekannter Vertreter in diese Bereich 
	- Viele Namhafte Unternehmen nutzen beretis Kafka. Twitter für das Senden und Empfangen von Tweets, Netflix und LinkedIn für der Verarbeitung von Userdaten, Zalando für BI, Spotify für logging, 
		- Adidas, airbnb, NYT, Cloudflare, Oracle, Paypal, Spotify, Mozilla
	- Keines dieser Unternehmen nutzt EDA für BPM.
	- Daraus stellt sich also die Frage: Was fehlt dieser Architektur um BPM zu betreiben? Bzw. Wie muss eine Architektur für BPM-Szenarien aussehen? 

## Forschungsfrage
*Wie kann eine ereignisorientierte Softwarearchitektur für BPM-Szenarien aussehen, die sowohl Interoperabilität, Agilität und Qualität bietet?*

## Methodik
- **DSR**
	- Die Gesamtmethode der BA verfolgte die DSR-Methode.
	- Zwei Phasen: Design und Evaluate
	- Das Artefakt des DSR-Prozess war die Architektur und der Prototyp welcher entwickelt wurde. 
		- ![[DSRMethodology.png]]

## Build
- **Entwicklung der Architektur**
	- Ein häufiger Anwendungsfall von Kafka ist das Umsetzen einer MS-Architektur
	- Hierbei werden granular, entkoppelte MicroServices mit einem Kafka Cluster verbunden. 
		- Diesem Architekturprinzip liegt die entworfene Architektur zugrunde. 
	- Ereignisgesteuerte Geschäftsprozesse
	- Hierbei müssen allerdings noch einige Änderungen vorgenommen werden, damit sich diese Architektur für BPM-Szenarien eignet. 
		1. Es muss eine Beschreibungssprache geben, mit welcher ereignisgesteurte Geschäftsprozesse beschrieben werden können. 
		2. Generation von Kafka-Komponenten anhand dieser Information
		3. Validierung der Prozesses 

- **Entwicklung des Prototyps**
	- Der Prototyp spiegelde diese Architektur wieder indem er diese drei Funktionalitäten in den dazu gehörigen Modulen implementiert.
		- ![[mermaid_component]]
- **Gesamtarchitektur**
	- ![[Zielhiarchien#Gesamtarchitektur]]
		- *(Darüber noc![[Zielhiarchien#Gesamtarchitektur]]tion Methodik**
	- Gängige Methoden für die Evaluierung von Softwarearchitekturen eigneteen sich nicht.
		- Diese testen an bereits produktiven Systemen und beziehen Stakeholder mit ein. Beides war im Kontext dieser Arbeit nicht vorhanden. 
	- Deshalb musste ich passende Qualitätsattribute finden. Diese befanden sich im gängingen ISO 9126 Standard. Diese Kriteren sind auf die Evaluierung von Software ausgelegt, allerdings nicht konkret defniert, weshalb sie auch für die Evaluation von Softwarearchitekturen genutzt werden könne.
		- Die 6 ISO-Kriterien und deren Subkriteren wurd bereits mehrfach in der Literathur auf Softwarearchitekturen angewendet
	- Für das konkrete Vorgehen bei der Evaluation habe ich die GQM-Methode gewählt
		- Bei dieser werd eine Hierarchie aus einem Ziel, mehreren Fragen und Metriken festgelegt.
	- Anhand dieser war es möglich die Architektur konkret zu evaluieren. 

## Evaluate
- **Tabelle**

|Ziel|Fragen|Metriken|
|----|------|--------|
|Tauglichkeit|- Erfüllt das Artefakt die funktionalen Anfoderungen? |- Evaluierung jeder einzelnen funktoitionalen Anfoderungen#|
|Fehlertoleranz|- Kann das <br> - Kann das Artefakt Fehler verarbeiten? | - Identifizierung von Komponenten zur Fehlererkennung und Fehlerverarbeitung |
|Interoperabilität|- Ist das Artefakt in der Lage, mit anderen Systemen zu interagieren? <br> - Nutzt das Artefakt Standards, um mit anderen Kompetenten zu kommunizieren?  | - Standardisierung der Anwendungskomponenten <br> - Schnittstellenstandardisierung <br> - Konnektoren      |
|Modifizibarkeit|Kann das Artefakt einfach verändert und modifiziert werden, um zum Beispiel neue Funktionalitäten zu implementieren?|- Geringe Komplexität <br> - Verhinderung von Redundanzen innerhalb des Artefakts |
|Austauschbarkeit|- Besitzt das Artefakt eine hohe Konsistenz? <br> - Sind die Komponenten des Artefakts entkoppelt und damit austauschbar? <br> - Existieren Redundanzen im System?|- Hohe fachliche Modularität der Komponenten <br> - Hohe technische Modularität der Komponenten <br> - Hohe Kohäsion und lose Kopplung der Komponenten |
|Anpassbarkeit|- Ist das Artefakt in der Lage kapazitive und funktionale Veränderungen schnell umzusetzen?|- Adaptionsfähigkeit der Komponenten <br> - Hohe kapazitive Agilität <br> - Hohe Skalierbarkeit |

## Ergebnisse 
- **DP1 Anpassparkeit**
	- **Hohe Skalierbarkeit**
		- Hohe Skalierbarkeit durch Publish/Subscribe Architektur
	- **Adaptionsfähigkeit der Komponenten**
		- Je nach defnierten Geschäfsprozess passen sich Kafka-Kompnenten an. Schema-Evoultion. 
		- Einzelne Komponenten können angepasst werden da sie weigehend entkoppelt sind.
- **DP2 Modifizierbarkeit**
	- **Komplexität**
		-  Anzahl der Komponenten wird durch Geschäftsprozesse festgelegt.
		-  Geringe Komplextität durch geringe Abhänigkeiten zwischen den Komponenten
		-  Unterschiedlickeit
	- **Redundanzfreiheit**
		- Keine funktionale Redundanzen durch Separation of concerns, funktionaliutäten sind nur an genau einer Stelle implementiert. 
			- Komponente kann wieder verwendet werden. 
		- Datenredundanzfreiheit kann ebenfalls vermieden werden.
- **DP3 Austauschbarkeit**
	- **Hohe Modularität**
		- Da jede Komponente nur genau eine Geschäftsfunktioanlität umsetzt ist eine hohe technische Modularität gewährleistet. 
		- Aus dem selbsten sind die Komponenten auch nach fachlichen Kriterien gegliedert. 
	- **Adäquate Kopplung**
		- Lose Kopplung
		- Hohe Kohäsion
		- Austauschbarkeit
- **DP4 Fehlertoleranz**
	- Durch die Valiador-Komponenten werden Fehler erkannt. 
	- Fehler können anschließend von weiteren Komponenten verarbeitet werden
		- -> Fehlererkennugn und Fehlerbehandlung gegeben
- **DP5 Interoparabilität**
	- Als zentraler Konnektor fungiert Apache Kafka. Im konkreten Broker, Producer, Consumer. 
	- Durch die weitreichende entkopplung ist eine Standardisierung der Komponenten zweitranging. Theoretisch können verschiedene Technologien genutzt werden.
	- Einzige Schnittstelle Apache Kafka und vllt. die Schemas -> Hohe Schnittstellenstandardisierung
- **DP6 Tauglichkeit**
	- Alle Anfoderungen wurden erfüllt. Im Prototyp wurden diese teilweise implementiert. 

- Im Ergebnis konnte festgestellt werden, dass alle 6 Kriteren von der Gesamtarchitektur erfüllt werden. Im Protoyp wurden die meisten Kriteren teilweise umgesetzt. 
- Es sind keine Grenzen der Technologien erkennbar, mit weiterem Entwicklungsaufwand könnte auch der Prototyp erweitert werden. 


## Fazit 

- Weitere Forschung
	- tbd

- Lessons learned
	- Strukturierte bei der Entwicklung vorgehen
	- DSR eigent sich gut als Ansatz
	- Zeitmanagemeht



## Jans Feedback
- Foliennummern
- Quellen
- Auf Motivaton eingehen
-  Kein "und dann"
-  Features -> Module
-  Für jedes erkäre DP Modul extra folie