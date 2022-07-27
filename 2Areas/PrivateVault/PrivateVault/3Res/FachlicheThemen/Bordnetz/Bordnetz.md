---
tags: bordnetz, confluence, sys
---

# Bordnetz

# Bordnetzentwicklungsprozess
- **SYS (Systemschaltplan)**
	- Funktionale Darstellung eines Systems (z.B. Sound-System)
	- Enthält E-Komonenten (Steuergeräte, Aktoren, Senoren) deren elektrische Verbindung in einer Pin-zu-Pin Verbindung dokmentiert ist. 
- **KAB (Kabelschaltplan)**
	- Schaltplan eines Leistungsstranges, enthält Anteile im SYS, die für den spezifischen Leistungsstrang vorgesehen sind. 
- **ELV (Elektro Logische Verlegung)** 
	- Die Verlegung der Leistungsstränge erfolgt im 3D-Raum
- **ELENA**
	- Konzernsystem, mit dem KAB nd ELV miteinander verknüpft werden
		- z.B. erhält eine vogesehene Leitung aus dem KAB ihre Länge aus der ELV
	- Daten werden in der ELZ (Elektro Logische Zeichung) dokumentiert+
- **KBL-XML (Kabel Baum Liste-XML)**
	- Schnittstellendatei, die Attribute der entsprechende PDA in XML dokumentiert
	- Nachfolger: VEC 
- **e42**
	- In der Bordnetzentwicklung verwaltete Baulteile werden hier verwaltet.
	- Systeme der Bordnetzentwicklung verwendne die in der e42 verwalteten Bauteile nd deren Attribute für die Entwicklung von SYS nd KAB.

# Modularisierung
- 150%
	- Kabelstränge, Verlegung und Freigabezeichnungen des BN werden stets als 150%-umfängliche Kabelstränge entwickelt.
		- Das bedeutet alle tatsächlichen Komponenten sind dargestellt, somit mehr als in einem gebauten Fahrzeug enthalten sind. 
- 100%
	- Kabelstränge welche letzten Endes verbaut werden. 
- **Modularisierung**
	- Steuerung von Leitungen
	- Gibt es verschiedene Varianten eines BN-Moduls besitzt ketzt Variante eine eigene PR-Nummer 
		- Das Bauteil wird verbaut wenn mindestenes einer dieser PR-Nummern für die Fahrzeugkonfig gültig ist
- **IC-Code**
	- Manche Komponenten müssen über merere Modulfamilien beschrieben werden. 
	- Neben der eigentlichen Modulzuordnung wird für jede Leitung der IC-code generiert und am Kabelstang angezeigt.
- **EBA (Easy Bordnetz API)**
	- Fachlich abstahierte Sicht auf ein Bordnetz.

# Neutraler Systemschaltplan
- **Neutral-Sys**
	- Zu Beginn der BN-Entwicklung werden Dokumente der Art Neutral-SYS für jedes System erstellt. 
	
```java
	static Datenkoffer dk;
    static EasyBordnetzProvider prov;
    private static final Logger log = LoggerFactory.getLogger(BarnyTest.class);

    @BeforeClass
    public static void loadDk() throws Exception {

        try (final InputStream is = ClassLoader
                .getSystemResourceAsStream("SYS_VNG.900.001_VNG_MiniBN_DV17_2019.11.28_(Export_1.3.8.0).zip")) {

            dk = DatenkofferLoader.getInstance().load(is);
            Method getter = dk.getClass().getDeclaredMethod("getEba");
            prov = (EasyBordnetzProvider) getter.invoke(dk);

        }
    } // shouldReturnHeaderData
```

- Code unter unter test mit neuer java klasse
- Daten unter source test resources

## Mini Bordnetz
- https://highway.porsche.com/confluence/display/BVISION/Testdaten?preview=/175931565/175931570/MiniBN%20DV17-6.dk

## Komplexität Bordnetz
- [[KomplexitätBordnetz.png]]
- [[KombinationenBordnetz.png]]

## Aufwämen kalter kabel strang kks
 - SYS wird über potenziale verbunden 
 - SYS ist eine arte lastenheft für den konstruktör
 - KAB, welche stecker gehören zusammen usw. 
 - Kalter Kabelstrang = KS ohne SYS Daten
	 - Aufwärmen = SYS daten wieder hinzufügen


## Kalter Kabelstrang
- Kabelstrang so betrachten wie er da liegt 
- Ziel: Methodik finden wie der Kabelstrang seinen Platz im Auto findet. 
- Kalter Kabelstrang = nicht eingebaut, weiß nichts über seine einbaulge 
- Mann muss nicht mehr alles manuell fitten sondern kann Harcon benutzen 
- 

# Source 
https://highway.porsche.com/confluence/pages/viewpage.action?pageId=57530039

![[Organisationen und Geschäftsprozesse-v6-20210311_100826 1.pdf]]