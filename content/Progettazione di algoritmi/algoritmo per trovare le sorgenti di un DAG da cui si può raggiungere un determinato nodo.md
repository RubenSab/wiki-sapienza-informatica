---
updated_at: 2026-03-13T18:29:36.412+01:00
---
L'approccio ingenuo sarebbe:

1. trovare le sorgenti del [[grafo]],
2. eseguire una [[DFS (algoritmo della visita in profondità)|DFS]] da ognuna, controllare se il nodo $x$ in input è raggiungibile

La [[complessità temporale]] è $O(n(n+m))$, ma c'è di meglio si può usare il grafo trasposto $G^{T}$, così che le **sorgenti di** $G$ **diventino i pozzi di** $G^{T}$.

Basterà fare una singola visita in $O(n+m)$ a partire da $x$ nel grafo $G^{T}$ alla ricerca dei pozzi raggiungibili.

# Implementazione con le [[implementazioni dei grafi|liste di adiacenza]]

``` python
def trova_sorgenti(liste, x):
	n = len(liste)
	grafo_trasposto = trasponi(liste)
	visitati = [False] * n
	dfs(x, grafo_trasposto, visitati)
	sorgenti = []
	for nodo in range(n):
		# un nodo è sorgente nel grafo se non ha archi uscenti nel grafo trasposto
		if grafo_trasposto[nodo] == [] and visitati[nodo]:
			lista.append(nodo)
	return sorgenti
```

