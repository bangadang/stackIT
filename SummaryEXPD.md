
#  Summary EXPD
## Vorträge
- realtives vs abs. Risiko
- true vs false positiv  -->  $positiver\ Vorhersagewert = true-pos. \div false-pos.$
## Einführung
### Grundberiffe
- **Grundgesamtheit**: Die Menge aller für eine Untersuchung relevanten Elemente. Je nach
Fragestellung ergibt sich eine andere Untersuchungsmenge.
	- Abstimmungen in der CH: alle stimmberechtigten Schweizer:innen
- **Vollerhebung** (Zensus): Bei **jedem** Individuum bzw. **jedem** Objekt der Grundgesamtheit werden
die Eigenschaften gemessen, abgefragt bzw. erhoben. (z.B. früher
Volkszählung)
- **Stichprobe** (*genügend grosse* Teilmenge Grundgesamtheit): Die Eigenschaften werden in einer Teilmenge der Grundgesamtheit
erhoben. Die Teilmenge wird nach bestimmten Gesichtspunkten aus-
gewählt. Sie kann **zufällig, systematisch, willkürlich** etc. sein.
- **Repräsentativität** (bezgl. Stichprobe): Auswahl aus der Grundgesamtheit, die alle typischen Merkmalen gemäss ihren relativen Häufigkeiten abbildet.
	- Bericht Health Students at ZHAW
- 
- 
Bsp Ab1Ex. 2
- “Sollten in der Stadt Zürich mehr Parkplätze angeboten werden?” Stichprobe: Befragung von 150 Passanten im Zürcher Hauptbahnhof.
	- Grundpopulation: Alle Erwachsenen der Stadt Zürich
	- Stichprobe nicht repr. --> Passanten am Hbf eher Pendler als Autofahrer--> Grösse nicht mehr releveant.
- “Wie stark überbucht die Lufthansa ihre Flüge?” Stichprobe: Auszählung von Tickets/Sitze in 40 zufällig ausgewählten Flügen.
	- GG: alle Flüge der Lufthansa
	- SP: zu kleine Stichprobe (kann der Zufall das kompensieren; wahrsch nicht)

### Variabeln
- Variablen: Merkmale der Grundgesamtheit
	- Körpergrösse von Einwohner, Umsatzzahlen eines KMUs etc.
	- Merkmale sind typisierbar
		- kategorisch (Kategorien) : qualitativ oder kategoriell: nominal oder ordinal
			- Bürgerort: nominal (keine Ordnung)
			- Zufriedenheit: ordinal
			- Gefahrenstufe Lawinengänge: ordinal
			- Farbe Verpackung: nominell
		- numerisch (Zahlen): quantitativ oder numerisch: diskret oder stetig 
			- diskret = ganzzahlig
			- stetig = float
	
#### Daten & Messungen
- **Accuracy** (Wie genau sind die Daten?) vs. **Precision** (Wie sehr streuen Daten?)
- **Bias**: Systematischer Fehler (Fall wenn Werte nicht Stimmen, tiefe Accuracy)

### kategorielle Variablen
- **Häufigkeitstabellen**
- Bsp. Umfrage Sternzeichen von 20 Personen. Wie kann man Ergebnisse darstellen?
	- Columns: Sternzeichen, abs. Häufigkeit, rel. Häufigkeit
	- Darstellung in R
		1. Vektor erstellen: Sternzeichen <-c(Ergebnisse)
		2. table(Sternzeichen) [abs. H]
		3. table(Sternzeichen) / length(Sternzeichen) [rel. H] 
	- Bei ordinalen Merkmalen sind kumuliert abs. /rel. Häufigkeiten sinnvoll. 
		1. noten <- c(Ergebnisse)
		2. table(noten) [abs. H]
		3. cumsum(table(noten)) [kumulierte absolute Häufigkeit; "Wie viele Leute haben Note x oder kleiner"]
		4. cumsum(table(noten))/length(noten)) [kumulierte rel. Häufigkeiten]
- **Balkendiagramm**
	-  **Pareto-Diagramm** ist ein sortiertes Balkendiagramm. Oft ist es sinnvoll es mit dem kumulierten Häufigkeiten zu kombinieren.
	- Darstellung in R
		1. barplot(table(Sternzeichen)) [abs. H]
		2. barplot()table(Sternzeichen) / length(Sternzeichen) [rel. H]
- **Kuchendiagramm**
	- rel. Häufigkeit einer Variable entspricht dem entsprechenden Kreissektor an der Gesamtfläche
	- Ausprägungen sind schwer zu erkennen, wenn Kreissektoren ähnlich gross sind
	- schwer leserlich mit vielen Sektoren
	--> Balkendiagramm >>>> Kuchendiagramm
- **Modus** einer kategoriellen Variable ist die am meisten vorkommende Ausprägung.
	- sinnvoll für kategorielle und diskrete Variablen
	- kann aus Häufigkeitstabelle oder Balkendiagramm (höchste Säule) abgelesen werden

### Univariate metrische Daten (Variablen)

<!--stackedit_data:
eyJoaXN0b3J5IjpbNDAzNDA3MTIwLDE2MTA2ODgyMzBdfQ==
-->