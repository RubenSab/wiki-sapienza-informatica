---
updated_at: 2026-04-04T11:34:21.624+02:00
---
L'[[algoritmo]] calcola il diametro di un [[grafo]] applicando la definizione di diametro.

> Per ogni nodo, si calcolano le distanze tra esso e tutti i nodi del grafo usando l'[[algoritmo per il calcolo del vettore delle distanze]], infine si restituisce la distanza massima.

La [[complessità temporale]] è $O(nm)$ perché si esegue una [[BFS]] da ogni nodo.

``` python
def diametro(grafo):
	n = len(grafo)
	massimo = 0
	for nodo in range(n):
		distanze = vettore_distanze_bfs(grafo, nodo)
		massimo = max(massimo, max(distanze))
	return massimo
```