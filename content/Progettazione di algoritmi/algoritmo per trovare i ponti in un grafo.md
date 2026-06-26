---
updated_at: 2026-06-26T17:43:03.647+02:00
---
*Si veda la [[grafo#^042a02|definizione di ponte]]*.

# Ricerca esaustiva in $O(m(n+m))$

Per ogni arco $(u, v)$ del [[grafo]] si esegue una [[DFS|DFS]] da $u$ escludendo l'arco $(u, v)$. Se $v$
 non viene raggiunto, l'arco è un ponte.

# Ricerca efficiente in $O(n+m)$ con l'algoritmo di Tarjan

Si basa sulla relazione tra i ponti e l'[[albero]] DFS: gli archi appartenenti a cicli non possono essere ponti, quindi **un arco $(u, v)$ è un ponte se fa parte dell'albero DFS e non è coperto da alcun arco non appartenente all'albero.**

Per implementare ciò si memorizzano due valori per ogni nodo $u$:

- **disc**: il tempo di scoperta (prima visita) del nodo,
- **low**: il tempo di scoperta del più antico antenato di $u$ nell'albero DFS che è raggiungibile partendo da $u$ e scendendo lungo zero o più archi dell'albero DFS, per poi usare al più un arco all'indietro.

Se un arco $(u, v)$ dell'albero ha `low[v] > disc[u]`, allora è un ponte, perché usando gli archi dell'albero DFS non esiste un cammino alternativo dal sottoalbero di $v$ a un antenato di $u$.

``` python
def cerca_ponti(liste):
	disc = [-1] * n
	low = [-1] * n
	ponti = []
	time = [0] # il tempo è passato alla funzione ricorsiva come una lista singleton per rendere il valore mutabile e persistente tra le chiamate ricorsive
	dfs_ponti(0, liste, disc, low, -1, time, ponti)
	return ponti

def dfs_ponti(nodo, liste, disc, low, padre, time, ponti):
	# scoperta del nodo
	disc[nodo] = low[nodo] = time[0]  
	time[0] += 1
	for vicino in liste[nodo]:
		if vicino == padre:
			continue
		if disc[vicino] != -1: # il vicino è stato scoperto prima del nodo corrente
			# arco all'indietro
			low[nodo] = min(low[nodo], disc[vicino])
		else:
			dfs_ponti(vicino, liste, disc, low, nodo, time, ponti):
			# controllo del ponte dopo la DFS del figlio
			if low[vicino] > disc[nodo]:
				ponti.append((nodo, vicino))
			low[nodo] = min(low[nodo], low[vicino])
```