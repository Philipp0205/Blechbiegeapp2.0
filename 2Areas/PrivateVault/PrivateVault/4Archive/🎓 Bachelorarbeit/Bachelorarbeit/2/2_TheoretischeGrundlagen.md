[[1]]
[[!Bachelorarbeit]] [[Bachelorseminar#Meta Bauplan]]
![[Bachelorseminar#Meta Bauplan]]
[[4 🗄️ Archive/🎓 Bachelorarbeit 1/Literatur/Bruns, Dunkel - Event-Driven Architecture]] 
[[4 🗄️ Archive/🎓 Bachelorarbeit 1/Literatur/Liteatur - Softwararchitektur]]
[[4 🗄️ Archive/🎓 Bachelorarbeit 1/Literatur/Literatur - Event-Driven-Architecture (EDA)]]
[[Jans BA#Research method]]
- DSR
- Vorgehensweise

# Einleitung
Diese Arbeit untersicht die Anwenung einer ereignisgesteuerter n Architektur für BPM-Szenarien auf der Basis von Apache Kakfa.

# Software Architekturen
Rund um den Bergriff Architektur hat sich in der Informatik und Wirtschaftsinformatik eine Vielzahl von Abelitungn wie IT-ARchitektur, Systemarchitektur, Softwarearchitektur, IS-Architektur, Unternehmenarchitektur etc. entwickelt. In diesem Feld existieren für die zentralen Begriffe bereits etablierte Definitionen. [@rennenkampffManagementITAgilitaetEntwicklung2015, p.54]

Eine der bedeutestens definitionen stammt aus dem IEEE Standard 1471:
*"Architecture is the fundamental organization of a system embodied in its components, their relationships to each other and to the environment and the principles guiding its design and evolution."* [Vogel 2009:66]

Diese umfassst die wichtigesten Aspekte einer Software-Architektur: [Vogel 2009:66]
- Die Software-Struktur beziehungsweise die Software-Strukturen eines Systems
- Die Software-Bausteine eines Systems
- Die Eigenschaften der Software-Bausteines eines Systems
- Die Beziehungen zwischen den Software-Bausteinen eines Systems 


# Ereignisse in Unternehmensnetzwerken
[[Wohlers BA ]]
- Bessers Definition Ereginis 
- Unernehmensprozesse und Ereignisse 
- Ereignisse in Unternehmen


Geschäftsprozesse global agierender Unternehmen, gleich welcher Branche, beruhen auf den Austausch von Ereignissen durch Nachrichten innterhalb des Unternehmen und unternehmensübergreifend mit Partnerinstitutionen über ein verteiltes Netzwerk. Ereignisgestuererte Unternehmen sind demnach in der Realität weit verbeitet. 

Ereignisgesteuerte Unternehmen sind sind dardurch gekennzeichnet, dass
- sie ereignisse erkennen, analyiseren und darauf reagieren
- sie durch den Austausch von Ereignissen miteinernder kommunizieren
- sie neue Ereignisse erzeugen und diese an ihre Partner senden und 
- ihre Aktivitäten durch Ereignisse ausgelöst werden. [@brunsEventDrivenArchitecture2010, p.20-21]

Mit Event-Driven-Architecture als Architekturstil und Complex Event Processing als Technologie zur Ereignisverarbiung stehen zwei ausdrucksstarte Ansätze zur Entwicklung ereignisgestuertet Geschäftsanwendungen zur Verfügung. Mit EDA und CEP lassen sich Geschäftsprozesse wirklichkeitsnah und problemadäqzat abbilden [@brunsEventDrivenArchitecture2010, p.24]

### Ereignisgesteuerte Geschäftsprozesse 
Ereignisse spielen eine zentrale Rolle in jedem Unternehmen und sind entscheiden bei der Steuerung von Geschäftsprozessen. Ein Geschäftsprozesse (business process) ist eine Folge von Schritten zur Erreichung eines angestrebten Arbeitsergebnisses und dient der Leistungserbgingen des Unternehmens [@brunsEventDrivenArchitecture2010, p.28].

Ein Geschäftsprozess lässt sich als Ereignisgestuert bezeichnen weinn eine Verarbeitungsfolge durch den ein Ereignis ausgelöst wird [@brunsEventDrivenArchitecture2010, p.28]. Ein Beipsiel für einen ereignisgesteuerten Prozess sind Fertigungprozeses welche durch den Auftritt von Ereignissen beeinfluss werden. Beipsielsweise muss auf Ereignisse wie die Bereitstellung eines Werkstücks, das Beenden eines vorherigen Schrittes oder das Auftreten eines Fehlers unmittelbar reagiert werden. 

> Ereignis (event) Ein Ereignis kann alles sein (eine Aktivität, ein Vorgang, eine Entscheidung etc.), was passiert oder von dem erwartet wird, dass es pas siert [68]. Im Allgemeinen bezieht sich ein Ereignis auf die Veränderung eines Zustands, also typischerweise auf die Änderung des Wertes einer Eigenschaft eines realen oder virtuellen Objekts.


### (Gegenüberstellung von konventionellen Architekturen zu EDA??)

# Event-Driven Architecture
Event-Driven Architecture (EDA) (oder ereignis gesteuerte Architekturen) repräsentieren einen Architekturstil von Unternehmensanwendungen, bei dem Ereignisse in das Zentrum der Softwarearchitektur rücken [@brunsEventDrivenArchitecture2010, p.4]. 

Ereignisgesteuerte Geschäftsprozesse unterscheiden sich von traditionellen, ablauforientierten Prozessen (vgl. Ereignisgestuerte Geschäftsprozesse). Die Eigenschaften, welche ereignissgestuerte Geschäftsprozesse unterscheiden wriken sich direkt auf Untnehmensanwendungen und deren zugrunde ligen Softwarearchitektur aus. 
Viele Aspekte von ereignigesteuerten Geschäftsprozessen können nur implementiert werden, wenn dies auch die darunter liegende Architektur unterstützt [@brunsEventDrivenArchitecture2010, p.43] [@schulteGrowingRoleEvents2003a]. 

Die Architektur besteht aus stark entkoppelten Komponenten, welche die Eereignisse asynchon empfangen und verarbeiten (Richards and Media:73) 

## Schichten
Bei einer Event-Driven Architecture lasssen sich drei logische Strukturierungsschichten unterscheiden, welche in der Abbildung dargestellt sind [@brunsEventDrivenArchitecture2010, p.43].

![EDASchichten](4Archive/%F0%9F%8E%93%20Bachelorarbeit/Bachelorarbeit/2/EDASchichten.png "Logische Schichten einer EDA")

**1. Schicht: Ereignisquellen** Jedes Ereignis muss ein Qzelle besitzten aus der es entsstammt. Diese Ereignisquellen sind in der Realität sehr heterogen. Beispiele für Quellen sind Sensoten, Feeds, Softwaremodule oder Web Services.

**2. Schicht: Ereignisverarbeitung** Ströme von Ereignisdaten aus meheren Ereignisqzellen diensen der Ereignisverarbeitung (event processing) als Eingabe. 

> Ereignisstrom Ein Ereignisstrom (event stream) ist eine linear geordnete Se-
quenz von kontinuierlich eintreffenden Ereignisobjekten. [@luckhamEventProcessingGlossary2011]

In ereignisgesteuerten Architekturen sind Ereignisstöme in der regel temporal geordnet, meist andhand der Auftritsszeitpunktes. Ein Strom kann unbegrenzt oder begrenzt sein. 

Die eigentliche Verarbeitung des Stroms und dessen Ereignisse erfolgt durch *Complex Event Processing* (CEP), auf welches später noch eingegangen wird.

**3. Schicht: Ereignisbehandlung** Die eigentliche Ereignisbehandlung (event handling), also die Reaktion auf eintreffende Ereignisse findet im Backend der Unternehmensanwendungen statt. Eine Softawrekomponente aus der Ereingisbehandlungschiht kann natü$lichselber wiederu Ereignisse genieren und somit eine Quelle sein. [@brunsEventDrivenArchitecture2010, p.64]  

## Typen ereignisgesteuerte Architekturen
Bei ereignisgesteuerten Architekturen wird hauptsächlichen zwischen zwei Topologien entschieden, der Mediator und der Broker. Die Medatior Topologie wird in der Regel genutzt wenn mehre Schritter innerhalb eines events orchestiert werden. Dies wird mit einem zentralen Mediator erreicht. 
Die Broker Topologie wird genutztm wenn die events zusammenhängend ohne Nutzung eines zentralen Mediators verarbeitet werden sollen. (Richards and Media:73)

![MediatorExample](4Archive/%F0%9F%8E%93%20Bachelorarbeit/Bachelorarbeit/2/MediatorExample.png "Mediator Topologie"){width=50%}
![BrokerExample](4Archive/%F0%9F%8E%93%20Bachelorarbeit/Bachelorarbeit/2/BrokerTopology.png "Broker Topologie"){width=50%}

Eine Broker Toplogie ist sinnvoll, wenn es sich um vergleichweise ablaufende Ereignisverarbeitung handelt und keine zentrale Orchestation der Ereignisse benötigt wird. 

Die Arbeit schänkt sich auf die Vewendung der Broker Technologie ein. 

Innerhalbt der Broker Technologie gibt es wei zwei Hauptytypen von Architekturkomponenten: Eine Broker Komponente sowie eine ereignisverarbeitende Komponente. Die Broker-Kompontent kann zentralisiert oder föderalisiert umgesetzt werden und enthält alle events channels welche in der Ereignisverarbeitung genutzt werden. (Richads and Media:76)

Die im Broker enthalten Ereigniskanäle können sogenannte message queues, messages topics oder eine Verbindung aus beiden sein. (Richards and Media :77)

### Vorteile 
- [[Wohlers BA]]
	- Bewertung 


**Agilität:** Agilität ist die Fähigkeit schnell auf ein sich ständig veränderndedes Umfeld anzupassen. Da bei einer ereignisgesteuerten Architektur die ereignisverarbeitenenden Komponenten weitgehend entkoppelt sind sowie jede Komponente nur genau einem Zeck dient ("single-purpose") kann sich das System schnell an Veränderungen an passen. Veräderungen der Umwelt betreffen meist nur eine beschänkte Anzahl an Komponenten welche schnell identifiziert und verändert werden können.

**Performance:** EDA ist in der lage parallel und asynchron viele Operationen auszuführen und somit sher performant.

**Skalierbarkeit:** Skalierbarkeit wird bei EDA in der Regel naürlich erreich aufgrund der entkoppelten Komponenten. Jede ereginisverarbeitende Komponente kann einzeln skaliert werden was eine sehr feinkörnige Skalier erlaubt. Des weiteren sind EDA leicht vertikal Skalierbar, da einfach neue Komponenten hinzugefügt oder entfernt werden können. 

Die Implementierung von EDA besitzt weitreichendes Potenzial. Aus der Ereignisorientiertung ergeben sich nach Bruns und Dunkel folgence Changen und Vorteile: [@brunsEventDrivenArchitecture2010, p.32]
- Echtzeitfähigkeit für Aktualität der operativen Entscheidungen
- Erkennen und Reagieren auf einfache und komplexe Ereignismusster fü$ eine schnelle unternehmerische Reaktionsfähigkeit
- Betrachtung von Ereignissen auf unterschiedlichen Abstraktionsebenen für mehr Transparenz der unternehmerischen Entscheidungen
- Verarbeitung von kontinuierlich und und in großen Mengen einstämenden Ereginissen für eine höhere Effizienz der Prozessabläufte
- Wirklichkeitsnahe Modellieung fachlicher Prozesse 
- Flexibilität und Agilität der Anwendungssysteme.  

Die Aussschöpfung des Potenzials von EDA bietet die Aussicht auf: [@brunsEventDrivenArchitecture2010, p.32]
- effizientere und transparentere Anwendungssysteme.
- neue Anwendungssystem, die ohne Idea nicht realisierbar wären. 

### Vergleich von Broker und Mediator Topologie (TODO)
- [[Wohlers BA]]
	- 23 Bewertung 
|                | Broker | Mediator |
|----------------|:------:|:--------:|
| Agilität       |        |          |
| Performance    |        |          |
| Testbarkeit    |        |          |
| Skalierbarkeit |        |          |
| Entwicklung    |        |          |

## Schichten 
- [[Wohlers BA]]
	- Event-Driven Architecture


# Complex Event Processing 
- [[Wohlers BA]]
	- 24  CEP


# Publish-Subscribe-Architektur
Piblish/Subscribe ist ein Mister (Bischmann et al. 1996) bzw. Stil (Shaw und Garlan 1996) und stelle einer Alternative zu klassichen Client/Server doer Peer-to-Peer Architekturen dar (Shar und Garlan. 1996), welcher auch Explicit Invocation spezialisiert, aber auf die direkte Kommunikation von Klienten setzt, statt mit einem zentralen Service zu kommunizieren (Vogel 2009:243). 

## Entkopplung
Der Austausch von Nachrichten in ereignisgesteuerten Architekturen erfolgt, in der Regel in Form von Nachrichten (messages).
Dies Architektur charakterisiert sich durch eine Komponenten welche Ereignisse erzeugen (Publisher), welche Ereignisse an eine Middleware weiterleiten, ohne zu wissen wie und wie die Weiterverarbeitung erfolgt. Stattdesen wird die Nachtich lassifiziert und der Empfänger abbiniert eine bestimmte Klasse an Nachrichten. 

Das heißt Aufruge werden nicht direkt unter den Kommunikatonsteilnehmern versendet, sondern Ereignisse werden dirch einen Vermittler, den sogenantnen Broker, weitergeleitet (Vogel,2009:244).

Die Architektur widmet sich dem Problem, dass eine Reihe von Klienten über Laufzeitereignisse informiert wrden müssen. Manchmal sollen eine Reohe von Klienten aktiv üver ein Ereignis informiaert werden, in anderen Fällen ist nur ein spezifischer Klient am Ereignis interessiert. Deshalb müssen der Produzent und Konsument eines Ereignisses voneinder entkoppelt werden, z. B. um getrennte Veränderbarkeit zu gewährle

Befor die Einzelheiten von Kafka beschrieben werden, ist das konzept von pulbish/subscribe messaging, welches Apache Kafka zugrunde liegt relevant. Dies ist ein Musster welches sichcarahterisiert durch einen Sender (publisher) welcher ein Nachricht (message) an keinen spezifischen Empfänger (receiver) schickt. Stattdesen wird die Nachticht klassifizziert und der Empfänger abboniert (subscribed) bestimme Klasse an Nachrichten. Dies wird üblicherweise mit einem zentralen Broker erreicht welche die Nachtichten hält (Narkhede et al.:1). 


## Asynchrone Kommunikation 
Die Kommunikations zwischen Publisher und Subscirver erolgt asyncrhon. Die Ereignisqzelle setzt ihre Verareitung unmittelbar fort, sobald sie eine Nachrichte gesendet hat. Diese Asynchronität basierend auf einer weitgehend Entkopplung bilden die Basis für die honte Interoperabilität von EDA [@brunsEventDrivenArchitecture2010, p.31].

## Ereignisverarbeitung
Um Ereignisorientierung als Architekturstil zu implementierten wird eine Technoloige zur komplexten Ereignisverarbeitung benötigt. *Complex Event Processing* (CEP) ist solch eine Technologie zur dynamischen Verarbeitung von Ereignissen. Mit ihr ist es mögliche Ereignisse aus unterscheidlichen Quellen nach Ereinismustern zu verarbeiten. Nach dem Erkennen eines Muster kann eine entsprechende Aktion z.B. Generierung eines neuen Ereignisses, Warnungen oder Aufruf eines Dienstes inititieren. [@brunsEventDrivenArchitecture2010, p44]. 

In DEP wird das Wissen über die Ereignisverarbeitung deklarativ in Form von regeln festgelegt. In Regelinterpreter wendet diese Regeln auf Ereignisstöme an. Aufgrund der expliziten und deklarativen Repräsentaton des fachlichen Wissens über Ereignisverarbeitung lassen sich Geschäftsprozesse ohne Unterbrechend des laufenden Betriebs modifizieren. 

# Apache Kafka
### Kurze History 
Apache Kafa Open Source Software der Apache Software Foundation, welches insbesondere der Verarbeitung von Datenstöment dient. Kafka ist ein verteiltes *messaging system* welches eine schnelle, skalierbare Architektur mittels eines *publish-subscibe* Models bietet.

Ursprünglich war Apache Kafka eines in-house Entwicklung von LinkedIn und sollte eine asynchrone publish-subscribe Architektur für das Netzwerk bieten (Narkahede:14). Ende 2010 wurde der Quellcode von Kafka veröffentlich und Kafka wurde Teil der Apache Foundation. Im Jahr 2014 gründeten die Entwickler das Unternehmen Confluent aus LinkedIn heraus, welches die Entwicklung von Apache Kafka fokussiert (Narkahede:15) (Rao).

### Kafka Terminologie
Die grundlegende Architektur ist um enige wenige Schlüsselbergriffe herum organisiert, welche im folgenden Erläutert werden. 

Die atomare Dateneinheit in Kafka sind *Records*. Diesse halten einen key, timestampt sowie einen wert (Doku).  Records werden in *Topics* organisiert. Sogenannte *Consumer* pullt Records aus einem Topic und *Producer* pushen message in ein Topic. Producer und Consumer sind synonym zu Publisher und Subscriber. (siehe sub/pub pattern).
Kafka wird üblicherweise auf einem oder mehreren Servern als Clusterbetrieben.

#### Topics, Records, Logs
Die Grundabstaktion von Kafka ist das *Topic* welches einen Menge an *Records* hält (auch *Stream genannt*). Ein *Topic* ist die Kategorie unter welcher ein Record veröffentlicht (gepublished) wird. Ein Topic ist in mehrere Partitionen aufgeteilt welche es erlauben das das Topic zu parallelisierung in dem Daten aus einem topics auf mehre Broker verteilt werden. 
 
![AnatomieTopic](4Archive/%F0%9F%8E%93%20Bachelorarbeit/Bachelorarbeit/2/AnatomyTopic.png "Anatomie eines Topics"){width=50%}

Jede Partition besteht aus einer unveränderlichen Sequenz aus Records welche kontionulich erweitert wird. Dies wird in Kafka auch *commit log* genannt. Jedem Record wird eine fortlaufende id, das *offset* zugeordnet welches jeden Record innerhalb einer Partition eindeutig identifiziert. (Kafka Doku)

#### Partitionen und Broker


#### Producer und Consumer
Dies sind die beiden essenziellen Komponenten welche eine publish-subscribe Architektur ausmachen:
*Producer* sind Komponenten welche Nachrichten auf ein Kafka topic veröffentlichen. Der Producer ist darüber hinau verantwortlich für die Zuordnung jeses Records zu einer Partition innerhalbt eines Topics. 
*Consumer* sind die Kompontent welche Nachrichten von den Topics beziehen. 

*Consumer* sind meist innerhalb einer *consumer group* geordnet und jeder record welcher zuvor auf ein Topic veröffentlich wurde wird zu einer Consumer Instanz vermittelt. 

Der *Broker* verwaltet die Speicherung der Records in Topics. Sollten mehrere Broker in einem System vorhanden sein spricht man von einem *Cluster*.

![KafkaCluster](4Archive/%F0%9F%8E%93%20Bachelorarbeit/Bachelorarbeit/2/KafkaCluster.png "Kafka Cluster"){width=50%}

# Anwendungsgebiete
- [[Wohlers BA]] 
	- Anwendungsgebiete

# Agilität
Es existieren keine dominanten allgemeint akzeptieren Definitonen von Flexibilität und Agilität un der Wirtschaftsinformatik und IS-Forschung. Dennoch lassen sich häufig verwendete Element und Definitionen finden, die eine grundsätzliche Cahrakterisierung des Begriffs ermöglichen [@rennenkampffManagementITAgilitaetEntwicklung2015, p.39]. 

Agilität wird als Eigenschaft einer Organisation gesehen, Veränderungen schnell umszusetzen [@terryanthonybyrdMeasuringFlexibilityInformation2000, p.170-172] [@sambamurthyShapingAgilityDigital2003, p.245]. 
Hierbei kann die Veränderung in kapazitative oder funktionale Veränderungen unterschieden werden. Kapazitative Veränderungen führen dazu, dass die Menge der erbrachten Leistung angepasst werden muss. Funktionale Änderungen hingegen führen zu inhaltlichen Anpassungen [@nissenMessungUndManagement2009, p.42-43]. 

Der Begriff Agilität wurde in den vergangenen Jahren in der deutschsprachigen Wirtschaftsinformatik hauptsächlich im Bereich der "agilen Softwareentwicklung" benutzt. [@rennenkampffManagementITAgilitaetEntwicklung2015, p.157].

Agilität ist ein weit gefasster Begriff. Deshalb ist eine Beschreibung der einzelnen Elemente von Agilität einer Softwarearchitektur nötig sowie die festlegung konkretet Ziele welche diese erreichen sollte. Zu diesem Zweck wird die Zielhierarchie von Rennenkampf et al. (2015), welche die verschiedenen Elemente der Agilität einer Anwendungslandschaft in eine Zeilhiararchie einordnet. 

Rennkammpf et al. (2015) Sieht die Anwendungslandschaft als Teil der IT-Architektur, allerdings lassen sich die Ziele für Agilität auch auf Software Architekturen übertragen. 

![[4 🗄️ Archive/🎓 Bachelorarbeit 1/Bachelorarbeit/4/ZielhiarchieKennzahlen.png]]

Die erste Unterteilung des Oberziels "Hohe Agilität der Anwendungslandschaft" erfolgt in "Hohe funktionale Agilität der Anwendungslandschaft" und "Hohe kapaziative Agilität der Anwendungslandschaft". 
Das Ziel der hohen kapazitiven Agilität sit die Fähigkeit der Anwendung sich schnell an veränderte kapazitative Anfoderungen anzupassen. Funktionale Agilität erfodert, dass die Anwendungs in der Lage ist, funktionale Änderungen an ihren Elementen schnell und effizient zu absorbieren [@dernITArchitekturGovernanceAufBasis2009, p.155].

## Hohe funktionale Agilität der Anwendungslandschaft
Die Architektur muss in der Lage sein funktionale Änderungen an ihren Elementen schnell und effizient zu absorbieren. Die Änderungen sollten einfach und prompt umgesetzt werden können. Die steigende Zahl an Anforderungen an eine Anwendung sowie die alternde und wachsende Anwendungslandschaft stellen Unternehmen vor Herausforderungen. Um eine pro funktionale Agilität zu erreichen sind zwei Unterziele von Bedeutung: eine geringe Komplexität und eine hohe Konsistenz der Anwendungslandschaft [@rennenkampffManagementITAgilitaetEntwicklung2015, p.156].

**Geringe Komplexität** Hohe Komplexität ist einer der zentralen Verhinderer von Agilität  [@dernITArchitekturGovernanceAufBasis2009]. Monolithische und historisch gewachsene und dadurch komplexe Anwendungssysteme sind schwer wartbar und änderbar und können daher veränderte Geschäftsprozesse nicht mehr abbilden. Hinzu kommen viele weitere Faktoren wie der Einsatz von alten Technologien für die nur noch schwer qualifizierte Mitarbeiter zu finden sind.

Die Komplexität kann aus theoretischer Sicht auf Basis der allgemeinen Systemtheorie beschrieben werden. Darunter wird unter einem System “eine Menge von Komponenten verstanden, die miteinander in Beziehung stehen.” [@ferstlGrundlagenWirtschaftsinformatik2013].Es scheint intuitiv, dass ein System mit wenigen Komponenten eine geringer Komplexität als ein System mit vielen Komponenten aufweist. Die Komplexität eines Systems kann durch drei Eigenschaften bestimmt werden: die Anzahl der Elemente eines Systems, deren Abhängigkeiten untereinander sowie die Unterschiedlichkeit der Elemente  [@dernITArchitekturGovernanceAufBasis2009, p.670-671] [@schnebergerComplexityCrossImplications2003, p.217]. Daraus lassen sich nach Rennkampf (2015) die zwei Subziele “Geringe Abhängigkeiten” und “Hohe Homogenität” ableiten, wobei die Anzahl der Systemelemente in die Gewichtung des Subziels der “Geringen Abhängigkeiten” einfließt.
[@rennenkampffManagementITAgilitaetEntwicklung2015, p.157].

**Subziel: Geringe Abhängigkeiten**
Abhängigkeiten entstehen durch die Verbindung von Teilen des Systems durch Schnittstellen. Sie führen dazu, dass die Änderung an einem Teil des Systems andere Teile beeinflussen. Eine maximale Abhängigkeit liegt vor, wenn Anwendungssysteme paarweise miteinander verbunden sind. Eine minimale Abhängigkeit liegt dann vor, wenn keine Verbindungen existieren [@dernITArchitekturGovernanceAufBasis2009a, p.670-671]. Je höher die Abhängigkeiten in einem System sind, desto schwieriger wird die Umsetzung von Änderungen, da für jede Änderung die Auswirkung auf weitere Komponenten beachtet werden müssen. Sind Abhängigkeiten minimal, können Änderungen isoliert und dadurch schnell, kosteneffizient und risikoarme vorgenommen werden [[@rennenkampffManagementITAgilitaetEntwicklung2015, p.158]. 

Um das Ziel der “Geringen Abhängigkeiten“ zu erreichen, muss das System eine geringe Vernetzung aufweisen und die vernetzten Systeme müssen adäquat gekoppelt sein. somit lassen sich die beiden Unterziele “Geringe Vernetzung” und “Adäquate Kopplung” ableiten.

Das Ziel der “Adäquaten Kopplung” lässt sich aus den beiden Gestaltungsprinzipien von serviceorienteren Architekturen “Hohe Kohäsion” und “Lose Kopplung” ableiten. Für eine hohe Kohäsion ist erforderlich, dass die Architektur intern möglich stark vernetzt ist. Die lose Kopplung erfordert, dass die Vernetzung zwischen den Elementen möglichst gering ist  [@vogelSoftwareArchitekturGrundlagenKonzepte2009, p.133-134]. 

Eine Anwendung lässt sich fachlich Gliedern in Domänen oder Module. Eine adäquate Kopplung erfordert, dass die Module einer Ebene untereinander möglichst weniger vernetzt sind (lose Kopplung), während sie intern stark vernetzt sind (hohe Kohäsion).

Das Prinzip der adäquaten Kopplung beschreiben Aier und Dogan (2005) als eine “Verschiebung von Abhängigkeiten in Modulen”. Damit werden externe Abhängigkeiten zwischen den Modulen eines Systems minimiert und dafür Abhängigkeiten in die Module verschöben. Aier und Dogan (2005) sehen den Vorteil, dass “sofern Schnittstellen unverändert bleiben […] einzelne Module verändert oder ausgetauscht werden können, ohne Änderungen an den übrigen vornehmen zu müssen.” [@aierIndikatorenZurBewertung2005, p. 616-618].


**Hohe Konsistenz** Das zweite Ziel, das neben "Geringe Komplexität" zur funktionalen Agilität der Anwenudngslandschaft beiträgt ist die "Hohe Konsistenz". Dies Ziel wird durch die hohe Modularität und Redudanzfreiheit einer Anwendungslandschaft erreicht. 
Durch eine modular Struktur und die Vermeidung von Redundanzen innerhalb der Anwendungslandschaft können bestehende Daten und Funktionen wiedervewedndet werden. Dies führt zu einer hohen funktionalen Agilität. [@rennenkampffManagementITAgilitaetEntwicklung2015, p.165].
Ein System mit hoher Konsistenz zeichnet sich auch durch einen geringen Kopplungsgrad der einzelnen Komponenten aus.

**Hohe Modularität** 
Modularität bedeutet, dass die Aufgaben der Anwendung in granulare, gekapselte Module aufgeteilt werden [@aierIndikatorenZurBewertung2005, p.616-617] [@gronauEntwicklungWandlungsfahigerAuftragsabwicklungssysteme2007, p.3] [@vogelSoftwareArchitekturGrundlagenKonzepte2009, p.145-148].  Modularität basiert auf dem Prinzip “Seperation of Concerns”, welches besagt, dass große umfangreiche Aufgaben in kleinere und dadurch unkomplexere Aufgaben aufgeteilt werden sollen [@vogelSoftwareArchitekturGrundlagenKonzepte2009, p.137]. 

Hierbei kann zwischen hoher fachlicher und hoher technischer Modularität unterschieden werden. Eine hohe fachliche Modularität erfordert, dass die Anwendung eindeutig anhand fachlicher Kriterien strukturiert ist.
Bei einer hohen technischen Modularität dass die Anwendung nach technischen Kriterien strukturiert ist. Hierbei sollte jedes Modul einen klaren eindeutigen technische Zweck haben. Engels et al. (2008) unterscheiden hierbei in vier Kategorien von Softwarekomponenten: [@engelsQuasarEnterpriseAnwendungslandschaften2008, p.161 ff.]

- Interaktionskomponenten: Komponenten dieser Kategorie dienen der Interaktion mit Anwendern oder mit anderen An wendungslandschaften. 
- Prozesskomponenten: Komponenten dieser Kategorie dienen der Abbildung und Steuerung fachlicher Geschäftsprozesse.
- Funktionskomponenten: Komponenten dieser Kategorie haben einen „algorithmischen Charakter“ und implementieren die Funktionalität. 
- Bestand: Komponenten dieser Kategorie verwalten die Datenbestände und den Zugriff auf diese. 

**Redudanzfreiheit**
Das Ziel der "Redundanzfreiheit" ist erfüllt, wenn keine Daten oder Funktionen mehr als einmal innerhabl der Anwendungs exisiteren. Werden Daten oder Funktionen an mehreren Stellen benötigt sollen diese trotzdem nur an einer Stelle vorhanen sein und werden dort wiederverwendet. 
Durch Redudanzfreiheit können Änderungen schnell und einheitlich durchgeführt werden und sind anschließend an allen Stellenk, wo diese benötigte werden verfügbar [@rennenkampffManagementITAgilitaetEntwicklung2015, p.171-172]. Redundanzfreiheit trägt somit entscheident zur Agilität der Anwendungslandschaf bei [@durstWertorientiertesManagementITArchitekturen2007, p. 109-110] [@rossEnterpriseArchitectureStrategy2006, p.37-39].

Hierbei wird zwischen fachlicher Redundanzfreiheit und Datenredundanzfreiheit unterschieden. Bei der fachlichen Redudanzfreiheit müssen fachlcihe Funktionen nur an genau einer Stelle der Anwenudngs implementiert sein. Wenn diese an einer anderen Stelle benöitgte werden dürfen diese nicht neu implementiert werden.  
Analog dazu verlangt die Datenredunanzfreiheit, dass Datenbstände jeweils von einem einzigen Teil der Anwendung verwaltet werden. Aller anderen Teile die diesen Datenbstand benötigen müssen auf den verwaltenden Teil zurück greifen [@rennenkampffManagementITAgilitaetEntwicklung2015, p.173].


# Interoperabilität
Nach Rennkampff et al. (2015) sind zwei der am häufigsten genannten Gestaltungsziele für agile Anwendungslandschaften "Standardisierung" und "Interoperabilität" [@aierIndikatorenZurBewertung2005, p. 620] [@andresenAbleitungITStrategienDurch2005, p.73] [@durstWertorientiertesManagementITArchitekturen2007, p.108-109] [@gronauEntwicklungWandlungsfahigerAuftragsabwicklungssysteme2007, p.4] [@rossEnterpriseArchitectureStrategy2006, p. 74-76].

Interoperabilität ist die Fähigkeit eines Systems mit anderen Systemem zu interagieren [@losavioISOQualityStandards2004]. Interoperabilität erfordert ein hohes Maß an Kompatibilität der Systeme und ihrer Schnittstelle inerhalb der Anwendungslandschaft. Dies wird vor allem durch die Festlegung von Standards erreicht [@gronauEntwicklungWandlungsfahigerAuftragsabwicklungssysteme2007, p.4] 

Standards können als Institution aufgefasst werden, mit dem Ziel mittels informalen Regeln etweder indiviudelle
"Allgmein versteht man unter Standardisierung eine Vereinheitlichung von Gütern, von Produktionsmethoden oder anderem." [@wieseNetzeffekteUndKompatibilitat1990, p.3-4].  Dabei kann sich die Standardisierung auf viele Bereiche erstrecken. 
In der vorliegenden Arbeit bezieht sich der der Begriff standardisierung ausschließlich auf betriebliche Anwendungssysteme. Standardisierung wird als Grundlage gesehen um diese miteinenader zu vernetzen. 

Müller (2005) unterscheidet hierbein drei Standarisierungskonzepte.

**1. Standardisierung von Anwendungssystemkomponenten** Diese kann durch die Drei-Ebenen-Architektur (Daten, Applikation, Präsentation) beschrieben werden auf der die Standardidiserung der software ansetzten kann. Dabei werden die Datenmodelle, Funktionalitäten und die Präsentationslogik standardisiert indem die gleichen Strukturmerkmale, wie beispielsweise die Verwendung der gleichen Datantypen verwendet werden. 

Die Standardisierung der Systemelement gestaltet sich unterschiedlich komplex, je nach Kontext. Im Fall dieser Ereignisgesteuerten Architektur sollten daher standardisiert werden in dem über alle Module und Komponent hinweg die gleichen Strukturmerkmale verwendet werden. Beispiel hierfür sind die Verwendung der selben Datentypen und Verhaltensmerkmale wie einheitlich Regeln zu sicherstellung der Konistenz der Objekte. 
Das Grundlegende Strukturmerkmal in der vorgeschlagnen Architektur ist das Ereignisse, welches wierum aus Eigenschaften besteht. 

**2. Schnittstellenstandardisierung** Das Konzept setzt bei der Kommunikations Answendungssystemen an. Es werden einheitliche regeln für den Informationsaustausch zwischen zwei Anwendungssystemen benötigt. Diese Regeln können sich wiederum auf die drei Systemebenden beziehen und stellen eine relationale Beziehung zwischen den betroffnen Elementen her. 
[@muellerWirtschaftlichkeitIntegration2005, p.60]

Es Bedarf einer gemeinsamen Sprache um den Informationsaustauschen von meheren Anwendungssystemem zu ermöglichen. Insgesamt gilt es zu beachten dass die nicht nur in der Maschine-Maschine Kommunikations möglich ist sondern auch Benutzerschnittstellen einbezogen werden können. 

Im Kontext der zu konzipierenden ereignisgesteuerten Architektur sollte daher die Beschreibungssprache (Modul 1) einge gute Schnittstelle zur technischen Beschreibung von Apache Kafka sein. Des weiteren sollen Formate genutzt werden welches der Architektur ohne weitere erlauben würden mit verschiedenen Microservices oder externen Anwendungssystemen zu kommunizieren. 

**3. Einsatz integrierter Standardanwendungssoftware** Eine vollständige Standardisierung alle Systemelement wird durch den Einsatz einer integrierten Standardsoftwarelösung erreicht. Diese exisitert aber für diesen Anwendungsfall nicht, daher ist dieser Punkt unerheblich. 

**Subziel: Hohe Homogenität:**
Das Ziel der "Hohen Homogenität" beinhaltet die Anfoderungen der Interoparbilität, Konnektivität, Standardisierung und Portierbarkeit. Eine hohe Homogenität erfodert einheitliche Systeme und Schnittstellen und setzt sich folgich aus den Zielen "Einheitliche Technologie" und "Einheitliche Schnittstellen" zusammen [@rennenkampffManagementITAgilitaetEntwicklung2015, p.163]. 


# Qualität
In der Praxis hat es siche etabliert, funtkionale Anwendungsfällte mittels Anwendungsfällten zu beschreiben. Die Dokumentatoin von Qzualitäten, die man z.B. als Qualitätsattrivbutszenarien umsetzen kann ist jedoch nicht soetabliert. In folgender Tabelle wird das Dokumentatonsschema von Qualtiätsattributsszenarien eingeführ une erklärt. Manche Qualität gelten jedoch nur für einen Teil der funktionalen Anfoderungen. Qualtiätsattributsszenarien können sowohol systemweit als anwendungsfallspezfifsich genutzt werden [@vogelSoftwareArchitekturGrundlagenKonzepte2009, p.196].

![Qualitätsattributsszenarien](Qualit%C3%A4tsattributsszenarien.png "Qualitätsattributsszenarien"){width= 60%}

Qzalitätattributsszenarien können nach Szenariotyp eingeteilt werden Bass et. al. (2013) untwescheiden in follgende allgemeine Szenariotypen: 
- Verfügbarkeit
- Änderbarkeit
- Perfomanz
- Sicherheit
- Testbarkeit
- Benutzbarkeit


