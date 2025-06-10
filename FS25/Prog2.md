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
**Operationen**
```python
a + b              # Elementweise Addition
a * 2              # Skalare Multiplikation
np.add(a, b)       # Alternativ als Funktion
np.sqrt(a)         # Wurzel
np.mean(a)         # Mittelwert
np.sum(a, axis=0)  # Summieren entlang Achse
np.dot(a, b)       # Matrixprodukt (1D/2D)

a.reshape(2, 3)       # Form ändern
a.flatten()           # 1D machen
np.concatenate([a, b], axis=0)  # Verbinden
np.split(a, 2)        # Aufteilen
np.transpose(a)       # Transponieren

np.where(a > 0, 1, 0)         # Konditional (if/else)
np.unique(a)                  # Einzigartige Werte
np.isin(a, [1, 2])            # Elemente prüfen
np.argmax(a), np.argmin(a)   # Index max/min
``` 
**Referenz vs. Kopie**
```python
a = np.array([1, 2, 3])
b = a                # Referenz (Änderung betrifft beide)
c = a.copy()         # Echte Kopie
```
### Pandas
**Series und Dataframe**
```python
import pandas as pd
s = pd.Series([10, 20, 30], index=["a", "b", "c"])

s.index      # Indexobjekt
s.values     # NumPy-Array
s.dtype      # Datentyp
s.shape      # (3,)

df = pd.DataFrame({
    "Name": ["Alice", "Bob"],
    "Alter": [25, 30]
})

df.columns     # Spaltennamen
df.index       # Zeilenindex
df.dtypes      # Datentypen pro Spalte
df.shape       # (2, 2)
df.values      # NumPy-Array-Daten
```
**Daten einlesen & exportieren**
```python
pd.read_json()
pd.read_csv("daten.csv"/api url, sep=";")    # CSV-Datei
pd.read_excel("daten.xlsx")          # Excel-Datei
pd.read_html()
df.to_csv("ausgabe.csv", index=False)
df.to_excel("ausgabe.xlsx")
```
**Datenzugriff**
```python
'''SPALTENZUGRIFF'''
df["Name"]        # Als Series
df.Name           # Kurzschreibweise (wenn kein Leerzeichen o. Sonderzeichen)
'''ZEILENZUGRIFF'''
df.loc[0]         # Zugriff über Label
df.iloc[0]        # Zugriff über Position
'''EINZELWERTE'''
df.at[0, "Name"]
df.iat[0, 0]
```
**Slicing und Filtern**
```python
df[ df["Alter"] > 25 ]      # Filter mit Bedingung
df.loc[0:1, ["Name"]]       # Zeilen + Spalten
```
**Daten bearbeiten**
```python
df["Stadt"] = ["Berlin", "München"]       # Neue Spalte
df.loc[1, "Alter"] = 35                   # Einzelwert ändern
df["Alter"] = df["Alter"] + 1            # Spalte verändern
```
**Aggregation und Statistiken**
```python
df.mean(), df["Alter"].mean()
df.sum(), df.min(), df.max()
df.describe()                # Zusammenfassung
df["Alter"].value_counts()   # Häufigkeiten
```
**Gruppieren**
```python
df.groupby("Stadt").mean()          # Mittelwert nach Gruppe
df.groupby("Stadt")["Alter"].sum()  # Summe für eine Spalte
```
**fehlende Werte**
```python
df.isnull(), df.notnull()          # Prüfen
df.dropna()                        # Zeilen mit NaN entfernen
df.fillna(0)                       # NaN ersetzen
```
**Daten umstrukturieren**
```python
df.T                           # Transponieren
df.sort_values("Alter")       # Sortieren
df.rename(columns={"Name": "Vorname"})
df.set_index("Name")          # Index setzen
df.reset_index()              # Index zurücksetzen
```
**Dataframes zusammenführen**
```python
pd.concat([df1, df2])              # Zeilen anhängen
pd.merge(df1, df2, on="ID")        # SQL-Join
df.append(neue_zeile, ignore_index=True)  # Zeile hinzufügen
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTUxNDMzNjA4Nl19
-->