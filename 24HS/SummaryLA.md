# Linear Algebra Summary

All definitions and formulas for all topics discussed during the lectures

## Topics
1. Vektoren

## 1. Vektoren
Vektoren sind ein mathematisches Objekt, welches geometrisch und algebraisch betrachet werden kann.

**Def. Vektor**: 
- Geometrisch ist ein Vektor ein Pfeil. Er besitzt eine *Richtung* und eine *Länge/Betrag*.
- Algebraisch ist ein Vektor ein Tupel von Zahlen (Komponenten)

$$
| \vec v | = \lvert \begin{bmatrix} v_1  \\ v_2 \\ ..\\v_n\end{bmatrix} \rvert = \sqrt{v_1^2+v_2^2+...+v_n^2}
$$

**Def. Gleichheit**
Zwei Vektoren sind:
- geometrisch gleich, wenn sie die *gleiche Richtung und Länge* haben.
- algebraisch gleich, wenn beide *gleich viele Komponenten* haben und diese *alle identisch* sind.
$$
\vec v = \vec u  \Rightarrow \begin{bmatrix} v_1  \\ v_2 \\ ..\\v_n\end{bmatrix} = \begin{bmatrix} u_1  \\ u_2 \\ ..\\u_n\end{bmatrix}
$$

### 1.1 Operationen
**Def. Nullvektor**
$$
\vec 0 = \begin{bmatrix} 0  \\ 0 \\ ..\\0\end{bmatrix} 
$$
Geometrisch hat der Nullvektor weder Länge noch Richtung. 
**Def. Gegenvektor**
$$
-\vec v = (-1) \vec v
$$
**Def. Addition**
$$
\vec v + \vec u = \begin{bmatrix} v_1  \\ v_2 \\ ..\\v_n\end{bmatrix} + \begin{bmatrix} u_1  \\ u_2 \\ ..\\u_n\end{bmatrix} = \begin{bmatrix} v_1 + u1 \\ v_2 + u_2 \\ ..\\v_n + u_n\end{bmatrix} 
$$

**Def. Subtraktion**
$$
\vec v - \vec u = \begin{bmatrix} v_1  \\ v_2 \\ ..\\v_n\end{bmatrix} - \begin{bmatrix} u_1  \\ u_2 \\ ..\\u_n\end{bmatrix} = \begin{bmatrix} v_1 - u1 \\ v_2 - u_2 \\ ..\\v_n - u_n\end{bmatrix} 
$$
**Def. Skalarmultiplikation**
$$
\alpha  \vec{v} = \alpha \begin{bmatrix} v_1  \\ v_2 \\ ..\\v_n\end{bmatrix} = \begin{bmatrix} \alpha v_1  \\ \alpha v_2 \\ ..\\\alpha v_n\end{bmatrix} 
$$

Die Grundrechenregeln von Vektoren sind kommutativ und assoziativ.

$$
( \vec u + \vec v ) + \vec w = (\vec u + (\vec v  + \vec w) 
$$ $$
  \vec u + \vec v  = \vec v +\vec u
$$ $$
 \vec u + \vec 0 =  \vec 0 + \vec u = \vec u
$$ $$
\vec v + (- \vec v ) =  (- \vec v )+ \vec v = \vec 0
$$ $$

$$ $$

$$
**Def. /Eigenschaft Kollinearität**
- Zwei Vektoren *heissen* kollinear, wenn ihre Pfeile parallel verlaufen. 
-  Zwei Vektoren *sind* kollinear, wenn sie gleiche oder entgegengesetzte Richtung ha-
ben oder ein Vielfaches voneinander sind.

**Def. Linearkombination (LK)**

**Def. Skalarprodukt**
$$
< \vec v, \vec u > = \vec u \cdot \vec v = \begin{bmatrix} v_1  \\ v_2 \\ ..\\v_n\end{bmatrix} \cdot \begin{bmatrix} u_1  \\ u_2 \\ ..\\u_n\end{bmatrix} = v_1 u_1 + v_2 u_2 + ... + v_n u_n
$$

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTY0MzU4ODk2MF19
-->