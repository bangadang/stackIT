### Numpy
```python
import numpy as np

a = np.array([1, 2, 3])           # 1D Array
b = np.array([[1, 2], [3, 4]])    # 2D Array

a.shape      # (3,) – Form (Dimensionen)
a.ndim       # 1 – Anzahl der Dimensionen
a.size       # 3 – Anzahl der Elemente
a.dtype      # dtype('int64') – Datentyp
a.itemsize   # z.B. 8 – Byte pro Element
a.T          # Transponiert (nur bei 2D+ sinnvoll)

```

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExODA3MjA0MDhdfQ==
-->