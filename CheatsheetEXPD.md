
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

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2OTU4Njg2NzBdfQ==
-->