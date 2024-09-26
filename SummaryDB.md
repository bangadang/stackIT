
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
	- **Fremdschlüssel** (Foreign-Key): Eine Menge von Attributen einer Relation S(B_1, .. B_n) zu deren eine Relation R gibt

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwOTI4MTY4NDQsLTQ5OTU2MzQxXX0=
-->