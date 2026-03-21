---
updated_at: 2026-03-17T17:56:10.089+01:00
---
> Dimostrare che in un DAG è sempre presente un nodo senza archi entranti.

Supponiamo per assurdo che tutti i nodi abbiano almeno un arco entrante.

Prendendo i nodi man mano, l'ultimo nodo preso deve avere un arco entrante e gli unici archi entranti possibili vengono dai nodi scelti prima. Si arriva all'assurdo.

---

> Contare quanti sono gli archi diretti che posso aggiungere a un DAG di $n$ nodi e $m$ archi senza aggiungere cicli.

$u_{0} < u_{1} < \ldots < u_{n}$

posso aggiungere $u_{i} \to u_{j}$ a patto che $i < j$.

$$
\frac{n(n-1)}{2} - m
$$

---

> $G$ è parzialmente orientato, cioè $G = (V, E_{0} \cup E_{N})$, con $u \to v \in E_{0}$ (archi orientati) e $(u, v) \in E_{N}$ (archi non orientati)

- dimostrare che se $G_{0} = (V, E_{0})$ è un DAG è sempre possibile orientare gli archi $E_{N}$ in modo che il grafo rimanga un DAG.

``` python
def orienta(n, E0, En):
	T = topologicalSort(n, E0)
	O = ordine_su_lista(T)
	forall (u, v) in En:
		if O[u] < O[v]:
			E = E \cup {u \to v}
		else:
			E = E \cup {v \to u}

def ordine_su_lista(T):
	O = [None for n in T]
	p = 0
	while T:
		u = T.pop()
		O[u] = p
		p = p+1
	return 0
```