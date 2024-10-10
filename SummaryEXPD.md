
#  Summary EXPD
## Vorträge
### 1
- relatives vs abs. Risiko
- true vs false positiv  -->  $positiver\ Vorhersagewert = true-pos. \div false-pos.$
### 2
- Korrelation =/= Kausalität (Korr=0 keine Korr.)
- Simpson Paradoxon
- Einfluss der dritten Variable um Scheinkorrelation zu vermeiden
- Korrelationen treten häufig auf. Kausalitäten können sich experimentell nachweisbar (oft nicht einfach durchzuführen) 
 ### 5
-  
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
	-  **Pareto-Diagramm** ist ein sortiertes Balkendiagramm. Oft ist es sinnvoll es mit dem kumulierten Häufigkeiten zu kombinieren. Quantitativere Aussagen so möglich 
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
- **Stripchart** 
	- Daten werden als Box/Punkt auf einer Linie aufgetragen: Datenpunkte mit gleichem Wert treten nur einmal auf. Um solche Datenpunkte sichtbar zu machen gibt es zwei Möglichkeiten, in dem Man die Punkte/Boxen verschiebt oder stapelt.
		- jittered Stripchart
		- stacked Stripchart
- **Histogramm**
	- Ziel des Histogramm ist die Verteilung der Datenpunkte über einen Wertebereich darzustellen. Umgesetzt wird das indem man Daten gruppiert bzw. in Spans/Intervalle zuordnet.
		- Wichtig ist die Entscheidung über die **Grösse der Klassen**/Buckets bzw Breite der Säulen auf der x-Achse
		- je kleiner die Klassen desto rauschiger wird das Histogramm
		- je grösser die Klassen desto weniger rauschen
			- Verschiedene Faustregeln um Klassenzahlen zu wählen. I.d.R. ist experimentieren ratsam.
	-  Auch die **Wahl des Startpunkt** kann ein Histogramm beeinflussen.
- **Empirische Verteilungsfunktion** $F_n(x)$ 
	- empirische Verteilungsfunktion Fn(x) zeigt den Anteil Datenpunkte ≤ x, d.h. die kumulierten relativen Häufigkeiten:
	- $F_n(x) = \frac{Anzahl beobachtungen \leq }{ n}$
	- Median an Grafik ablesbar
- **Boxplot**
	- 
- **Form der Verteilung**
	- symmetrisch: m lässt sich annähernd in der Mitte an einer vertikalen Linie (Symmetrieachse) spiegeln.
	- rechts-/linksschief: Das Histogramm steigt auf der linken (/rechten) Seite steil an und ist rechts (/links) ganz flach.
- **Modalität** = Anzahl Gipfel der Verteilung
	- unimodal
	- bimodal
	- multiodal

### Statistische Kennzahlen
- **Lagemasse**: Verteilung der Daten um einen "mittleren" Wert
- **Streuungsmasse**: wie stark Streuen die Werte
#### Lagemasse
- **arithmetischer Mittelwert**: Anfällig auf Ausreisser
- **geometrischer Mittelwert**: Mittelwert von Wachstumsraten
	- $g = (x_1 \cdot x_2 \cdot ... \cdot x_n)^{\frac{1}{n}}$ 
	- 
- **harmonischer Mittelwert**: Mittel von Qutienten 
	- Bspw. Geschwindigkeiten
- **Median**: Teilt Daten, sodass 50% der Daten über bzw. unter dem Median liegen.
	- n gerade: Mittelwert zwischen den zwei Werten in der Mitte
		- $$\text{Median}(x_1, x_2, \ldots, x_n) = x_{\frac{n+1}{2}}, \& \text{if } n \text{ is odd}, \\ \frac{x_{\frac{n}{2}} + x_{\frac{n}{2} + 1}}{2}, & \text{if } n \text{ is even}.$$
	- rechtsschief: Mittelwert > Median
	- linksschief: Mittelwert < Median
	- symmetrisch: Mittelwert ~ Median
- **Modus**: numerische Variable, die am häufigsten Auftritt.
- **Quantile** $\alpha$: Werte die Datenpunkte einer Variable prozentual bzw in ein Verhältnis aufteilen. $\alpha :(1-\alpha)$
	-  Bei grossen Stichproben nehmen Quantile ähnliche Werte an
#### Streungsmasse
- **Varianz** s~x~^2^ 
- **Standardabweichung** s~x~
	- für symmetrische Verteilungen ohne Ausreisser
- **median absolute deviation** MAD: 
	- robust gegenüber Ausreissern
- **inter quartile range** IQR: Differenz zw. Q~3~ und Q~1~
	- mittlere 50% der Datenpunkte
- **Spannweite**
### Zusammenfassung Darstellungsmöglichkeiten ==für eine Variable==
|datatype| kategoriell  | metrisch
|--|--|--|
| numerisch | Häufigkeitsttabelle/ Modus | Lagemasse( AVG, Median, Quantile)/ Streumasse( Varianz, Stndardabweichung, IQR, MAD) |
| grafisch | Kuchen-/Balkendiagramm | Histogramm/ Stripchart/ empir. Verteilungsfunktion/ Boxplot |


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTYyNTA5MjcyNywtMTU4NDg2MzEwMywxOT
I3NTI5MDE4LDIwNDI1MTg1NywtNDE3NjU1MzI0LC0xMTk0NDY0
NzkxLC0yMDIzNDU2OTYzLC01NzYwODQ1NzMsLTE2OTY5MTQ2Mz
YsLTgwMzQxMTIyMCwxMDEwNTgzNzI0LDg4NDE0NzQwMiwxMTc5
MDcwMDYxLDIxMDAyMzg4MTYsLTE5NTA0NTc0MDIsLTIwMzczOD
A4NzksMTYxMDY4ODIzMF19
-->