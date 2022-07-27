# Abstract
"Die Komplexität globaler Unternehmensverbände erzeugt eine hohe Heterogenität hinsichtlich der beteiligten Informationssysteme. Damit verbunden nimmt die Anzahl verwobener und den Geschäftsablauf beeinflussender Ereignisse erheblich zu, die von zahlreichen Quellen produziert werden. Das in dieser Arbeit vorgestellte Einsatzszenario einer Serviceorientierten Architektur (SOA) in Verbindung mit der Technologie der Event-Driven Architecture (EDA) bietet großes Potential, Struktur in die Fülle an auftretenden Ereignissen zu bringen, diese effektiv zu verarbeiten und gewinnbringend in den Geschäftsablauf zu integrieren. Intelligent verbunden und die Vorteile dieser Informationsarchitektur ausnutzend, kann ein derartiges Konzept Wettbewerbsvorteile für die gesamte, globale Lieferkette und damit einhergehend für jedes einzelne beteiligte Unternehmen schaffen." (Buckel :15)

# 2.2 Prozessorientierung" (Buckel :17)

"Viele Probleme im Rahmen von Unternehmensnetzwerken und dem damit verbundenen Supply Chain Management (SCM) entstehen aufgrund von Defiziten in der Visibilität kritischer und kurzfristigen Änderungen unterworfenen Geschäftsprozessen (GP). Viele GP sind dementsprechend zunehmend ereignisgesteuert und von einer dramatischen Vielzahl an Einflussfaktoren abhängig. Es gilt, möglichst in Echtzeit auf derartige Informationen zu reagieren [6]. Erfolgsfaktoren hierfür sind insbesondere: 
 Eine transparente Prozessgestaltung für alle Stufen der Supply Chain (SC) [4, 18], 
 eine logisch vernetzte sowie schnelle Entscheidungsfindung [5, 17], 
 eine frühzeitige Erkennung von Problemen und Volatilitäten in sämtlichen unternehmens- übergreifenden GP und Identifikation von Konstellationen, um eine flexible Anpassung der Planung und Ausführung mit minimaler Reaktionszeit einzuleiten [14, 21] sowie 
 ein Einsatz von ereignisorientierten Systemen zur systematischen Verarbeitung von komplexen, den Geschäftsablauf beeinflussenden Ereignissen [1, 13]." (Buckel :17)

---
[6] Dunkel, J et al (2008): Systemarchitekturen für Verteilte Anwendungen. Hanser, 
München. 

[4] Cohen, S; Roussel, J (2006): Strategisches Supply-Chain-Management. Springer, 
Berlin.

[17] Senactive IT-Dienstleistungs GmbH (2008): Praktiker beurteilen Ereignisgesteuerte 
Architektur. http://www.i-bi.de/extdoc/SENACTIVE_UmfrageIT-Trends%202009.pdf. 
Abgerufen am 17.03.2011. 

[18] Springer, F; Emmersberger, C (2010): Event-Driven Business Process Management 
(ED-BPM). http://www.hlmc.de/cepconf/downloads/eventdrivenbusinessprocessmanage-
mentedbpm.pdf. Abgerufen am 17.03.2011.

[13] Luckham, D C (2007): The Power of Events. 5. Auflage, Addison-Wesley, Boston.

[14] Poluha, RG (2010): Quintessenz des Supply-Chain-Managements. Springer, Berlin. 

[21] Tibco Software Inc.: Optimizing the Supply Chain. http://www.tibco.com/multimedia/wp-optimizing-the-supply-chain-ecosystem_tcm8-2461.pdf  Abgerufen am 14.03.2011. 

# 2.4 Komplexität und Heterogenität" (Buckel :17)
"Die technischen Anforderungen wachsen durch Fortschritte der Informationserfassung und -weitergabe, wie z. B. durch mobile Endgeräte oder die zunehmende Volatilität der Endkunden. Weiterhin ist eine „Explosion der Interoperabilität" [20] zu beobachten - durch die beschriebene, zunehmende Verflechtung von Unternehmen und die damit verbundene Vielzahl an größtenteils heterogenen Informationssystemen ist eine Harmonisierung und Standardisierung schwer zu erreichen [4, 20]. Zusammenfassend beeinflussen folgende Probleme die Stabilität von komplexen Unternehmensverbänden:" (Buckel :17)

"Die Komplexität in Verbindung mit der herrschenden Dynamik des Umfelds sowie  die schwer zu erreichende Harmonisierung von stark gewachsenen ERP-Systemen Systemlandschaften [9, 18]." (Buckel :18)

"3 Event-Driven Architecture in Verbindung mit Serviceorientierter Architektur als Lösung für bestehende Herausforderungen" (Buckel :19)

"3.1 Die Kombination beider Architekturen" (Buckel :19)

"Da EDA und SOA in der Literatur oft unsauber abgegrenzt werden und z. T. fälschlicherweise synonym verwendet werden, vergleicht Tabelle 1 beide Architekturen anhand mehrerer einschlägiger Kategorien und Kriterien." (Buckel :19)

"Ein großer Vorteil einer EDA ist die Tatsache, dass dieses Konzept keine ausschließenden Gegensätze zu anderen Architekturstilen aufweist und folglich sehr gut als ergänzende Komponente zu implementieren ist. Der EDA-Ansatz ist demzufolge weder der manchmal fälschlicherweise bezeichnete Nachfolger von SOA, noch soll er SOA ersetzen. Trotz der erwähnten Unterschiede der Prinzipien sind jedoch beide Architekturen in ihrer Grundidee" (Buckel :19)

"der flexiblen und anpassungsfähigen GP identisch. In der Literatur wird daher auf die Komplementarität jener Konzepte hingewiesen und der kombinierte Einsatz auch als „Event-Driven SOA" oder „SOA 2.0" bezeichnet [3, 6, 16]." (Buckel :20)

"3.3 Anwendungen für Event-Driven Architecture" (Buckel :22)

"EDA wird in vielen Bereichen der „Business Intelligence" (BI) verwendet, um die Entscheidungsunterstützung für Unternehmen zu verbessern sowie die dafür verwendete Datenbasis möglichst aktuell zu halten. Das wohl bekannteste Einsatzszenario hinsichtlich BI ist das sogenannte „Business Activity Monitoring" (BAM). BAM ist ein spezieller unternehmerischer Ansatz, dem Benutzer relevante Indikatoren und Kennzahlen über ein Monitoring-Tool zu vermitteln [1, 2, 7]." (Buckel :22)

"Ein weiteres Konzept ist das „Event-Driven Process Management" - eine Kombination aus dem klassischen Business Process Management und EDA [1, 2, 18]. Bild 4 zeigt beispielhaft einen vereinfachten Auftragsabwicklungsprozess. In diesem sind unvorhergesehene Events integriert, welche automatisiert neue Prozessinstanzen erzeugen. So bewirkt der Ausfall einer essentiell an der Produktion beteiligten Maschine einen neuen „Event-Driven Process" (EDP) mit zwei möglichen Maßnahmen zur Behebung des Problems. Durch diese Ausnahmehandlung wird das Produkt trotz des auftretenden Events „Maschinenausfall" basierend auf der vorgesehenen Terminierung fertig gestellt. Der EDP endet mit dem Ereignis des Hauptprozesses „Produkt produziert"." (Buckel :23)

"3.6 Partnerintegration, Komplexität, Einführung und Erfolgsmessung" (Buckel :24)

"EDA weist allerdings Schwächen hinsichtlich der Standardisierung auf. Damit die Kommunikation der ereignisverarbeitenden Komponenten einer EDA sowie die Suche nach und Verbreitung von signifikanten Mustern in der Event-Cloud möglich ist, werden dafür entworfene Sprachen verwendet. Momenten existieren allerdings viele verschiedene Formen dieser Sprachen, was einen einheitliche Modellierung, die Vergleichbarkeit und Erweiterbarkeit, sowie einen standardisierten Einführungsprozess erschwert [1, 7, 13, 18]." (Buckel :25)

"Werden sämtliche Erkenntnisse und getroffenen Aussagen zusammengefasst und auf die systematisch aufbereiteten Probleme und Herausforderungen aus Bild 1 bezogen, wird ersichtlich, dass der kombinierte Einsatz einer EDA in Verbindung mit SOA Abhilfe für viele aktuelle Probleme und Herausforderungen in komplexen Unternehmensnetzwerken bieten kann - sofern beide Konzepte intelligent verbunden und die daraus resultierenden Vorteile" (Buckel :25)

"ausgenutzt werden." (Buckel :26)