
#  Summary EXPD

## Einführung
### Grundberiffe
#### Grundgesamtheit: 
- Die Menge aller für eine Untersuchung relevanten Elemente. Je nach Fragestellung ergibt sich eine andere Untersuchungsmenge.
	- Abstimmungen in der CH: alle stimmberechtigten Schweizer:innen
#### Vollerhebung (Zensus): 
- Bei **jedem** Individuum bzw. **jedem** Objekt der Grundgesamtheit werden
die Eigenschaften gemessen, abgefragt bzw. erhoben. (z.B. früher
Volkszählung)
#### Stichprobe (*genügend grosse* Teilmenge Grundgesamtheit):
- Die Eigenschaften werden in einer Teilmenge der Grundgesamtheiterhoben. Die Teilmenge wird nach bestimmten Gesichtspunkten ausgewählt. Sie kann **zufällig, systematisch, willkürlich** etc. sein.
#### Repräsentativität (bezgl. Stichprobe): 
- Auswahl aus der Grundgesamtheit, die alle typischen Merkmalen gemäss ihren relativen Häufigkeiten abbildet.
	- Bericht Health Students at ZHAW

*Bsp Ab1Ex. 2*
- “Sollten in der Stadt Zürich mehr Parkplätze angeboten werden?” Stichprobe: Befragung von 150 Passanten im Zürcher Hauptbahnhof.
	- Grundpopulation: Alle Erwachsenen der Stadt Zürich
	- Stichprobe nicht repr. --> Passanten am Hbf eher Pendler als Autofahrer--> Grösse nicht mehr releveant.
- “Wie stark überbucht die Lufthansa ihre Flüge?” Stichprobe: Auszählung von Tickets/Sitze in 40 zufällig ausgewählten Flügen.
	- GG: alle Flüge der Lufthansa
	- SP: zu kleine Stichprobe (kann der Zufall das kompensieren; wahrsch nicht)

## Variabeln
- Merkmale der Grundgesamtheit
	- Bsp: Körpergrösse von Einwohner, Umsatzzahlen eines KMUs etc.
- Merkmale sind typisierbar
#### kategorisch: 
- **nominal oder ordinal**
		- Bürgerort: nominal (keine Ordnung)
		- Zufriedenheit: ordinal
		- Gefahrenstufe Lawinengänge: ordinal
		- Farbe Verpackung: nominell
#### numerisch (Zahlen): 
- **diskret oder stetig**
		- diskret = ganzzahlig
		- stetig = float
	
## Daten & Messungen
- **Accuracy** (Wie genau sind die Daten?) vs. **Precision** (Wie sehr streuen Daten?)
- **Bias**: Systematischer Fehler (Fall wenn Werte nicht Stimmen, tiefe Accuracy)

-
-
-
-
-
-

## univariate kategorielle Variablen
- **Häufigkeitstabellen**
```r
vec <- c(val1, ..., valn)
table(vec) #abs. Häufigkeiten
table(vec) / length(vec) #rel. Häufigkeiten
cumsum(table(vec)) #kumulierte abs. Häufigkeiten sind bei ordinalen Variablen sinnvoll
cumsum(table(vec)) / length(vec) #kumulierte rel. Häufigkeiten
```
- Bsp. Umfrage Sternzeichen von 20 Personen. Wie kann man Ergebnisse darstellen?
	- Columns: Sternzeichen, abs. Häufigkeit, rel. Häufigkeit

- **Balkendiagramm**
```r
barplot(table(vec)) #abs. Häufigkeiten
barplot(table(vec)) / length (vec) #rel. Häufigkeiten

```
-  **Pareto-Diagramm** ist ein sortiertes Balkendiagramm. Oft ist es sinnvoll es mit dem kumulierten Häufigkeiten zu kombinieren. Quantitativere Aussagen so möglich 

- **Kuchendiagramm**

```r
pie(table(vec))
```
- rel. Häufigkeit einer Variable entspricht dem entsprechenden Kreissektor an der Gesamtfläche
	- Ausprägungen sind schwer zu erkennen, wenn Kreissektoren ähnlich gross sind
	- schwer leserlich mit vielen Sektoren
	--> Balkendiagramm >>>> Kuchendiagramm
- **Modus** einer kategoriellen Variable ist die am meisten vorkommende Ausprägung.
	- sinnvoll für kategorielle und diskrete Variablen
	- kann aus Häufigkeitstabelle oder Balkendiagramm (höchste Säule) abgelesen werden

## Univariate metrische Daten (1 Variable)
#### Stripchart
```r
vec <- daraframe$column
stripchart(vec, xlab="Beschriftung x-Achse", method="jitter" oder "stacked")
```
- Daten werden als Box/Punkt auf einer Linie aufgetragen. Datenpunkte mit gleichem Wert treten nur einmal auf. Um solche Datenpunkte sichtbar zu machen gibt es zwei Möglichkeiten, in dem Man die Punkte/Boxen verschiebt oder stapelt.
	- jittered Stripchart
	- stacked Stripchart

#### Histogramm
```r
classes <- cut(vec, breaks  = seq(start, end, by))
table(classes) #abs. Häufigkeit der versch. Klassen
hist(	vect, 
		freq=TRUE/FALSE, #abs./rel. Häufigkeiten
		breaks = seq(start, end, by), 
		xlab="x-Achse Beschriftung",
		ylab="y-Achse Beschrriftung", 
		main="Title Hist.", 
		col=color-value-or-func, 
		ylim = vec, las=1)
```
- Ziel des Histogramm ist die Verteilung der Datenpunkte über einen Wertebereich darzustellen. Umgesetzt wird das indem man Daten gruppiert bzw. in Spans/Intervalle zuordnet.
	- Wichtig ist die Entscheidung über die **Grösse der Klassen**/Buckets bzw Breite der Säulen auf der x-Achse
		- je kleiner die Klassen desto rauschiger wird das Histogramm
		- je grösser die Klassen desto weniger rauschen
	- Verschiedene Faustregeln um Klassenzahlen zu wählen. I.d.R. ist experimentieren ratsam.
	-  Auch die **Wahl des Startpunkt** kann ein Histogramm beeinflussen.
	- Konsruktion der Balken über rel. Häufigkeit: 
		$$
		Balkenhöhe = \frac{Anzahl Beobachtungen In Einer Klasse}{Anzahl Beobachtungenen Total \times (obere Klassengrenze - untere Klassengrenze)}
		$$
#### Empirische kumulierte Verteilungsfunktion $F_n(x)$ 
```r
vec <- dataframe$column
plot(ecdf(vec))
ecdf(vec)(value) #ouput: kumulierte rel. H. von value
```
- empirische Verteilungsfunktion Fn(x) zeigt den Anteil Datenpunkte ≤ x, d.h. die kumulierten relativen Häufigkeiten:
	$$F_n(x) = \frac{Anzahl Beobachtungen \leq x}{ n}$$
- Median und Quantile an Grafik ablesbar

- **Boxplot**
	- gibt sofortige Auskunft über 5 Kennzahlen und Symmetrie der Daten
	- sagt nichts über Shape/ Modalität der Daten aus, d.h. nur geeignet für unimodalen Verteilungen
	- eignet sich zum Vergleich mehrerer Datensätze
- **Form der Verteilung**
	- symmetrisch: m lässt sich annähernd in der Mitte an einer vertikalen Linie (Symmetrieachse) spiegeln.
	- rechts-/linksschief: Das Histogramm steigt auf der linken (/rechten) Seite steil an und ist rechts (/links) ganz flach.
- **Modalität** = Anzahl Gipfel der Verteilung
	- unimodal
	- bimodal
	- multiodal

## Statistische Kennzahlen
- **Lagemasse**: Verteilung der Daten um einen "mittleren" Wert
- **Streuungsmasse**: wie stark Streuen die Werte

### Lagemasse
- **arithmetischer Mittelwert**: Anfällig auf Ausreisser
```r
mean(vec)
```
$$\bar x = \frac{val_1+val_2+...+val_n}{n}$$
- **geometrischer Mittelwert**: Mittelwert von Wachstumsraten
	
	$$g = (x_1 \cdot x_2 \cdot ... \cdot x_n)^{\frac{1}{n}}$$
	- Bspw. Zinssätze

- **harmonischer Mittelwert**: Mittel von Qutienten 
$$$$
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
### Streungsmasse
- **Varianz** s~x~^2^ 
	- nicht robust gegen Ausreisser
- **Standardabweichung** s~x~
	- für symmetrische Verteilungen ohne Ausreisser
	- nicht robust, wird stark verzerrt bei auuhc nur einer falschen Beobachtung
- **Spannweite** = Maxima- Minima bzw. max(A)-min(A)
	- anfällg auf Ausreisser
	- nimmt zu bei grösseren Stichproben
	- nicht geeignet als Streuungsmass
- **median absolute deviation** MAD: 
	- robust gegenüber Ausreissern
- **inter quartile range** IQR: Differenz zw. Q~3~ und Q~1~
	- mittlere 50% der Datenpunkte
	- Für rechts-/linksschiefe Verteilungen
	- robust gegenüber Ausreissern

## Zusammenfassung Darstellungsmöglichkeiten ==für eine Variable==
|datatype| kategoriell  | metrisch
|--|--|--|
| numerisch | Häufigkeitsttabelle/ Modus | Lagemasse( AVG, Median, Quantile)/ Streumasse( Varianz, Stndardabweichung, IQR, MAD) |
| grafisch | Kuchen-/Balkendiagramm | Histogramm/ Stripchart/ empir. Verteilungsfunktion/ Boxplot |


## Bivariate Darstellungen
- Beziehungen und Korrelationen können so untersucht werden.
- verschiedene Variablentypen brauchen versch. Handhabung
### Kategoriell vs. Kategoriell
- **Kontingenztafel** Kreuztabelle
	- enthält die absoluten und relativen Häufigkeiten der Merkmalskombination zweier kategorieller Variablen
	- Bei der Angabe von relativen Häufigkeiten gibt es mehrere Möglichkeiten:
			1. Anteil am Gesamten: absoluten Häufigkeiten durch die Anzahl Datenpunkte -->  relativen Häufigkeiten für jede einzelne Merkmalskombination
			2. Anteil pro Zeile: relative Häufigkeit pro Zeile brechnet sich, indem man den jeweiligen
Eintrag durch das Zeilentotal dividiert
			3. Anteil pro Spalte:  relative Häufigkeit pro Spalte brechnet sich, indem man den jeweiligen
Eintrag durch das Spaltentotal dividiert.
	-  Spalten und Zeilennormierung kann man nicht gleichzeitig aus einer Tabelle ablesen. --> Vorsicht bei Interpretation bei Zeilen/Spalten normierten Tabelle
- **gestapeltes Balkendiagramm**:
	- Die Gesamthöhe der Balken zeigt die absolute Häufigkeit für ein Merkmal.
	- Höhe der Balkenabschnitte eines Balkens ist absolute Häufigkeit einer bestimmten Merkmalskombination.
- **gruppiertes Balkendiagramm**:
	- Höhe der Balken zeigt die absolute Häufigkeit für eine bestimmte Merkmalskombination.
- **Mosaikplot**: 
	- Teilt ein Quadrat, welches die Gesamtheit der Datenpunkte darstellt, vertikal und horizontal anhand relativen Häufigkeiten für zwei Merkmale  auf.
	- Fläche ist proportional zur Anzahl Beobachtung für die Merkmalskombination in der Stichprobe. 
	- man sieht nur proportionen --> Die Anzahl an Beobachtungen ist  nicht ablesbar
	- Breite der Säulen ist proportional zur relativen Häufigkeit der ersten Variable, die Höhe proportional zur zweiten Variable.
	- Vertauschen der Variaben führt zu einem anderen Mosaikplot

### Kategoriell vs. Metrisch
- **Kennzahlentabelle**: Die Daten lassen sich über die kategorielle Grösse Gruppieren. Dannach kann man die nummerischen Daten pro Gruppe über eine Kennzahl, wie Mittelwert und Standardabweichung, zusammenfassen.
-  **Boxplots** für monomodale Verteilungen: So kann die Verteilung der metrischen Variable gruppiert nach der kategoriellen Variable dargestellt werden.
	- monomodale Verteilungen können so gut verglichen werden
- **Stripcharts** bimodale Verteilungen
	- wird unübersichtlich bei vielen Stufen

### Metrisch vs. Metrisch
- **Streudiagramm**: Eine metrische Variable bildet die x-Achse, die andere die y-Achse. Die Koordinaten der Datenpunkte sind die dementsprechenden Werte der Variablen.
	- Zusammenhänge und Ausreisser zwischen zwei variablen werden so ersichtlich. 
	- Wird bei grossen Datensätzen aber schnell unübersichtlich --> Stichprobe um Datensatz zu verkleinern
- **Gleitender Mittelwert** (bspw. über ein Streudiagramm)
	1. Wähle ein Fenster von x-Werten
	2. Bilde den Mittelwert über die y-Werte im Fenster
	3. Zeichne den Mittelwert in der Mitte des Fensters ein
	4. Verschiebe das Fenster, so dass es mit dem ersten Fenster immer noch überlappt.
	5. Wiederhole 2. - 4. bis der ganze Wertebereich von x abgedeckt ist.
	6. Verbinde alle Mittelwerte

### Zusammenfassung Darstellungsmöglichkeiten bivariate Darstellungen (2 Variablen)
| Datentypen | Darstellungsart | Kommentar |
|--|--|--|
| **Kategoriell vs. Kategoriell** | Kreuztabelle |  eher langweilig|
|  | gruppierte Balkendiagramme | mässig übersichtlich |
| | Mosaikplot | gut, nicht bekannt|
| **Metrisch vs. Kategoriell** | Tabelle mit Kennzahlen| beschränkte Information |
||Boxplot|generell gut geeignet|
||Stripcharts|generell gut geeignet|
|**Metrisch vs. Metrisch**|Streudiagramm|zeigt Verteilung der Daten|
<!--stackedit_data:
eyJoaXN0b3J5IjpbOTA2NTU0NzI2LC0xNjk3ODgzODE1LDEyNT
k5ODgxNDEsNTYyNjg3ODIzLDUxNjY5NDU3MywxMTQ5MDAwMjUx
LDExNjA1ODg4NTgsLTQwMTY5OTYxNywtODk5MjE3NTM0LDEyNz
AwNjEzMDgsMjA0MTQ5MDU3OCwxNDUxMTQxOTI4LC0yMDAwNzE3
NjI3LDUwNDYxNjM3LDIxMjE2NTc1MzgsMTI3NTMwNTQwMiwyMT
MyMTA4MjEyLDUyMzM2MzUxMywxNTQ5MDcwNTI3LDE2MjUwOTI3
MjddfQ==
-->