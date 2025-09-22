
''Blenden Sie beim ersten Versuch die Musterlösung aus und versuchen Sie, die Aufgabe ohne Hilfe zu lösen. Recherchieren Sie selbständig, wenn Ihnen eine physikalische Formel nicht bekannt ist. Wenn Sie die Musterlösung nicht verstehen, fragen Sie in der Übungsstunde nach oder chatten Sie mir per MS Teams''

== Aufgabe ==

Warum treten bei der Ausschlagmethode immer, wenn auch kleine, Rückwirkungen auf die Messgrösse auf? 

Begründen Sie die vorrangige Verwendung der Kompensationsmethode für hochgenaue Messeinrichtungen.



== Aufgabe ==

Die relative Abweichung infolge der Quantisierung soll kleiner als 0,02% bleiben.<br />
Wie gross muss die Auflösung des zu verwendenden AD-Wandlers mindestens sein?



== Aufgabe ==

AD-Wandler werden häufig mit einem Full-Scale-Wert ''FS'' = 10V realisiert. Wie gross ist der Spannungswert, der ein Umschalten des LSB (''least significant bit''')''''' bewirkt, für einen:

a) 8-Bit AD-Wandler,

b) 10-Bit AD-Wandler,

c) 12-Bit AD-Wandler?



== Aufgabe ==

Für einen Spannungsverstärker wird ein Pegelverhältnis von 35,6 dB angegeben. Welcher Verstärkung als lineare Angabe entspricht das?







== Aufgabe ==

Gegeben ist ein Spannungsverhältnis ''U<sub>a</sub>''/''U<sub>e</sub>'' = 1234. Seben Sie das zugehörige Pegelverhältnis in dB an.



= Lösungen =

{{DSP.PGS.Collapsible-Start|id=coll-1|showText=Lösungen|hideText=ausblenden}}
== Lösung ==

Die zur Realisierung des Anzeigeausschlags notwendige Energie wird dem Messobjekt entzogen, damit liegen, wenn auch nur geringfügig, andere Belastungen des Messobjekts vor, als ohne Anschluss einer Messeinrichtung. Beim Kompensationsfall, auch Abgleichfall genannt, sind Messgrösse und Kompensationsgrösse gleich gross. In diesem Fall wird dem Messobjekt keine Energie entzogen, d. h. es tritt keine Rückwirkung auf das Messobjekt auf. Bei geeigneter Konstruktion eines Messsystems, das nach der Kompensationsmethode arbeitet, wirken Störungen aus der Umwelt in gleicher Weise auf Messgrösse und Kompensationsgrösse und die Störwirkungen kompensieren sich zu Null.



== Lösung ==

$$ \begin{align*}
&A_\text{rel} = \frac{1}{2^n -1} < 0,0002\\[2mm]
&2^n -1 >\frac{1}{0,0002}\\[2mm]
&2^n > \frac{1}{0,0002} + 1 = 5000 + 1 = 5001\\[2mm]
&\lg 2^n = n \cdot \lg 2 > \lg {5001}\\[2mm]
&n > \frac{\lg {5001}}{\lg 2} = \frac{3,699}{0,301} = 12,288
\end{align*} $$

Es ist ein AD-Wandler mit einer Auflösung von mindestens 13 Bit erforderlich.

== Lösung ==

a) 8-Bit-AD-Wandler: 1 LSB = $$\frac{10\ \text{V}}{2^8 -1} \approx \frac{10\ \text{V}}{2^8} = 0,0390625\ \text{V} \approx 0,04 \ \text{V}$$

b) 10-Bit-AD-Wandler: 1 LSB = $$\frac{10\ \text{V}}{2^{10} -1} \approx \frac{10\ \text{V}}{2^{10}} = 0,009765625\ \text{V} \approx 0,01 \ \text{V}$$

c) 12-Bit-AD-Wandler: 1 LSB = $$\frac{10\ \text{V}}{2^{12} -1} \approx \frac{10\ \text{V}}{2^{12}} = 0,00244140625\ \text{V} \approx 0,0024 \ \text{V}$$



== Lösung ==




Umstellung zur Berechnung der linearen Verstärkung:
$$ \begin{align*}   
x_{dB} = 20 * lg(\frac{U_2}{U_1})\\[2mm]
\frac{U_2}{U_1} = 10^{\frac{x_{dB}}{20}}\\[2mm]
\frac{U_2}{U_1} = 10^{\frac{35.6 dB}{20}} = 10^{\frac{35.6}{20}} = 10^{1.778} = 60.
\end{align*}$$ 

[[Kategorie:Seiten mit defekten Dateilinks]]

== Lösung ==

$$ \begin{align*}
\left (\frac{U_2}{U_1} \right )_{\text{dB}} &= 20 \cdot \lg \frac{U_2}{U_1} = 20 \cdot \lg 1234 = 20 \cdot 3,09 = 61,8 \text{dB}
\end{align*} $$

{{DSP.PGS.Collapsible-End}}

[[Kategorie:Seiten mit defekten Dateilinks]]


> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIxNDUyODgyMzJdfQ==
-->