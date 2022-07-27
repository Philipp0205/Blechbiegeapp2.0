# 1 Motivation

**Notes**

- Es ist momentan noch schwierig zwischen prozesse software-architektur
- EPL fehlt, beschreibung von Ereignissen in DSL Brücke bpm software
- Einleitung (Digitale Transformation und Etablierung von EDA)
- Schwächen konventioneller systeme
- Lösung der Probleme durch EDA
- Problem: Keine Anweundung von EDA in BPM
- Gründe dafür

### 1 Digitalisierung führt zu schnelleren Prozessen -> Etablierung von EDA

- Der Einstieg ist mir persönlich ein bisschen zu weit weg von Problem. Wie wäre es stattdessen eher mit: Digitalisierung führt dazu, dass Prozesse immer effizienter werden --> daher immer mehr Interaktion in Echtzeit (um Latenzen, Liegezeiten, Waste... zu vermeiden) --> als Folge davon hat sich EDA mehr und mehr etabliert
    - Der echtzeit apsekt fehlt hier noch
    - Eventuell habe ich hier falsch zitiert, es geht eher um das "steuern" de Prozesse als um die Flexibilität.
    - "Durch digitale Vernetzung neu geschaffener Informationsflüsse und daraus resultierender höherer Informationsverfügbarkeit können benötigte Informationen zum richtigen Zeitpunkt am richtigen Ort bereitgestellt werden. Diese Vernetzung ermöglicht es, Produktionsund Logistikprozesse effizienter und flexibler zu steuern 2, 3]." (Universität Augsburg, Kernkompetenzzentrum Finanz- & Informationsmanagement, Projektgruppe Wirtschaftsinformatik des Fraunhofer FIT, Augsburg, Deutschland et al 2020:710)
    - "Neben den gängigen Verschwendungsarten, wie u.a. unnötige Materialbewegungen aufgrund ungeeigneter Prozesse, wurden auch Verschwendungen ermittelt, die durch ungeeignete Informationsflüsse und mangelhafte Informationsverfügbarkeit entstehen. Beispielsweise seien die mangelnde Transparenz der Lagerbestände in dezentralen Lagern oder vorhandene, aber ungenutzte Informationen genannt." (Universität Augsburg, Kernkompetenzzentrum Finanz- & Informationsmanagement, Projektgruppe Wirtschaftsinformatik des Fraunhofer FIT, Augsburg, Deutschland et al 2020:711)
    - "Analytics and big data, which enable companies to make well-founded decisions (sometimes in real time) and to develop data-based business models." (Châlons and Dufft 2017:14)
    - In the last few years, Service-Oriented Architecture (SOA) has received increasing attention in line with the move towards tackling challenges associated with the improvement and maintenance of diverse environments (Hamzah, Baharom, & Mohd, 2019; Shaheen, Anees, Hussain, & Obaid, 2019)."
    - To modernise the organisations software system, migrating from a legacy system to an SOA-based system has become a mainstream trend (Abdellatif et al., 2018).
    - Furthermore, the benefits of adopting SOA in organisations include reduced costs, a greater return on investment (ROI), the reuse and integration of services and traditional systems, reduced time to market, and improved alignment between business and IT (Koumaditis et al., 2012; Marks, 2008; Mueller, Viering, Legner, & Riempp, 2010).
    - Unternehmen sind seit jeher einer permanent Evolution ausgesetzt. Markt -bedingungen und -teilnehmer ändern sich stetig und es gilt sich den veränderten Rahmenbedingungen anzupassen. Deshalb streben Unternehmen nach Agilität und Effizient ihrer Geschäftsprozesse um angemessen auf die sich verändernden Marktbedienungen reagieren zu können (vgl. Bruns & Dunkel, 2010, S. 3–4).

### 2 Problem: Flexibilität und Agilität könnten durch EDA gelöst werden, werden sie aber auch nicht

- Hier wäre dann mein Übergang: "Das ist erstaunlich, denn Unternehmen leiden heute häufig an einem Problem, das durch EDA gelöst werden könnte: Einem Mangel an Flexibilität und Agilität."
- Und dann würde ich es fortführen mit einer kurzen Erklärung, woher dieser Mangel entstanden ist (Einführung von Standardsoftware seit Ende der 90er, jeweils mit vorgegebenem "Korsett" für die Gestaltung der Geschäftsprozesse).
    - Flexibilität: ERP-Applikationen müssen beispielsweise mit der wachsenden Komplexität innerhalb der Firmenstrukturen mithalten können. Gerade im Zuge von Akquisitionen beziehungsweise Veränderungen im Geschäftsmodell kann es passieren, dass ein älteres ERP-System mit einem Mal nicht mehr zur veränderten Situation des Unternehmens passt. "Der frühere Ansatz in Sachen ERP sah so aus, dass man feste Prozesse in Unternehmen in Software gepresst hat", erläutert Keith Mattioli, Analyst von KPMG.
        - ‘Anwender brauchen mehr Flexibilität und Agilität: ERP in Zeiten der Digitalisierung’. Accessed 24 April 2020. [https://www.computerwoche.de/a/erp-in-zeiten-der-digitalisierung,3314781](https://www.computerwoche.de/a/erp-in-zeiten-der-digitalisierung,3314781).
    - "Seit Anfang der 90er Jahre wurden solche ERP-Systeme sukzessive fl‰chendeckend in nahezu allen Unternehmen weltweit eingef ̧hrt und dieser Boom h‰lt ungebrochen an. Am bekanntesten sind die Systeme von SAP, BAAN, J.D. Edwards oder PeopleSoft." (Bungard 2005:14)
    - "In der Vergangenheit scheiterten solche partizipativen Ans‰tze an der rigiden,unflexiblen Software.Der Anbieter proklamiert die universelle Anwendbarkeit seines Produkts, Probleme werden der mangelnden Anpassung der Organisation angelastet. F ̧r motivationsfˆrdernde Mitsprachepotenziale bleibt da wenig Raum." (Bungard 2005:21)
- Bisher wird EDA / event-driven SOA hauptsächlich für IoT Systeme angewendet und noch niccht wirklich im BPM
- Es ist relativ schwierig zu beweisen das etwas nicht angewendet wird. / die Abwesenheit von etwas zu beweisen

### 3 Kein CEP im BPM Umfeld

- Auch hier hätte ich einen etwas anderen Spin: Während CEP sich für bestimmte Anwendungsszenarien (z.B. Clickstream-Analyse, IoT Sensordaten, Log Aggregation, ...) bereits durchgesetzt hat (hier brauchen Sie unbedingt ein paar Beispiele), gibt es keine nennenswerten Anwendungen im BPM-Umfeld.
    - Typische Anwendungsgebiete sind Smarthome, Fahrzeugüberwachung, Aktienhandel oder Business Activity Monitoring (Hedstück 2017 S.5-9)
    - Deshalb geht die Marktforschungsagentur Gartner davon aus, dass 2020 ereignisgesteuerte, Echtzeitdatenverarbeitung für 80% der digitalen Geschäftsmodelle erforderlich sein wird (Gartner, 2018).

### 4 Überleitung Problembereich / Forschungskonzept

- Der Abschluss der Einleitung sollte m.E. hinführen zu dem Problembereich, den Sie in Ihrer Arbeit untersuchen werden.
- Das können Sie elegant machen, in dem Sie noch einmal die Relevanz des Themengebiets unterstreichen, z.B. in dem Sie irgendwie belegen, dass Kunden schnelle Interaktionen mehr und mehr erwarten und dass Unternehmen "Waste" durch ineffiziente Prozesse entstehen.
- Sie könnten auch die These in den Raum stellen, dass für die Partizipation an der Data-driven Economy echtzeitfähige Prozesse notwendig sind, aber das ist wahrscheinlich nicht so einfach zu belegen und wäre daher mit Vorsicht zu genießen.

### 5 Gründe für die fehlender Verbeitung von EDA

Hier müssen Sie auf das alter der Quelle eingehen! 10 Jahre ist in der IT ja eine ganze Epoche. Damals gab es z.B. noch kein Apache Kafka. Es bestehen daher zumindest Zweifel, dass die Findings von damals noch gültig sind. Daher sollten Sie das zumindest ansprechen und sagen, dass es nur eine Studie zu den Gründen gibt, die Ergebnisse aber wahrscheinlich noch heute zutreffen (und dann sollten Sie bei den beiden Punkten kurz ausführen, warum).

- In der Vergangenheit zählte hierzu auch noch die Abwesenheit einer passenden Werkzeugunterstützung, dies ändere sich aber in den letzten Jahren mit Technologien wie Apache Kafka, welche sich derzeit großer Beliebtheit erfreuen.

### 10 Überleitung & Kriterien für eine gute Architektur

- Flexiblität
- Standards
- Qualität

# 2 Zielsetzung und Erkenntnisinteresse

# 3 Forschungskonzept + Forschungsfrage

### 6 Forschungskonzept

Bei der Validierung müssten Sie Bezug zu den drei Aspekten der Forschungsfrage nehmen und für jeden Aspekt darlegen, wie Sie demonstrieren möchten, dass Ihr Framework diesen Aspekt erfüllt.

- Beispiel Flexibilität: Sie können typische Szenarien definieren, welche Flexibilität benötigen, z.B. (1) das Einfügen eines weiteren Prozessschritts oder (2) das Ersetzen einer Komponente mit einer anderen. Sie würden dann demonstrieren, wie diese Szenarien mit Ihrem Prototypen umgesetzt werden können.
- Ähnlich kann das auch bei Qualität gemacht werden (typische Fehlerszenarien)
- Bei Standards müssen Sie darlegen, welche Teile der Architektur Ihres Prototyps "standardisiert" sind (v.a. EPL...).

### 7 Forschungsfrage

"Wie kann ein ereignisorientierte Architektur für BPM-Szenarien aussehen, die sowohl Standard, Qualität und Flexibilität bietet?"

- Die drei Ziele müssen in der Motivation aufgegriffen werden.
- Fehlende Standards und Flexibilität (Agilität) haben Sie bereits genannt, Qualität jedoch noch nicht. Darauf müssen Sie also noch ein wenig eingehen. Bsp.: Werkzeuge wie Kafka sind sehr mächtig, da bis zu 1 Mio. Nachrichten pro Sekunde verarbeitet werden können. Im Kontext von BPM kann daher mit diesem Werkzeug auch "sehr viel in kurzer Zeit schief gehen". Daher braucht es unbedingt Mechanismen, die verhindern, dass sich bei der Integration Fehler einschleichen, welche die Prozesskonsistenz unterminieren.

# 4 Vorläufige Gliederung

- Wichtig - machen Sie hier nicht den Fehler, eine Art "Lehrbuch" zu schreiben! Alles was Sie hier diskutieren muss (!) einen Bezug zu Ihrer Forschungsfrage haben oder zu dieser hinleiten.
- Bitte behalten Sie das im Hinterkopf, dann diesen Fehler machen viele Studierenden in ihrer Abschlussarbeit.

### 8 Gliederung

1. Einleitung
	- Motivation 
	- Ziele & Forschungsfragen
	- Methodische Vorgehensweise
2. Theoreitsche Grundlagen
	2.1. Ereignisse in Unternehmensanwendungen
		2.1.1. Ereignisgesteuerte Geschäftsprozesses
		2.1.2. Grenzen von konventionellen Softwarearchitekturen
	2.2. Event-Driven Architecture
	2.3. Complex Event Processing
	2.4. Entwurfsmuster von Architekturen für EDA
4. Methodik / Behandlung der Thematik
5. Ergebnisse
6. Zusammenfassung & Fazit
	- Reflextion des Vorgehens
	- Beantwortung der Forschungsfragen
	- Kritische Betrachtung & Ausblick
 

# 5 Zeitplan

[Expose2.odt](Expose%20fa28cb74febc4d6283869f967bcd0112/Expose2.odt)