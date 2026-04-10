---
updated_at: 2026-04-04T11:31:25.380+02:00
---
La [[BFS]] visita i nodi del [[grafo]] in ordine di distanza dalla sorgente della visita. Possiamo quindi costruire un [[array]] di distanze $D$ dove $D[i]$ è la distanza minima dal nodo sorgente al nodo $i$. Per convenzione possiamo imporre $D[i] = +\infty$ se $i$ non è raggiungibile da $s$.

La [[complessità temporale]] è $O(n+m)$.

# [[Algoritmo]]

``` python
def vettore_distanze_bfs(grafo, sorgente):
	n = len(grafo)
	distanze = [float('inf')]*n
	distanze[sorgente] = 0
	coda = [sorgente]
	testa = 0
	while testa < len(coda):
		nodo_corrente = coda[testa]
		testa += 1
		for vicino in grafo[nodo_corrente]:
			if grafo[vicino] == float('inf'):
				distanze[vicino] = distanze[nodo_corrente] + 1
				coda.append(vicino)
```