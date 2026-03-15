---
updated_at: 2026-03-15T10:44:31.058+01:00
---
L'[[algoritmo]] prende in input un [[grafo]] diretto $G$ e un nodo $u$ e fa tre passi:

1. calcola l'insieme $A$ dei nodi raggiungibili da $u$ con la [[DFS (algoritmo della visita in profondità)|DFS]],
2. calcola l'insieme $B$ dei nodi che in $G$ portano a $u$ (si usa lo stesso trucco dell'[[algoritmo per trovare le sorgenti di un DAG da cui si può raggiungere un determinato nodo]], con il **grafo trasposto** $G^{T}$).
3. restituisce l'intersezione di $A$ e $B$.

La [[complessità temporale]] è $O(n+m)$.

``` python
def componente_nodo(liste, nodo):
	n = len(liste)
	visitati_1 = [0] * n
	dfs(liste, nodo, visitati_1)
	
	visitati_2 = [0] * n
	dfs(liste, nodo, visitati_2)
	componente = []
	for nodo in range(n):
		if visitati_1[nodo] == 1 and visitati2[nodo] == 1:
			componente.append(nodo)
	return componente
```