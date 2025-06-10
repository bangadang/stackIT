### Basics
-   **Immutable (unveränderlich)**: `int`, `float`, `complex`, `bool`, `str`, `tuple`, `range`, `frozenset`, `bytes`, `NoneType`
-   **Mutable (veränderlich)**: `list`, `set`, `dict`, `bytearray`, `memoryview`, `function*`, `module*`
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

df.head(), df.tail()                # Erste/letzte Zeilen
df.info()                           # Strukturinfo
df.describe()                 # Statistische Zusammenfassung
df.apply(func)                      # Funktion auf Zeile/Spalte
df["Name"].str.upper()              # String-Methoden
df["Datum"] = pd.to_datetime(df["Datum"])  # Datetime-Konvertierung
df.columns.tolist()          # Liste der Spaltennamen
df.index.tolist()            # Liste der Zeilen-IDs

df["Alter"] = df["Alter"].astype(int) #Typenkonvertierung

```
**Daten einlesen & exportieren**
```python
pd.read_json("daten.json")  
pd.read_csv("daten.csv"/api url, sep=";")    # CSV-Datei
pd.read_excel("daten.xlsx")          # Excel-Datei
pd.read_html("https://...") 

df.to_json("ausgabe.json")
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
**fehlende/doppelte Werte**
```python
df.isnull(), df.notnull()          # Prüfen
df.dropna()                        # Zeilen mit NaN entfernen
df.fillna(0)                       # NaN ersetzen
df.duplicated()
df.drop_duplicates()
```
**Daten umstrukturieren**
```python
df.T                           # Transponieren
df.sort_values("Alter")       # Sortieren
df.sort_index()
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
**Strings bearbeiten**
```python
df["Spalte"].str.lower()
df["Spalte"].str.contains("abc")
df["Spalte"].str.replace("alt", "neu")
```
**Datum/Zeit bearbeiten**
```python
df["Datum"] = pd.to_datetime(df["Datum"])
df["Jahr"] = df["Datum"].dt.year
df["Monat"] = df["Datum"].dt.month
```
**bedingte Logik**
```python
df["Neu"] = np.where(df["Wert"] > 10, "hoch", "niedrig")
df["Kategorie"] = df["Wert"].apply(lambda x: "gut" if x > 80 else "ok")
```
### OOP
```python
class ClassName(Class2InheritFrom):
	GLOBAL_CONST = some_val #same for every instance
	def __init__(self, val1):
		self.atrribute1 = val1
	def methods(self):
		#do sth
```
**Inheritance und Method Resolution Order**
```python
class A:
    def __init__(self):
        print("A", end="")

class B(A):
    def __init__(self):
        print("B", end="")
        super().__init__()

class C(A):
    def __init__(self):
        print("C", end="")
        super().__init__()

class D(B, C):
    def __init__(self):
        print("D", end="")
        super().__init__()

if __name__ == "__main__":
    o = D()
```
```css
# D.__mro__()
D → B → C → A
```
**Magic Methods**
```python
# Konstruktion & Zerstörung
def __new__(cls, *args, **kwargs): pass           # Erstellt eine neue Instanz (vor __init__)
def __init__(self, *args, **kwargs): pass         # Initialisiert das Objekt
def __del__(self): pass                           # Wird beim Löschen des Objekts aufgerufen

# String-Darstellung
def __str__(self): pass                           # Für str(obj), print(obj)
def __repr__(self): pass                          # Für repr(obj), Entwickler-Repräsentation
def __format__(self, format_spec): pass           # Für format(obj, "spec")
def __bytes__(self): pass                         # Für bytes(obj)

# Numerische Operatoren
def __add__(self, other): pass                    # obj + other
def __sub__(self, other): pass                    # obj - other
def __mul__(self, other): pass                    # obj * other
def __truediv__(self, other): pass                # obj / other
def __floordiv__(self, other): pass               # obj // other
def __mod__(self, other): pass                    # obj % other
def __pow__(self, other): pass                    # obj ** other
def __neg__(self): pass                           # -obj
def __pos__(self): pass                           # +obj
def __abs__(self): pass                           # abs(obj)
def __round__(self): pass                         # round(obj)

# Reversed / Reflected Operatoren
def __radd__(self, other): pass                   # other + obj (wenn left operand kein __add__ hat)
# ... analog für __rsub__, __rmul__, etc.

# In-Place Operatoren
def __iadd__(self, other): pass                   # obj += other
def __isub__(self, other): pass                   # obj -= other
# ... analog für __imul__, __itruediv__, etc.

# Vergleichsoperatoren
def __eq__(self, other): pass                     # obj == other
def __ne__(self, other): pass                     # obj != other
def __lt__(self, other): pass                     # obj < other
def __le__(self, other): pass                     # obj <= other
def __gt__(self, other): pass                     # obj > other
def __ge__(self, other): pass                     # obj >= other

# Typumwandlung
def __bool__(self): pass                          # bool(obj)
def __int__(self): pass                           # int(obj)
def __float__(self): pass                         # float(obj)
def __complex__(self): pass                       # complex(obj)

# Container-Protokoll
def __len__(self): pass                           # len(obj)
def __getitem__(self, key): pass                  # obj[key]
def __setitem__(self, key, value): pass           # obj[key] = value
def __delitem__(self, key): pass                  # del obj[key]
def __contains__(self, item): pass                # item in obj
def __iter__(self): pass                          # iter(obj)
def __next__(self): pass                          # next(obj)
def __reversed__(self): pass                      # reversed(obj)

# Kontextmanager
def __enter__(self): pass                         # with obj as x: ...
def __exit__(self, exc_type, exc_val, exc_tb): pass # Nach dem Verlassen des with-Blocks

# Aufrufbares Objekt
def __call__(self, *args, **kwargs): pass         # obj() – macht das Objekt aufrufbar

# Attributzugriff
def __getattr__(self, name): pass                 # Wenn Attribut nicht existiert
def __getattribute__(self, name): pass            # Wird bei jedem Attributzugriff aufgerufen
def __setattr__(self, name, value): pass          # obj.name = value
def __delattr__(self, name): pass                 # del obj.name
def __dir__(self): pass                           # dir(obj)

# Klassenverhalten
def __class_getitem__(cls, key): pass             # Für generische Typen: MyClass[int]
def __instancecheck__(self, instance): pass       # isinstance(obj, cls)
def __subclasscheck__(self, subclass): pass       # issubclass(sub, cls)
```
### API Calls
```python
import urllib.request

url = "https://api.example.com/data"

with urllib.request.urlopen(url) as response:
    data = response.read().decode("utf-8")
    print(data)
    
    # data is json format
    data = json.loads(raw_data)
	
	#data is csv format
	csv_file = io.StringIO(data)
    reader = csv.reader(csv_file)
    for row in reader:
	    print(row)

```
**Beispiel Code mit Erweiterungen**
```python
	try:  
	    headers = {  
	        'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) '  
	 'AppleWebKit/537.36 (KHTML, like Gecko) ' 'Chrome/122.0.0.0 Safari/537.36'  }  
	      
	    req = ur.Request(self._url, headers=headers)  
	  
	    s = ur.urlopen(req).read().decode("utf-8")  
	  
	    exchange_rate_info = json.loads(s)  
	  
	    with open(self.latest_version_path, "w") as f:  
	        json.dump(exchange_rate_info, f)  
	    return exchange_rate_info  
	  
	except:   
	    with open(self.latest_version_path, "r") as f:  
	        exchange_rate_info = json.load(f)  
	    return exchange_rate_info
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3NjE2NjQ5OTcsLTEwOTE4MjE5NDIsNT
M0NjYwNTU4LC0yMTM4NjUxNzQ0LC0xMjU0MzgyMDIzXX0=
-->