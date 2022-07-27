---
marp: true
tite: Biegeverkürzung Präsentation
keywords:
  - präsentation
  - marp 
---

![bg right 50% 90%](csm_Blechdickentoleranzen_Homepage_339d31e20b.jpg)

# Biegeverkürzung
Philipp Kurrle 

<!-- 
footer: Bild: https://www.ras-online.de/produkte/biegen/vergleich-schwenkbiegen-gesenkbiegen/
-->

--- 

# Grundlagen

<!-- 
footer: '' 
-->


---

## Grundlagen
- Beim Biegen wird der Werktstoff etwas gestreckt und damit verlängert. 
    - Daher muss das Blechteil vor dem Biegen gekürzt werden. 
- Einflussparameter sind: Werkstoff, Blechdicke, Lage der Biegung zur Walzrichtung, Art des Biegens, Oberflächenrauikeit, Schmierstoff, Biegeradius, Biegewinkel.
- **Auch wenn genannte Parameter theoretisch genau bekannt sind kommt es in der Fertigung dennoch zu Abweichungen*

<!-- 
footer: '' 
-->

---

## Eigenheiten Schenkbiegen

<style scoped>
	ul {
		font-size: 25px;
	}
</style>



![bg right:40% 100%](MaterialDickeÄnderung.png)
- Radiusverlauf etwas unsymmetrisch da ein Teil des Blechs gehalten und der andere frei gebogen wird
- Material wird im Biegebereich dünner und Blech wird länger (Schlupf)
- Innenseite der Biegezone wird gestaucht und die Außenseite gestreckt.
- Dicke der Biegezone wird ca. 10-20% geringer
- Bei kleinem Radius geht Materialdicke idR. stärker zurück
- Es gibt einen minimalen Biegewinkel da das Material sonst reißt

--- 

## Neutraler Faser
- "Diejenige Faser oder Schicht eines Balkenquerschnitts, deren Länge sich bei Verdrehen bzw. Biegen nicht ändert." (1)
- Ideale Neutrale Faser liegt theoretisch in der Blechmitte (s/2)
- k-Faktor gibt eine Korrektur bezogen auf den Randabstand der ideal neutralen Faser an. 
- Lage/Radius der korrigierten neutralen Fase = (s/2)*k
    - K=1: Ideale Neutrale Faster
    - K=0,7: (70% der Strecke bis zur Blechmitte) bedeutet tatsächliche Neutrale Faser hat einen Abstand von nur 70% des Abstandes den die ideale Neutrale Faster in der Blechmitte zum Rand hat. 

<!-- 
footer: 1: https://de.wikipedia.org/wiki/Neutrale_Faser
-->

---

# Berechnungsmethoden

---

## Berechungmethoden

![bg right:40% 100%](images/Methoden%C3%9Cbersicht.png)

- a, b = Schenkel
- k = k-Faktor
- s = Bleckdicke
- r = Innenradius, Biegeradius

- Da die Einflussparameter mathematisch kaum vollständig erfasst werden können verweden die meisten Blechverarbeiter eigene empirisch emittelte Tabellen die auf das Material und ewrkzeuge abgestimmt sind. (Technologietabellen?)


<!-- 
footer: '' 
-->

---



![bg right:40% 105%](MethodenUebersicht.png)

## Berechnungsmethoden: 1. Empirische Methode mit Zuschlag

- Alle Längen an der Innenseite + Bogenlänge innenradius + pauschaler Zuschlag
- Zuschläge können empirisch durch Proben ermittelt werden.

- L = a'+b'+lb'(+x)

a', b' = Gerade (ungebogene) Längen
lb'    = Bogenlänge am Innenradius
x      = Ermittelter Zuschlag

---

![bg right:40% 100%](images/Methoden%C3%9Cbersicht.png)
## Berechnungsmethoden: 2. Biegeverkürzung nach DIN6935 

- Addition der Schenkellängen und Abzug eines Korrekturwertes (v). 

-  L = a + b - v 

a, b = äußere Schenkellängen
v = Korrekturwert (Verkürzung)


--- 



![bg right:40% 100%](images/Methoden%C3%9Cbersicht.png)
## Berechnungsmethoden: 3. Allgemeintgültige Methode

- Addition der geraden Teilstücke und des Bogenstücks. 
- Berechnung des Bogens mit korrigierten (imaginären) neutralen Faser.

- L = a' + b' + lb 

**a',b'** = gerade (ungebogene) Länge 
**lb** = korrigierte Bogenlänge

---

## Fragen
- Welche Parameter wollen wir mittels ML herausfinden? Nur die Biegeverkürzung? 

---