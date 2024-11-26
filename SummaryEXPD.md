
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
# kategorisch: 
- **nominal oder ordinal**
		- Bürgerort: nominal (keine Ordnung)
		- Zufriedenheit: ordinal
		- Gefahrenstufe Lawinengänge: ordinal
		- Farbe Verpackung: nominell
#### numerisch (Zahlen):i diskret oder stetig**
		- diskret = ganzzahlig
		- stetig = float
	
## Daten & Messungen
- **Accuracy** (Wie genau sind die Daten?) vs. **Precision** (Wie sehr streuen Daten?)
- **Bias**: Systematischer Fehler (Fall wenn Werte nicht Stimmen, tiefe Accuracy)


## univariate kategorielle Variablen
kumulierte Häufigkeiten- **, rel. Häufigkeitstabellen**
```r
vec <-c() abs. H
cumsum(table(vec)) [kumulierte abs. Häufigkeiten sind bei ordinalen Variaben -  
```
**Pareto-Diagramm** ist ein sortiertes Balkendiagramm. Oft ist es sinnvoll es mit dem kumulierten Häufigkeiten zu kombinieren. Quantitativere Aussagen so möglich 

**Kuchendiagramm**

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

## Univariate metrische Daten (1 Variable)*Stripchart
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
		Balkenhöhe = \frac{Anzahl eobachtungen In Einer Klasse}{Anzahl Beobachtungenen Total \times (obere Klassengrenze - untere Klassengrenze)}
		$$
#### Empirische kumulierte Verteilungsfunktion $F_n(x)$ 
```r
vec <- dataframe$column
plot(ecdf(vec))
ecdf(vec)(value) #ouput: kumulierte rel. H. von value
```
- empirische Verteilungsfunktion Fn(x) zeigt den Anteil Datenpunkte ≤ x, d.h. die kumulierten relativen Häufigkeiten:
	$$F_n(x) = \frac{Anzahl Bbeobachtungen \leq x}{ n}$$
- Median und Quantile an Grafik ablesbar

- **Boxplot**
	- gibt sofortige Auskunft über 5 Kennzahlen und Symmetrie der Daten
	- sagt nichts über Shape/ Modalität der Daten aus, d.h. nur geeignet für unimodalen Verteilungen
	- eignet sich zum Vergleich mehrerer Datensätze
	- eignet sich um schiefe der Daten und Ausreisser zu erkennen
	- enthält weniger Info als Histogramm, ist dafür kompakt

#### Form der Verteilung
- **symmetrisch**: m lässt sich annähernd in der Mitte an einer vertikalen Linie (Symmetrieachse) spiegeln.
- **rechts-/linksschief**: Das Histogramm steigt auf der linken (/rechten) Seite steil an und ist rechts (/links) ganz flach.
#### Modalität = Anzahl Gipfel der Verteilung
	- unimodal
	- bimodal
	- multiodal

## Statistische Kennzahlen
- **Lagemasse**: Verteilung der Daten um einen "mittleren" Wert
- **Streuungsmasse**: wie stark Streuen die Werte

## Lagemasse
- **arithmetischer Mittelwert**: Anfällig auf Ausreisser
```r
mean(vec)
```
$$\bar x = \frac{val_1+val_2+...+val_n}{n}$$
- **geometrischer Mittelwert**: Mittelwert von Wachstumsraten
	
	$$\bar g = (x_1 \cdot x_2 \cdot ... \cdot x_n)^{\frac{1}{n}}$$
	- Bspw. Zinssätze

- **harmonischer Mittelwert**: Mittel von Qutienten 
$$\bar h = \frac{n}{\frac{1}{x_1}+...+\frac{1}{x_n}}$$
	- Bspw. Geschwindigkeiten
- **Median**: Teilt Daten, sodass 50% der Daten über bzw. unter dem Median liegen.
	- Symmetrie vs. Mittelwert/Median
		- rechtsschief: Mittelwert > Median
		- linksschief: Mittelwert < Median
		- symmetrisch: Mittelwert ~ Median
```r
median(vec)
```
 $$\text{Median}(x_1, x_2, \ldots, x_n) = \tilde x= \begin{cases} x_{\frac{n+1}{2}}, & \text{if } n \text{ is odd}, \\ \frac{x_{\frac{n}{2}} + x_{\frac{n}{2} + 1}}{2}, & \text{if } n \text{ is even} \end{cases}$$

- **Modus**: numerische Variable, die am häufigsten Auftritt.
	- von Barplot einfach abzulesen
	
- **Quantile** $\alpha$: Werte die Datenpunkte einer Variable prozentual bzw in ein Verhältnis aufteilen. $\alpha :(1-\alpha)$
	-  Bei grossen Stichproben nehmen Quantile ähnliche Werte an
- Ansatz 1: für eine geordnete Stichprobe mit Grösse n
$$Q_{\alpha}=x_{[\lceil n\alpha\rceil]}$$
```r
vec <- c(values)
quantile(vec, probs= c(Q1,...,Qn), type=1) 
# Bei Typ 1 stimmt das 50%-Quantil nich mit dem Median überrein,
# wenn der Vektor eine gerade Anzahl Elemente hat.
# Definition ist nicht symmetrisch
```
- Ansatz 2: Lineare Interpolation zwischen den nächsten zwei  Werten. --> Standardmethode
$$Q_\alpha= x_{[\lfloor h \rfloor]}+(h - \lfloor h \rfloor )\cdot(x_{[\lfloor h \rfloor + 1]}-x_{[\lfloor h \rfloor]})$$
$$h = (n-1)\cdot \alpha + 1$$
- \+ 1 bei h wegen 1 Indizierung
```r
quantile(vec, probs=c(0.1,..0.75), type=7)
```
### Streungsmasse
- **Varianz** s~x~^2^ 
	- mittlere quadratische Abweichung der Beobachtungen vom arith. Mittelwert
	- nicht robust gegen Ausreisser
	$$\text{Var}(X) = s_x^2=\frac{1}{n-1} \sum_{i=1}^{n} (x_i - \bar{x})^2$$
```r
var(vec)
```
#### Streungsmasse
- **Varianz** s~x~^2^ 
	- nicht robust gegen Ausreisser
- **Standardabweichung** s~x~
	- für symmetrischVerteilungen ohne Ausreisser
	- nicht robust, wird stark verzerrt bei auuhc nur einer falschen Beobachtung
	$$s = \sqrt{\frac{1}{n-1} \sum_{i=1}^{n} (x_i - \bar{x})^2}
$$
```r
sd(vec) or sqrt(var(vec))
```
- **Spannweite** = Maxima- Minima bzw. max(A)-min(A)
	- anfällg auf Ausreisser
	- nimmt zu bei grösseren Stichproben
	- nicht geeignet als Streuungsmass
	$$max(A)-min(A)$$
- **median absolute deviation** MAD: 
	- Man zieht von jedem Element der geordneten Liste der Median ab und generiert den Median aus all diesen Differenzen.
	-  robust gegenüber Ausreissern
 
	$$MAD_x = 1.4826 \cdot median(|x_1-\tilde x|, ..., |x_n-\tilde x|)$$
```r
mad(vec) or 1.4826 * median(abs(vec - median(vec)))
```
- inter quartile range** IQR
	- mittlere 50% der Datenpunkte
	- Für rechts-/linksschiefe Verteilungen
	- robust gegenüber Ausreissern
	$$IQR=Q_3 -Q_1$$
```r
IQR(vec) or quantile(vec,0.75) - quantile(vec,0.25)
```

### Zusammenfassung Darstellungsmöglichkeiten ==für eine Variable==
|datatype| kategoriell  | metrisch
|--|--|--|
| numerisch | Häufigkeitsttabelle/ Modus | Lagemasse( AVG, Median, Quantile)/ Streumasse( Varianz, Stndardabweichung, IQR, MAD) |
| grafisch | Kuchen-/Balkendiagramm | Histogramm/ Stripchart/ empir. Verteilungsfunktion/ Boxplot |


## Bivariate Darstellungen
- Beziehungen und Korrelationen können so untersucht werden.
- verschiedene Variablentypen brauchen versch. Handhabung
### Kategoriell vs. Kategoriell
#### - **Kontingenztafel** Kreuztabelle
	- enthält die absoluten und relativen Häufigkeiten der Merkmalskombination zweier kategorieller Variablen
	-  Bei der Angabe von relativen Häufigkeiten gibt es mehrere Möglichkeiten:
			1. Anteil am Gesamten: absoluten Häufigkeiten durch die Anzahl Datenpunkte -->  relativen Häufigkeiten für jede einzelne Merkmalskombination
			2. Anteil pro Zeile: relative Häufigkeit pro Zeile brechnet sich, indem man den jeweiligen
Eintrag durch das Zeilentotal dividiert
			3. Anteil pro Spalte:  relative Häufigkeit pro Spalte brechnet sich, indem man den jeweiligen
Eintrag durch das Spaltentotal dividiert.
	-  Spalten und Zeilennormierung kann man nicht gleichzeitig aus einer Tabelle ablesen. --> Vorsicht bei Interpretation bei Zeilen/Spalten normierten Tabelle
```r
#abs. Häufigkeiten
table(df$kateg.Variable1, df$kateg.Variable2) 

# rel. Häufigkeiten zur Gesamtheit
prop.table(table(df$kateg.Variable1, df$kateg.Variable2)) 

#rel. Häufigkeiten pro Zeile
prop.table(table(df$kateg.Variable1, df$kateg.Variable2), margin=1)

#rel. Häufigkeit pro Spalte
prop.table(table(df$kateg.Variable1, df$kateg.Variable2),margin=2)
```
#### - **gestapeltes Balkendiagramm**:
	- Die Gesamthöhe der Balken zeigt die absolute Häufigkeit für ein Merkmal.
	- Höhe der Balkenabschnitte eines Balkens ist absolute Häufigkeit einer bestimmten Merkmalskombination.

#### - **gruppiertes Balkendiagramm**:
	- Höhe der Balken zeigt die absolute Häufigkeit für eine bestimmte Merkmalskombination.
```r
barplot(table(df$kateg.Variable1, df$kateg.Variable2), beside=TRUE/FALSE)
#beside bestimmt ober Säulen gestapelt oder nebeneinander stehen sollen
```
#### - **Mosaikplot**: 
	- Teilt ein Quadrat, welches die Gesamtheit der Datenpunkte darstellt, vertikal und horizontal anhand relativen Häufigkeiten für zwei Merkmale  auf.
	- Fläche ist proportional zur Anzahl Beobachtung für die Merkmalskombination in der Stichprobe. 
	- man sieht nur proportionen --> Die Anzahl an Beobachtungen ist  nicht ablesbar
	- Breite der Säulen ist proportional zur relativen Häufigkeit der ersten Variable, die Höhe proportional zur zweiten Variable.
	- Vertauschen der Variaben führt zu einem anderen Mosaikplot
```r
mosaicplot(table(df$kateg.Variable1, df$kateg.Variable2))
```
### Kategoriell vs. Metrisch
#### Kennzahlentabelle:
Die Daten lassen sich über die kategorielle Grösse Gruppieren. Dannach kann man die nummerischen Daten pro Gruppe über eine Kennzahl, wie Mittelwert und Standardabweichung, zusammenfassen.
```r
m <- tapply(X = df$num.variable, INDEX = df$kateg.variable, FUN = "mean")
s <- tapply(X = df$num.variable, INDEX = df$kateg.variable, FUN = "sd")
cbind(Mittelwert = m, Standardabweichung = s)
```
#### Boxplots für monomodale Verteilungen: 
So kann die Verteilung der metrischen Variable gruppiert nach der kategoriellen Variable dargestellt werden.
	- unimonomodale Verteilungen können so gut verglichen werden
```r
par(mfrow = c(1,2)) # 2 Grafiken nebeneinander
boxplot(num.var ~ kateg.var1, data = kdata)
boxplot(num.var ~ kateg.var2, data = kdata)
```
#### - **Stripcharts für** bimodale Verteilungen
	- wird unübersichtlich bei vielen Stufen
```r
par(mfrow = c(1,2)) # 2 Grafiken nebeneinander
stripchart(num.var ~ kateg.var1, data = kdata, vertical=TRUE, method="stack")
stripchart(num.var ~ kateg.var2, data = kdata, vertical=TRUE, method="stack")
```

#### Metrisch vs. Metrisch
#### **Streudiagramm**: 
Eine metrische Variable bildet die x-Achse, die andere die y-Achse. Die Koordinaten der Datenpunkte sind die dementsprechenden Werte der Variablen.
- Zusammenhänge und Ausreisser zwischen zwei variablen werden so ersichtlich. 
- Wird bei grossen Datensätzen aber schnell unübersichtlich --> Stichprobe um Datensatz zu verkleinern
```r
#Falls Datensatz zu gross eine Stichprobe darstellen
stichprobedf <- sample(1:nrow(kdata), 500)
plot(	df$num.var1, 
		df$num.var2, 
		main = "Title",
		ylab = "y-Achse Beschriftung", 
		xlab = "x-Achse Beschriftung", 
		las = 1, 
		cex=.5, pch=20 (filled) or as.numeric(dat$factor),
		col=colvec)
legend("topleft", 
		legend=c("meaning1", "meaning2"),
		,fill = c(col1, col2),bty= "n")
```
#### - **Gleitender Mittelwert** (bspw. über ein Streudiagramm)
	1. Wähle ein Fenster von x-Werten
	2. Bilde den Mittelwert über die y-Werte im Fenster
	3. Zeichne den Mittelwert in der Mitte des Fensters ein
	4. Verschiebe das Fenster, so dass es mit dem ersten Fenster immer noch überlappt.
	5. Wiederhole 2. - 4. bis der ganze Wertebereich von x abgedeckt ist.
	6. Verbinde alle Mittelwerte
```r
scatter.smooth(	df$num.var1, 
				df$num.var2, 
				main = "Title",
				ylab = "y-Achse Beschriftung", 
				xlab = "x-Achse Beschriftung", 
				las = 1, 
				lpars = list(col = "red"))
several scatterplots as pairs
pairs(df[, c("col1", "col2", "coln")],col = rgb(0,0,0, alpha= 0.2))
```
### Ergänzung Code
```r
möglichkeiten fehlende datenwerte zu entfernen df[df$col != "",] oder df[!is.na(df$col),]

#MAD and sd have attribute na.rm
head(df, n_elem), tail(, n_elem)
which(df$col = val & df$col = val | df$col) 
# return indexes of df rows that fulfill conditions

# vertikale Linien bei gewissen x-Stellen einzeichnen
abline(v= x-stelle, col="red")

map values to certain label:
	foot2height <- as.numeric(Fragebogen_ExpD$Schuhgrösse / Fragebogen_ExpD.reduced$Koerpergroesse)
	Fragebogen_ExpD.reduced$foot2height <- cut(foot2height,                                     breaks = c(-Inf, 0.236, 0.243, Inf), / defines the classes --> 3 classes                                          labels = c("klein", "mittel", "gross"), /defines the labels make sure not to mistake wit lvels
String manipulation
toupper()
tolower()
Mit grep() und grepl() (l für logisch) kann man Objekte identifizieren, welche ein spezifisches Muster enthalten.

# Ausgabe: Index Positionen der Zeichenketten, die 'a' enthalten.
grep(pattern = "a", x = namen)
grepl gibt logischer vektor aus
substring(namen, 3, 4) # extrahiere alle Zeichen vom 3 bis zum 4
paste(vec, 1:5 oder " Z., sep=" "=)
paste(strings, collapse="mit diesem Zeichen verbinden") verbindet strings
sub(pattern="str", replacement = "str2", x=string) Ersetz das erste Vorkomnis des Patterns
gsub(pattern="str", replacement = "str2", x=string) Ersetz ein pattern in string so oft es vorkommt
nchar() length of string
strsplit
 

```
### Zusammenfassung Darstellungsmöglichkeiten bivariate Darstellungen (2 Variablen)
| Datentypen | Darstellungsart | Kommentar |
|--|--|--|
| **Kategoriell vs. Kategoriell** | Kreuztabelle |  eher langweilig|
|  | gruppierte Balkendiagramme | mässig übersichtlich |
| | Mosaikplot | gut, nicht bekannt|
| **Metrisch vs. Kategoriell** | Tabelle mit Kennzahlen| beschränkte Information |
||Boxplot|generell gut geeignet|
||Stripcharts|generell gut geeignet|
|**Metrisch vs. Metrisch**|Streudiagramm|zeigt Verteilung der Daten (Form, Richtung, Stärke)|


## Kovarianz & Korrelation 

### Zusammenhang von Datenpunkten
Form: linerarer oder anderer Zusammenhang zw. Datenpunkten (monotone Kurve, Punktewolke) (muss nicht konstant sein. Kann "brechen"..
Richtung: positiv oder negativ 
Stärke: Wie breit ist die Punktewolke. Je breiter, deto schwächer der Zusammenhang.

### Kovarianz
$$Cov(x,y)=\frac{1}{n-1}\sum_{i=1}^n{[(x_i-\bar x)(y_i-\bar y)]} $$
```r
1/(nrow(df)-1) * sum(df$column) #oder
cov(df$column1, df$column2)
```
Kennzahl zur Richtung des Zusammenhangs bzw Streunung der Daten. 
Definiert als durchschnittliches Produkt der Abweichung beider Variablen vom Mittelwert
cov = 0 --> keine Beziehung
cov > 0 --> pos. Bezieung
con < 0 --> neg. Beziehung

**Grenzen der Kovarianz**
- informiert nur über Richtung eines Zusammenhangs nicht dessen Stärke
- Wert der Kovarianz ist schwer zu interpretieren, da er vom Masstab von x und y abhängig ist
- anfällig für Ausreisser

#### Pearson-Korrelation
$$r_{xy}= \frac {\sum_{i=1}^n{[(x_i-\bar x)(y_i-\bar y)]}} {\sqrt {\sum_{i=1}^n{(x_i-\bar x)^2 \sum_{i=1}^{n}{(y_i-\bar y)^2}}}}$$
$$r_{xy}=\frac{Cov(x,y)}{s_xs_y}$$
```r
cor(var1, var2)
```
**Korrealtion misst nicht die Steigung und sind ohne Betrachtung  der Streuwolke wenig aussagefähig**
misst die Stärke des **linearen** Zusammenhangs, d.h. wie eng die Punkte um eine Gerade liegen bzw. wie stark sie streuen, und entspricht der standardisierten Kovarianz. Es können verschiedene Formen auftreten mit der gleichen Korrelation, d.h. sie wird nicht von der Korrelation geprüft.

AB 7 Ex 1

#### Spearman Rang Korrelation
```r
cor(var1, var2, method=spearman)
```
Misst nicht lineare aber monotone Zusammenhänge, d.h. wie nahe die Punkte an einer Kurve liegen. Man definiert dafür die Ränge der x- und y-Werte und berrechnet auf diesen Rängen die Pearson Korrelation. Spearman soll der Pearsono-Korr vorgezogen werden, wenn der Zusammenhan nicht linerar ist, sonder monoton, es Ausreisser geben könnte und die Werte nicht glockenförmig verteilt sind.

AB 7 Ex 2
a) monoton abfallende Kurve. Exponentialfunktion oder 1/x

## Korrelation und Kausalität
Korr. =/= Kaus. <-> Ursache und Wirkung, Problematik des Lineraren-Denkens
Richtung der Abhängigkeit ist nicht immer klar. Hängt X von Y oder umgekehrt ab.
**confounding factor** versteckte Variable beeinflusst beide beobachtenden Variabeln und verursacht eine vermeintliche Korrelation.
Korrelationen können rein zufällig sein --> tylervigen.com/spurious-correlations

## Multivariate Darstellung
### Simpson Paradoxon
Entsteht/Beinhaltet min. 3 Variablen:
- Zielvariable
- Beobachtete Variable
- Störvariable
Falsche Eindrücke, die entstehen, indem man wichtige beeinflussende Variabeln nicht berücksichtigt. Tritt häufig auf, wenn heterogene Gruppen aggregiert werden.
### mehrere kategorielle Variablen
#### Mosaikplot
```r
mosaicplot(~ kat_var1+ kat_var2 + kat_var3, data = df, main = "Title", col = c("red", "blue", "green"), cex.axis = 0.7)

library(vcd)
mosaic(~ kat_var1+ kat_var2 + kat_var3, data = df, direction = c("v","h","v"), highlighting = "kat_var3", highlighting_fill = c("red", "blue", "green"), main = "Title", cex.axis = 0.7)
```
### 1 quantitative und mehrere kategoriellen Variablen
#### Boxplots (1num + 2kat)
```r
boxplot(num_var ~ kat_var1+ kat_var2, data = df, col = c("red", "yellow", "blue", "green"))
```
Kann bei kategoriellen Variablen mit vielen Ausprägungen schnell unübersichtlich werden.
```r
boxplot(Miete ~ Ort + Zimmer2,
        data = wg,
        col = c("orange", "magenta", "purple", "skyblue"),
        xlab = "Anzahl Zimmer",
        las = 1,
        ylab = "Miete",
        at = c(1:20)[-seq(5,20,5)], #x-Koordinaten für die Boxplots
        xaxt = "n" #keine xAchse zeichnen
        )
# x-Achse mit Levels der Zimmeranzahl hinzufügen
axis(1, #Achsennummer 
     at= seq(2.5, 17.5, 5), #Stellen wo labels stehen
     labels = levels(wg$Zimmer2)) # factor levels sind labels
legend("topleft", #Ort wo legende stehen soll
       legend = levels(wg$Ort),#namen für Legende
       fill = c("orange", "magenta", "purple", "skyblue"), #Farben mit der Legende ausgefüllt werden soll
       title = "Ort", #Titeö für Legende
       bty = "y", #Box/Kontur um Legende
       y.intersp = 0.8, # Vertikaler Abstand Linienabstand der einzelnen Legendeneinträge
       x.intersp = 1.4) #Abstand zwischen Farbboxen und Farblegende
abline(v = seq(5, 20, 5), #vertikale Linien an bestimmten x Stellen
       col = "grey", 
       lty = 1) #Linienstil
```
#### Faktorplot (1num + >2kat)
```r
plot.design(num_var ~ kat_var1+ kat_var2 + kat_var3 + kat_var4, data = df)
```
 Für jede Ausprägung wird hier der Mittelwert von der quantitativen Variable dargestellt. Man muss jedoch aufpassen, dass man nicht versucht Informationen über eine Variable abzulesen. Dieser Plot stell Zusammenhänge von allen Variablen miteinander dar.
 
### 2 quantitative und mehrere kategoriellen Variablen
#### Streudiagramme
Die 2 quantitativen Variablen werden mittels eines Streudiagramms aufgezeichnet und die kategorieller Variable zusätzlich durch Farben, Symbolform und Symbolgrösse visualisiert.
#### 2 num + 1 kat als Farbe
```r
plot(
	num_var1 ~ num_var2, 
	data = df, 
	col = c("red","yellow","blue","green")[df$kat_var]
	pch = 19,
    xlab = "x-Achsen Titel",
    ylab = "y-Achsen Titel"
	)
legend(
	"topleft", 
	legend = levels(df$kat_var),
    fill = c("red","yellow","blue","green")
    )
```
#### 2 num + 1 kat als Symbol
```r
plot(
	num_var1 ~ num_var2, 
	data = df, 
	pch = c(15,16,17)[df$kat_var], 
	cex = 2 #Skalierfaktor der Symbole
	xlab = "x-Achsen Titel",
    ylab = "y-Achsen Titel"
	)
legend("topleft", 
       legend = levels(df$kat_var),
       pch = c(15, 16, 17)
       )
```
#### 2 num + 1 kat als Symbolgrösse
```r
plot(
	num_var1 ~ num_var2, 
	data = df, 
	cex = c(0.5,1,1.2,1.8)[df$kat_var], 
	pch = 16,
	xlab = "x-Achsen Titel",
    ylab = "y-Achsen Titel"
	)
legend("topleft", 
       legend = levels(df$kat_var),
       pch = 16,
       pt.cex = c(1, 1.25, 1.5, 1.75)
       )
```
#### 2 num + >2 kat
```r
par(mar = c(4,4,1,8), 
	xpd = TRUE) # Vergrössern des rechten Randes für die Legenden	
plot(
	num_var1 ~ num_var2, 
	data = df, 
	col = c("red","yellow","blue","green")[df$kat_var1], 
	pch = c(15,16,17)[df$kat_var2], 
	cex = c(1, 1.25, 1.5, 1.75)[df$kat_var3]
	)
legend(210, 3000, 
       legend = levels(df$kat_var3),
       pch = 16,
       pt.cex = c(1, 1.25, 1.5, 1.75))
legend(210, 2000, 
       legend = levels(df$kat_var2),
       pch = c(15, 16, 17))
legend(210, 1200, 
       legend = levels(df$kat_var1),
       fill = c("red","yellow","blue","green"))
```
### GGPLOT2
```r
library(ggplot2)
ggplot(wg, 
	mapping = aes(
		x = num_var1, 
		y = num_var2, 
		shape = kat_var1,
		colour= kat_var2, 
		size = kat_var3
		)
	) +
geom_point() + 
theme_classic()
```

### >2 quantitative stetige und mehrere kategoriellen Variablen
### mehrere metrische Variablen

#### 3D-Plots oder Coplots
für genau 3, allenfalls 4, metrische Variablen
```r
library(scatterplot3d)
library(plotly) # interaktiv

scatterplot3d(
	df$num_var1, 
	df$num_var2,
	df$num_var3, 
	xlab = "x-Achsen Titel",
    ylab = "y-Achsen Titel",
    zlab = "x-Achsen Titel",
    type = "h", # "l für Linie "p" für nur Punkte, "h", für vertikale Linien zur x-y-Ebene
    highlight.3d = TRUE, #Punkte bekommen andere Farbe je nach Koordinaten, geht nur mit type = "h" oder "p"
    mar = c(4,4,4,4), #margin around the plot unten, links, oben, rechts
    pch = 16,
    cex.symbols = 2, #Skalierung der Punkte
    cex.lab = 2, #Skalierung Achsentitel
    cex.axis = 2 # Skalierung Achsenbeschriftung 
    )

plot_ly(mtcars, x = ~wt, y = ~disp, z = ~mpg)
```
#### Matrix von Streudiagrammen/ Pairs-Plot
für max. 6-8 metrische Variablen
#### Korrelationsmatrix
#### Dimensionsreduktion (Hauptkomponentenanalyse)

## Visualisierungregeln
- zu beachtende Reihenfolge mit abnehmder Wirksamkeit:
	1. Grösse
	2. Farbe
	3. Orientierung (einer Linie, eines Rechtecks etc.)
	4. Form (Stern, Kreis, Rechteck etc.)
	5. Intensität
	6. Farbton/Farbsättigung
	7. Text 	
- Berücksichtigung Farbschwächen: Rot/Grün auch Braun/Orange oder Farbmischungen können problematisch sein. Besser geeignet sind Rot/Orange bzw Hell/Dunkel Kontraste oder versch. Symbole zur Unterscheidung.
```r
# install.packages('colorBlindness')
library(colorBlindness)
displayColors(safeColors)
```



<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0NDAwNjYxOTMsMTE2MjI1MDY2MSwtMT
MxMzcwNjEzNSwtMTYxMDk2MzQ3NywtMzM5MDk0OTc5LC0yNzM4
NDA0MzcsMTIzNTgyMzM0LDEwNDE0NDMzNjgsMTI2MTg2MzkyNi
wtMTU0NjI4MDMzMCwxMDA1Mzg2MDcwLDkzNTkxMjcwLC01MTY2
NTU4OTMsMTgxNDczMTg0MCw3MzAzNDA5NjIsOTQwMjc0NTgwLC
02NDcwMDQ0ODUsNTcxNTc5OTgsMTMzMzk4Mjk1MCwzMjI1NzE1
NDhdfQ==
-->