---
updated_at: 2026-04-10T12:01:00.416+02:00
---
Il diametro di un [[albero]] si potrebbe calcolare con l'[[algoritmo esaustivo per il calcolo del diametro di un grafo]] in $O(nm)$, considerando che gli alberi sono [[grafo|grafi]], però esiste un algoritmo più efficiente che richiede solo $O(n)$ di [[complessità temporale]].

# Implementazione dell'[[algoritmo]]

1. Si usa l'[[algoritmo per il calcolo del vettore delle distanze]] partendo da un nodo arbitrario, ad esempio il primo memorizzato, per trovare il nodo più lontano da esso.
2. Si usa di nuovo l'algoritmo delle distanze per trovare il nodo più lontano da esso e si ritorna la sua distanza.

``` python
def diametro_albero(grafo):
	distanze_dal_primo = vettore_distanze_bfs(grafo, 0)
	nodo_più_lontano_dal_primo = distanze_dal_primo.index(max(distanze_dal_primo))
	distanze_dal_secondo = vettore_distanze_bfs(grafo, nodo_più_lontano_dal_primo)
	return max(distanze_dal_secondo)
```

> N.B.: Questo algoritmo funziona solo sugli alberi perché sui grafi generali può restituire una distanza minore del vero diametro.

# Dimostrazione di correttezza

#dadimostrare 15 PL7