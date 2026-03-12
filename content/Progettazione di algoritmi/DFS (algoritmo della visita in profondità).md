---
updated_at: 2026-03-12T17:00:51.562+01:00
---
> L'[[algoritmo]] di *Depth First Search* (DFS) ($O(n+m)$) trova tutti i nodi **raggiungibili** in un [[grafo]] da un nodo sorgente. Segue un cammino profondo, visitando i vicini del nodo corrente e tornando indietro solo quando tutti i vicini del nodo corrente sono stati visitati (backtracking), per terminare nel nodo sorgente.

![[dfs.gif]]

# Con [[implementazioni dei grafi|matrice di appartenenza]]

La [[complessità temporale]] è $O(n^{2})$ perché per ogni nodo visitato è necessario scorrere l'intera riga della matrice per trovare i vicini del nodo.

``` python
def dfs_matrice(matrice, sorgente):
	visitati = [False]*len(matrice)
	ricerca_ricorsiva(matrice, sorgente, visitati)
	return visitati

def ricerca_ricorsiva(matrice, sorgente, visitati):
	visitati[sorgente] = True
	for nodo in range(len(matrice)):
		if matrice[sorgente][nodo] == 1 and not visitati[nodo]:
			ricerca_ricorsiva(matrice, nodo, visitati)
	return visitati
```

# Con [[implementazioni dei grafi|liste di adiacenza]] o dizionari

Ha complessità temporale $O(n^{2})$ perché per ogni nodo visitato è necessario scorrere l'intera riga della matrice.

``` python
def dfs_liste(liste, sorgente):
	visitati = [False]*len(liste)
	ricerca_ricorsiva(liste, sorgente, visitati)
	return visitati

def ricerca_ricorsiva(liste, sorgente, visitati):
	visitati[sorgente] = True
	for nodo in liste[sorgente]:
		if not visitati[nodo]:
			ricerca_ricorsiva(liste, nodo, visitati)
	return visitati
```

## Ottimizzazione con set

Usando un **set di nodi visitati** piuttosto che una lista nella DFS implementata con le liste di adiacenza, si può ridurre la complessità temporale a $O(n+m)$ **nel caso medio**, perché le operazioni di inserimento e controllo su un set hanno un costo ammortizzato di $O(1)$.

Il costo al caso pessimo (estremamente più raro del caso medio) è $O(n^{2} + nm)$.

``` python
def dfs_liste_e_set(liste, sorgente):
	visitati = set()
	ricerca_ricorsiva(liste, sorgente, visitati)
	return visitati

def ricerca_ricorsiva(liste, sorgente, visitati):
	visitati.add(u)
	for nodo in liste[sorgente]:
		if nodo not in visitati:
			ricerca_ricorsiva(liste, nodo, visitati)
	return visitati
```

# Implementazione iterativa con [[stack]]

Le implementazioni **ricorsive** hanno il problema di non poter percorrere un cammino lungo più di $\approx 1000$ nodi, cioè la dimensione massima dello **stack delle chiamate ricorsive**.

Per evitare questo limite, si può fare affidamento su uno stack implementato esplicitamente.

``` python
def dfs_iterativa(liste, sorgente):
	visitati = [False]*len(liste)
	stack = [sorgente]
	while len(stack) > 0:
		nodo = stack.pop()
		if not visitati(nodo):
			visitati[nodo] = True
			for vicino in liste[nodo]:
				if not visitati[vicino]:
					stack.append(vicino)
	return visitati
```

``` python
def dfs_iterativa_con_set(liste, sorgente):
	visitati = set()
	stack = [sorgente]
	while len(stack) > 0:
		nodo = stack.pop()
		if nodo not in visitati:
			visitati.add(nodo)
			for vicino in liste[nodo]:
				if vicino not in visitati:
					stack.append(vicino)
	return visitati
```

# Albero DFS

> La DFS costruisce implicitamente una struttura ad [[albero]], detta **albero DFS**. Questo è il *sottografo aciclico connesso e orientato* del grafo originale, percorso dai nodi raggiunti e dagli archi traversati a partire dal nodo scelto.

## Implementazione in $O(n+m)$

Il modo più compatto per rappresentare l'albero DFS è con il [[implementazioni degli alberi binari#^26ee6b|vettore dei padri]], che può essere generato con una DFS modificata.

``` python
def vettore_padri(liste, sorgente):
	padri = [-1] * len(liste)
	padri[sorgente] = sorgente # la sorgente è resa padre di se stessa
	dfs_padri(liste, sorgente, padri)

def dfs_padri(liste, nodo, padri):
	for vicino in liste[nodo]:
		if padri[vicino] = nodo
		dfs_padri(liste, vicino, padri)
```

## Algoritmo per ottenere i cammini in $O(n)$

per ottenere il cammino da un nodo alla radice dell'albero, risaliamo il vettore dei padri.

``` python
def percorri_cammino(nodo, padri):
	cammino = []
	if padri[nodo] == -1
		return cammino
	while cammino[nodo] != nodo:
		cammino.append(nodo)
		nodo = cammino[nodo]
	cammino.append(nodo)
	cammino.reverse()
	return cammino
```

---

La [[DFS (algoritmo della visita in profondità)]] è legata a:

- [[algoritmo per la 2-colorazione dei grafi]]
- [[algoritmo per trovare i ponti in un grafo]]
- [[algoritmo per trovare le componenti connesse]]
- [[algoritmo per trovare i ponti in un grafo]]