---
updated_at: 2025-10-26T18:49:49.213+01:00
---
> È il test di [[primalità]] più comune.

Implementazione in Python:

``` python
import math

def crivello(numero: int) -> bool:
    for i in range(2, int(math.sqrt(numero))+1):
        if numero%i == 0:
            return False # il numero non è primo
    return True # il numero è primo
```
