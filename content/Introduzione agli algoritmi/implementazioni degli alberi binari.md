---
updated_at: 2026-03-11T20:28:19.125+01:00
---
# Con [[array]]

^28a0a1

Dato un nodo all'indice $i$:

- il figlio sinistro si trova a $2i+1$ (se esiste),
- il figlio destro si trova a $2i+2$ (se esiste),
- il genitore si trova a $\left\lfloor \frac{i-1}{2} \right\rfloor$ (se esiste).

Ciò costruisce un [[albero]] seguendo la [[albero#^34c59b|visita per ampiezza]].

Non si adatta bene ad alberi sbilanciati, in quanto nel peggiore dei casi (albero degenere di $n$ nodi), è necessario un array lungo $\Theta(2^{n})$ con molti spazi vuoti.
## Implementazione

### Vettore -> albero

``` python
def da_lista_a_albero(lista, i=0) -> Nodo:

    if i >= len(lista) or lista[i] is None:
        return None

    nodo = Nodo(lista[i])
    nodo.left = da_lista_a_albero(lista, 2 * i + 1)
    nodo.right = da_lista_a_albero(lista, 2 * i + 2)
    return nodo

```

### Albero -> vettore

Si usa [[albero#^34c59b|l'algoritmo della visita per ampiezza]] che produce esattamente ciò che vogliamo.
# Con il vettore dei padri

^26ee6b

Si assegna a ogni nodo un'indice di un'[[array]] (possibilmente con un criterio intuitivo, come l'ordine crescente da 0 a $n$), e in quella posizione del vettore si inserisce l'indice del nodo padre. L'assenza di padre del **nodo radice** è rappresentata da un **valore speciale** come $-1$.

Esempio:

```
albero:

		0
        /\
       /  \
      /    \
     1      2
    / \      \
   /   \      \
  3     4      5
 / \   /      / \ 
6   7  8     9  10

vettore dei padri:

[-1, 0, 0, 1, 1, 2, 3, 3, 4, 5, 5]
```

Vantaggi:

- facilità d'implementazione,
- [[complessità spaziale]] $\Theta(n)$ migliore della rappresentazione con array.

Svantaggi:

- Le operazioni sull'albero sono meno efficienti rispetto alla rappresentazione con puntatori.
- Non si può distinguere tra figlio sinistro e figlio destro direttamente

## Implementazione

``` python
# Trova la dimensione massima per preallocare il vettore
def trova_max_key(nodo):
	if nodo is None:
		return -1
	return max(nodo.key,
		trova_max_key(nodo.left),
		trova_max_key(nodo.right))

def vettore_padri(root):

    # crea un vettore da modificare dopo
    max_key = trova_max_key(root)
    vettore = [-1] * (max_key + 1)

    # aggiorna man mano il vettore dei padri
    def visita(nodo, padre_key=-1):
        if nodo is None:
            return
        vettore[nodo.key] = padre_key
        visita(nodo.left, padre_key = nodo.key)
        visita(nodo.right, padre_key = nodo.key)

    visita(root)
    return vettore
```


---
## Con i [[puntatore|puntatori]]

``` python
class Nodo:
    def __init__(self, key = None, right = None, left = None):
        self.key = key
        self.right = right
        self.left = left
```

Ogni nodo dell'albero viene implementato come una [[struttura dati]] con tre [[campi]]:

- key: le informazioni memorizzate nel nodo,
- left: il puntatore al figlio sinistro,
- right: il puntatore al figlio destro.

Vantaggi

- struttura dinamica,
- inserimenti ed eliminazioni di nodi più efficienti.

Svantaggi

- la gestione della [[memoria]] richiede l'allocazione dinamica,
- i nodi occupano più spazio in memoria per via dei puntatori.
