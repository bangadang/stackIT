
# Stochastik
20.02.25

Wahrscheinlichkeitsrechnung: von einem Modell auf Daten zu schliessen. wichtig für schliessende Statistik
Nutzen: Auf viele Fragen gibt es keine eindeutige, sichere Antwort. WR bietet  die Möglichkeit solche Fragen mit Wahrsch.-modellen zu bearbeiten.
--> Quantifizierung Zufall/Risiko/Unsicherheit
• Wie lange werde ich am Postschalter warten müssen?
• Soll ich einen Regenschirm mitnehmen?
• Wie viel Anrufe gibt es bei einer Hotline in der nächsten Stunde?
• Wieviel gewinne ich, wenn ich heute einen Lotto-Schein löse?

## Begriffe
### Modell
vereinfachte Darstellung der Realität mit oftmals eingeschränktem Gültigkeitsbereich. Abstrahiert die Realität im Sinne der Beantwortung der Fragestellung 
- **deterministische** Modelle --> liefert immer das gleiche Resultat
	- Es gibt keine Unsicherheit/Unbestimmtheit
	- Es ist determiniert auf Grund dem Moment jetzt was in der Zukunft passieren wird
- **Stochastische** Modelle --> zufälliges Resultat
	- Es gibt Faktoren, die eine Rolle spielen, aber nur mit Messfehler behaftet erhoben werden können
	- deterministische Phänomene sind zu komplex für eine exakte Modellierung. Phänomene wie: menschliches Verhalten, Wetter, Wirtschaft
	- Zufall, Unsicherheit oder Unbestimmtheit werden in stochastischen Modellen berücksichtigt.
	- stoch. Modelle sind nicht eindeutig <-> "Alle Modelle sind falsche, aber manche sind nützlich"
	- Bsp 1.  Wartezeit an einem Schalter: Histogramm vor Daten --> Annäherungslinie des Histogramm gibt Annäherungsmodell für die Wartezeit x. --> $f(x)=\lambda e^{-\lambda x}$ 
	- Bsp 2. Körpergrösse der Klassenerhebung
	- 

### Normalverteilung
$f(x)=\frac{1}{\sqrt{2\pi\sigma^2}}exp\frac{(x-\mu)^2}{2\sigma^2}$

### Zufallsexperiment
Ein Versuch/ Eine Situation, wo das Ergebnis nicht bekannt ist.
	 - Können theoretisch unter gleichen Bedingungen wiederholt werden.
	 -  Ob ein Versuch / eine Situation ein Zufallsexperiment ist, fragt man sich, ob sich bei einer  Wiederholung (unter gleichen Bedingungen) immer exakt dasselbe Resultat einstellen würde. Ist die Antwort “nein”, dann handelt es sich um ein Zufallsexperiment.
 - Bsp Treibstoffverbrauch für Flug ist Zufallsmodell, weil es zu viele beeinflussende Faktoren gibt um das sicherlich deterministisch zu bestimmen
### Ergebnis / Outcome
konkrete Ergebnisse eines Zufallsexperiments. Es tritt bei jedem Experiment genau ein Ergebnis ein. Ergebnisse schliessen sich aus.
### Ergebnisraum $\Omega$
Menge aller möglichen Ergebnisse eines Zufallsexperiments. Ergebnisse sind Elemente von $\Omega$.
Bsp:
- 1 x Würfelwurf: Ω = {1, 2, 3, 4, 5, 6}
- Fussballmatch: Ω = {0 : 0, 0 : 1, 1 : 0, 0 : 2, . . .}
- Geburtsmonat: Ω = {Jan, Feb, Mär , . . . , Nov , Dez}
- Anzahl Anrufe Ω = {0, 1, 2, 3, . . . , x }
- Treibstoffverbrauch: Ω = [a, b], zwischen a (minimal möglicher
Verbrauch) und b (maximal möglicher Verbrauch, Tankvolumen).

### Mächtigkeit Ergebnisraum $|\Omega|$
Anzahl Elemente des Ergebnisraums. Kann endlich, abzählbar unendlich, überabzählbar unendlich sein.

### Ereignis A
Ein Ereignis ist eine nicht leere Teilmenge des Ergebnisraumes $A \subseteq \Omega$. Ein bezeichnet man eine Konstellation, die unter
Umständen von mehreren Ergebnissen erfüllt wird. Ein Ereignis bezeichnet eine Konstellation, die unter Umständen von mehreren Ergebnissen erfüllt wird. Ein Ereignis gilt als eingetroffen, wenn ein passendes Ergebnis aus dem
Zufallsexperiment resultiert.

**Unterschied Ereignis vs. Ergebnis:**
	- Ergebnisse sind elementare Outcomes.
	- Ereignisse sind Eigenschaften von Ergebnissen
	- Fussballmatch: FCW - FCZ ist 0:2 (Ergebnis)
	- Fussballmatch: FCW gewinnt gegen FCZ (Ereignis)

Bemerkung: Ein Ereignis kann auch nur ein einziges Ergebnis enthalten.
Somit kann man auch einem Ergebnis eine Wahrscheinlichkeit zuordnen.

#### spezielle Ereignisse
- Elementarereignisse entahlten nur ein Ereignis
- Gegenereignis von A : $\text{A}^{\text{C}}$
	- $\text{A}\cup\text{A}^{\text{C}}=\Omega$
- sicheres Ereignis $\text{A}=\Omega$
- Unmögliches Ereignis $\text{A}=\emptyset$ 
### Wahrscheinlichkeit für Ereignis A P(A)

## Mengenoperationen
### Schnittmenge
$$\text{A }\cap\text{ B}$$
### Vereinigung
$$\text{A }\cup\text{ B}$$
### Komplement
$$\text{A}^{\text{C}}$$
### Differenz
$$\text{A}\setminus\text{C}$$

### disjunkte Ergebnisse
Zwei Ergebnisse A und B sind disjunkt, wenn Sie sich gegenseitig ausschliessen
$\text{A} \cap \text{B}=\emptyset$

### Ereignis A ist Teilmenge von B
Alle Ereignisse von A sind auch in B enthalten



## Laplace Wahrscheinlichkeiten
Alle Elementarereignisse des Ereignisraums sind gleich Wahrscheinlich.
Dann ist die Wahrscheinlichkeit, dass ein Ereignis A eintritt: $$\text{P(A)} = \frac{|A|}{|\Omega|}$$

## Frequentistische Wahrscheinlichkeiten
In vielen Situationen ist nicht klar wie der Ergebnisraum aussieht oder ob alle Ergebnisse gleich wahrscheinlich sind. Wahrscheinlichkeiten können dann aufgrund vergangener Beobachtungen abgeschätzt werden.
- müssen identisch Wiederholbar sein
- Beispiel: Anzahl E-Mails, die in der nächsten Minute über die ZHAW Mailserver abgefertigt werden
Ein Zufallsexperiment wird n-mal durchgeführt und gezählt wie oft das Ereignis A eintritt.
$$\text{P(A)} \approx \frac{n_A}{n} = \text{r(A)}$$
r(A) ist die relative Häufigkeit

$r_n(A_1 \cup A_2) =r_n(A_1) + r_n(A_2)$

### Frequentistische Wahrscheinlichkeit Grenzwert
$P(A) =\lim_{n \rarr\inf} r_n(A)$ 
### Simulation
```r
set.seed()
sample(x = 1:6, size = 5, replace = TRUE)
```
### Sample Würfeln mit manipulierten Wahrsch.
```r
(round(p <- c(1,2,2,2,2,3)/12,3))
w <- sample(x = 1:6, size = 1000, replace = TRUE,
prob = p)
r_6 <- sum(w == 6) / length(w) # 0.249
```
### 2-mal würfeln Simulation mit for Schlaufe
```r
n <- 50000
w1 <- matrix(NA, nrow = n, ncol = 2)
for (i in 1:n) {
w1[i,] <- sample(1:6, size = 2, replace = T)
}
#wie häufig bei 2x Würfeln mindestens eine 6 enthalten ist
w_tf <- w1 == 6 # feststellen, welche Einträge Sechser sind, true/false matrix
summen <- rowSums(w_tf)
sum(summen>0)/length(summen) # 0.30944
```
## subjektive Wahrscheinlichkeit
Wahrscheinlichkeit = Mass des persönlichen Glaubens (Bayesianische Interpretation), Abschätzung von Experten 
- auch Aussagen über Wahrscheinlichkeiten möglich, wo keine Frequenz-Aussagen möglich sind, da in der Praxis es unmöglich ist gewisse
Experimente durchzuführen
- Bsp. wie wahrscheinlich ist ein atomarer Unfall in der Schweiz

## Axiome von Kolmogorov
Jedem Ereignis $A \subseteq \Omega$ wird eine Zahl P(A) zugeordnet:
- **Axiom 1**: $P(A) \geq 0$ für jedes Ereignis A
- **Axiom 2**: $P(\Omega) = 1$
	- Wahrscheinlichkeit das irgendetwas eintritt
- **Axiom 3**: Falls $A \cap B = \emptyset$, dann gilt $P(A\cup B) = P(A) + P(B)$ 
	- Wenn zwei Ereignisse sich ausschliessen, dann ist die Wahrscheinlichkeit der Vereinigung (A oder B tritt ein) gleich der Summe der Wahrsch. der einzelnen Ereignisse

**Frequentistische, Laplace-Definition und Bayesianische Interpretation erfüllen diese Axiome.**

### weiterre Formeln durch Herleitungen aus Axiomen
1. $P(A) + P(A^C ) = 1$
2. $P(\emptyset) = 1 − P(\Omega) = 0$
3. Wenn $A \subseteq B$, so gilt $P(A) \leq P(B)$
4. Für jedes Ereignis **A** gilt $0 \leq P(A) \leq 1$
5. $P(A_1 \cup A_2 \cup . . . \cup A_k ) = P(A_1) + P(A_2) + . . . + P(A_k )$, falls $A_i ∩ A_j = \emptyset , \forall i,j$
6. **Additionssatz** $P(A \cup B) = P(A) + P(B) − P(A ∩ B)$ 
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjE4Njc3NTk0XX0=
-->