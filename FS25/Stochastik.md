
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

## Kombinatorik

### Urnenmodell
Gesucht ist die Anzahl Möglichkeiten eine Auswahl von **k** Objekten aus **n** Objekten anzuordnen/auszuwählen
|  | Ohne Wiederholung/ Zurücklegen | Mit Wiederholung/ Zurücklegen |
|--|--|--|
| Auswahl k = n Reihenfolge wichtig| $$n!$$ Permutation ohne Wiederholung| $$\frac{n!}{k_1!\cdot...\cdot k_s!}$$ Permutation mit Wiederholung $$\text{}$$ Möglichkeiten, n Objekte, die sich in s Gruppen mit jeweils k1,…,ks identischen Objekten einteilen lassen, anzuordnen.|
| Auswahl k Reihenfolge wichtig | $$\frac{n!}{(n-k)!}$$ | $$n^k$$ |
| Auswahl k Reihenfolge unwichtig | $$n \choose k$$ | $$n+k-1 \choose k$$ |

### Produktregel
Anzahl Möglichkeiten berechnet sich als **Produkt der Möglichkeiten pro Stufe**
**Bsp**: Fuhrunternehmen mit 6 Chauffeuren, 4 Zugfahrzeugen und 8 Anhängern. Wie
viele Kombinationen gibt es?
$z=6\cdot 4 \cdot 8 = 192$

Wie können wir in R alle 192 verschiedenen Züge generieren?
```r
zuege <- expand.grid(chauffeur=1:6,
zugfahrzeug=1:4,
anhaenger=1:8)
nrow(zuege) # 192
```

### Permutationen 
Permutationen ist ein **Aufzählen von Reihenfolgen**
**Bsp**: Es gibt 4 Flugzeuge und 4 Gates. Wie viele Möglichkeiten gibt es, die Flugzeuge an die Gates zu stellen?
$s=4!=4\cdot3\cdot2\cdot1$
```r
factorial(n)
```
 "BIRNE" Wie viele Möglichkeiten gibt es, die
Buchstaben anzuordnen?
$z = 5! = 5 \cdot 4 \cdot 3 \cdot 2 \cdot 1 = 120$
```r
library(combinat)
s <- permn(c("B","I","R","N","E"))
length(s) # 120
s[[1]] # "B" "I" "R" "N" "E"
s[[2]] # "B" "I" "R" "E" "N"
```

"ERBSE" Wie viele Möglichkeiten gibt es, die
Buchstaben anzuordnen? Achtung E kommt zwei mal vor!
```r
s <- permn(c("E","R","B","S","E"))
s[[4]] # "E" "E" "R" "B" "S"
s[[5]] # "E" "E" "R" "B" "S"
length(unique(s)) # 60
```
Formel: $\frac{n!}{n_1!\cdot...\cdot n_s!}$

**Bsp**: Wir betrachten die Anordnung von Zugwagen: Ein Zug besteht aus 4 Wagen
der 1. Klasse, 7 Wagen der 2. Klasse, 1 Speisewagen, 2 Gepäckwagen.
- Wie viele unterschiedliche Wagenfolgen sind möglich? $\frac{14!}{4!\cdot 7! \cdot 1!\cdot 2!} = 360360$
- Wie viele unterschiedliche Wagenfolgen sind möglich, wenn die Wagen der 1. Klasse nicht getrennt werden dürfen? -> 1Klasse Wagen als ein Element Betrachten  $\frac{11!}{1!\cdot 7! \cdot 1!\cdot 2!} = 3960$
- Was ist die Wahrscheinlichkeit bei einer zufälligen Anordnung der Wagen, dass alle Wagen der 1. Klasse zusammen sind? $3960/360360=0.011$

### Geordnete Stichprobe ohne Zurücklegen
**Bsp**: In einer Urne befinden sich n = 6 verschieden farbigeSmarties. Wir ziehen 3 Mal ein Smartie, notieren die Farbe und legen es nicht zurück. Die gezogene Farbenreihenfolge ist uns wichtig.
Wie viele unterschiedliche Ziehungen gibt es?
$$\frac{n!}{(n-k)!}=\frac{6 \cdot 5\cdot 4}{(6-3)!} = 120$$
### Geordnete Stichprobe mit Zurücklegen
**Bsp** In einer Urne sind n = 6 verschieden farbige Smarties. Wir ziehen k = 3 Mal ein Smartie, notieren die Farbe und legen das Smartie jedes Mal wieder zurück. Die gezogene Farbenreihenfolge ist uns wichtig.
Wie viele unterschiedliche Ziehungen gibt es?
$$n^k=6\cdot 6\cdot6=6^3=216$$
**Bsp**: Bei einem Kombinationsschloss sind die einzelnen Einstellungen durch 3-ziffrige Zahlen mit Ziffern aus 0 bis 9 möglich. Wie viele mögliche Einstellungen gibt es?
$$10^3=1000$$
Wie gross ist die W’keit, dass jemand beim ersten Versuch die richtige Kombination findet? $$P(A)=\frac{1}{1000}$$
Wie gross ist die W’keit, dass jemand (nicht sehr  intelligent) durch 3x Probieren die Kombination findet?
Über Gegenw'keit: Ereignis: 
$A^c$ = Nach drei mal raten nicht gefunden= $999^3$ 
Anzahl mögliche Fälle = $1000^3$
$$P(A)=1-P(A^c)= 1-\frac{999^3}{1000^3}\approx 0.003$$
$$P(A)=\frac{1}{1000}+\frac{999}{1000}\cdot \frac{1}{1000}+(\frac{999}{1000})^2 \cdot \frac{1}{1000}$$
beim ersten Mal erraten + beim zweiten Mal erraten + beim dritten Mal erraten 

W'keit nach 1000 mal raten: $1-(\frac{999}{1000})^{1000}\approx 0.632$

Wie gross ist die Wahrscheinlichkeit, dass jemand (etwas intelligenter, d.h. eine probierte Kombi wird nicht wieder verwendet) durch 3x
Probieren die Kombination eines Zahlenschlosses findet?
Anzahl günstiger Fälle (3x Nicht Finden): $999 \cdot 998 \cdot 997$
Anzahl mögliche Fälle: $1000 \cdot 999 \cdot 998$
$$P(\text{in 3 mal finden})= 1-\frac{999 \cdot 998 \cdot 997}{1000 \cdot 999 \cdot 998}$$

### Ungeordnete Stichprobe ohne Zurücklegen
In einer Urne sind n = 6 verschieden farbige Smarties.
Wir ziehen k = 3 mal ein Smartie. Wie viele solcher
Auswahlen gibt es, wenn das Smartie nicht zurückgelegt wird.
Uns ist wichtig, welche Farben gezogen wurden, aber nicht in welcher Reihenfolge. D.h. Es gäbe z = 6 · 5 · 4 = 120 Ziehungsmöglichkeiten. Jedoch müssen wir
“identische” Ziehungen eliminieren.
{rot, blau, gelb} = {rot, gelb, blau} = {blau, rot,
gelb}
$$\frac{n!}{(n-k)!\cdot k!}={n \choose k} =\frac{6\cdot 5 \cdot 4}{3!}= {6 \choose 3}$$

**Bsp**
```r
choose(n=9, k=3) #84
s <- combn(x = 1:9, m = 3, simplify = FALSE) #alle Kombis auflisten

#Wahrscheinlichkeit Nr. 7 im Testset zu haben
m <- dim(s)[2] # Anzahl mögliche Fälle
g <- sum(apply(s, 2, function(x) sum(x == 7 ))) # Anzahl günstige Fälle, d.h. ob 7 in Auswahl drin ist, sum(x == 7) --> 1, wenn 7 drin ist
g/m #0.33333
```
### Ungeordnete Stichprobe mit Zurücklegen

In einer Urne sind n = 6 verschieden farbige Smarties.
Wir ziehen k = 3 Mal ein Smartie, notieren die Farbe und legen das Smartie wieder zurück. Uns ist wichtig,
welche Farben gezogen wurden, aber nicht in welcher Reihenfolge.
Wie viele unterschiedliche Ziehungsresultate gibt es?
$$\frac{(n+k-1)!}{k!(n-1)!}={n + k -1 \choose k}$$

Die Frage ist äquivalent zur Anordnung von 3 "x" auf 6 Fächer 
--> 5 "|" machen 6 fächli für die Farben --> daher kommt das -1
R G  Gl B  P   O
_ | _ | _ | _ | _ | _ |
--> Permutation von 3 "x" und 5 "|"
bsp: xx||x||| <-> 2 rote, 1 gelbes

**Bsp**: Wie viele Möglichkeiten gibt es, aus 6 Früchtesorten einen Korb mit 20 Früchten zusammenstellen? n = 6, k = 20
$${6+20-1 \choose 20} = \frac{25!}{20! \cdot 5!} = 53130$$
```r
library(partitions)
t.comb <- compositions(n = 20, m = 6)
rownames(t.comb) <- paste0("Sorte",1:6)
ncol(t.comb) # Anz. Mögl. = Anz. Spalten 53130
```
**Bps**: An einem Taxistand warten 6 Grossraumtaxis, die jeweils bis zu 7 Fahrgäste aufnehmen können. Wie viele Möglichkeiten gibt es, 5 Fahrgäste auf die Taxis aufzuteilen, wenn die Taxis, nicht jedoch die Fahrgäste unterschieden werden sollen?

## Bedingte Wahrscheinlichkeiten
 
 ### Ereignisbäume
Mehrstufige Zufallsexperimente lassen sich nicht mehr durch Abzählen von güünstigen und möglichen Fällen bestimmen. 
Bsp: Urne mit 4 roten, 3 gelben und 2 blauen Kugeln. Ziehe zwei Kugeln ohne Zurücklegen. Falls beide Kugeln dieselbe Farbe haben, dann ziehen wir noch eine Kugel. Sonst ziehen wir zwei weitere Kugeln.
→ Zusfallsexperiment mit bis zu 4 Stufen.

### Aufbau eines Ereignisbaums
- Startpunkt: Wurzel
- Zeichne je eine Kante für die Ausgänge der ersten Stufe. An jeder  Kante wird eine Wahrscheinlichkeit notiert.
- Jeder Knoten der ersten Stufe ist entweder ein Endknoten/ Blatt oder läuft weiter zum Ausgang der 2. Stufe.
- Der Baum wird erweitert bis alle möglichen Teilausgänge aufgetragen sind.
- Die Wahrscheinlichkeit eines Endknoten ist das Produkt der W'keiten entlang des Pfades.
- Endwahrscheinlichkeiten aller Blätter addieren sich zu 1.
Ein Pfad des Ereignisbaumes entspricht einem Elementarereignis des mehrstufigen Experiments

### Beispiel Ziegenproblem
Der Gewinn ist hinter Tor 1, 2 oder 3.
Der Kandidat wählt eine Tür.
Der Moderator öffnet eine der nicht gewählten Toren.
--> Lohnt es sich für den Kandidaten zu wechseln?
Wahrscheinlichkeit zu Gewinnen, wenn man nie wechselt ist 1/3 weil
Immer wechseln--> Gewinnchance von 2/3. Denn wenn man zuerst falschlag und wechselt gewinnt man mit 100%. Wahrscheinlichkeit am anfang falsch zu liegen ist 2/3

### Wahrscheinlichkeit A unter Geschehnis B
**Bsp**: 
- hinter Tor 2, wenn B = Moderator Tor 1 öffnet
- A = Klausur bestehen, wenn B = intensive Vorbereitung
- A = Herzinfarkt, wenn B = Bluthochdruck
Sei A und B zwei Ereignisse mit P(B) > 0, dann ist die bedingte W'keit von A gegeben B definiert als:
$$P(A|B)=\frac{P(A \cap B)}{P(B)}$$
Man sagt Wahrscheinlichkeit von A gegeben B.
**Spezialfälle**
- $A\subset B$: $P(A|B)=\frac{P(A)}{P(B)}\ge P(A)$
- $A \cap B = \empty$:  $P(A|B)=0$
- $B\subset A$: $P(A|B)=\frac{P(B)}{P(B)}=1)$
- $P(A^c|B)=1-P(A|B)$ aber $P(A|B^c)!=1-P(A|B)$

### Multiplikationssatz 
$A \cap B=P(A|B)\cdot P(B)$
Wahrscheinlichkeit, dass A und B zusammen eintreten (“der Fall sind”), ist das Produkt der Wahrscheinlichkeit von B und der bedingten Wahrscheinlichkeit von A gegeben B.

### Satz der totalen Wahrscheinlichkeit
Sei $B_1, ..., B_k$ paarweise disjunkte Ereignisse und $B_1\cup ... \cup B_k = \Omega$
--> d.h. ein $B_i$ tritt immer ein.
--> Jedes Ergebnis von einem weiteren Ereignis A liegt genau in einem $B_i$.
$$P(A) = \sum^k_{j=1}P(A|B_j)\cdot P(B_j)$$
**Bsp**:  Bei Niederschlag beträgt die Wahrscheinlichkeit, dass ein Flugzeug pünktlich ist 50%. Bei schönem Wetter ist das Flugzeug in 90% der Fälle pünktlich. Morgen wird es mit 70% Wahrscheinlichkeit schön sein.
Wie gross ist die Wahrscheinlichkeit, dass morgen ein Flugzeug pünktlich eintreffen wird?
P(pünktlich) = P(pünktlich|schön) * p(schön) + P(pünktlich|schlecht) * p(schlecht) = 0.9 *0.7 + 0.5 * 0.3 = 0.78
--> gewichtete Wahrscheinlichkeit

### Satz von Bayes
Beschreibt die Beziehung zwischen der Umkehrung einer bedingten Wahrscheinlichkeit. Der Satz von Bayes erlaubt unterschiedliche sich gegenseitig ausschliessende Möglichkeiten Bi (Hypothesen) auf Grund von beobachteten Daten (A) zu  vergleichen.

simpel: $$P(B|A) = \frac{P(A|B)\cdot P(B)}{P(A)}$$
allgemein: $$P(A) = \sum^k_{j=1}P(A|B_j)\cdot P(B_j)$$ daraus folgt **Satz von Bayes**:
$$P(B_i|A)= \frac{P(A|B_j)\cdot P(B_i)}{\sum^k_{j=1}P(A|B_j)\cdot P(B_j)} $$

**Bsp** Ziegenproblem
1. Ereignisse beschreiben:
	- $G_i$ = Der Gewinn ist hinter Tor i
	- $M_i$ = Der Moderator **hat** Tor i geöffnet.
2.  Situation betrachten
	- Der Kandidat hat Tor 1 gewählt und der Moderator hat daraufhin das Tor 3 geöffnet.
3. Frage mit einer bedingten Wahrscheinlichkeit betrachten:
	- Wie gross ist die Wahrscheinlichkeit, dass das Auto hinter Tor 2 ist, wenn der Moderator das dritte Tor geöffnet hat? Ergo, lohnt es sich für den Kandidaten zu wechseln? 
	- $P(G_2|M_3)$
4. Formel aufstellen:
	- $P(G_2|M_3) = \frac{P(M_3|G_2)\cdot P(G_2)}{P(M_3)}$
5. Einzelne Wahrscheinlichkeiten bezüglich Situation ausrechnen und in die Formel einsetzen:
	- $P(G_1) = P(G_2) = P(G_3) = \frac{1}{3}$
	- $P(M_3|G_1) = \frac{1}{2}$
	- $P(M_3|G_2) = 1$
	- $P(M_3|G_3) = 0$
6.  $P(G_2|M_3) = \frac{P(M_3|G_2)\cdot P(G_2)}{P(M_3)} = \frac{1 \cdot \frac{1}{3}}{\frac{1}{2}} = \frac{2}{3}$

### Diagnostische Tests
**Bsp**: Aids-Test beim Blutspenden: Dazu wird das Blut mit dem ELISA-Test (Enzyme-linked-Immunosorbent Assay) auf HIV-Antikörper untersucht. Kein Test mit vernünftigem Aufwand ist perfekt, auch der ELISA-Test nicht.
Es gibt zwei verschiedenartige mögliche Fehldiagnosen:
1. **False positives**: Eine HIV **negative** Person erhält ein **positives** Resultat
2. **False negatives**: Eine HIV **positive** Person erhält ein **negatives** Resultat
Zahlen einer Studie:

|  | positives Resultat | negatives Resultat | Total |
|--|--|--|--|
| HIV positiv | 4985 | 15 | 5000 |  
| HIV negativ | 14925 | 980075 | 995000 |  
| Total | 19910 | 980090 | 1000000 |  

a) false positives: 14925
b) false negatives: 15
False negatives sind der schlimmere Fehler, Gefahr auf Weiteransteckung
### Begriffe
**Sensitivität**:  Anteil der HIV-positiven Blutproben, welche durch den ELISA-Test erkannt werden. Anteil der **true positives**
$P(ELISA^+|HIV^+) = \frac{4985}{5000} =99.7\%$

**Spezifizität**: Anteil an HIV-negativen Personen ist, die auch einen negatives Testresultat erhalten. Anteil der **true negatives**.
$P(ELISA^-|HIV^-) = \frac{980075}{995000} =98.5\%$

**Prävalenz**: Wahrscheinlichkeit, dass eine zufällig
herausgegriffene Blutspende HIV-positiv ist. Wahrscheinlichkeit eines **true oder false positive**
$P(HIV^+) = \frac{4985}{1000000} = 0.5\%$

**Satz von Bayes**: Nun ist das Testergebnis einer Blutprobe aus dem Labor gerade eingetroffen: positiv! 
Wie gross ist die Wahrscheinlichkeit, dass die Person, von der das Blut stammt, tatsächlich HIV-positiv ist?

$$P(HIV^+ | ELISA^+)=\frac{P(ELISA^+|HIV^+)\cdot P(HIV^+) }{P(ELISA^+)}$$$$=\frac{P(ELISA^+|HIV^+)\cdot P(HIV^+) }{P(ELISA^+|HIV^+)\cdot P(HIV^+)+P(ELISA^+|HIV^-)\cdot P(HIV^-)} $$$$=\frac{0.997\cdot 0.005}{0.997\cdot 0.005 + 0.015\cdot 0.995}$$$$=0.2504$$

Die Chance trotz positivem Test doch nicht HIV-Positiv zu sein, ist relativ gross (nahezu 75%). 
Solche Wahrscheinlichkeiten werden häufig (teilweise auch von Medizinern) falsch berechnet, weil unterschiedliche Wahrscheinlichkeiten verwechselt werden. So wird z.B. aus der Sensitivität von 99.7% fälschlicherweise gefolgert, dass ein positiver Test zu 99.7% bedeute, dass der Patient positiv sei. Man verwechselt die bedingten W'keiten.

## Stochastische Unabhängigkeit
Zwei Ereignisse sind stochastisch unabhängig, wenn sie sich gegenseitig **nicht** beeinflussen.
**Def.**: $$P(A \cap B)=P(A)\cdot P(B)$$
D.h. Die Wahrscheinlichkeit das Ereignis A **und** B eintreffen ist das Produkt der W'keiten der Ereignisse A und B.
Ist $P(B)>0$ aber die Ereignisse A und B sind **unabhängig**, sehen wir das B einen Einfluss auf A hat wenn wir die Ereignisse bedingt betrachten.
$$P(A|B)=\frac{P(A\cap B)}{P(B)} = \frac{P(A)\cdot P(B)}{P(B)} = P(A)$$
Dasselbe gilt analog für $P(A) > 0$.
### disjunkt ist NICHT gleich unabhängig
- Zwei Ereignisse A, B sind disjunkt, wenn A ∩ B = ∅, d.h. sie treten nicht gemeinsam auf.
- Falls P(A) > 0 und P(B) > 0 schliessen sich die Eigenschaften disjunkt und unabhängig aus. Ereignisse können nicht beide Eigenschaften gleichzeitig besitzen.

**Beweis**: 
Sind A und B disjunkt, so ist $P(A \cap B) = 0 \neq P(A) \cdot P(B)$, da $P(A) > 0$ und $P(B) > 0$. → Also **disjunkt ⇒ abhängig**.
Umgekehrt: 
Sind A und B stochastisch unabhängig ($P(A) > 0$ und $P(B) > 0$), dann $P(A \cap B) = P(A) \cdot P(B) > 0$, d.h. $P(A \cap B) \neq 0$
(stochastisch unabhängig ⇒ nicht disjunkt)

### Stochastische Unabhängigkeit >2 Ereignisse
Mehr als zwei Ereignisse $A_1, ..., A_k$ heissen stochastisch unabhängig, wenn für jede Auswahl von Ereignissen $A_{i_1},..., A_{i_j}$ gilt:
$$P(A_{i_1}\cap ... \cap A_{i_j})=P(A_{i_1})\cdot ...\cdot P(A_{i_j})$$
Die Formel impliziert unter anderem, dass jedes **Paar** von Ereignissen $A_i$ und $A_j$ unabhängig sein muss.
**Aber** auch wenn mehrere Ereignisse paarweise unabhängig sind, heisst das **nicht** das alle Ereignisse zusammen stochastisch unabhängig sind. Schlussfolgerung ist geht **nicht** in beide Richtungen.

## Wahrscheinlichkeitsverteilungen
Grundfragestellung: Wie verteilen sich bei einem Zufallsexperiment die W'keiten auf die verschiedenen Ergebnisse?
Bsp:
- Würfelwurf bei physikalischen Modellen
- Passagiere bei datengestützen Modellen
- atomarer Störfall bei subjektiven Modellen
**Mischform Modell & empirisch geschätze Parameter**

### Definition W'keitsmodell
Ein Modell für den Zufall, dessen W'keiten sich immer auf **künftige** oder **unbekannte** Ereignisse beziehen. 
Ziel: Ein Ergebnis eines Zufallsexperiments soll dur eine einzelne Zahl beschrieben werden.

### Definition Zufallsvariable
Eine Grösse, die unter **bestimmten, konstanten Bedingungen** unterschiedliche, durch den Zufall bedingte Zahlenwerte annehmen kann, nennt man Zufallsvariable
Mathematisch ist es eine Funktion $X: \Omega \mapsto \mathbb{R}$, die jedem Element des Ereignisraumes eine Zahl zuordnet.
Es ist demnach eine Quantifizierung des Zufallsexperiments mit Raum $\Omega$.

**X heisst Zufallsgrösse oder Zufallsvariable, weil die Werte, die X annehmen kann, vom Zufall abhängig sind (bzw. nicht deterministisch sind).**

### diskrete Zufallsvariablen
- X nimmt endlich oder unendlich abzählbare viele Werte an
- Überall wo gezählt wird: Anzahl Kunden, Fahrzeuge Unfälle etc.
### stetige Zufallsvariablen
- X kann jeden beliebigen Wert eines Intervalls annehmen
- Überall wo gemessen wird: Länge, Gewicht, Temperatur

### Definition W'keitsverteilung
Die Wahrscheinlichkeitsverteilung gibt an, welche Werte eine Zufallsvariable mit welcher Wahrscheinlichkeit annimmt.

Je nach Ausprägung der Zufallsvariablen gibt es disrekte oder stetige W'keitsverteilungen

### diskrete W'keitsverteilung
Die Wahrscheinlichkeitsfunktion einer diskreten Zufallsvariable gibt zu jedem möglichen Wert (Realisierung) $x_i$ die entsprechende Wahrscheinlichkeit $p_i$ an.
|X| $x_1$  $x_2$ $...$ $x_N$|
|--|--|
| $p(\cdot)$ | $p_1$  $p_2$ $...$ $p_N$ |

**Bmk.**
- Die Summe aller $p_i$ ist gleich 1
- Die Wahrscheinlichkeitsfunktion heisst **diskrete Gleichverteilung**, wenn alle $p_i$ gleich sind.
	- **Bsp**
Beim Würfeln hat X = "gewürfelte Augenzahl" eine diskrete Gleichverteilung $p_i = \frac{1}{6}$

### kumulative Verteilungsfunktion (diskreter) W'keitsverteilungen
$$F(x) = P(X \leq x)$$
Die kumulative Verteilungsfunktion gibt die Wahrscheinlichkeit an, mit welcher die Zufallsvariable X einen Wert annimmt, der kleiner oder gleich einem vorgegebenen Wert ist.
**Eigenschaften**
- $F(-\infty) = 0$ und $F(\infty) = 1$
- Eine kumulative Verteilungsfunktion ist monoton wachsend, d.h. für $u \lt v$ gilt $F (u) ≤ F (v )$.
- Für diskrete Zufallsvariablen ist F(x) eine Treppenfunktion.

### Erwartungswert
Der Erwartungswert $E [X ]$ einer Zufallsvariable $X$ ist das, was man “im Schnitt” bei unendlich vielen Realisierungen von $X$ erhält. Er ist ein **Lagemass**
des Wahrscheinlichkeitsmodells.







<!--stackedit_data:
eyJoaXN0b3J5IjpbNzcyNjE2NzIsLTgyNzYyMDY5OCwxOTE1MT
UwNDcsOTk5ODU5MTEsLTI1Nzc5OTE2OCwtMTI1NDM0MTk3MCwt
MTI3NDIwMzUyMSw0MzU3MTg0MjQsLTgyMTI1NDI4Miw2ODIyOD
A0MDMsLTM1ODIzNzEyNywtMTgxMzU4NDY4NiwtMjIwNzc2NTY1
LDYyMDY0NjU5MiwtNjU4NjkwOTk4LC0xNzA5NzE4MjExLC0yMD
MwMzA3NDY2LC02MDE4NjE2NDMsNzM1NDU4NDcwLC03NDI0ODQy
OTddfQ==
-->