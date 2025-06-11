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
### Files lesen und bearbeiten
```python
'''lesen'''
with open("datei.txt", "r", encoding="utf-8") as f:
    inhalt = f.read()

'''Zeilenweise lesen'''
with open("datei.txt", "r") as f:
    for zeile in f:
        print(zeile.strip())

'''Scheiben (überschreibt Datei)'''
with open("datei.txt", "w", encoding="utf-8") as f:
    f.write("Neuer Inhalt")

'''Schreiben (an Datei anhängen)'''
with open("datei.txt", "a") as f:
    f.write("Neuer Inhalt")
```
**CSV Dateien**
```python
import csv

with open("daten.csv", newline='', encoding="utf-8") as f:
    reader = csv.reader(f)
    for zeile in reader:
        print(zeile)

'''als Dictionary einlesen'''
with open("daten.csv", newline='') as f:
    reader = csv.DictReader(f)
    for row in reader:
        print(row["Name"], row["Alter"])

'''Schreiben'''
daten = [
    ["Name", "Alter"],
    ["Alice", 30],
    ["Bob", 25]
]

with open("daten.csv", "w", newline='', encoding="utf-8") as f:
    writer = csv.writer(f)
    writer.writerows(daten)
```
**JSON Dateien**
```python
import json
'''Lesen'''
with open("daten.json", "r", encoding="utf-8") as f:
    daten = json.load(f)
    print(daten)

'''Schreiben'''
with open("daten.json", "w", encoding="utf-8") as f:
    json.dump(daten, f, indent=4)
```
**Excel Dateien**
```python
import pandas as pd

df = pd.read_excel("datei.xlsx")
df["Alter"] += 1
df.to_excel("neu.xlsx", index=False)
```
**Binärdateien**
```python
'''Lesen'''
with open("bild.jpg", "rb") as f:
    inhalt = f.read()
'''Schreiben'''
with open("bild.jpg", "rb") as f:
    inhalt = f.read()
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
	        'AppleWebKit/537.36 (KHTML, like Gecko) ' 
			'Chrome/122.0.0.0 Safari/537.36'  }  
	      
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
```python
import datetime  
import time  
import urllib.request as ur  
import json  
  
class Requester:  
  MAX_REQUESTS = 5  
  _HEADERS = {  
        'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) '  
					  'AppleWebKit/537.36 (KHTML, like Gecko) ' 
					  'Chrome/122.0.0.0 Safari/537.36',  
        'Accept': 'application/json'  
  }  
  
    def __init__(self):  
		self._URL = ""  
	    self._data_retrieved = False  
	    self._last_retrieval_date = None  
	    self._data = None  
	    self._failed_requests = 0  
  
  def set_url(self,url):  
	  self._URL = url  
  
    def request_data(self):  
        while not self._data_retrieved and self._failed_requests < self.MAX_REQUESTS:  
            try:  
                req = ur.Request(self._URL, 
				                 headers=self._HEADERS,  
                                 method="GET")  
                with ur.urlopen(req) as response:  
                    #print(f"HTTP Status: {response.status}")  
				    s = response.read().decode("utf-8")  
                  
				self._data = json.loads(s)  
                self._data_retrieved = True  
                self._last_retrieval_date = datetime.datetime.now()  
                self._failed_requests = 0  
	    except Exception as e:  
                print("Request failed because: ")  
                print(f"{e}")  
                print(f"Will reuqest again in {2 ** self._failed_requests}s")  
                time.sleep(2 ** self._failed_requests)  
                self._failed_requests += 1  
  
  def return_data(self):  
        return self._data  
  
    def set_new_request(self, new_url): 
		self._URL = new_url  
        self._data = None  
        self._last_retrieval_date = None  
        self._data_retrieved = False
```
### Optimization
**Datenverarbeitung**
```python 
'''SLOW: Standard-Loop'''
newlist = []
for word in oldlist:
    newlist.append(word)

'''FASTER: map Funktion'''
newlist = map(str, oldlist)

'''FASTEST in place list comprehension'''
newlist = [s.upper() for s in oldlist]
```
**Imports**
```python
'''SLOW: Imports in Loops/Funktionen'''
def func():
    import math
    math.sqrt(4)

'''FAST: Import am Dateianfang'''
import math
def func():
    math.sqrt(4)
```
**Funktionsaufrufe**
Funktionsaufrufe kosten Performance, besonders bei vielen Wiederholungen.
```python
# Direkt in der Schleife (schneller)
val += i + i + 1

# Durch Funktion (langsamer)
def func(a, b): return a + b
val += func(i, i + 1)
```
### Profiling
```python
import profile
profile.run('quicksort(my_list, 0, len(my_list)-1)')
```
Ausgabe enthält:
-   `ncalls`: wie oft Funktion aufgerufen 
-   `tottime`: reine Zeit in dieser Funktion
-   `cumtime`: Zeit inklusive aufgerufener Subfunktionen
-   `percall`: Zeit pro Aufruf
 
 Ein Programm kann auch mit einem Alternativen Interpreter wie PyPy verschnellert werden.
 **Vorteile**:
 - Just-in-Time Compiler → viel schnellere Ausführung
-  Kein Code muss geändert werden
**Nachteile**:
-   Nicht 100 % kompatibel mit allen Bibliotheken
-   Manche Pakete wie NumPy schlechter unterstützt
### Sorting Algos und Performance
**Insertion Sort (auch: „Card Sort“)**
**Idee:**  
Jedes Element wird an der richtigen Stelle in die bereits sortierte Teilliste eingefügt. Ähnlich wie Kartensortieren mit der Hand.

**Ablauf:**
-   Iteriere durch die Liste von links nach rechts. 
-   Vergleiche jedes Element rückwärts mit dem bereits sortierten Teil. 
-   Füge es an der korrekten Stelle ein (mittels Austausch)
**Komplexität:**

| Fall | Laufzeit |
|--|--|
| Best Case | O(n) (bereits sortiert) |
|  |  |
|  |  |
O(n²)

Worst Case

O(n²) (umgekehrt sortiert)

**Praxisbeispiel:**

-   Sehr langsam bei großen Datenmengen.
    
-   Schnell für kleine, fast sortierte Listen.
    

----------

## 2️⃣ **Quicksort**

**Idee:**  
Ein Divide-and-Conquer-Algorithmus. Nutzt ein „Pivot“-Element zum Aufteilen der Liste in kleinere (kleiner als Pivot) und größere (größer als Pivot) Teile, die rekursiv sortiert werden.

**Ablauf:**

1.  Wähle zufällig ein Pivot-Element.
    
2.  Teile Liste in:
    
    -   links: ≤ Pivot
        
    -   rechts: > Pivot
        
3.  Sortiere beide Seiten rekursiv.
    
4.  (Keine Kombination notwendig, da In-place-Sortierung)
    

**Komplexität:**

Fall

Laufzeit

Best Case

O(n log n)

Average Case

O(n log n)

Worst Case

O(n²) (schlechtes Pivot)

**Praxiswerte (gemessen):**

Elemente

Zeit

1.000

0.013 s

10.000

0.144 s

1.000.000

120 s (2 min)

**Besonderheit:**

-   Schneller als InsertionSort für große Listen.
    
-   Wird häufig verwendet (z. B. Python's `sorted()` basiert auf TimSort, was Quicksort-ähnlich ist).
    

----------

## 3️⃣ **Count Sort**

**Idee:**  
Zählt die Anzahl der Vorkommen von Elementen in einer Liste – nur sinnvoll, wenn **alle Werte in einem kleinen, bekannten Bereich liegen**.

**Ablauf:**

1.  Erstelle ein Zählarray der Größe `max+1`.
    
2.  Iteriere durch die Eingabe und erhöhe den jeweiligen Zähler.
    
3.  Erzeuge daraus die sortierte Liste.
    

**Komplexität:**

Fall

Laufzeit

Immer

O(n + k)

-   `n`: Anzahl der Elemente
    
-   `k`: Bereich der Werte (maximaler Wert)
    

**Praxiswerte (gemessen):**

Elemente

Zeit

1.000

0.009 s

10.000

0.002 s

1.000.000

0.4 s

**Voraussetzung:**

-   Wertebereich muss klein und positiv sein.
    
-   Keine Vergleichsoperationen nötig → extrem schnell.
    

----------

## 🔢 **Vergleich aller Sortierverfahren**

Algorithmus

Strategie

Beste Laufzeit

Durchschnitt

Schlechteste

Stabil?

Voraussetzung

Insertion Sort

Vergleichsbasiert

O(n)

O(n²)

O(n²)

✅ Ja

Gut für kleine Listen

Quicksort

Divide & Conquer

O(n log n)

O(n log n)

O(n²)

❌ Nein

Pivotwahl ist kritisch

Count Sort

Zählverfahren

O(n + k)

O(n + k)

O(n + k)

✅ Ja

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTg0NzEyNjk2NywxODI2ODcxODIsLTQwOT
c0Mzk0OSwzODMzMTUyOTcsLTEwOTE4MjE5NDIsNTM0NjYwNTU4
LC0yMTM4NjUxNzQ0LC0xMjU0MzgyMDIzXX0=
-->