tags: #bachelorarbeitdoc 
refs: [[!Bachelorarbeit]]

# Motivation
### Digitalisierung führt zu schnelleren Prozessen -> Etablierung von EDA
Durch digitale Vernetzung und die dadurch resultierende Informationsverfügbarkeit können benötigte Informationen zum richtigen Zeitpunkt am richtigen Ort bereitgestellt werden. Diese Vernetzung ermöglicht effizientere und flexiblere Prozesse (vgl. Gimpel et al., 2018, S. 31–54). Durch ungeeignete sowie mangelhafte Informationsverfügbarkeit entstehen Verschwendungen wie unnötige Materialbewegungen, Liegezeiten und Latenzen (vgl. Heger et al., 2020, S. 711). [[4 🗄️ Archive/🎓 Bachelorarbeit 1/Literatur/Heger - Value Stream Model and Notation – Digitale Transformation von Wertströmen]]

### Problem: Flexibilität und Agilität könnte durch EDA gelöst werden, werden sie aber nicht. 
Konventionelle betriebliche IT-Systeme bieten häufig nicht die erforderliche Flexibilität, um die fachliche Agilität abzubilden. Erschwerend kommt hinzu, dass die internen und externen Anforderung an Agilität stetig wachsen, unter anderem durch erweitere technische Möglichkeiten oder verändertes Kundenverhalten (vgl. Avery, 2019; vgl. Bruns & Dunkel, 2010, S. 3). [[1 🚧 Projects/🎓 Bachelorarbeit/Literatur/Bruns, Dunkel - Event-Driven Architecture.md]]

### Lösung EDA
Lösungsansätze bieten Event-Driven Architecture (EDA), als Architekturstil und Complex Event Processing (CEP) als Softwaretechnologie. Sie repräsentieren einen neuen Stil von betrieblicher Softwarearchitektur, bei dem Ereignisse in das Zentrum der Softwarearchitektur rücken. Die resultierenden ereignisgesteuerten Anwendungssysteme ermöglichen eine realitätsnahe Abbildung der ereignisgesteuerten Geschäftsprozesses eines Unternehmens   (vgl. Bruns & Dunkel, 2010, S. 4–5). [[4 🗄️ Archive/🎓 Bachelorarbeit 1/Literatur/Bruns, Dunkel - Event-Driven Architecture]]

### Kein CEP im BPM Umfeld
EDA und insbesondere Event-Driven Service-Oriented Architecture (ED-SOA) erfahren in den letzten Jahren wachsende Aufmerksamkeit in verschiedensten Bereichen (vgl. Hamzah, 2020, S. 273–304; vgl. Shaheen et al., 2019, S. 149–154).  Des Weiteren bietet zunehmende Verbreitung von CEP zahlreiche neue Möglichkeiten im Business Process Management (BPM) (vgl. Lundberg, 2006, S. 55–65). 

Trotz dieser Tatsache finden EDA und CEP selten Anwendung in diesem Bereich. Während in Anwendungsgebieten wie Smart Home, Fahrzeugüberwachung, Aktienhandel oder Business Activity Monitoring diese Technologien bereits Anwendung finden (vgl. Hedtstück, 2017, S. 5–9), gibt es noch keine nennenswerten Anwendungen im BPM-Umfeld.

### Überleitung Problembereich / Forschungskonzept
Dies scheint verwunderlich, denn gerade diese mangelnde Flexibilität und Agilität könnte durch den Einsatz von CEP gelöst werden. Grund für die Etablierung von rigider und unflexibler Software ist die sukzessive flächendeckende Einführung solcher Systeme seit Anfang der 90er Jahre (vgl. Bungard, 2005, S. 14–21). In der Vergangenheit wurden feste Unternehmensprozesse in Software „gepresst“ (Bayer, 2016). Um sich von diesen technischen Schulden zu lösen ist die Modernisierung von konventionellen betrieblichen Systemen zu SOA basierten Systemen zu einem Mainstream-Trend geworden (vgl. Abdellatif et al., 2018, S. 634–650).

### Gründe für die fehlende Verbreitung von EDA
Die Gründe für die fehlende Verbreitung sind wenig erforscht, Bruns und Dunkel (2010) nennen mehre Gründe, von denen die zwei trotz des Alters auch heute noch beobachtbar sind. Der erste möglichen Grund  sind unvollständige sowie fehlende Standards. Dazu gehören vor allem fehlende technische Standards für wichtige EDA-Komponenten wie eine Event Processing Language (EPL) zur Beschreibung von Ereignis -typen und -regeln. Als weiterer Grund wird die Abwesenheit einer etablierten Entwicklungsmethodik genannt. Es existieren nur wenige ausgereifte Methodiken für die Entwicklung von ereignisgesteuerten Anwendungssystemen. Insbesondere Richtlinien, Entwurfsmuster, Best-Practise-Beispiele, wiederverwendbare Komponenten oder Vorgehensmodelle für EDA existieren oftmals nur in rudimentärer Form (vgl. Bruns & Dunkel, 2010, S. 234–235). [[4 🗄️ Archive/🎓 Bachelorarbeit 1/Literatur/Bruns, Dunkel - Event-Driven Architecture]]

### Überleitung & Kriterien für eine gute Architektur
Darüber hinaus ist die Qualität der angewendeten Systeme von Bedeutung. Unternehmen mit ereignisgesteuerten Architekturen verarbeiten Millionen von Ereignissen pro Sekunde (Churchward, 2008)  hier kann bereits ein kleiner Fehler in der Architektur großen Schaden anrichten.
Aus dieser Beobachtung der momentan Situation lassen sich insbesondere die drei Kriterien der fehlenden Standardisierung, Flexibilität sowie Qualität hervorheben.

# Ziele & Forschungsfragen
[[Jans BA#Forschungsfragen]]

Ziel der Arbeit ist es herauszufinden, wie eine Softwarearchitektur konzipiert und implementiert werden muss, um einen Lösungsansatz für die zuvor definierten drei Probleme der fehlenden Standards, Flexibilität sowie Qualität zu bieten.
In einem ersten Schritt sollen hierbei Anforderungen für solch eine Architektur definierten werden.
In nachfolgenden Schritten wird mithilfe der Plattform Apache Kafka ein Prototyp implementiert, welcher es ermöglicht ereignisgesteuerte Prozesse zu beschreiben, zu erstellen und diese zu validieren.
Um das Ziel zu erreichen wird ein Prototyp einer Softwarearchitektur für ereignisgesteuerte Geschäftsprozesse mit den folgenden Schwerpunkten entwickelt:
    1. Definition einer Event Processing Language (EPL) für die Beschreibung von Prozessen deren Ereignisse sowie Prozesslogik.
    2. Erzeugung von Kafka-Komponenten anhand der EPL.
    3. Validierung der Prozesse und Ereignisse anhand der definierten Logik. Hierbei liegt der Fokus auf der Vermeidung von inkonsistenten Prozessinstanzen. 

Anhand des Prototyps kann getestet werden, inwiefern die zuvor definierten Probleme gelöst werden können. Hierfür werden zuvor Tests definiert, an deren der Prototyp gemessen werden kann. Die Flexibilität könnte beispielsweise durch das Einfügen neuer Ereignisse in einen Prozess geschehen oder durch das Ersetzen einer Komponente mit einer anderen. Die Qualität kann anhand typischer Fehlerszenarien wie inkonsistente Prozessinstanzen oder Syntaxfehler der EPL getestet werden. Das Level der Standardisierung kann anhand der definierten EPL und der gesamten Entwicklungsmethodik des Prototyps bewertet werden. 
Anhand der Ergebnisse soll die folgende Forschungsfrage beantwortet werden:

*Wie kann ein ereignisorientierte Architektur für BPM-Szenarien aussehen, die sowohl Standard, Qualität und Flexibilität bietet?*

*Oder mehrere Forschungsfragen*

[[3]]