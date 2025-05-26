---
updated_at: 2025-05-26T09:18:44.552+02:00
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

### ✅ **Perché NON è O(n²)**

Anche se c’è un **ciclo annidato**, la **quantità totale di iterazioni** del ciclo interno su `range(freq)` è **uguale a `n`**, ovvero al numero totale di elementi nella lista originale.

- Ogni `freq` è **quante volte un numero appare**
    
- La **somma di tutte le freq** è esattamente **n**
    

> ✔️ Quindi anche se fai tanti piccoli cicli, la **somma totale** di tutte le iterazioni interne è **n**