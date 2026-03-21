---
updated_at: 2026-03-18T14:51:34.759+01:00
---
> L'[[algoritmo]] di *Breadth First Search*, o visita in ampiezza, visita i nodi di un [[grafo]] livello per livello come un onda che si espande. **Ogni** nodo viene raggiunto seguendo il percorso più breve dalla sorgente della visita.

L'implementazione ottima ha [[complessità temporale]] $O(n+m)$.

La BFS fa uso di una [[queue]] come [[struttura dati]] di appoggio: durante ogni livello della visita i nodi vengono inseriti in essa, processati e espulsi (LIFO).

> N.B.: In tutti questi algoritmi i grafi sono [[implementazioni dei grafi|implementati con le liste di adiacenza]].

La BFS si usa in:

# Implementazioni

## Con la [[lista di Python|lista]] che simula una coda $O(n^{2})$

``` python
def bfs_array(grafo, nodo):
	n = len(grafo)
	visitati = [False] * n
	coda = [nodo]
	visitati[nodo] = True
	while coda:
		nodo_corrente = coda.pop(0) # costo O(n)
		for vicino in grafo[nodo]:
			if not visitati[nodo]:
				visitati[nodo] = True
				coda.append(y)
	return [nodo for nodo in range(n) if visitati[nodo]]
```

## Con la lista che simula una coda, ma con la cancellazione logica $O(n+m)$

## Con la deque di collections $O(n+m)$

# Albero BFS