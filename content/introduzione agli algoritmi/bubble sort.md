---
updated_at: 2025-05-25T22:26:55.471+02:00
---
> È l'algoritmo di ordinamento naive più semplice dal punto di vista dell'implementazione. Si implementa iterando su tutta la lista `len(lista)` volte e invertendo le coppie di elementi che hanno il primo elemento maggiore del secondo.

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