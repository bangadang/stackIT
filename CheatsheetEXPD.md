
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
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTQ1NTc2MTE0NCwtMjU3NTcyMDE5XX0=
-->