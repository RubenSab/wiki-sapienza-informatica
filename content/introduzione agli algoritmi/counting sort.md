---
updated_at: 2025-05-29T11:54:37.884+02:00
---
#todo

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

l'inizializzazione non costa $O(n)$ ma $O(1)$, dipende dal massimo del vettore.

incrementare i contatori costa $O(n)$ in totale.

i due for annidati costano $O(k\cdot n)$, non $\Theta(k \cdot n)$ (in realtà costano $\Theta(k+n)$).