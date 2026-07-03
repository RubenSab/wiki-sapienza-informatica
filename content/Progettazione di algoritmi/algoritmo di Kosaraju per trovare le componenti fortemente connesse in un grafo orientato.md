---
updated_at: 2026-06-27T10:43:32.329+02:00
---
È un [[algoritmo]] che ha [[complessità temporale]] $O(n+m)$.

Agisce in 2 fasi:

1. [[DFS|DFS]] sull'intero grafo $G$ creando una lista di nodi orientati per tempo di visita.
2. Costruzione del [[grafo]] trasposto $G^{T}$.
3. DFS su $G^{T}$ considerando i nodi in ordine **decrescente** rispetto al tempo di visita. Ogni nuova DFS su un nodo non ancora visitato identifica una nuova componente connessa nel grafo $G$.

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
	ID_componente = 0
	ordine.reverse()
	for nodo in ordine:
		if not visitati[nodo]
			ID_componente += 1
			dfs_etichetta_componenti(
				nodo,
				grafo_trasposto,
				visitati,
				ID_componente,
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
	ordine.append(nodo)

def dfs_etichetta_componenti(nodo, grafo_trasposto, visitati, ID_componente, lista_ssc):
	lista_ssc[nodo] = ID_componente
	visitati[nodo] = True
	for vicino in grafo_trasposto[nodo]:
		if not visitati[vicino]:
			dfs_etichetta_componenti(
				vicino,
				grafo_trasposto,
				visitati,
				ID_componente,
				lista_ssc
			)

def trasponi(liste):
	n = len(liste)
	grafo_trasposto = [[] for _ in range(n)]
	for u in range(n):
		for v in liste[u]:
			grafo_trasposto[v].append(u)
	return grafo_trasposto
```