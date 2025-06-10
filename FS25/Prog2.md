### Numpy 
**Erzeugung**
```python
import numpy as np

a = np.array([1, 2, 3])           # 1D Array
b = np.array([[1, 2], [3, 4]])    # 2D Array
```
**Attribute**
```python
a.shape      # (3,) – Form (Dimensionen)
a.ndim       # 1 – Anzahl der Dimensionen
a.size       # 3 – Anzahl der Elemente
a.dtype      # dtype('int64') – Datentyp
a.itemsize   # z.B. 8 – Byte pro Element
a.T          # Transponiert (nur bei 2D+ sinnvoll)
```
**Arrays erzeugen**
```python
np.zeros((2, 3))        # Array mit Nullen
np.ones((2, 3))         # Array mit Einsen
np.full((2, 3), 7)      # Array mit einer Konstante
np.eye(3)               # Einheitsmatrix
np.arange(0, 10, 2)     # Wie range()
np.linspace(0, 1, 5)    # Gleichmäßig verteilte Werte
np.random.rand(2, 3)    # Zufallszahlen [0,1)
np.random.randn(2, 3)   # Normalverteilung
np.random.randint(0, 10, (2, 3))  # Ganzzahlen
```
**Indexierung & Slicing**
```python
a = np.array([10, 20, 30, 40])
a[0]        # 10
a[-1]       # 40
a[1:3]      # [20 30]

b = np.array([[1, 2, 3],
              [4, 5, 6]])

b[0, 0]         # 1
b[1, 2]         # 6
b[0, :]         # Erste Zeile: [1 2 3]
b[:, 1]         # Zweite Spalte: [2 5]
b[1] = [7, 8, 9]  # Ganze Zeile ersetzen

a = np.array([1, 2, 3, 4, 5])
a[a > 3]       # [4 5]
a[[0, 2, 4]]   # [1 3 5]
```
**Element ändern**
```python
a[0] = 100          # Einzelnes Element ändern
b[:, 1] = 9         # Ganze Spalte ersetzen
a[a > 3] = 0        # Alle Elemente >3 auf 0 setzen

```

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTU3NTA2NDU3M119
-->