---
updated_at: 2026-06-26T20:20:21.756+02:00
---
Rilevare cicli in [[grafo|grafi]] orientati è un problema fondamentale; ad esempio, nel contesto delle dipendenze, un ciclo indica una dipendenza circolare, che è un'incoerenza logica.

Si potrebbe pensare che la strategia più semplice da implementare sia una [[DFS|DFS]] che si ferma appena si imbatte in un arco che punta a un nodo già visitato, ma questa strategia è errata, perché non distingue tra i tipi diversi di archi.

Ad esempio la DFS che parte da $0$ nel grafo $(0, 1), (0, 2), (1, 2)$ sarebbe un falso positivo.

La **vera** condizione per trovare un ciclo in un grafo **ORDINATO** è l'incontro di un **arco all'indietro**, cioè un arco $(u, v)$, dove $v$ è un antenato (non padre) di $u$.

Nel concreto, $v$ è un antenato di $u$ se, mentre $u$ viene visitato, $v$ è ancora in visita.

# Implementazione con [[implementazioni dei grafi|liste di adiacenza]]

L'[[algoritmo]] usa l'[[array]] *visitati*, a valori:

- 0: il nodo corrispondente all'indice non è stato visitato,
- 1: il nodo corrispondente all'indice è in visita,
- 2: il nodo è stato visitato.

``` python
def ha_cicli(liste):
	n = len(liste)
	visitati = [0] * n
	for nodo in range(n):
		if visitati[nodo] == 0:
			if dfs(nodo, liste, visitati):
				return True
	return False

def dfs(nodo, liste, visitati):
	visitati[nodo] = 1
	for vicino in liste[nodo]:
		if visitati[vicino] == 0:
			if dfs(vicino, liste, visitati):
				return True
		elif visitati[vicino] == 1:
		# il nodo e un suo vicino sono entrambi in visita contemporaneamente -> c'è un arco all'indietro -> c'è un ciclo
			return True
	visitati[nodo] = 2
	return False
```