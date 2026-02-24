---
updated_at: 2025-05-25T23:19:27.678+02:00
---
Avendo una sequenza di elementi **ordinata**, si può progettare un [[albero di ricerca]] migliore della [[ricerca lineare]].

> La ricerca binaria consiste nel prendere l'elemento a metà dello spazio di ricerca, se è minore\* rispetto a quello cercato, allora si cerca nella seconda metà, mentre se è maggiore\* si cerca nella prima metà, invece se corrisponde a quello cercato si finisce.

\*serve un criterio che ordini lo spazio di ricerca rendendo possibile giudicare un elemento minore o maggiore di un altro, come l'ordinamento per lunghezza, l'ordine alfabetico o altro.

Rispetto alla ricerca lineare, il numero di elementi da controllare in futuro dimezza a ogni iterazione, quindi ha complessità $O(\log{n})$.

- [[albero di ricerca#Implementazioni dell'algoritmo di ricerca|implementazione sugli alberi di ricerca]]
# implementazione su una [[lista di Python|lista]] in Python

``` python
def ricerca_binaria(lista, query):

    inizio = 0
    fine = len(lista)-1

    while inizio <= fine:

        mezzo = (inizio + fine) // 2

        if lista[mezzo] == query:
            return True

        elif lista[mezzo] > query:
            fine = mezzo - 1

        elif lista[mezzo] < query:
            inizio = mezzo + 1

    return False
```

## implementazione ricorsiva

``` python
def ricerca_binaria(lista, query, inizio=0, fine=None):

    if fine == None:
        fine = len(lista)-1

	# se dopo troppe divisioni la lista si rimpicciolisce fino ad avere un numero negativo di elementi, bisogna fermarsi
    if inizio > fine:
        return False
    
    mezzo = (inizio + fine) // 2

    if lista[mezzo] == query:
        return True

    elif lista[mezzo] > query:
        fine = mezzo-1

    elif lista[mezzo] < query:
        inizio = mezzo+1

	# chiamata ricorsiva
    return ricerca_binaria(lista, query, inizio, fine)

    return False

```