
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
Mathematisch ist es eine **Funktion** $X: \Omega \mapsto \mathbb{R}$, die jedem Element des Ereignisraumes eine Zahl zuordnet.
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

### Erwartungswert für eine diskrete Zufallsvariable X
$$\mu = E[X] = \Sigma^{\inf}_{i=1}x_i \cdot p_i = \Sigma^{\inf}_{i=1}x_i \cdot P(X=x_i)$$

**Bsp** Würfeln $E[X ] = \frac{1}{6} · 1 + \frac{1}{6} · 2 + \frac{1}{6} · 3 + \frac{1}{6} · 4 + \frac{1}{6} · 5 + \frac{1}{6} · 6 = 3.5$

**Bsp** AB 5.1 $E[X] = 0.3 \cdot 4 + 0.1 \cdot -6 + 0.6 \cdot -1 = 1.2-0.6-0.6 =0$

### Varianz
Die Varianz $Var (X )$ ist ein Streuungsmass einer Zufallsvariablen und gibt an, wie breit die angenommenen Werte des Wahrscheinlichkeitsmodells streuen.

**Varianz für diskrete Zufallsvariable**
$$Var(X) = E[(X- E[X])^2] = E[X^2]-E[X]^2$$
$$$$

**Bsp** Würfeln 
$E[X^2]=\frac{1}{6}\cdot 1^2 +\frac{1}{6}\cdot 3^2+\frac{1}{6}\cdot 4^2+\frac{1}{6}\cdot 5^2+\frac{1}{6}\cdot 6^2=15.17$
$E[X^2]-E[X]^2=15.17-3.5^2=2.92$

# Diskrete W'keitsverteilungen

## Bernoulli Verteilung X ~ Bernoulli(_p)
Ein Bernoulli-Zufallsexperiment ist ein Experiment mit zwei möglichen Ausgängen:
Erfolg (Ja = 1) und Misserfolg (Nein = 0).
|$X$| $x_1=0$ | $x_2=1$ |
|--|--|--|
| $p(\cdot)$ | $1-p$| $p$ |

p= P(X=1) ist die Erfolgswahrscheinlichkeit

**Bsp**
-Werfen einer Münze
- Würfeln eines Sechsers
- Bestehen einer Prüfung
- Ein Swiss-Flug ist pünktlich

### Kennwerte
Erwartungswert $E[X]= p$
Varianz $Var(X)= p\cdot (1-p)$

**Anpassung der Verteilung**:
Den Parameter p lässt sich aus vergangenen Daten schätzen.
**Bsp**: Ein Swiss-Flug ist pünktlich:
Im Jahr 2018 waren 109’748 von 140’074 Flügen pünktlich:
$$p = \frac{109748}{140074}=0.7835$$

### Mehrstufige Bernoulli Experimente
**Bsp**. Galton-Brett

## Binomialverteilung N ~ Bin(n,p)
Def.: n unabhängige Bernoulli Experimente mit jeweils konstanter Erfolgswahrscheinlichkeit p, die n-mal nacheinander ausgeführt wurden.
Anzahl Erfolge: $$P(X=k) = {n \choose k}\cdot p^k(1-p)^{n-k}$$
(n und p sind fix gegeben)
$p^k(1-p)^{n-k}$ = Wahrscheinlichkeit für ein Ereignis mit k Erfolgen und n − k Misserfolgen.
${n \choose k}$ =  Anzahl Ereignisse mit k Erfolgen in n Versuchen

```r
dbinom(x = 15, size = 20, prob = 0.684)

#Ganze Verteilung plotten
k <- 0:22
pk <- dbinom(x = 0:22, size = 22, prob = 28/34)
plot(k, pk, type = "h",main = "Bin(n=20, p=0.684)")
```

### Eigenschaften
- Der **Ergebnisraum** einer binomialverteilten Zufallsvariable ist **endlich**
- Eine binomialverteilte Zufallsgrösse kann auch als **Summe S von $n$ unabhängigen Wiederholungen einer bernouilliverteilte Zufallsgrösse $X_i$** mit Parameter p beschrieben werden, d.h. $$S = \Sigma^{n}_{i=1}X_i$$
- Erwartungswert $E[S] = n\cdot p$
- Varianz: $Var(S) = n\cdot p\cdot (1-p)$
- Symmetrische Verteilung bei wachsendem n, Falls np(1 − p) > 10, gilt Bin(n,p) als symmetrisch

### kumulative Verteilung der Binomial Verteilung
 $$F(x)=P(X \le x)= \Sigma _{k=0}^x {n \choose k}\cdot p^k(1-p)^{n-k}$$
```r
pbinom(x, size = n, prob = p)
```
### Quantile
Umkehrfunktion der kumulativen Verteilungsfunktion

```r
qbinom(alpha/bsp 0.25, size = n, prob = p)
```
## Geometrische Verteilung
Bsp: Eile mit Weile
Um das Haus zu verlassen, muss eine 5 gewürfelt
werden. X = “Anzahl Fehlwürfe, bis man das Haus
verlassen kann.”

P(0) = $\frac{1}{6}$
P(1) = $\frac{5}{6}\cdot \frac{1}{6}$
P(2) = $(\frac{5}{6})^2 \cdot \frac{1}{6}$
P(k) = $(\frac{5}{6})^k \cdot \frac{1}{6}$

### Definition
Führen wir ein Bernoulli-Experiment mit Erfolgswahrscheinlichkeit p genauso lange durch, bis wir den ersten Erfolg erzielen (also nicht mit einer
vorgegebene Anzahl Wiederholungen wie im Falle der Binomialverteilung), erhalten wir die geometrische Verteilung

Die Anzahl **Fehlversuche** vor dem **ersten** Erfolg X hat dann die Verteilung
$$P(X=k)=p\cdot (1-p)^k$$

### Eigenschaften
- $E(X) = \frac{(1-p)}{p}$
- $Var(X) = \frac{(1-p)}{p^2}$
- Achtung: In vielen Büchern findet man eine etwas andere Definition, bei der nicht die Anzahl der Misserfolge bis zum ersten Erfolg, sondern die Anzahl der Versuche (einschliesslich des ersten Erfolgs) gezählt werden. Die Zufallsvariable ist dann um 1 verschoben, und die Formeln sind leicht anders. Achten Sie immer darauf, welche Definition verwendet wird!
- Verteilung ist monoton abfallend, je grösser p desto abfallender
- $P(X > k+j | X \ge k) = P(X > j)$
	- geometrische Gedächtnislosigkeit
	- **Gedächtnislosigkeit**, d.h. Wahrscheinlichkeit dafür, dass der **erste Erfolg noch mindestens j weitere Fehlversuche lang auf sich warten lässt**, ist unabhängig davon, wie viele Misserfolge man schon beobachtet hat.

```r
dgeom(k, prob = p)
```

### kumulative Verteilung der geom. Verteilung
 $$F(x)=P(X \le x)= \Sigma _{k=0}^K  p\cdot (1-p)^{k} = 1-(1-p)^{K+1}$$

```r
pgeom(x, prob=p)
qgeom(alpha, prob = 1/6) #quantile
rgeom(1, prob = 1/6) #Erzeugen einer Zufallszahl in dieser Simulation Eile mit Weilegab es 2 Fehlwürfe
```

## Negative Binomialverteilung X ∼ NBin(r , p)
Die Anzahl der Misserfolge vor dem r-ten Erfolg, wobei die Erfolgswahrscheinlichkeit p konstant sei
$$P(X = k) = {k + r -1 \choose k}p^r (1-p)^k$$

- Serie der Experimente wird beim Eintritt des r-ten Erfolg abgebrochen
- bei k Fehlversuchen gab es Gesamthaft k+r Versuche
- Binomialkoeffizient gibt die Anzahl Möglichkeiten die ersten r-1 Erfolge und die k Fehlversuche anzuordnen
- Jede Anordnung hat die Wahrscheinlichkeit $p^{r−1}(1 − p)^k$ , die wir dann mit p multiplizieren müssen, da im k+r Versuch der r-te Erfolg auftreten soll.

### Eigenschaften
- Ergebnisraum ist unendlich abzählbar 
- $E(X)= \frac{r \cdot (1-p)}{p}$
- $Var(X) = \frac{r \cdot (1-p)}{p^2 }$$
- Wenn Y ~ Geom(p) dann ist Y ~ NBin(1, p)

```r
dnbinom(x = , size = r, prob = p) # Wahrscheinlichkeitsfunktion
pnbinom(q = , size = r, prob = p) # Kum. Verteilungsfunktion
qnbinom(p = , size = r, prob = p) # Quantilfunktion
rnbinom(n = , size = r, prob = p) # Zufallszahlen
```

## Hypergeometrische Verteilung X ~ Hyp(m,n,k)
Bsp: Wenn wir k Kugeln aus einer Urne mit m weissen und n schwarzen Kugeln ziehen, und wir nach jedem Zug die gezogene Kugel wieder in die Urne legen , dann gilt für die Anzahl X der weissen gezogenen Kugeln X ~ Bin($k, \frac{m}{n+m}$). Was ist, wenn wir die Kugeln **nicht** zurücklegen? Fall der Hypergeometrischen Verteilung

### Definition
Ziehen ohne Zurücklegen von k Kugeln aus einer Urne mit m weissen und n schwarzen Kugeln, wobei die Zufallsvariable die Anzahl Erfolge in k Versuchen ist

$$P(X=j)=P(A_j) = \frac{|A_j|}{|\Omega|}= \frac{{m \choose j}{n \choose k-j}}{{n+m \choose k}}$$

### Eigenschaften
- Ergebnisraum ist unendlich abzählbar
- $E(X)=k\cdot \frac{m}{m+n}$
- $Var(X) = k\cdot \frac{m}{m+n}\cdot (1-\frac{m}{m+n}\cdot \frac{n+m-k}{m+n-1}$
```r
dhyper(x = , m = m, n = n, k = k) # Wahrscheinlichkeitsfunktion
phyper(q = , m = m, n = n, k = k) # Kum. Verteilungsfunktion
qhyper(p = , m = m, n = n, k = k) # Quantilfunktion
rhyper(n = , m = m, n = n, k = k) # Zufallszahlen
```
Bsp. : In einer Lieferung von 1000 Schrauben sind 27 defekt. Der Empfänger überprüft 30 zufällig ausgewählte Schrauben.
m = 27
n = 1000-27 = 973
k = 30
X ~ Hyp(27, 973, 30)
Mit welcher Wahrscheinlichkeit sind die Schrauben in der Stichprobe alle in Ordnung?
```
dhyper(0, 27, 973, 30)
```

## Poisson Verteilung X ~ Pois($\lambda$)
Für Vorfälle, die im Laufe der Zeit eintreten und sich an einem bestimmten Ort ereignen.
X = Anzahl Ereignisse pro Zeiteinheit/Gebiet
Bsp:
- Unfälle in einer Fabrik, auf Strassen, oder anderswo pro Jahr
- Defekte in Geräten, an Fahr- oder Flugzeugen pro Woche
- Das Eintreffen von Kunden an einem Schalter in einer Stunde

$$P(X=k)=\frac{\lambda ^k e^{(-\lambda)}}{k!}$$
### Parameter $\lambda$
Die Rate mit welcher die Ereignisse, in vorgegebener Zeiteinheit und/oder Gebiet eintreffen
### Eigenschaften
- Ergebnisraum ist abzählbar unendlich ohne klar definierte Obergrenze
- $E(x) = \lambda$  innerhalb einer Zeit und/oder Flächen-Einheit λ Ereignissezu erwarten
- $Var(x) = \lambda$
- Für kleine λ stark rechtsschief.
-  Je grösser λ, desto symmetrischer. Generell gute Symmetrie ab λ > 10
- Verteilungsfunktion $F(x) = P(X \le x)= \Sigma^x_{k=0}\frac{\lambda ^k e^{(-\lambda)}}{k!}$

**Bsp**:
- Wenn X die Anzahl tödliche Verkehrsunfälle pro Jahr in der Schweiz beschreibt, so gilt bei durchschnittlich 230 tödlichen Unfällen
X ∼ Pois(230).
2) Wenn X die Anzahl Kunden am Postschalter pro Stunde beschreibt, so gilt bei durschnittlich 32 Kunden pro Stunde 
X ∼ Pois(32)

```r
dpois(k, lambda = lambda)
ppois(x, lambda = lambda) #Verteilugnsfunktion
qpois(alpha, lambda)
rpois(n-simulationen, lambda)
#Wie gross ist die Wahrscheinlichkeit, dass in einer Stunde zwischen 30 und 35 Kunden am Postschalter eintreffen?
sum(dpois(30:35, lambda = 32))
#Welche Kundenanzahl (weniger oder gleich viel) treffen mit 10% Wahrscheinlichkeit in einer Stunde am Postschalter ein?
qpois(0.1, lambda = 32)
```
**Bmk**:
Was passiert mit der Binominal Verteilung wenn $n \rarr \infty$ und $p \rarr 0$
-Erwartungswert bleibt konstant $E(X) = n\cdot p = \lambda$
$$\lim_{n \rarr \infty} P(X=k) = \frac{\lambda ^k e^{(-\lambda)}}{k!}$$

## Binominal vs. Poisson
| Binominal | Poisson |
|--|--|
| bekannte Anzahl von n Einzelversuchen, d.h. Wertebereich von X: {0, .., n} | Grösse der Population ist unbekannt, keine deinierte Obergrenze |
| Erfolgswahrscheinlichkeit p für den Einzelnversuch | Rata $\llambda$, mit welcher das Ereignis auftritt |

- Anzahl Wahlberechtigter, die bei einer Umfrage unter 5000 Personen eine Gesetzesvorlage befürworten. (Bin)
- Anzahl Schadensfälle einer Versicherung pro Jahr. (Poi)
- Anzahl Kunden, die einen Kredit beantragen pro Jahr (Poi).
- Anzahl Fahrzeuge, die bei einer Kontrolle von 100 angehaltenen Fahrzeugen beanstandet werden müssen. (Bin)

# Stetige Wahrscheinlichkeitsverteilung

**Stetige Zufallsvariable**:
- X kann jeden **beliebigen Wert** einer Intervalls annehmen
- Anwendung überall dort, wo gemessen wird

**Stetige Wahrscheinlichkeitsverteilung**
- nicht möglich einzelnen Ergebnissen eine W'keit zuzordnen, es geht nur noch **W'keiten für Intervalle**
- Anstatt einer Wahrscheinlichkeitsfunktion p(x) gibt es eine **Dichtefunktion $f_X(x)$**
	- Fläche unter der Wahrscheinlichkeitsdichte beträgt  $\int^\infty_{-\infty} f_X(x) dx = 1$
	- Diese Dichten beschreiben die Verteilung unendlicher Ergebnisse
	- Werte von $f_X(x)$ sind **keine** W'keiten sondern W'keitendichten! 
	- $f_X(x)$ beschreibt die Form der Verteilung der ZV X
	- Wenn X als stetig gilt, dann ist P(X=c) = 0 für ein beliebiges c im Intervall von X
	- $f_X(x) \ge 0$ kann Werte grösser als 1 annehmen, nimmt aber keine negative Werte an
	- $f_X(x)$ ist stückweise stetig

**Bsp**:
Sei X die Abweichung in cl beim Abfüllen einer 33cl Flasche.
Wir nehmen an, dass X die folgende Dichte hat:
$$
f(x) = \begin{cases}
-\frac{3}{4}x^2 + \frac{3}{4} & \text{für } -1 \leq x \leq 1 \\
0 & \text{sonst}
\end{cases}
$$
Frage: Ist f(x) wirklich eine Dichte?
- Der Wertebereich von f ist grösser gleich 0
- Funktion is stückweise stetig
- Fläche im Intervall [-1, 1] ist gleich 1

### Wahrscheinlichkeiten über bestimmte Bereiche
Wahrscheinlichkeiten werden als Integrale über bestimmte Bereiche berechnet:
$$P(a \le X\le b)= \int^b_{a} f_X(x) dx$$
Für stetige Zufallsvariablen gilt:
$P(a \le X\le b)=$
$P(a \lt X\le b)=$
$P(a \le X\lt b)=$
$P(a \lt X\lt b)$

### Kumulative Verteilungsfunktion
$$F_X(x)= P(X \le x)=\int^x_{-\infty}f_X(z) dz$$

**Eigenschaften**:
- Verteilungsfunktion ist für stetige Verteilungen stetig.
- Die Dichtefunktion f(x) ergibt sich als Ableitung der Verteilungsfunktion F (in allen Punkten in denen diese
differenzierbar ist):
$$f_X(x) = F_X'(x) = \frac{d}{dx}F_X(x)$$

**Bsp Flasche**:
$$F_X(x) = P(X \le x)=\int^x_{-\infty}f_X(z) d$$
$$
F(x) = \begin{cases}
0 & \text{falls } x < -1 \\
\int_{-1}^{x} \left( -\frac{3}{4}z^2 + \frac{3}{4} \right) \, dz & \text{falls } -1 \leq x \leq 1 \\
1 & \text{falls } x > 1
\end{cases}
$$
$$
F(x) = \begin{cases}
0 & \text{falls } x < -1 \\
\frac{1}{4}(-x^3+3x+2) & \text{falls } -1 \leq x \leq 1 \\
1 & \text{falls } x > 1
\end{cases}
$$

### Erwartungswert von $f_X(x)$
Der Erwartungswert für stetige Zufallsvariablen entspricht dem, *was man im Schnitt, bei unendlich vielen Realisierungen, erhalten würde*.
Er ist ein **Lagemass** für die Zufallsvariable und entspricht geometrisch dem **Schwerpunkt (in x-Richtung)** der Wahrscheinlichkeitsdichte.
$$\mu = E(X) = \int_{-\infty}^\infty x\cdot f_X(x) dx$$
(Im Vergleich zum diskreten Fall wurde die Summe durch ein Integral und die Wahrscheinlichkeitsfunktion p(x ) durch die Dichte f (x ) ersetzt.)

### Varianz von $f_X(x)$
Die varianz ist ein **Streuungsmass** einer Zufallsvariablen. Sie gibt die erwartete quadratische Abweichung der Zufallsvariable X von ihrem Erwartungswert an, d.h. es wird **durch die Breite der Verteilung** bestimmt.

Sei X eine stetige Zufallsvariable mit Dichtefunktion f (x ) und Erwartungswert E (X ) = µ. Dann ist die Varianz definiert als
$$Var(X)= E((X-E(X))^2)= \int_{-\infty}^\infty (x-\mu)^2\cdot f_X(x) dx$$
Alternativ:
$$Var(X)= E(X^2)-(E(X))^2$$
mit $E(X^2)\int_{-\infty}^\infty x^2\cdot f_X(x) dx$

### Median F(x) = 0.5
### Modus $max(f_X(x))$

## Uniformverteilung X~Unif([a,b])
Bei der Uniformverteilung (auch stetige Gleichverteilung) treten alle Werte gleich oft ein. 
- Dichtefunktion 
$$
f(x) = \begin{cases}
0 & \text{falls } x < a \\
\frac{1}{b-a} & \text{falls } a \leq x \leq b \\
0 & \text{falls } x > b
\end{cases}
$$
- Verteilungsfunktion
$$
F(x) = \begin{cases}
0 & \text{falls } x < a \\
\frac{x-a}{b-a} & \text{falls } a \leq x \leq b \\
1 & \text{falls } x > b
\end{cases}
$$
- Erwartungswert $E(X) = \frac{a+b}{2}$
- Varianz $Var(X) = \frac{(b-a)^2}{12}$

```r
dunif(x, min=a, max=b)
#P(X <= x)
punif(q=x, min=a, max=b)
#P(x<=X<=y)
punif(q=y, min=a, max=b) - punif(q=x, min=a, max=b)
#P(X > x )
1 - punif(q = x, min = a, max = b)
#quantile
qunif(p = alpha, min = a, max = b)
#simulation
runif(n= n, min = a, max = b)
```
**Beispiele**
- Regen fällt auf einen 100cm langen Randstein. Der Ort des Aufpralls X ∼ Unif([0,100])
- Rundungsfehler bei der Zeugnisnote, d.h. wenn man auf halbe Noten genau rundet. Z = “Rundungsfehler.” Y ∼ Unif([-0.25,0.25])
- X = Wartezeit auf den Bus, welcher exakt alle 8 Minuten fährt. Intuitiv kann man sich überlegen, dass jede Wartezeit im Intervall [0,8] gleich häufig auftritt, wenn man zufällig an die Haltestelle kommt. Damit hat X eine Uniformverteilung: X ∼ Unif([0,8])

## Exponentialverteilung X~Exp($\lambda$)
**einleitendes Beispiel**: An einem Schalter (z.B. in der Bahnhof-Apotheke in Winterhur) treffen im langfristigen Schnitt 3.6 Personen pro Minute ein.
X = “Anzahl eintreffender Personen pro Minute” kann mit Pois(λ = 3.6)
modelliert werden.
**Gesucht: Y = “Zeitdauer bis nächste Person eintrifft”**
Y ist eine stetige Zufallsvariable mit stetiger Verteilung.

Wartezeit simulieren:  Eintreffen von Kunden (Pois(λ = 3.6)) in einer kleinen Zeiteinheit von 0.1 s, s.d. nie 2 Kunden gleichzeitig eintreffen.  
```r
set.seed(11)
n <- 20*60*10 # 20 Minuten in 0.1s
lambda <- 3.6/600 # umgerechnet auf 0.1s
# Kunden pro Zehntelsekunde
Kunden <- rpois(n, lambda = lambda)
plot(1:n, Kunden, type = "h")

# Wartezeit in Minuten
Wartezeiten <- diff((1:n)[Kunden > 0])/600
head(round(Wartezeiten,2))
[1] 0.11 0.07 0.19 0.36 0.11 0.36
hist(Wartezeiten, freq = FALSE)
```

### Definition
geeignetes Modell für Wartezeiten zwischen dem unabhängigen Eintreffen von Ereignissen.
- Dichtefunktion mit Wertebereich [0,$\infty$[$$
f(x) = \begin{cases}
\lambda e^{-\lambda x} & \text{falls } x \geq 0 \\
0 & \text{falls } x \lt 0 
\end{cases}
$$
- Je grösser $\lambda$ desto grösser ist der Abfall der exponentiellen Kurve
- Verteilungsfunktion $$F(x) = P(X\leq x) = \begin{cases}
1- e^{-\lambda x} & \text{falls } x \geq 0 \\
0 & \text{falls } x \lt 0 
\end{cases}
$$
- Erwartungswert $E(X)=\frac{1}{\lambda}$
- Varianz$Var(X)=\frac{1}{\lambda ^2}$
- Gedächtnislosigkeit auf, d.h. das Eintreffen des letzten Kunden hat keinen Einfluss auf das Eintreffen aller folgenden Kunden.
```r
dexp(x = x, rate = lambda)
# P(X ≤ x )
pexp(q = x, rate = lambda)
# P(x ≤ X ≤ y ) :
pexp(q = y, rate= lambda) - pexp(q= x, rate= lambda)
# P(X > x ) :
1 - pexp(q = x, rate = lambda)
# Quantile
qexp(p = alpha, rate = lambda)
# Simulation
 rexp(n = n, rate = lambda)
```

## Weibullverteilung X ~ Weibull($\beta$, $\lambda$)
Die Weibullverteilung  ist eine Erweiterung der Exponentialverteilung, die den Betrachtungszeitpunkt berücksichtig und daher gedächntnisbehaftet ist.
Oft verwendet für verbleibende Lebensdauern oder Fehlerraten über Zeit

###Eigenschaften
- Dichtefunktion $$f(x) = \begin{cases}
\lambda \cdot \beta \cdot (\lambda \cdot x)^{(\beta -1)} \cdot e^{-(\lambda x)^\beta} & \text{falls } x \geq 0 \\
0 & \text{falls } x \lt 0 
\end{cases}$$
- $\beta$ ist der Formparameter
	- $\beta \lt 1$: Fehlerrate abnehmend
	- $\beta = 1$: Fehlerrate konstant
	- $\beta \gt 1$: Fehlerrate zunehmend
- NICHT gedächtnislos, Zeitfaktor spielt eine Rolle
	- W’keit, dass ein Handy noch 1 Jahr funktioniert ist bei Occasion Handys (>2Jahrealt) kleiner als bei neuen Handys (>1 Monat alt).
	- W’keit, dass ein Kartenhaus die nächsten 10 Sekunden hält ist bei Kartenhäusern, die bereits 15 Sekunden stehen (> 15 Sekunden) grösser als bei Kartenhäusern, die eben erstellt wurden (> 0.5 Sekunden).
- Verteilungsfunktion: $$F(x) = \begin{cases}
1- e^{-(\lambda x)^\beta} & \text{falls } x \geq 0 \\
0 & \text{falls } x \lt 0 
\end{cases}$$
- Erwartungswert: $$E(X) = \frac{1}{\lambda}\Gamma(1 + \frac{1}{\beta})$$
- Varianz: $$Var(X)= \frac{1}{\lambda^2}[\Gamma(1 + \frac{2}{\beta})-\Gamma^2(1 + \frac{1}{\beta})]$$	
- Modus der Dichtefunktion ist um den Wert $\lambda herum$

### Exkurs Gammafunktion
Die Gammafunktion ist eine Verallgemeinerung der Fakultät für reelle Zahlen. Sie ist für $\alpha > 0$ definiert als: $$\Gamma(\alpha)=\int_0^\infty t^{\alpha-1}e^{-t}dt$$

**Eigenschaften**:
- $\Gamma(\alpha)=(\alpha -1)\Gamma(\alpha-1)$
- für $\alpha = 1$ $\Gamma(1) = 1$
- Für $n\in \N$ gilt: $\Gamma(n)=(n-1)!$

### Beispiel Weibull
Wir betrachten eine Population von Geräten, deren mittlere Lebensdauer bekannt sei, nämlich 3 Jahre. Je nachdem, ob die Population eher durch Geräte mit Kinderkrankheiten (β < 1) oder Geräte mit Alterserscheinungen (β > 1) charakterisiert ist, sieht die Verteilung der Lebenszeiten der Geräte in dieser Population unterschiedlich aus.
Die mittlere Lebensdauer einer Weibull-Verteilten Population ist (1/λ)Gamma(1 + 1/β).
```r
# Erwartungswert der Weibull-Verteilung
expected_val <- 3

# Raster von shapes: von "hält länger, je länger schon gehalten" (beta <1) zu
# "hält weniger lang, je länger schon gehalten" (beta >1). Wir erstellen ein
# exponential-verteiltes beta-Raster
beta_vec <- c(0.4, 1, 7)

# Definiere scale (=1/lambda) so, dass der Erwartungswert der Weibull-Verteilung =
# `expected_val` ist
scale_vec <- expected_val / gamma(1 + 1/beta_vec)

# Berechnung der Dichten
x <- seq(0,10,.05)
# Hier werden die theoretischen Dichteverteilungen abgelegt
pdf <- matrix(NA, nrow = length(beta_vec), ncol = length(x))
for (i in 1:length(beta_vec)){
pdf[i,] <- dweibull(x, shape = beta_vec[i], scale = scale_vec[i])
```

```r
# scale = 1/lambda,
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTgzNjg0OTAzNCwtODQ3NjU4NTMzLDYwMz
gxNTkxLC02NDE1NzMyNSwtMTkwNzkzMjM5MSwxOTI1NzA2NDYs
LTE0NDUzMTAzODYsMTk0NTIxMTQ4OSw5OTg5OTM0NjIsMTI1Mz
c2NTUxLC0xMDUyNjMzNjc0LDU2MDkzMzUxOSwtMTYyMjA4NzUz
OSw1NzEwMjMxMDIsMzY1NjU3Mjk4LDEyMDM4NzczMzksMTI0ND
IxNjI0MCwxNTQzMjM4NzA2LDE4OTIyMDg0MSwtNDU1Mjk0ODgw
XX0=
-->