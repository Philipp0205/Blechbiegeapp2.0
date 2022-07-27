[[Liteatur - Softwararchitektur]]
#software #softarearchitektur #book #highlights #zotero

---
Extracted Annotations (04/06/2020, 14:42:24)

# Definitionen 
Software-Architektur beschreibt die Software-Bausteine eines Systems. 
Um dies genauer zu fassen, kann auf eine Definition zurückgegriffen 
werden, die den strukturellen Charakter von Software-Architektur gut 
wiedergibt und in der Literatur sowie der Praxis weit verbreitet ist. Es 
handelt sich dabei um die Definition von Software-Architektur nach -  Bass et al. [Bass et al. 2003]

Die Software-Architektur eines Systems beschreibt dessen Soft-
ware-Struktur respektive dessen -Strukturen, dessen Software-
Bausteine sowie deren sichtbare Eigenschaften und Beziehungen 
zueinander.

Diese Definition ist sehr allgemein gehalten. Sie beinhaltet jedoch die 
wichtigsten Aspekte einer Software-Architektur: 
- die Software-Struktur beziehungsweise die Software-Strukturen 
eines Systems. 
- die Software-Bausteine eines Systems. 
- die Eigenschaften der Software-Bausteine eines Systems. 
- die Beziehungen zwischen den Software-Bausteinen eines Systems. 


"Eine weitere wichtige Definition von Architektur stammt von der IEEE:" (Vogel 2009:66)

"Architecture is the fundamental organization of a system embodied in its components, their relationships to each other and to the environment and the principles guiding its design and evolution." (Vogel 2009:66)

"Diese Definition wurde von der IEEE in ihrem Standard 1471 [IEEE 2007] eingeführt, welcher sich mit der Beschreibung softwareintensiver Systeme beschäftigt. Softwareintensive Systeme sind die Systeme, deren Charakter größtenteils von Software geprägt wird, jedoch nicht nur aus Software bestehen." (Vogel 2009:66)

"Aus der Definition nach Bass und der Definition nach IEEE lässt sich folgende Definition von Software-Architektur ableiten, die den strukturellen Charakter von Software-Architektur würdigt:" (Vogel 2009:66)

"Die Software-Architektur eines Systems beschreibt dessen Software-Struktur respektive dessen -Strukturen, dessen SoftwareBausteine sowie deren sichtbaren Eigenschaften und Beziehungen zueinander und zu ihrer Umwelt." (Vogel 2009:66)

"Architektur beschäftigt sich ganz allgemein mit der Strukturierung von Systembausteinen eines Systems. Software-Architektur legt dabei den Fokus auf die Software-Bausteine eines Systems. Unabhängig davon, mit welcher Architektur-Disziplin man sich schwerpunktmäßig in der Informationstechnologie beschäftigt, ist es wichtig, die grundlegenden Arten von Systembausteinen zu kennen." (Vogel 2009:79)

# Architektur und die Bausteine eines Systems

"In dem in Abbildung 3.4-1 vorgestellten Modell werden die wichtigsten Systembausteine und ihre Beziehungen zueinander vorgestellt. Der Schwerpunkt liegt hierbei auf der einfachen Darstellung der für Architektur relevanten Bausteine eines Systems." (Vogel 2009:80)

![[4 🗄️ Archive/🎓 Bachelorarbeit 1/res/Systembausteine.png]]

*Genauerere Beschreibung der Systembausteine?*


# Schichten
"Ein weiteres, wichtiges Konzept, welches im eingeführten Modell nicht enthalten ist, ist die Anordnung eines Systems in Schichten (englisch: layers). Ein System kann in Schichten organisiert sein, die Subsysteme beinhalten. Eine Schicht dient zur logischen Strukturierung eines Systems in Hierarchieebenen. Subsysteme einer Schicht besitzen gemein-" (Vogel 2009:83)

"same Merkmale und Aufgaben. Sie können nur auf Subsysteme darunter liegender Schichten zugreifen. Je nachdem wie streng diese Konvention ausgelegt wird, sind sogar nur Zugriffe auf die nächsttiefere Schicht erlaubt. Für eine genaue Beschreibung dieses Prinzips sei an dieser Stelle auf das Layers-Architektur-Muster verwiesen [Buschmann et al. 1996]." (Vogel 2009:84)

![[4 🗄️ Archive/🎓 Bachelorarbeit 1/res/SystemSchichten 1.png]]

"Abbildung 3.4-6 illustriert die Schichten des MIS-Beispiels und die Positionierung der Subsysteme je nach Aufgabenbereich. Es wird deutlich, dass das MIS in eine Präsentationslogik-, Geschäftslogikund Persistenzlogik-Schicht unterteilt ist. Das Importund das Berichts-Subsystem sind auf der Geschäftslogik-Schicht angesiedelt, und beide können von dem Benutzerschnittstellen-Subsystem der Präsentationslogik-Schicht genutzt werden." (Vogel 2009:84)

# Anfoderungen
## Definition
"Eine Definition von Anforderungen stammt von Dorfmann und Thayer [Dorfmann und Thayer 1990]:" (Vogel 2009:120)

"Eine Anforderung ist > eine vom Anwender benötigte Fähigkeit (englisch: capability ) des Systems, um ein Problem zu lösen oder ein Ziel zu erreichen, oder > eine Fähigkeit, die das System besitzen muss, damit es einen Vertrag, einen Standard, eine Spezifikation oder ein anderes formelles Dokument erfüllt." (Vogel 2009:120)

"Wie aus Abbildung 5.2-1 ersichtlich wird, können Anforderungen generell in funktionale und nicht-funktionale Anforderungen unterteilt werden. Diese können an Organisationen (Organisationsanforderungen), Systeme (Systemanforderungen) und Bausteine (Bausteinanforderungen) gestellt werden" (Vogel 2009:122)

## Anfoderungsarten

"Funktionale Anforderungen definieren benötigte Funktionalitäten. Dabei können Organisationen, Systeme und Bausteine funktionale Anfor-" (Vogel 2009:122)
"derungen erfüllen. Tabelle 5.2-1 gibt einen Überblick über die verschiedenen funktionalen Anforderungsarten." (Vogel 2009:123)

"Nicht-funktionale Anforderungen verkörpern Erwartungen und Notwendigkeiten, die von Interessenvertretern (Auftraggeber, Benutzer, Architekt, Entwickler etc.) neben den funktionalen Anforderungen als wichtig erachtet werden und über die reine gewünschte Funktionalität hinausgehen. Dabei können unmittelbare und mittelbare nichtfunktionale Anforderungen unterschieden werden." (Vogel 2009:123)

"Eine Anforderung ist eine vom Anwender benötigte Fähigkeit (englisch: capability) des Systems, um ein Problem zu lösen oder ein Ziel zu erreichen bzw. eine Fähigkeit, die das System besitzen muss, damit es einen Vertrag, einen Standard, eine Spezifikation oder ein anderes formelles Dokument erfüllt." (Vogel 2009:138)

"Anforderungen können in funktionale und nicht-funktionale Anforderungen unterteilt werden." (Vogel 2009:138)

"Funktionale Anforderungen definieren benötigte Funktionalitäten" (Vogel 2009:138)

"Nicht-funktionale Anforderungen verkörpern Erwartungen und Notwendigkeiten, die von Interessenvertretern als wichtig erachtet werden und über die reine, gewünschte Funktionalität hinausgehen." (Vogel 2009:138)

"Es können unmittelbare und mittelbare nicht-funktionale Anforderungen unterschieden werden." (Vogel 2009:138)

# Architekturprinzien

"Trotzdem gibt es allgemeine Prinzipien, die man beim Entwurf einer Software-Architektur beachten sollte. In diesem Abschnitt werden einige zentrale Architektur-Prinzipien näher erläutert. Diese setzen sich mit verschiedenen architektonischen Fragestellungen und Problemen auseinander. Es gibt zwei Hauptprobleme, die für so gut wie alle in der Folge behandelten Prinzipien eine Rolle spielen: die Reduktion der Komplexität einer Architektur und die Erhöhung der Flexibilität (oder Änderbarkeit) einer Architektur." (Vogel 2009:144)

## 6.1.1 Prinzip der losen Kopplung" (Vogel 2009:145)

"Ein wichtiger Kern der Definition von Software-Architektur ist, dass Software-Architekturen sich in erster Linie mit den Bausteinen eines Software-Systems und deren Interaktion beschäftigen. Die Bausteine können wiederum durch viele Konstrukte realisiert werden, beispielsweise durch Module, Komponenten, Klassen, Prozeduren etc. Einerseits kann man die Bausteine der Software-Architektur unabhängig voneinander betrachten, andererseits stehen sie aber auch in einer Beziehung zueinander. Solche Beziehungen unter den Bausteinen einer SoftwareArchitektur werden als Kopplung bezeichnet. Die Kopplung ist besonders wichtig, da sie gerade die Interaktionen der Bausteine charakterisiert, welche ja zentral für die Betrachtung aus architektonischer Sicht sind." (Vogel 2009:145)

"Das Prinzip der losen Kopplung besagt, dass die Kopplung zwischen Systembausteinen möglichst niedrig gehalten werden soll. Das Prinzip" (Vogel 2009:146)

"beschäftigt sich mit dem Problem, dass es für das Verstehen und Ändern eines Bausteins oft auch notwendig ist, weitere Bausteine zu verstehen oder zu ändern [Yourdon und Constantine 1978]. Es wird angenommen, dass diese Qualitätsattribute positiv durch lose Kopplung beeinflusst werden." (Vogel 2009:147)

## 6.1.2 Prinzip der hohen Kohäsion" (Vogel 2009:148)

"Kopplung beschäftigt sich mit den Abhängigkeiten von verschiedenen Bausteinen einer Architektur. Ein Baustein besteht aber häufig selbst aus vielen Teilen. Beispielsweise besteht eine Klasse aus Variablen und Methoden. Die Abhängigkeiten innerhalb eines Systembausteins werden als Kohäsion bezeichnet." (Vogel 2009:148)

"Auch die Kohäsion kann man sich an Beispielen klarmachen. Bezogen auf die Methoden einer Klasse kann man die Kohäsion sinnvoll durch die Aufrufbeziehungen der Methoden dieser Klasse untereinander messen. In der Laufzeitsicht hat ein Objekt x dann eine hohe Kohäsion, wenn es sich oft selbst aufruft." (Vogel 2009:148)

## 6.1.3 Prinzip des Entwurfs für Veränderung" (Vogel 2009:150)

"Das Prinzip des Entwurfs für Veränderung (englisch: Design for Change) [Parnas 1994] ist ein sehr allgemeingültiges Prinzip. Dahinter steht das Problem, dass sich Software ständig ändert und Änderungen häufig schwer vorhersehbar sind. Manche Software-Architekturen gehen jedoch tendenziell mit Änderungen leichter um als andere. Die Idee hinter dem Entwurf für Veränderung ist, dass man vorhersehbare Änderungen architektonisch vorausplant." (Vogel 2009:150)

## 6.1.4 Separation-of-Concerns-Prinzip" (Vogel 2009:152)

"Das Prinzip Separation of Concerns (deutsch in etwa: Trennung von Aufgabenbereichen oder Belangen) sagt allgemein aus, dass man verschiedene Aspekte eines Problems voneinander trennen und jedes dieser Teilprobleme für sich behandeln soll. Separation of Concerns ist ein allgemeines Software-Engineering-Prinzip, das nicht nur in der Software-Architektur, sondern auch in vielen anderen SoftwareEngineering-Bereichen zum Einsatz kommt. Es ist zurückzuführen auf das römische Prinzip „Teile und herrsche" - ein generelles Prinzip, das man auch in vielen Situationen des täglichen Lebens einsetzt, um die Schwierigkeiten, auf die man stößt, zu lösen. Generell reduziert Separation of Concerns die Komplexität eines Problems und erlaubt die arbeitsteilige Bearbeitung." (Vogel 2009:152)

## 6.1.7 Modularitätsprinzip" (Vogel 2009:160)

"Die Architektur sollte aus wohl definierten Systembausteinen bestehen, deren funktionale Verantwortlichkeiten klar abgegrenzt sind. Das heißt, dass die Systembausteine leicht austauschbar und in sich abgeschlossen sind. Insbesondere dient die Modularität der Änderbarkeit, Erweiterbarkeit und Wiederverwendbarkeit von Bausteinen einer Architektur." (Vogel 2009:160)

## 6.1.9 Selbstdokumentationsprinzip" (Vogel 2009:163)

"Selbstdokumentation bedeutet, dass der Architekt oder Entwickler eines Systembausteins sich bemühen sollte, jede Information über den Systembaustein zum Teil des Systembausteins selbst zu machen [Meyer 1997]. Dies hat zunächst den Sinn, den Entwurf für Veränderung hinsichtlich der Änderung von Dokumentationen und anderen Zusatzinformationen zu unterstützen." (Vogel 2009:163)

## 6.1.10 Inkrementalitätsprinzip" (Vogel 2009:164)

"Ein erster Architektur-Entwurf wie auch Veränderungen einer bestehenden Architektur sollten möglichst inkrementell umgesetzt werden. Dies hängt damit zusammen, dass Software-Architekturen oft hochkomplex sind. Daher scheitert ein Versuch oft, ein ganzes System direkt komplett zu entwerfen, beispielsweise weil auf nebensächliche Aspekte zu viel Wert gelegt wurde oder weil wichtige Aspekte übersehen wurden." (Vogel 2009:164)

# Grundlegende architektonische Konzepte
## 6.2.5 Generative Erzeugung von Systembausteinen" (Vogel 2009:181)

"Die generative Erzeugung von Systembausteinen und das ive Programmieren [Czarnecki und Eisenecker 2000] verfolgen das Ziel, einen zu anderen Ingenieurdisziplinen ähnlichen Automatisierungsgrad auch in der Software-Entwicklung zu erreichen. Im Kern des generativen Ansatzes stehen zwei wesentliche Schritte. Zunächst muss der Fokus vom Entwurf eines einzelnen Systems hin zum Entwurf einer ganzen Familie" (Vogel 2009:181)

"von Systemen beziehungsweise vom Entwurf eines einzelnen Anwendungsbausteins hin zu einer Menge ähnlich aufgebauter Bausteine verschoben worden." (Vogel 2009:182)

"Entscheidendes Kriterium ist dabei die Herausfaktorisierung der gemeinsamen, schematischen Anteile der Anwendungen einer solchen Systemfamilie beziehungsweise der ähnlich strukturierten Systembausteine. In einem zweiten Schritt müssen geeignete Techniken eingesetzt werden, um diese schematischen Anteile automatisiert zu erzeugen. Darunter fallen die Auswahl von Mitteln zur präzisen maschinenlesbaren Spezifikation der zu generierenden Systemanteile auf einem möglichst hohen Abstraktionsniveau (wie beispielsweise die Bildung von Modellen, siehe Abschnitt 6.6) sowie der Einsatz von Generatoren, welche die abstrakten Spezifikationen (Input) einlesen und daraus letztlich die zu generierenden Systembausteine (Output) automatisiert erzeugen (siehe Abbildung 6.2-10)." (Vogel 2009:182)

"Sind im regulären Quelltext Konstrukte enthalten, die während des Übersetzungsvorgangs (Kompilierung) weiteren Quell-, Zwischenoder Maschinencode erzeugen, so spricht man von Inline-Generierung. Als Beispiel dieser Generierungstechnik sind Anweisungen an den Präprozessor einer Sprache zu nennen. Programmiersprachen mit Präprozessor sind beispielsweise C oder C++." (Vogel 2009:184)


# Qualität 
## 6.3.1 Qualitätsattributszenarien" (Vogel 2009:211)
"Taktiken benötigen eine Analyse der Qualitätsattribute als Voraussetzung. Ein geeignetes Mittel dazu sind Qualitätsattributszenarien [Bass et al. 2003], die in diesem Abschnitt kurz eingeführt werden sollen." (Vogel 2009:211)

"In der Praxis hat es sich etabliert, funktionale Anforderungen mittels Anwendungsfällen zu beschreiben. Die Dokumentation von Qualitäten, die man z. B. mit Qualitätsattributszenarien umsetzen kann, ist noch nicht so etabliert. In Tabelle 6.3-1 wird das Dokumentationsschema von Qualitätsattributszenarien eingeführt und erklärt. Manche Qualitäten gelten für das System als Ganzes. Andere Qualitäten gelten jedoch nur für einen Teil der funktionalen Anforderungen. Qualitätsattributszenarien können sowohl für systemweite als auch für anwendungsfallspezifische Qualitäten genutzt werden." (Vogel 2009:211)

![[4 🗄️ Archive/🎓 Bachelorarbeit 1/Bachelorarbeit/2/Qualitätsattributsszenarien.png]]

"Man kann Qualitätsattributszenarien nach Qualitätsattributen in Szenariotypen einteilen. Z. B. gibt es die folgenden allgemeinen Szenariotypen [Bass et al. 2003]: > Verfügbarkeitsszenarien > Änderbarkeitsszenarien > Performanzszenarien" (Vogel 2009:211)

"Sicherheitsszenarien > Testbarkeitsszenarien > Benutzbarkeitsszenarien" (Vogel 2009:212)
# Basisarchitekturen
In diesem Abschnitt werden einige grundlegende Basisarchitekturen 
behandelt, die in vielen Systemen zum Einsatz kommen. Diese Basisar-
chitekturen setzen die verschiedenen Architektur-Mittel, die bereits in 
den vorhergegangenen Abschnitten diskutiert wurden, zur Architektur-
Strukturierung ein. 

## 6.4.7 Peer-to-Peer-Architektur" (Vogel 2009:243)

"Client/Server ist ein Architektur-Stil, der eine Spezialisierung des allgemeinen Explicit-Invocation-Stils [Shaw und Garlan 1996] ist. Das heißt der Klient kommuniziert mit dem Server über direkte, explizite Aufrufe und bekommt Antworten auf diese Aufrufe vom Server. Eine Alternative stellt der Peer-to-Peer-Stil dar [Shaw und Garlan 1996], der auch Explicit Invocation spezialisiert, aber auf die direkte Kommunikation von Klienten setzt, statt mit einem zentralen Service zu kommunizieren." (Vogel 2009:243)

## 6.4.8 Publish/Subscribe-Architektur" (Vogel 2009:243)

"Publish/Subscribe ist ein Muster [Buschmann et al. 1996] bzw. Stil [Shaw und Garlan 1996] und stellt eine Alternative zu Client/Server und Peer-to-Peer dar. Im Gegensatz zu Client/Server und Peer-to-Peer basiert Publish/Subscribe nicht auf dem Explicit-Invocation-Stil [Shaw" (Vogel 2009:243)"und Garlan 1996], sondern stellt eine Form des Implicit-Invocation-Stils [Shaw und Garlan 1996] dar." (Vogel 2009:244)

[Buschmann et al. 1996] 
Buschmann, Frank; Meunier, Regine; Rohnert, Hans; Sommerlad, Peter; Stal, 
Michael, Pattern-Oriented Software Architecture Vol. 1, A System of Patterns, John 
Wiley & Sons, New York, 1996 

[Shaw und Garlan 1996] 
Shaw, Mary; Garlan, David, Software Architecture - Perspectives on an Emerging 
Discipline, Prentice Hall, Upper Saddle River, N. J., 1996 


"Das heißt, Aufrufe werden nicht direkt unter den Kommunikationsteilnehmern versendet, sondern Ereignisse werden durch einen Vermittler weitergeleitet." (Vogel 2009:244)

"Publish/Subscribe widmet sich dem Problem, dass eine Reihe von Klienten über Laufzeitereignisse informiert werden müssen. Diese Ereignisse haben eine andere Natur, als die direkten, expliziten Invokationen, die man in Client/Server und Peer-to-Peer vorfindet: Manchmal sollen eine Reihe von Klienten aktiv über ein Ereignis informiert werden, in anderen Fällen ist nur ein spezifischer Klient am Ereignis interessiert. Im Gegensatz zum Explicit-Invocation-Stil müssen der Produzent und Konsument eines Ereignisses voneinander entkoppelt sein, z. B. um getrennte Veränderbarkeit zu gewährleisten oder damit eine beliebige Zeit zwischen dem Auftreten und der Behandlung des Ereignisses verstreichen kann." (Vogel 2009:244)

"Publish/Subscribe ermöglicht es dem Ereigniskonsumenten, sich für bestimmte Ereignistypen zu registrieren. Wenn ein solches Ereignis stattfindet, informiert der Ereignisproduzent alle registrierten Konsumenten - z. B. mithilfe eines Publish/Subscribe-Systems. Das Publish/ Subscribe-System entkoppelt also die Produzenten und Konsumenten von Ereignissen." (Vogel 2009:244)

## 6.4.11 Serviceorientierte Architekturen" (Vogel 2009:250)

"Serviceorientierte Architekturen sind eine Basisarchitektur, welche die fachlich funktionalen Schnittstellen von Software-Bausteinen als wiederverwendbare, verteilte, lose gekoppelte und standardisiert zugreifbare Dienste (englisch: Services) repräsentiert (siehe [Zdun et al. 2006] und [Zdun und Hentrich 2006])." (Vogel 2009:251)

## 6.6 Architektur-Modellierungsmittel" (Vogel 2009:279)
- UML 

## 6.6.3 Domain Specific Languages (DSL)" (Vogel 2009:291)
"Unter einer Domäne versteht man in diesem Zusammenhang ein begrenztes Interessensoder Wissensgebiet, welches sowohl fachlich, als auch technisch motiviert sein kann. Typische Domänen sind beispielsweise Eingebettete Systeme, Versicherungen, Finanzdienstleistungssysteme, aber eben auch Software-Architekturen. Ziel einer domänenspezifischen Sprache (englisch: Domain Specific Language, kurz DSL) ist es," (Vogel 2009:291) die für eine jeweilige Domäne relevanten Eigenschaften formal zu erfassen und in Form einer geeigneten Sprache abzubilden. Das Gegenstück zu DSLs bilden General Purpose Languages (GPL), also Sprachen, die so generisch konzipiert sind, dass sie für alle Anwendungen und Problemstellungen einsetzbar sind. Typische Beispiele für GPLs sind bekannte 3GL-Programmiersprachen wie beispielsweise Java oder auch die in Abschnitt 6.6.2 behandelte UML." (Vogel 2009:292)

## 6.7.3 Datenaustausch und Datentransformation mit XML" (Vogel 2009:315)

"Der reibungslose Austausch von strukturierten Daten und deren Transformation ist für viele Informationssysteme von enormer Bedeutung. Ein typisches Beispiel sind B2B-Transaktionen, wie einfache OnlineBestellungen. Hier ist es notwendig, dass der Einkäufer auf die Angebote des Anbieters zugreifen, diese interpretieren und dann automatisiert bestellen kann. Hier stellt sich das Problem, dass unter Umständen verschiedene Datenbeschreibungen bei den beiden beteiligten Unternehmen benutzt werden, denn meist fehlt ein industrieweiter Daten-" (Vogel 2009:315)

"standard. Die gleiche Situation kann selbst innerhalb eines einzigen Unternehmens entstehen. Z. B. entwickeln verschiedene Abteilungen größerer Unternehmen Software oft unabhängig voneinander, was zu unterschiedlichen Konventionen und Definition der Daten führt." (Vogel 2009:316)

"Der XML-Schema-Standard [W3C 2004] hat das Ziel, diese Probleme zu lösen. Jedes Schema ist ein gültiges XML-Dokument und XML-Schemata" (Vogel 2009:316)

"erlauben typisierte Daten, auf Basis von primitiven und selbst definierten Datentypen." (Vogel 2009:317)