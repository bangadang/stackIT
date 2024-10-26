
# Summary lecture Datenbanken

## 1. Relationales Datenmodell

Die Datenstrukut eines RD baut auf Relationen auf. (math. Objekt) 
Relationen sind Mengen, die den Vorteil haben, sich als Tabellen darstellen zu lassen. (Relation =/= Tabelle)

Die Implementation um die Daten handzuhaben erfolgt mit der Programmiersprache SQL.

### 1.1 Grundbegriffe

- **Domänen** (Wertebereich): sind endliche Mengen von Werten desselben Typs. (Attributenwerte sind Element einer Domäne)
	- Integers, Floats, Strings, Aufzählungstypen, wie bspw. Farben, Währungen etc. 
- **Attribute**: bestehen aus einer Bezeichnung und einer Domäne und nehmen konkrete Werte aus der Domäne an. Die Werte können sich ändern, stammen aber stets aus der am Anfang definierten Domäne.
	- Attribut Geburtstag nimmt den Wert einer Datums an. Bspw.: 01.06.1990
- **Tupel**: Ist eine feste Zahl von Komponenten mit einer beliebigen Anordnung. (Zeilen oder Spalten einer Tabelle)
	- Zeile einer Tabelle mit den Attributen Vorname, Name, Geburtstag (Max, Muster, 01.02.03)
- **Format**(Schema/Heading): Eine endliche Menge von zusammenhörigen Attributen in beliebiger Reihenfolge, solange nicht festgelegt.
	- Kunde(Konto-ID, Vorname, Name)
	- kann wie als **Relationsvariable** betrachtet werden; Objekt Kunde mit 3 Attributen. 
- Eine **Relation**: ist definiert durch:
	1. **Relationenformat**: Eine Menge von Attributennamen $\{A_1, ..., A_n\}$, wobei jedem Attributennamen $A_i$ eine Domäne/Wertebereich $dom(A_i)\in \{D_1,...,D_m\}$ zugeordnet wird.
		- Attributennamen = {Vorname, Name, Alter, Gewicht}
		- Domänen = {String, Integer, Float}
		- $dom$(Vorname) = $dom$(Name) = String
		- $dom$(Alter) = Integer
		- $dom$(Gewicht) = Float
	2. **Ausprägung** (Extension) : ist eine Menge von Tupeln, welche dem Relationenformat entsprechen. $$ ext(R) \subseteq D_1 \times ... \times D_n$$
	- Relationen sind Mengen (no order or doubles) und können tabellarisch, als Menge von Tupeln oder als Schema dargestellt werden.
- **Schlüssel**
	- Definition **Schlüsselkandidat**: Gegeben ist $R(A_1, ..., A_n)$ (Relation). Eine nicht-leere Menge K von Attributen $K \subseteq \{ A_1, ..., A_n\}$ heisst Schlüsselkandidat, 
		- wenn zwei Tupel aus der Relation gleich sind, dann ist es auch sind es auch ihre Schlüsselattributwerte.
		- Das heisst K ist eindeutig definiert. Wird ein Attribut aus K weggelassen sind die Tupel nicht mehr zu identifizieren.
	- Kurz gesagt, sind Schlüsselkandidaten ein bzw. mehrere Attributen (Spalten in einer Tabelle), die es einem ermöglichen die Tupel einer Relation zu identifizieren (Reihen in einer Tabelle)
	- Es gibt immer Schlüsselkandidaten, im Extremfall die ganze Menge an Attributen.
	- **Primärschlüssel** (Primary-Key): In der Anwendung die Spalte/n welche alle Reihen einer Tabellen eindeutig kennzeichnen. Das sind in der Praxis häufig IDs. Ist keine solche Spalte vorhanden lässt sich immer eine, als Surrogate-Key erstellen.
		- UserID in einer User-Tabelle
		- OrderID in einer Bestellungstabelle
- **Fremdschlüssel** (Foreign-Key): Eine Menge von Attributen einer Relation S(B_1, .. B_n) zu denen es eine Relation R(A_1, ..., A_n) gibt, welche einen Primärschlüssel hat, der diese Attribute von S referenziert. (Konzept referentielle Integrität)
		- 
## Relationale Algebra
-**Algebra**: Auf einem Wertebereich definierte Operationen
- **Operand**: Variablen oder Werte auf welche Operationen angewendet werden können
- **O perationen**: Prozeduren die durch Symbolerepräsentiert werden.
-  **Äquivalenz**: Gleichheit zweier math. Ausdrücke 
	- zwei äquivalente Relationen $R_1~R_2$
- **Prädikat**: Funktion die einem math. Ausdruck einen Wahrrheitswert {TRUE, FALSE} bzw. {0,1} zuuordnet
### relative Operatoren
- $\sigma$: Selektion
	- Syntax: $\sigma_{predicate}(R)$
	- Bsp: $\sigma_{Körpergrösse\lt150}(Person)$
	- SQL: SELECT Körpergrösse FROM Person WHERE Körpergrösse < 150;
	- unärer Operator der Zeilen herausfiltert anhand Selektionsprädikat. Erzeugt also eine Relation mit gleichem Schema aber weniger Tupeln/Zeilen.
	- Selektionsprädikat wird für jede Zeile der Relation geprüft.
	- Selektion ist kommutativ 
- $\pi$: Projektion
	- Syntax: $\pi_{A_1,..,A_n}(R)$
	- Bsp: $\pi_{Name, Gewicht}(Person)$ 
	- SQL: SELECT Name, Gewicht FROM Person
	- unärer Operator der Attribute/Spalten der Relation filtert. Erzeugt also eine neue Relation mit einer Teilmenge der ursprünglichen Attribute aber gleichem Schema.
	- nicht kommutativ
-  $\rho$: Umbenennung
	- Syntax: $\rho_{neuerName}(R)$ 
	- Bsp: $\rho_{S(C,D)}(R(A,B)) \Rightarrow R.A \rightarrow S.C, R.B \rightarrow S.D$


- $\times$ (kartesisches Produkt/cross join)
	- Syntax: $R \times S = R'$
	- binärer Operator, welcher das Kreuzprodukt zweier Relationen bildet.
	- Bildet die Menge aller Tupel, wenn man jedes Tupel aus einer Relation R mit jedem Tupel aus einer Relation S kombiniert.
	- Das Schema des Kreuzprodukts hat ein Attribut für jedes Attribut aus R und S. Treten gleichnamige Attribute auf müssen sie umbenannt werden.
	- nicht kommutativ
-  $\bowtie$ (natural join)
	- $R \bowtie S = R'$
	- binärer Operator, der eine Relation R' erzeugt, in welcher die alle Attribute von R, gefolgt von gemeinsamen Attributen von R und S und die restlichen Attribute aus S kombiniert werden. 
	- nicht kommutativ
	- Bsp. (insert image)
	- Nachteile des natural joins treten durch die Voraussetzung auf, dass beide Relationen gleiche Attribute und Attributwerte besitzen müssen. Falls keine Gleichheiten auftreten, erzeugt man einfach das Kreuzprodukt. 
- $\bowtie_\Rho$ (theta join)
	- Syntax: $\bowtie_\Rho  = \sigma_{P}(R \times S)$
		- Join Prädikat kann ein beliebiger logischer Ausdruck sein
	- Natural Join ist ein Speziall Fall des Theta Joins
- **Equi Join**: (weitere Verallgemeinerung des natural Joins) Prüft mit einem gegebenen Prädikat auf Gleichheit. Gleichzeitig sind die Attribute mit einem  verknüpft.
	- Jeder Equi Join ist ein natural Join aber nicht umgekehrt, da bei einem natural Join immer alle Gleichheiten berücksichtigt werden. Bei einem Equi Join kann auch nur auf die Gleichheit von einem Attribut geprüft werden. 
- **Mengenoperatoren**
	- Vereinigung
	- Durchschnitt
	- Differenz
-  **Queries** bzw. Ausdrücke der rel. Algebra

## "Bag" Algebra
- Relationelle Algebra unter der Berücksichtigung von Multimengen
- **Multiplizität** eines Tupels
	- Da in der bag Algebral Tupel mehrfach auftreten können, kann solchen Tupeln eine Multipliztät zugeschrieben werden
#### Operatoren der Bag Algebra
- Selektion, Projektion, Kreuzprodukt und Joins funktionieren gleich wie in der RA. Duplikate werden wie normale Tupel behandelt
- bag union $\cup$: Wie bei RA, nur das bei Duplikaten, die grössere Multiplizität übernommen wird. 
- bag concatenation $\sqcup$: Wie Union, aeer die Summe der Mulitplizitäten wird übernommen.
- intersection $\cap$: Wie bei RA, aber bei Duplikaten wird die kleinere Multiplizität übernommen.
- difference \: Gibt es in der linken Menge mehr Muplikate nimmt man die Differenz der Multiplizitäten, ansonsten wird die Multipliztät 0.
- Duplikatenelimination $\delta$: Entfernt Duplikate.

### Outer Joins
Bei outer joins werden alle Tupel des linken (oder rechten, oder 
von beiden) Operatoren ins Resultat übernommen. Wenn es einen 
passenden «Join-Partner» gibt, so wird normal gejoint, ansonsten werden 
die fehlenden Werte durch den Platzhalter «NULL» ersetzt. Für outer-joins 
verwendet man spezielle «bowtie»-Symbole (siehe folgende Slides).

NULL ist selbst kein Wert sondern ist ein Indikator für fehlende Werte! --> Führen oft zu Problemen
vermeiden (siehe Vorlesungsteil SQL).

- Left outer Join  &#10197;
- Right outer Join &#10198;
- Full outer Join &#10199;

## Entity Relationship Design
Ein Entitiy Relationship Model ist eine Diagrammsprache für das Design von Datenbanken, welche einfach zum relationalen Model gemapped werden kann. 
Der ER-"Dialekt":
 - liefert Relationen in Inclusion Dependency Normal Form
 - vermeidet NULLs
 - Lässt nur überwachbare Semantik zu
 
 ### Grundstrukturen
- Entitätstyp und Entitäten: Ein Entitätstyp steht für eine Menge von Entitäten. Bzw. ist eine Entität eine Instanz eines Entitätstyps
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2MjMxMDg4NTAsLTE3NjMyMzIyMDEsLT
IwMzMyMjk3NTQsMTA5MDA2MTUzOCwtNDM0Mzg0NDYyLDQ3Nzc1
ODg2NywxODI4MjE3Njg1LDExOTU4Mzk1NywtMTIzMTgzOTc0LC
0xMjIxMTk3NDc5LDE4NDcxNjI0NzksLTE3NTAyMjEzNDYsLTE4
NTYxNzgyMiwxNTA5OTU0MTA2LC0yMTA4MTQxODcyLC03MzExOT
gxNzQsMTgyNjE3NjQ3MiwtNDk5NTYzNDFdfQ==
-->