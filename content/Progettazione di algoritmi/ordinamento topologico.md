---
updated_at: 2026-06-26T21:21:54.973+02:00
---
> Un'ordinamento topologico è una sequenza lineare dei nodi di un [[grafo]] diretto aciclico (DAG). I nodi di un grafo si definiscono ordinati topologicamente se sono disposti in modo tale che ogni nodo viene prima di tutti i nodi collegati ai suoi archi uscenti.

> N.B. Un grafo può essere ordinato topologicamente se e solo se **non** ha cicli.

L'ordinamento topologico non è un [[proprietà, tipi di relazioni e ordini#^61d991|ordine totale]] perché un grafo può avere più ordinamenti topologici validi.

# [[Algoritmo]] $O(n+m)$ delle sorgenti

Un DAG ha sempre almeno una sorgente.
L'idea è di selezionare una sorgente del grafo e aggiungerla all'ordinamento, poi rimuoverla dal grafo insieme a tutti i suoi archi uscenti.
La sua rimozione non può creare cicli, quindi risulterà in un DAG.
Ma ogni DAG ha una sorgente, quindi la si cerca e si continua così finché non ci sono più nodi da aggiungere nell'ordinamento.

Se alla fine tutti i nodi sono stati rimossi, è stato costruito un ordinamento topologico; altrimenti, se non è più possibile trovare nuove sorgenti, il grafo contiene un ciclo.

``` python
def topo_sort(liste):
	n = len(liste)
	gradi_entranti = [0] * n
	
	for nodo in range(n):
		for vicino in liste[nodo]:
			gradi_entranti[vicino] += 1
	
	sorgenti = [nodo for nodo in range(n) if gradi_entranti[nodo] == 0]
	
	ordinamento = []
	while sorgenti:
		nodo = sorgenti.pop(0) # si rimuove la prima sorgente
		ordinamento.append(nodo)
		for vicino in liste[nodo]:
			gradi_entranti[nodo] -= 1
			if gradi_entranti[nodo] == 0:
				sorgenti.append(nodo)
	
	if len(ordinamento) == n:
		return ordinamento
	return None
```

# Algoritmo $O(n+m)$ basato sulla [[DFS|DFS]]

Si esegue la DFS del grafo e si aggiungono i nodi a una lista man mano
che le loro visite terminano, poi si inverte la [[lista di Python|lista]].

``` python
def topo_sort(liste):
	visitati = [False] * len(liste)
	ordinamento = []
	for nodo in range(len(liste)):
		if visitati[nodo] == False:
			dfs(nodo, liste, visitati, ordinamento)
	return list(reversed(ordinamento))

def dfs(nodo, liste, visitati, ordinamento):
	visitati[nodo] = True
	for vicino in liste[nodo]:
		if visitati[vicino] == False:
			dfs(vicino, liste, visitati, ordinamento)
	ordinamento.append(nodo)
```