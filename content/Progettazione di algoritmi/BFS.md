---
updated_at: 2026-03-26T11:50:29.047+01:00
---
> L'[[algoritmo]] di *Breadth First Search*, o visita in ampiezza, visita i nodi di un [[grafo]] livello per livello come un onda che si espande. **Ogni** nodo viene raggiunto seguendo il percorso più breve dalla sorgente della visita.

L'implementazione ottima ha [[complessità temporale]] $O(n+m)$.

Nella sua implementazione più [[efficienza degli algoritmi (costo computazionale)|efficiente]], la BFS fa uso di una [[queue]] come [[struttura dati]] di appoggio: durante ogni livello della visita i nodi vengono inseriti in essa, processati e espulsi (LIFO).

> N.B.: In tutti questi algoritmi i grafi sono [[implementazioni dei grafi|implementati con le liste di adiacenza]].

La BFS si usa in:

- [[algoritmo per il calcolo del vettore delle distanze]]
- [[algoritmo per il calcolo del diametro di un albero]]

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

Si usa un indice `testa` che si sposta in avanti, simulando la rimozione degli elementi.

``` python
def bfs_array_logico(grafo, primo_nodo):
	n = len(grafo)
	visitati = [False] * n
	coda = [primo_nodo]
	testa = 0
	visitati[primo_nodo] = True
	while testa < len(coda):
		nodo_corrente = coda[testa]
		testa += 1
		for vicino in grafo[nodo_corrente]:
			if not visitati[nodo_corrente]:
				visitati[nodo_corrente] = True
				coda.append(vicino)
	return [nodo for nodo in range(n) if visitati[nodo]]
```

## Con la deque di collections $O(n+m)$

``` python
from collections import deque

def bfs_deque(grafo, primo_nodo):
	n = len(grafo)
	visitati = [False] * n
	coda = deque()
	coda.append(primo_nodo)
	visitati[primo_nodo] = 1
	while coda:
		nodo_corrente = coda.popleft() # O(1)
		for vicino in grafo[nodo_corrente]:
			if not visitati[nodo_corrente]:
				visitati[nodo_corrente] = True
				coda.append(vicino)
	return [nodo for nodo in range(n) if visitati[nodo]]
```

# Albero BFS

> La BFS costruisce implicitamente l'[[albero]] BFS ovvero il [[sottoinsiemi|sottoinsieme]] del grafo formato da tutti i nodi raggiungibili dalla sorgente e dagli archi usati per raggiungerli. È l'**albero dei cammini minimi dalla sorgente della BFS**.

Viene rappresentato con il [[implementazioni degli alberi binari#^26ee6b|vettore dei padri]] $P$ dove $P[v]$ è il nodo da cui si è raggiunto $v$ per la prima volta. Per convenzione si usano:

- $P[v] = -1$ se il nodo non è mai stato visitato.
- $P[v] = v$ (un cappio) per la radice della BFS.

``` python
def albero_bfs(grafo, nodo):
	n = len(grafo)
	vettore = [-1] * n
	vettore[nodo] = nodo
	coda = [nodo]
	testa = 0
	while testa < len(coda):
		nodo_corrente = coda[testa]
		testa += 1
		for vicino in grafo[nodo_corrente]:
			if vettore[vicino] == -1:
				vettore[vicino] = nodo_corrente
				coda.append(vicino)
	return vettore
```