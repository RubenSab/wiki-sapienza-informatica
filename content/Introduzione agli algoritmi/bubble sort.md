---
updated_at: 2025-11-23T17:15:06.286+01:00
---
> È l'[[algoritmi di ordinamento|algoritmo di ordinamento]] naive più semplice dal punto di vista dell'implementazione. Si implementa iterando su tutta la [[lista di Python|lista]] `len(lista)` volte e invertendo le coppie di elementi che hanno il primo elemento maggiore del secondo.

``` python
def bubble(lista):
    for i in range(len(lista)):
        for j in range(len(lista)-1):
            if lista[j] > lista[j+1]:
                lista[j], lista[j+1] = lista[j+1], lista[j]
    return lista
```

Costa sempre $\Theta(n^{2})$.

# Ottimizzazione

Si può ottimizzarlo aggiungendo una flag che controlla se al primo ciclo avvengono scambi. In caso contrario, cioè quando la lista è già ordinata, costa $O(n)$.

``` python
def bubble(lista):
    for i in range(len(lista)):
	    scambi = False
        for j in range(len(lista)-1):
            if lista[j] > lista[j+1]:
                lista[j], lista[j+1] = lista[j+1], lista[j]
                scambi = True
        if not scambi:
	        break
    return lista
```