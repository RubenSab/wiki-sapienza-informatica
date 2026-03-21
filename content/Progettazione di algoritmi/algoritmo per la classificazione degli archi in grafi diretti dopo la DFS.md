---
updated_at: 2026-03-13T17:14:12.653+01:00
---
L'[[albero]] [[DFS|DFS]] può essere usato come uno strumento per categorizzare i nodi in 4 tipologie. Ciò è utile per rilevare proprietà come [[algoritmo per il rilevamento dei cicli in grafi orientati|la presenza di cicli]].

Un arco diretto $(u, v)$ può essere un:

- **arco dell'albero**: se fa parte dell'albero DFS ($v$ è il **padre** di $u$).
- **arco all'indietro**: se $v$ è l'**antenato** di $u$ nell'albero DFS.
- **arco in avanti**: se $v$ è il **discendente** di $u$ nell'albero DFS.
- **arco di attraversamento**: se $v$ non è **né antenato né discendente** di $u$.

L'[[algoritmo]] usa due [[lista di Python|liste]]:

- *visitati*, a valori:
	- 0: il nodo corrispondente all'indice non è stato visitato,
	- 1: il nodo corrispondente all'indice è in visita,
	- 2: il nodo è stato visitato.

- *tempo_visita*: il momento in cui il nodo all'indice corrispondente è stato visitato per la prima volta.

Questi due valori insieme possono assegnare a ogni arco $(u, v)$ una delle quattro categorie:

- **arco dell'albero**: `visitati[v] == 0`
- **arco all'indietro**: `visitati[v] == 1`
- **arco in avanti**: `visitati[v] == 2 and tempo_visita[u] < tempo_visita[v]`
- **arco di attraversamento**: `visitati[v] == 2 and tempo_visita[u] > tempo_visita[v]`

L'algoritmo restituisce una lista dove:

- `lista[0]` è il numero di archi dell'albero
- `lista[1]` è il numero di archi all'indietro
- `lista[2]` è il numero di archi in avanti
- `lista[3]` è il numero di archi di attraversamento

L'algoritmo ha [[complessità temporale]] lineare.

# Implementazione con [[implementazioni dei grafi|liste di adiacenza]]

``` python
def conta_tipologie(liste):
	n = len(liste)
	visitati = [0] * n
	tempo_visita = [-1] * n
	tempo = [0] # lista singleton per renderlo persistente tra le chiamate ricorsive
	lista = [0, 0, 0, 0]
	for nodo in range(n):
		if visitati[i] == 0:
			dfs(nodo, liste, visitati, tempo_visita, tempo, lista)
	return lista

def dfs(nodo, liste, visitati, tempo_visita, tempo, lista):
	visitati[nodo] = 1
	tempo_visita[nodo] = tempo[0]
	tempo[0] += 1
	for vicino in liste[nodo]:
		if visitati[vicino] == 0:
			lista[0] += 1
			dfs(vicino, liste, visitati, tempo_visita, tempo, lista)
		elif visitati[vicino] == 1:
			lista[1] += 1
		else:
			if tempo_visita[nodo] < tempo_visita[vicino]:
				lista[2] += 1
			else:
				lista[3] += 1
	visitati[nodo] = 2
```