---
updated_at: 2026-03-13T18:34:55.525+01:00
---
L'[[algoritmo]] itera su tutti i nodi del [[grafo]] **non orientato** e fa partire una [[DFS|DFS]] dal nodo corrente solo se non è stato ancora visitato, assegnando un nuovo ID ai nodi raggiunti.

La [[complessità temporale]] è $O(n+m)$ perché ogni vertice e ogni arco sono visitati una sola volta.

``` python
def componenti_connesse(liste):
	n = len(liste)
	IDs_componenti = [0] * n
	ID_corrente = 0
	for nodo in range(n):
		if IDs_componenti[nodo] == 0:
			ID_corrente += 1
			dfs(liste, nodo, IDs_componenti, ID_corrente)
	return componenti_connesse

def dfs(liste, sorgente, IDs_componenti, ID_corrente):
	IDs_componenti[sorgente] = ID_corrente:
	for vicino in liste[sorgente]:
		if IDs_componenti[vicino] == 0:
			dfs(liste, vicino, IDs_componenti, ID_corrente)
```
