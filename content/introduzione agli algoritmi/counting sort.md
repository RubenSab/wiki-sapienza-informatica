---
updated_at: 2025-06-01T15:12:46.270+02:00
---
``` python
def counting(lista):

    frequenze = [0]*(max(lista)+1)

    for intero in lista:
        frequenze[intero] += 1

    lista_ordinata = []
    for indice, freq in enumerate(frequenze):
        lista_ordinata.extend([indice]*freq)

    return lista_ordinata
```

> N.B.: Può ordinare solo interi.