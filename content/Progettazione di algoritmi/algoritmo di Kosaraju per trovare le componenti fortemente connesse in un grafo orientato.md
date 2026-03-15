---
updated_at: 2026-03-15T10:58:05.286+01:00
---
#todo 

È un [[algoritmo]] che ha [[complessità temporale]] $O(n+m)$.

Agisce in 2 fasi:

1. [[DFS (algoritmo della visita in profondità)|DFS]] sull'intero grafo $G$ annotando il tempo di fine visita per ciascun nodo.
2. Costruzione del [[grafo]] trasposto $G^{T}$ e DFS su $G^{T}$ considerando i nodi in ordine decrescente rispetto al tempo di visita. Ogni nuova DFS su un nodo non ancora visitato identifica una nuova componente connessa nel grafo $G$.

``` python
def kosaraju(liste):
	n = len(liste)
	visitati = [False] * n
	ordine = []
	
	for nodo in range(n):
		if not visitati[nodo]:
			dfs_nodi_ordinati_per_tempo_visita(
				nodo,
				liste,
				visitati,
				ordine
			)
	
	grafo_trasposto = trasponi(liste)
	visitati = [False] * n
	lista_ssc = [0] * n # lista con ID della componente del nodo all'indice corrispondente
	componente = 0
	ordine.reverse()
	for nodo in ordine:
		if not visitati[nodo]
			componente += 1
			dfs_etichetta_componenti(
				nodo,
				grafo_trasposto,
				visitati,
				componente,
				lista_ssc
			)
	return lista_ssc

def dfs_nodi_ordinati_per_tempo_visita(nodo, liste, visitati, ordine):
	visitati[nodo] = True
	for vicino in liste[nodo]:
		if not visitati[vicino]:
			dfs_nodi_ordinati_per_tempo_visita(
				vicino,
				liste,
				visitati,
				ordine
			)
	ordine.append(vicino)

def dfs_etichetta_componenti(nodo, grafo_trasposto, visitati, componente, lista_ssc):
	lista_ssc[nodo] = componente
	visitati[nodo] = True
	for vicino in grafo_trasposto[nodo]:
		if not visitati[vicino]:
			dfs_etichetta_componenti(
				vicino,
				grafo_trasposto,
				visitati,
				componente,
				lista_ssc
			)
```