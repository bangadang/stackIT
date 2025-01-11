
### Begriffe
**Grundgesamtheit**: Die Menge aller für eine Untersuchung relevanten Elemente
**Vollerhebung**: Bei **jedem** Individuum/Objekt der Grundgesamtheit werden
die Eigenschaften gemessen, abgefragt bzw. erhoben. 
**Stichprobe**:  Teilmenge Grundgesamtheit
**Repräsentativität**: Auswahl aus der Grundgesamtheit, die alle typischen Merkmalen gemäss ihren relativen Häufigkeiten abbildet.
**Accuracy**: Wie genau sind die Daten
**Precision**: Wie sehr streuen Daten?
**Bias**: Systematischer Fehler (Fall wenn Werte nicht Stimmen, tiefe Accuracy)
**Modalität**: uni-, bi-, multimodal
### Lagemasse
**arithm. MW**: $\bar x = \frac{val_1+val_2+...+val_n}{n}$
**geom. MW**: $\bar g = (x_1 \cdot x_2 \cdot ... \cdot x_n)^{\frac{1}{n}}$	(Wachstumsraten)
**harm. MW**: $\bar h = \frac{n}{\frac{1}{x_1}+...+\frac{1}{x_n}}$ (Quotienten)
anfällig auf Ausreisser

**Median**: $\text{Median}(x_1, x_2, \ldots, x_n) = \tilde x= \begin{cases} x_{\frac{n+1}{2}}, & \text{if } n \text{ is odd}, \\ \frac{x_{\frac{n}{2}} + x_{\frac{n}{2} + 1}}{2}, & \text{if } n \text{ is even} \end{cases}$
**Modus**
**Quantile**:  $Q_\alpha= x_{[\lfloor h \rfloor]}+(h - \lfloor h \rfloor )\cdot(x_{[\lfloor h \rfloor + 1]}-x_{[\lfloor h \rfloor]})$ 
$h = (n-1)\cdot \alpha + 1$
### Streumasse
**Varianz**: $\text{Var}(X) = s_x^2=\frac{1}{n-1} \sum_{i=1}^{n} (x_i - \bar{x})^2$ (anfällig auf Ausreisser)
**Std.-Ab**: $s = \sqrt{\frac{1}{n-1} \sum_{i=1}^{n} (x_i - \bar{x})^2}$ (anfällig auf Ausreisser)
**Spannweite**: max(A)-min(A)
**MAD**: $MAD_x = 1.4826 \cdot median(|x_1-\tilde x|, ..., |x_n-\tilde x|)$
**IQR**: Q3-Q1
### String Manipulation
```r
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
### Kovarianz & Korrelation
**Kovarianz**:
### Univariate Darstellung
| Darstellungsart | kategoriell | metrisch |
|--|--|--|
| numerisch | Häufigkeitsttabelle/ Modus | **Lagemasse**( AVG, Median, Quantile) **Streumasse**( Varianz, Stndardabweichung, IQR, MAD) |
| grafisch | Kuchen-/Balkendiagramm | Histogramm/ Stripchart/ empir. Verteilungsfunktion/ Boxplot |

```r
table <- table(df/df$var)
cumsum(table(vec)) (kum. abs. Häufigkeiten)
pie/barplot(table)
```
```r
stripchart(	df$var, 
			xlab="Beschriftung x-Achse",
			method="jitter"/"stacked")
classes/breaks <- cut(vec, breaks = seq(start, end, by))

hist(	vect, 
		freq=TRUE/FALSE, #abs./rel. Häufigkeiten
		breaks = seq(start, end, by), 
		xlab="x-Achse Beschriftung",
		ylab="y-Achse Beschrriftung", 
		main="Title Hist.", 
		col=color-value-or-func,
		xlim=c(start, end), 
		xlim=c(start, end), 
		las=1)
		
plot(ecdf(df$var)) 
ecdf(df$var)(value)
boxplot(df$var)
```

### Bivariate Darstellung
| Datentypen | Darstellungsart | Kommentar |
|--|--|--|
| **Kategoriell vs. Kategoriell** | Kreuztabelle |  eher langweilig|
|  | gruppierte Balkendiagramme | mässig übersichtlich |
| | Mosaikplot | gut, nicht bekannt|
| **Metrisch vs. Kategoriell** | Tabelle mit Kennzahlen| beschränkte Information |
||Boxplot|generell gut geeignet|
||Stripcharts|generell gut geeignet|
|**Metrisch vs. Metrisch**|Streudiagramm|zeigt Verteilung der Daten (Form, Richtung, Stärke)|

```r
# 2 kategorische
#abs. Häufigkeiten
table(df$kateg.Variable1, df$kateg.Variable2) 

# rel. Häufigkeiten zur Gesamtheit
prop.table(table(df$kateg.Variable1, df$kateg.Variable2)) 

#rel. Häufigkeiten pro Zeile
prop.table(table(df$kateg.Variable1, df$kateg.Variable2), margin=1)

#rel. Häufigkeit pro Spalte
prop.table(table(df$kateg.Variable1, df$kateg.Variable2),margin=2)

barplot(table(df$kateg.Variable1, df$kateg.Variable2), beside=TRUE/FALSE)

mosaicplot(table(df$kat.var1, df$kat.var2))
mosaicpot(~kat.var1+kat.var2, data=df)

#kategorisch vs. metrisch
m <- tapply(X = df$num.variable, INDEX = df$kateg.variable, FUN = "mean")
s <- tapply(X = df$num.variable, INDEX = df$kateg.variable, FUN = "sd")
cbind(Mittelwert = m, Standardabweichung = s)

par(mfrow = c(1,2)) # 2 Grafiken nebeneinander
boxplot(num.var ~ kateg.var1, data = df)
boxplot(num.var ~ kateg.var2, data = df)

stripchart(num.var ~ kateg.var1, data = df, vertical=TRUE, method="stack")

stichprobedf <- sample(1:nrow(kdata), 500)
plot(	df$num.var1, 
		df$num.var2, 
		main = "Title",
		ylab = "y-Achse Beschriftung", 
		xlab = "x-Achse Beschriftung", 
		las = 1, 
		cex=.5, pch=20)

scatter.smooth(	df$num.var1, 
				df$num.var2, 
				main = "Title",
				ylab = "y-Achse Beschriftung", 
				xlab = "x-Achse Beschriftung", 
				las = 1, 
				lpars = list(col = "red"))
#several scatterplots as pairs
pairs(df[, c("col1", "col2", "coln")],col = rgb(0,0,0, alpha= 0.2))
```
### Multivariate Darstellung
| Variablen | Plot |
|--|--|
| >2 kat. | Mosaikplot |
| 1 num. + >2 kat. | Boxlot |
| 2 num. + >2 kat. | Streudiagramm mir Farben und Formen |
| >2 num. | Streudiagramm-Matrix und Korrelationsmatrix |

```
mosaicplot(~ kat_var1+ kat_var2 + kat_var3, 
			data = df, main = "Title", 
			col = c("red", "blue", "green"), 
			cex.axis = 0.7)

boxplot(num_var ~ kat_var1+ kat_var2, 
	data = df, 
	col = c("red", "yellow", "blue", "green"))
plot.design(num_var ~ kat_var1+ kat_var2 + kat_var3 + kat_var4, data = df) #Faktorplot

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
scatterplot3d(
	df$num_var1, 
	df$num_var2,
	df$num_var3, 
	xlab = "x-Achsen Titel",
    ylab = "y-Achsen Titel",
    zlab = "z-Achsen Titel",
    type = "h", # "l für Linie "p" für nur Punkte, "h", für vertikale Linien zur x-y-Ebene
    highlight.3d = TRUE, #Punkte bekommen andere Farbe je nach Koordinaten, geht nur mit type = "h" oder "p"
    mar = c(4,4,4,4), #margin around the plot unten, links, oben, rechts
    pch = 16,
    cex.symbols = 2, #Skalierung der Punkte
    cex.lab = 2, #Skalierung Achsentitel
    cex.axis = 2 # Skalierung Achsenbeschriftung 
    )
 coplot( num_var1 ~ num_var2 | num_var3, 
	 data = df, 
	 xlab =  "x-Achsen Titel", 
	 ylab =  "y-Achsen Titel", 
	 number =  3,  #wv dataslices sollen generiert werden, wird nicht gebraucht bei factors 	
 	overlap =  0.2,  #Overlap von dataslices mit < 0 entstehen gaps rows =  1,  # auf wv zeilen sollen die panels aufgeteilt werden 
 	pch =  16)

pairs(df[,c(1,3,6)]
cor(df[, c(1:6)], method = "pearson")
cor(df[, c(1:6)], method = "spearman")
library(ellipse)
plotcorr(cor(df))
```
### PCA
```r
pca <-prcomp(df, scale=TRUE) #numerisch stabiler
summary(pca)
princomp() #Alternative mit mehr Optionen
pca$rotation #rotationsmatrix
screeplot(pca)

plot(	PC1~PC2, 
		data=pca$x,
		pch=16,
		las=1,
		col= c(n-colors for n datapoints),
		main="title")
text(x=pca$x[,1], 
	y=pca$a[,2],
	labels=df$Rang,
	pos=4)
biplot(pca)
library(ggfortify)
autoplot(pca, 
	loadings=True, 
	loadings.label=True, 
	label=True, 
	label.hjust=-0.3, 
	main="title")
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2MTMxNTAzNDIsLTY4NTQ5OTgsLTI1Nz
U3MjAxOV19
-->